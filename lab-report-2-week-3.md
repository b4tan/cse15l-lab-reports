
# Lab Report 2

## Search Engine



	class Handler implements URLHandler {
	    // The one bit of state on the server: a number that will be manipulated by
	    // various requests.
	    ArrayList<String> dictionary = new ArrayList<>();
	    ArrayList<String> temp = new ArrayList<>();
	    public String handleRequest(URI url) {
		temp.clear();
		if (url.getPath().equals("/")) {
		    return String.format("Ask me anything! Type in what you're looking for in the URL space(?s=).");
		} else if (url.getPath().contains("/add")) {
		    String[] parameters = url.getQuery().split("="); 
		    if (parameters[0].equals("s")) {
			dictionary.add(parameters[1]);
			return String.format(parameters[1] + " is added to the dictionary.");
		    }
		} else if (url.getPath().contains("/search")) {
		    String[] parameters = url.getQuery().split("="); 
		    if (parameters[0].equals("s")) {
			for (int num = 0; num < dictionary.size(); num++) {
			    if (dictionary.get(num).contains(parameters[1])) {
				temp.add(dictionary.get(num));
			    }
			}
			return String.format("Here's what we found about your related search:" + temp);
		    }
		    }
		return "Alert! 404 not found.";
	    }
	}


	class SearchEngine {
	    public static void main(String[] args) throws IOException {
		if(args.length == 0){
		    System.out.println("Missing port number! Try any number between 1024 to 49151");
		    return;
		}

		int port = Integer.parseInt(args[0]);

		Server.start(port, new Handler());
	    }
	}

                  
#### The page when you first launch
			
![localhost](localhost.png)

#### Adding a bunch of stuff to the dictionary..

![apple](apple.png)          
![pineapple](pineapple.png)        
![orange](orange.png)         

The algorithm running here is in the else if condtional "else if (url.getPath().contains("/add"))". Since I made the algorithm to add String after the '=' operator, we can just type anything after the '=' (localhost:4235/add?s=) operator and the algorithm will save it in our arraylist. The way this works is by splitting the path before and after '='. Anything after '=' is considered parameter[1] and will be added to the arraylist. Aside that, my algorithm also notifies the user if they have added a word. For example here, when I type in "apple", the String "apple" will be saved in the arraylist dictionary and the algorithm will notify the user that "apple" has been added to the arraylist dictionary.

#### Searching for the added terms in the dictionary...
			
![applepineapple](apple_pineapple.png)              
![a](a.png)       

The algorithm running here is in the else if conditional "else if (url.getPath().contains("/search"))". Same as before, the String being searched in the arraylist is parameters[1], which is the string after the '=' operator. After that, I made a dummy arraylist to store the elements that contains the String being searched. For example, when I search "apple", the algorithm goes through a for-loop that looks through all of the elements inside of the arraylist dictionary. If the String being searched is contained in one of the elements of the arraylist dictionary, then that element will be stored in my dummy arraylist temp. At the end of the for-loop iteration, the dummy arraylist filled with the elements that contain the String being searched will be printed.

## Debugging

#### ArrayExamples

The actual code         
Ignore the method "reverseInPlace" and focus on "reversed.

	  // Changes the input array to be in reversed order
	  static void reverseInPlace(int[] arr) {
	    for(int i = 0; i < arr.length; i += 1) {
	      arr[i] = arr[arr.length - i - 1];
	    }
	  }

	  // Returns a *new* array with all the elements of the input array in reversed
	  // order
	  static int[] reversed(int[] arr) {
	    int[] newArray = new int[arr.length];
	    for(int i = 0; i < arr.length; i += 1) {
	      arr[i] = newArray[arr.length - i - 1];
	    }
	    return arr;
	  }
My test values:

![arr](array.png)  

The error:

![arr_errors](array_errors.png)

Here, we can see that I tested the method reversed using testReversed1 and the array [0 , 1, 2] as input. I expect that testReversed1 should return [2, 1, 0] based on how the code is described to do. However, this is not the case as the algorithm is bugged and this is shown in the error. The error tells us that instead of starting with 2, the first element of the array is still 1. This is becasue the method "reversed" returns the old array or the array being used as input. The method should have returned newArray (input array being reversed).

The fix required:

![arr_fixed](array_fixed.png)  



#### LinkedList

The actual code:

    public void append(int value) {
        if(this.root == null) {
            this.root = new Node(value, null);
            return;
        }
        // If it's just one element, add if after that one
        Node n = this.root;
        if(n.next == null) {
            n.next = new Node(value, null);
            return;
        }
        // Otherwise, loop until the end and add at the end with a null
        while(n.next != null) {
            n = n.next;
            n.next = new Node(value, null);
        }
    }

My test values:

![linked](linked1.png)      

The error:

![linked_errors](linked_error.png) 

Here, we see that after testing the append method using 3 different values, JUnit tells us that the testing the append method takes too much time and causes the OutOfMemory error, which is likely caused by the loop running infinitely. The error here is caused in the last while loop "while(n.next != null)". There, "n.next = new Node(value, null);" should be out of the scope because if it is inside the scope of the while loop, the end of the list will never be null and the loop will run indefinitely.


The fix required:

![linked_fixed](linked_fixed.png)      




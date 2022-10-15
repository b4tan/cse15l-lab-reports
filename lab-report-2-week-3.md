
#Lab Report 2

## Search Engine

'''
import java.io.IOException;
import java.net.URI;
import java.util.*;

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
'''
                  
#### The page when you first launch
			
![localhost](localhost.png)

Adding a bunch of stuff to the dictionary..

![apple](apple.png)          
![pineapple](pineapple.png)        
![orange](orange.png)         

Searching for the added terms in the dictionary...
			
![applepineapple](apple_pineapple.png)              
![a](a.png)       
                  

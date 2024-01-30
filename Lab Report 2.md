# Lab Report 2

## code block for ChatServer
```
class ChatHandler implements URLHandler {
    private List<String> chatHist = new ArrayList<>();
    public String handleRequest(URI url) {
        
        if (url.getPath().equals("/add-message")) {
            String[] parameters = url.getQuery().split("&");
            String message = "";
            String user = "";
            for(String parameter : parameters){
                String[] tempArr = parameter.split("=");
                if(tempArr[0].equals("s")){
                    message = tempArr[1];
                } if(tempArr[0].equals("user")){
                    user = tempArr[1];
                }
            }
            if(!message.isEmpty() && !user.isEmpty()) {
                String messageFormatTemp = user + ": " + message;
                messages.add(messageFormatTemp);
                return String.join("\n" , messages);
            } else{
                return "Invalid input";
            }    
        } else{
            return "404 Not Found!";
        }    
    }
  ```
### screenshots using /add-message

### (Screenshot 1) Which methods in your code are called?
In this screenshot, the `String handleRequest` method is called. Within this method, the `url.getQuery().split()`, `parameter.split()`, `message.isEmpty()`, `user.isEmpty`, `chatHist.add` , `String.join` are all called.

### (Screenshot 1) What are the relevant arguments to those methods, and the values of any relevant fields of the class?

The relevant arguemtns to these methods are in this case the url for the `handleRequest` method. With this, it passes in to check the path and if the path equals `add-message` then it will go on to check more items. When doing this, an arrary of the parameters is created with an important argument of "&", seperating them into both s=<string> and user=<string>.This process happens again this time splitting the parameters further in the for loop to split the paramters with the argument "=". After this, the values are added to an array and are then assigned to their corresponding fields, message and user. 

### (Screenshot 1) How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.

From this specific request, the values of the `message` field changed from "" to `Hello` and the `user` field changed from "" to `jpolitz`. Alongside this, the `chatHist` arrayList was changed from being to holding this `jpolitz: Hello`

###(Screenshot 2) Which methods in your code are called?
The same methods I mentioned earlier called with this screenshot as well. `String handleRequest`, `url.getQuery().split()`, `parameter.split()`, `message.isEmpty()`, `user.isEmpty`, `chatHist.add` , `String.join`

### (Screenshot 2) What are the relevant arguments to those methods, and the values of any relevant fields of the class?

In this case the relevant arguments to this method are the url for the handleRequest method. With this the `add-message` path is checked but since this time it is different, the resulting final values of the `message` to equal `Hi there` and `user` to equal `Sur` field will be different. However, the program will follow the same format as before going through the first split("&") with the important argument being "&" and the second one inside the for loop with the important argument being "=". Now when adding to the chatHist arrayList, it will add a second entry being `Hi+there: Sur`

### (Screenshot 2) How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.

The values of the relevant fields of the class are changed with the `message` field being changed from "" to `Hi there` and the `user` being changed from "" to `Sur`. Also, the arrayList will now Look like `["jpolitz: Hello","Hi+there: Sur"]`

### Private key
![image](https://github.com/sur-shah/cse15l-lab-reports/assets/156368641/45f96e34-003a-4249-91e5-0a33ce7a502c)

### Public key
![image](https://github.com/sur-shah/cse15l-lab-reports/assets/156368641/18712236-f0af-434c-bcd3-2b88047c3cec)


### log in without password:
![image](https://github.com/sur-shah/cse15l-lab-reports/assets/156368641/501b32f4-f3a0-4088-b0c4-371dfe12ea0a)



### What I learned from lab
Between lab 2 and lab 3, I did not know how to build a server beforehand. I found it very cool that I was able to code my own server and see it launch very fast in front of my eyes. Also, being able to customize paths and their behavior was something I was never exposed to before.




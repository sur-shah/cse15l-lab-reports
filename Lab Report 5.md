# Lab report 5

## Debugging scenario

### 1: Original post from student:
Hi, I was wondering why even after inputting the path arguments according to the instructions, I am recieving a blank screen. I should be seeing a message with "Sur: hello" correct?
![image](https://github.com/sur-shah/cse15l-lab-reports/assets/156368641/97d0dee8-5fdc-4d54-a038-3c15ac102ea0)

### 2: TA Response on edstem:
Hello, did you check that within your ChatServer.java file, that the arguments within the if statements are correct? For example: ensure that in an if statement like this `else if (url.getPath().equals("/save"))` that everything is spelled correctly. Additionally, ensure that your string splitting is proper. Another example would be to ensure that ` String[] shouldBeUser = params[0].split("=");` that the `=` character is not something else like `:`

### 3: Student fix
**Website Output**
![image](https://github.com/sur-shah/cse15l-lab-reports/assets/156368641/925a7775-84b6-4081-9579-25731d8ff3ca)

**Terminal Output**
![image](https://github.com/sur-shah/cse15l-lab-reports/assets/156368641/a71bd86a-112f-477b-9fb5-fb9ca5bb2606)

After looking at what the TA had replied to my post, I had found spelling errors within my ChatServer.java file. 
**Code with problems**
```
if (url.getPath().equals("/chet")) {
      String[] params = url.getQuery().split("&");
      String[] shouldBeUser = params[0].split(":");
      String[] shouldBeMessage = params[1].split("=");
      if (shouldBeUser[0].equals("user") && shouldBeMessage[0].equals("message")) {
        String user = shouldBeUser[1];
        String message = shouldBeMessage[1];
        this.chatHistory += user + ": " + message + "\n\n";
        return this.chatHistory;
      } else {
        return "Invalid parameters: " + String.join("&", params);
      }
    }
```
**Code with fixes**
```
if (url.getPath().equals("/chat")) {
      String[] params = url.getQuery().split("&");
      String[] shouldBeUser = params[0].split("=");
      String[] shouldBeMessage = params[1].split("=");
      if (shouldBeUser[0].equals("user") && shouldBeMessage[0].equals("message")) {
        String user = shouldBeUser[1];
        String message = shouldBeMessage[1];
        this.chatHistory += user + ": " + message + "\n\n";
        return this.chatHistory;
      } else {
        return "Invalid parameters: " + String.join("&", params);
      }
    }
```
This was my original code that I had. As it is visible, in the if statement, there is a spelling error with `/chet` when it is supposed to be `/chat` Doing this made it so that I was unable to run the website with the expected output and input of `http://localhost:4000/chat?user=sur&message=hello`
Another minor error was in the `shouldBeUser` varialbe in which it states `params[0].split(":");` when in reality it should be `params[0].split("=");`
This made it so that it would invoke invalid parameters as it would not properly split the string in the path. 



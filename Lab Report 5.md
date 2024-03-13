# Lab report 5

## Debugging scenario

### 1: Original post from student:
![image](https://github.com/sur-shah/cse15l-lab-reports/assets/156368641/1e7ed078-71a6-4031-9910-6d9caa63d929)

Hello, I was wondering why that whenever I type in my path with incorrect paramaters, it still works as expected? Like in this case, I did not input `user` before `sur` and instead put `324ser =` and it still worked. Any help would be appreciated. Thank you!


### 2: TA Response on edstem:
Hi, I know that I do not have access to your code, but in your `/chat` if statement, did you ensure that the parameters are being checked? By this I mean did you check that the parameters at those positions should be `user` and `message`? Please try this. Hope it helps!
### 3: Student fix
![image](https://github.com/sur-shah/cse15l-lab-reports/assets/156368641/66d3e40f-84f5-40ae-b0c5-d024a123c0af)

It seems that the bug has to do with the `/chat` query in the `ChatServer.java` file. I had to edit and create an if statement to ensure that the parameters at position 0 were checked to be proper. With this, it makes sure that within the path, `user` and `message` are the only arguments allowed for the messages and users. Without this, it allows anything before the `=` sign to work. So using a command `curl "http://localHost:4000/chat?'1412=sur&,qwenm1=hello"` would print a message `sur: hello` in the output, which is not correct.

### 4: Contents:
**File directory**
```
 -Chat-Server-Pro-Main
      -chatserver
      -lib
      -Other files
      -ChatServer.java
```
      
The file that needed to be fixed was the `ChatServer.java` file

**Code with problems**
```
import java.io.IOException;
import java.net.URI;
import java.io.BufferedWriter;
import java.io.File;
import java.io.FileWriter;

class ChatHandler implements URLHandler {
  String chatHistory = "";

  public String handleRequest(URI url) {

    // expect /chat?user=<name>&message=<string>
    if (url.getPath().equals("/chat")) {
      String[] params = url.getQuery().split("&");
      String[] shouldBeUser = params[0].split("=");
      String[] shouldBeMessage = params[1].split("=");
      String user = shouldBeUser[1];
      String message = shouldBeMessage[1];
      this.chatHistory += user + ": " + message + "\n\n";
      return this.chatHistory;
  } 
    }
    // expect /retrieve-history?file=<name>
    else if (url.getPath().equals("/retrieve-history")) {
      String[] params = url.getQuery().split("&");
      String[] shouldBeFile = params[0].split("=");
      if (shouldBeFile[0].equals("file")) {
        String fileName = shouldBeFile[1];
        // String fileName = shouldBeFileName[0]; // bug4: should be shouldBeFile[1]
        ChatHistoryReader reader = new ChatHistoryReader();
        try {
          String[] contents = reader.readFileAsArray("chathistory/" + fileName);
          for (String line : contents) {
            this.chatHistory += line + "\n\n";
          }
        } catch (IOException e) {
          System.err.println("Error reading file: " + e.getMessage());
        }
      }
      return this.chatHistory;
    }
    // expect /save?name=<name>
    else if (url.getPath().equals("/save")) {
      String[] params = url.getQuery().split("&");
      String[] shouldBeFileName = params[0].split("=");
      if (shouldBeFileName[0].equals("name")) {
        File directory = new File("chathistory");
        File file = new File(directory, shouldBeFileName[1]);

        try (BufferedWriter writer = new BufferedWriter(new FileWriter(file))) {
          writer.write(this.chatHistory);
          return "Data written to " + shouldBeFileName[1] + "in 'chat-history' folder.";
        } catch (IOException e) {
          e.printStackTrace();
          return "Error: Something wrong happen during file save, check StackTrace";
        }
      }
    }

    return this.chatHistory;
  }
}

class ChatServer {
  public static void main(String[] args) throws IOException {
    int port = Integer.parseInt(args[0]);
    Server.start(port, new ChatHandler());
  }
}
```
**Code with fixes**
```
import java.io.IOException;
import java.net.URI;
import java.io.BufferedWriter;
import java.io.File;
import java.io.FileWriter;

class ChatHandler implements URLHandler {
  String chatHistory = "";

  public String handleRequest(URI url) {

    // expect /chat?user=<name>&message=<string>
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
    // expect /retrieve-history?file=<name>
    else if (url.getPath().equals("/retrieve-history")) {
      String[] params = url.getQuery().split("&");
      String[] shouldBeFile = params[0].split("=");
      if (shouldBeFile[0].equals("file")) {
        String fileName = shouldBeFile[1];
        // String fileName = shouldBeFileName[0]; // bug4: should be shouldBeFile[1]
        ChatHistoryReader reader = new ChatHistoryReader();
        try {
          String[] contents = reader.readFileAsArray("chathistory/" + fileName);
          for (String line : contents) {
            this.chatHistory += line + "\n\n";
          }
        } catch (IOException e) {
          System.err.println("Error reading file: " + e.getMessage());
        }
      }
      return this.chatHistory;
    }
    // expect /save?name=<name>
    else if (url.getPath().equals("/save")) {
      String[] params = url.getQuery().split("&");
      String[] shouldBeFileName = params[0].split("=");
      if (shouldBeFileName[0].equals("name")) {
        File directory = new File("chathistory");
        File file = new File(directory, shouldBeFileName[1]);

        try (BufferedWriter writer = new BufferedWriter(new FileWriter(file))) {
          writer.write(this.chatHistory);
          return "Data written to " + shouldBeFileName[1] + "in 'chat-history' folder.";
        } catch (IOException e) {
          e.printStackTrace();
          return "Error: Something wrong happen during file save, check StackTrace";
        }
      }
    }

    return this.chatHistory;
  }
}

class ChatServer {
  public static void main(String[] args) throws IOException {
    int port = Integer.parseInt(args[0]);
    Server.start(port, new ChatHandler());
  }
}
```
**Command line argument to test the bugs**
In a seperate terminal:
`curl "http://localhost:4000/chat?324ser=sur&message=hello"`
**Explanation of edits needed**

After looking at the TA feedback, I had found that it was important to implement an if statmenet checking if the string of the `shouldBeUser` array, at index 0 (because of the split) is equal to to the string `user`. A similar approach is attached on for the `shouldBeMessage` array. By adding the if statement `if (shouldBeUser[0].equals("user") && shouldBeMessage[0].equals("message"))`, it checks these things and if the input does not match this, then it will print that the parameters being used are invalid. I created a bash script to compile and run the server. Here is how I did that:
![image](https://github.com/sur-shah/cse15l-lab-reports/assets/156368641/27ba6e6e-a0c2-4e50-bbf5-76f9da95c4e9)

## Reflection:

One thing that I never thought I would be able to do, that I learned in my lab experience within the second half of the quarter was creating an autograder. I was always really confused on how exactly this was achieved, but actually coding a `grade.sh` script was truly interesting to me and was one of my favorite things throughout the quarter.








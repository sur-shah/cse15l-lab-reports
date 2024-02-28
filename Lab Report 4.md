# Lab Report 4
## Step 4:
![image](https://github.com/sur-shah/cse15l-lab-reports/assets/156368641/6e42d60f-04c4-4fb7-9c3e-2e48b3e60c76)
Keys pressed: ```ssh sushah@ieng6.ucsd.edu<enter>```. I used these keystokes to ssh into ieng6 using my ucsd email.

## Step 5:
![image](https://github.com/sur-shah/cse15l-lab-reports/assets/156368641/05afff3c-d743-40e6-9f72-66d123dedca8)
Keys pressed: ```git clone https://github.com/sur-shah/lab7.git<enter>```. These were the keys I pressed to clone the github repository so that we can edit the files within it.

## Step 6:
<img width="594" alt="Screenshot 2024-02-26 at 1 01 04 AM" src="https://github.com/sur-shah/cse15l-lab-reports/assets/156368641/d6f73072-a355-4b5b-9611-b6c4548fd461">

Keys pressed: cd lab7 ```<enter>, ls, <enter> ,<up><up><up><up><up><up><up><up><up><up><up><up><up><up><up><up><up><up><up><enter>,<up><up><up><up><up><up><up><up><up><up><up><up><up><up><up><up><up><up><up><enter> ``` I changed the current working directory to be into the new lab7 directory we just created with our
git clone command. I then checked the contents of this new directory with the ls command. I then pressed up 19 times and `enter` to retrieve and run the ```javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java```. This compiled all of the files ending in `.java`. After this, I pressed up another 19 and then `enter` after times to retrieve and run the ```java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests``` which ended up running all of the tests and providing the given output above.

## Step 7:
![image](https://github.com/sur-shah/cse15l-lab-reports/assets/156368641/ce17a44e-b0d3-4bd3-b0e5-7c7b8704a5ee)

Keys pressed: ``` vim ListExamples.java <enter>, 43 <enter>, e r2 :wq! <enter>``` I pressed ```vim ListExamples.java``` I pressed `vim ListExamples.java <enter>` to open the file in vim so that I can edit it. I then pressed `43 <enter>` to go to line 43 of the document. Then, pressing `e` brings the cursor to the end of the word. Lastly pressing `r2 :wq! <enter>` replaces the `1` with `2` and the `:wq!` saves the changes and lastly pressing enter exits the document.

## Step 8:
![image](https://github.com/sur-shah/cse15l-lab-reports/assets/156368641/8ccdccef-bbe2-401d-b63b-2b61150a1447)
Keys Pressed: ```<up><up><up><up><up><up><up> <enter>, <up><up><up><up><up><up><up> <enter> ``` I pressed up 7 times to access the ```javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java```. Then I pressed `<enter>` to run the command which will recompile all the files within the directory ending in `.java`. I then pressed `<up>` another 7 times to access the ```java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests``` command. Then I pressed `<enter>` to run it. By doing this, it ran the tests, and in the picture it is clear to see that all tests passed.

## Step 9:
![image](https://github.com/sur-shah/cse15l-lab-reports/assets/156368641/bc1bcb9a-c483-4edc-a9cf-318283106b2a)
Keys pressed: ```git add ListExamples.java <enter>, git commit -m "ListExamples.java updated" <enter>, git push```. Here, the changes made to the `ListExamples.java` file were added, and then they were committed. They were committed with the message seen above "ListExamples.java updated". I then pushed it to update the repository.



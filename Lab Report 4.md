# Lab Report 4
## Step 4:
![image](https://github.com/sur-shah/cse15l-lab-reports/assets/156368641/6e42d60f-04c4-4fb7-9c3e-2e48b3e60c76)
Keys pressed: ```ssh sushah@ieng6.ucsd.edu<enter>```. I used these keystokes to ssh into ieng6 using my ucsd email.

## Step 5:
![image](https://github.com/sur-shah/cse15l-lab-reports/assets/156368641/76a428bc-722a-4fb1-8756-a3e60db0cd9c)

Keys pressed: ```git clone git@github.com:sur-shah/lab7.git lab7ssh <enter>```. These were the keys I pressed to clone the github repository into a directory that I named as ```lab7ssh``` so that I know that I am accessing the files from the ssh repository


## Step 6:
<img width="594" alt="Screenshot 2024-02-26 at 1 01 04 AM" src="https://github.com/sur-shah/cse15l-lab-reports/assets/156368641/d6f73072-a355-4b5b-9611-b6c4548fd461">

Keys pressed: ```cd lab7ssh <enter``` ```vim test.sh``` ```:q!``` ```bash test.sh <enter>``` I changed the current working directory to be into the new lab7 directory we just created with our
git clone command. I then checked the contents of this new directory with the ls command. Then, I saw that there was a test.sh script, and utilized vim to open and view the contents. After this, I saw that it contained the script to compile and run the test needed. So then I quit out of the vim editor and ran the script to get the desired test failure output given above.

## Step 7:
![image](https://github.com/sur-shah/cse15l-lab-reports/assets/156368641/ce17a44e-b0d3-4bd3-b0e5-7c7b8704a5ee)

Keys pressed: ``` vim ListExamples.java <enter>, :44 <enter>, e r2 :wq! <enter>``` I pressed ```vim ListExamples.java``` I pressed `vim ListExamples.java <enter>` to open the file in vim so that I can edit it. I then pressed `:44 <enter>` to go to line 44 of the document. By using the ```:44 <enter>``` command instead of the ```43 <enter>``` one, it took the cursor directly to line 44 instead of adding 43 onto the current line I was on (in this case 1). Then, pressing `e` brings the cursor to the end of the word. Lastly pressing `r2 :wq! <enter>` replaces the `1` with `2` and the `:wq!` saves the changes and lastly pressing enter exits the document.

## Step 8:
![image](https://github.com/sur-shah/cse15l-lab-reports/assets/156368641/8ccdccef-bbe2-401d-b63b-2b61150a1447)
Keys Pressed: ```bash test.sh <enter>``` I reran the bash script to run the tests needed. This gave the output above displaying that the tests passed after the fixes in VIM. Instead of doing ```bash test.sh <enter>``` I could have also done ```<up> <up> enter``` to access the same ```bash test.sh``` command. By doing this, it ran the tests, and in the picture it is clear to see that all tests passed.

## Step 9:
![image](https://github.com/sur-shah/cse15l-lab-reports/assets/156368641/bc1bcb9a-c483-4edc-a9cf-318283106b2a)
Keys pressed: ```git add ListExamples.java <enter>, git commit -m "ListExamples.java updated" <enter>, git push <enter>```. Here, the changes made to the `ListExamples.java` file were added, and then they were committed. They were committed with the message seen above "ListExamples.java updated". I then pushed it to update the remote repository on GitHub.



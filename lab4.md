Step 4:
![image](https://github.com/joasheng/cse15l-lab-reports/assets/125727125/beeb6fbd-915e-47ad-8a76-ed8e01276a0d)
```
ssh cs15lfa23rw@ieng6.ucsd.edu <enter>  
(my password) <enter>
```
This terminal command accesses my ieng6 machine remotely.

Step 5: 
![image](https://github.com/joasheng/cse15l-lab-reports/assets/125727125/55d2fbd0-3a15-423f-96d1-e0073b20d1a4)
```
git clone git@github.com:joasheng/lab7.git <enter>
```
I cloned my repository by finding my ssh URL from my fork, and then using it with the git clone command. 

Step 6:
![image](https://github.com/joasheng/cse15l-lab-reports/assets/125727125/dc52042d-17c8-4096-9b26-afb980c9fd6b)
```
cd lab7 <enter>  
javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java <enter>  
java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests <enter>
```
First I switched into the lab7 directory, and then I compiled all the java files in the directory and ran ListExamplesTests using the javac and java commands. To compile and run them with JUnit, I found commands from an earlier lab and added it on. 

Step 7:
![image](https://github.com/joasheng/cse15l-lab-reports/assets/125727125/549e25d8-279d-492a-8edf-e8ade5774c76)
```
vim ListExamples.java <enter>
<downArrow> <downArrow> <downArrow> <downArrow> <downArrow> <e> 2 <delete>
<esc> :wq <enter>
```
First I used vim followed by the file to enter vim from the command line. When I opened the editor, my cursor was 5 lines above where it was supposed to be, so I just pressed the down arrow key 5 times to get to the right line, and then pressed E to go to the end of the word (which was index1). I then switched to insert mode by pressing I and switched the 1 to a 2. Finally, I pressed Escape to leave Insert Mode and then typed in :wq to save and quit.

Step 8:
![image](https://github.com/joasheng/cse15l-lab-reports/assets/125727125/1189afe9-3ea4-4655-b2c7-5cb9217d8e5d)
```
<up> <up> <up> <enter>  
<up> <up> <up> <up> <enter>
```
I used the up buttons to access my previous java and javac commands, and ran them.

Step 9:
![image](https://github.com/joasheng/cse15l-lab-reports/assets/125727125/78c47f2d-f4de-47bc-9480-77dcd4f6e5a9)
```
git add ListExamples.java <enter>  
git commit -m "Fixed ListExamples Bug" <enter>  
git push <enter>
```
I used the git add, commit, and push commands to add my changes to the repository, and I left a message of "Fixed ListExamples Bug" to explain what changes I made.



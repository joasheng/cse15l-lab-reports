Part 1:

Code:

![image](https://github.com/joasheng/cse15l-lab-reports/assets/125727125/a3324e8c-2369-4f67-8aab-bd1986a6aac0)
![image](https://github.com/joasheng/cse15l-lab-reports/assets/125727125/eca7663a-8220-49e8-a163-b86dea5423c4)

Add-message calls:

![image](https://github.com/joasheng/cse15l-lab-reports/assets/125727125/75b220b1-7e91-451c-b4c6-c3a3c0b39932)
#1. Upon the server starting and before the URL request was sent, a ServerHttpHandler was created, which manages all the URL requests. After the request is received, the method "handle" is run, which tries to run the command specified by the URL request. To do that, the method handleRequest, part of the Handler class in StringServer.java, is run. This method takes in a URL, and checks the path of it. Here, /add-message?s=banana is the path, and the code now checks the query of the path (the text after the ?). It splits the query into two parameters, and updates the values of "displayText" and "counter", which are variables used within the Handler class. Finally, displayText is returned, which is displayed on the screen by the "handle" method in Server.java. From StringServer, the variables displayText, counter, and parameters are modified, with displayText being updated to show the correct String, counter being incremented as a new String was added, and parameters being created to process the data from query. 

![image](https://github.com/joasheng/cse15l-lab-reports/assets/125727125/7a9a1c56-2eeb-45a7-82e0-82861f2783e2)

#2. The same starting methods are run as the first screenshot, all the way to the "handleRequest" method. However, since this query is invalid (there is no s= before the string), none of the variables are updated and a 404 error message is returned instead. This error message is processed once again like the first one. Here, no fields were changed, since the URL request was not recognized. 

Part 2:

Private path: ![image](https://github.com/joasheng/cse15l-lab-reports/assets/125727125/32a0facc-991f-4591-ad3c-f33e00f1fd20)

Here, you can see that the path is C:\Users\jiash\.ssh\id_rsa, as when I run the command it returns the directory the key is in and its position within the directory, along with some other details about the file. This additional information is due to the fact that I am on a windows PowerShell terminal, which does not display only the filename when using ls (unlike linux terminals).  

Public path: ![image](https://github.com/joasheng/cse15l-lab-reports/assets/125727125/5b514d58-117f-4546-9e5c-b540f642e49f)
Here, I am in the .ssh directory within my ieng6 account. Using ls /home/linux/ieng6/cs15lfa23/cs15lfa23rw/.ssh/authorized_keys, I can show that the file does in fact exist within the directory, as it returns the filepath back to me.

Logging in without ssh:
![image](https://github.com/joasheng/cse15l-lab-reports/assets/125727125/b7bc97b4-6371-4c4d-b9c9-b21285126a4f)

Part 3:
Honestly, I had not encountered any of the information from these labs prior to doing them; everything has been new to me. If I had to pick one interesting thing I learned, it was how to deploy a local web server just by using Java and a terminal; I had no idea it was that easy to get something online like that.

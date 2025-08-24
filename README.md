# local-authority-CTF
# Pico-CTF
web exploitation CTFs

Today i will be tackling the easy cookie monster CTF. This is my first attempt at CTFs after a very long hiatus. 
Here is what you need to know

Difficulty
------------------------------
easy
------------------------------

Type 
------------------------
web exploitation
------------------------

Description
----------------------
Can you get the flag?
Go to this website and see what you can discover
------------------------

The steps i took were the following 

1. launch the website and inspect the code. (ctrl + shift + c)


2. To get more information on what to look for i clicked the hint.
Hint: check how the password is checked
Inspected the javascript code whos function handles the password check 
<img width="688" height="573" alt="image" src="https://github.com/user-attachments/assets/d3455eab-a915-4ba9-96e9-475057e99362" />
<img width="682" height="608" alt="image" src="https://github.com/user-attachments/assets/572fc0e5-4714-41c0-8403-4031da0c4571" />
<img width="655" height="195" alt="image" src="https://github.com/user-attachments/assets/f17cf71c-966c-4510-af22-3029f3532b3a" />



3. Based on the screenshot and the hint the solution will remain in the function string and its conditions for what passes and what fails. 
Which I assume is the inside the if statement. If a string of characters is greater than or equal to 48 && if a string of characters less than or equal to 57. 
I also assume the first condition is for the username and the second is the password.



4. Let me experiment, I entered a username that has a greater than or equal to string count of 48 and a password string count of less than or equal to 57
Login failed.
After a deeper look, it looks like the fuction creates a hash and then compares the hash created from the users input and compares it to the adminForHash.value
I can take the value and reverse engineer the value to find the actual username:password. 
The value is a MD5 hash: 2196812e91c29df34f5e217cfd639881



5.  After decrypting the hash its revealed to just be "successfullogin"
<img width="1417" height="592" alt="image" src="https://github.com/user-attachments/assets/4ed12972-0f63-4492-aba0-e33cbf6f4b9c" />




   After some more inspection, I noticed that there is a hyperlink in the javascript code "secure.js". After clicking on it, I see there is a new function.
<img width="887" height="517" alt="image" src="https://github.com/user-attachments/assets/15e68fe0-9c37-491f-80f2-59218cab050e" />


6. Clearly it gives me the username and password. After putting those into the login prompt
I get the CTF
<img width="927" height="340" alt="image" src="https://github.com/user-attachments/assets/684e6562-498b-4ebc-8da5-212845bedda8" />

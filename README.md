# GuestNigga

Challenge Name:
The level is average
At first you will read the source code for the page
there is a public account with username and password `guest:guest`
let's log in..
<img src="https://raw.githubusercontent.com/CaesarEG0x01/GuestNigga/main/Screenshot%20at%202021-02-17%2023-05-47.png">

there is hidden form To change the user's password
For some similar scenarios, the attacker can modify the `username` parameter From the current username to the victim's username

There is a comment in the source code for the site
`userid` is `11` This account was Created in `Wednesday, February 17, 2021 10:15:12 PM`
and `xsrfparameter` value is `1613600112`


If you can know the time of admin account creation, you will be able to change its password
<img src="https://raw.githubusercontent.com/CaesarEG0x01/GuestNigga/main/Screenshot%20at%202021-02-17%2023-31-31.png">

after bruteforcing the directory i found this file `info.php` and 
getting 403 when access it by GET request , i will try to send HTTP POST Request with parameter `userid` and value `11`
you will get the account creation time `Wednesday, February 17, 2021 10:15:12 PM`

lets try to change userid value to `1`
you can get admin account creation time `Friday, January 10, 2020 10:15:12 PM`
<img src="https://raw.githubusercontent.com/CaesarEG0x01/GuestNigga/main/Screenshot%20at%202021-02-17%2023-56-07.png">

using https://www.epochconverter.com/ to convert from data to timestamp 
admin xsrftoken : `1578694512` 

````
   <form method="POST" action="http://127.0.0.1/ctf/welcome.php">
   <input type="hidden" name="username" value="admin">
   <input type="hidden" name="xsrftoken" value="1578694512">
   <input type="newpassword" name="newpassword" value="helloworld">
   <input type="submit">
   </form>
````
done. admin password is changed to `helloworld`

<img src="https://raw.githubusercontent.com/CaesarEG0x01/GuestNigga/main/Screenshot%20at%202021-02-18%2000-06-19.png">

Lets Login ..
<img src="https://raw.githubusercontent.com/CaesarEG0x01/GuestNigga/main/Screenshot%20at%202021-02-18%2000-08-22.png">


Flag : Flag{Ca3sarl33T0g33KS}

   

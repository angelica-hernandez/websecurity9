# Project 8 - Pentesting Live Targets

Time spent: **10** hours spent in total

> Objective: Identify vulnerabilities in three different versions of the Globitek website: blue, green, and red.

The six possible exploits are:
* Username Enumeration
* Insecure Direct Object Reference (IDOR)
* SQL Injection (SQLi)
* Cross-Site Scripting (XSS)
* Cross-Site Request Forgery (CSRF)
* Session Hijacking/Fixation

Each version of the site has been given two of the six vulnerabilities. (In other words, all six of the exploits should be assignable to one of the sites.)

## Blue

Vulnerability #1: SQL Injection (SQLi)
* GIF Walkthrough:
    <img src='' title='Blue 1' width='' alt='' />
* Description: Using SQL injection to the id attribute of each section (Blue, Green and Red), we can see from above that trying to use ``` ' OR 1=1'-- ``` in the Blue section we receive the message "Database query failed." Additionally, for the Red and Green sections the SQL injection statement redirected the screen and it cannot do any change to them.

Vulnerability #2: Session Hijacking/Fixation
  * GIF Walkthrough:
    <img src='' title='Blue 2' width='' alt='' />
  * Description: Login in to the Blue section, and once logged in change the url from ```public/... ``` and onwards to ``` public/hacktools/change_session_id.php ```. Also, from this the session ID is retreived. Essentially, I can log in in one browser and get the session ID which can be used by a past login process in another browser. This hacking method demonstrates that the session can be hijacked and user informations can be stolen.


## Green

Vulnerability #1:  Username Enumeration
 * GIF Walkthrough:
   <img src='' title='Green 1' width='' alt='' />
 * Description: As you can see from above, the GIF illustrates that when you enter in a username that exisits in the system/database along with a random password and you inspect the page the class of the span HTML attribute is ```failure```. Also, when a wrong username/ a username that isn't in the system is entered with a random password, inspect will display ```failed```. 

Vulnerability #2: Cross-Site Scripting
 * GIF Walkthrough:
   <img src='' title='Green 2' width='' alt='' />
 * Description: (Steps to recreate) In the Green section, click on ```Contact``` and enter into the form, where in the Feedback textbook write a alert script such as ```<script>alert('Connie found the XSS!')</script>```. Then login and from there, click on ```Feedback``` on the dashboard and you will encounter your Feedback lssert pop-up. 
 NOTE: From the GIF, it can be seen that other alert pop-ups are also encountered; they are feedbacks that are already in the system submitted by others, but our recent feedback input will be shown last. 

## Red

Vulnerability #1: Insecure Direct Object Reference (IDOR)
 * GIF Walkthrough:
   <img src='' title='Red 1' width='' alt='' />
 * Description: Find sales person/people that is/are not listed in the ``` Find a Salesperson``` in any of the sections. In order to achieve this, click on an exisiting salesperson and in the url set the ```id``` attribute to different id numbers such as 9, 10, 11, etc..

Vulnerability #2: Cross-Site Request Forgery (CSRF)
 * GIF Walkthrough: 
   <img src='' title='Red 2' width='' alt='' />
 * Description: In this exploit, we can see from the GIF that the user who doesn't have admin privilege can still access the website's data and change it. 

## Bonus Objective 2: Build on Objective #4 (Cross-Site Scripting)
 * GIF Walkthrough: 
   <img src='' title='bonus' width='' alt='' />
 * Description: (Steps to recreate) In the Green section, go to ```Feedback``` and fill in the form along with a redirect script write in the Feedback textbox like for instance: ```<script>document.location="https://www.facebook.com"</script>```. Then go to login and click ```Feedback``` and you will encounter Feedbacks from others and your feedback with directs you to the link you wrote in the Feedback text box. 


## Notes

Describe any challenges encountered while doing the work

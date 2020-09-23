<div align="center">

## PHP: Forms and Email


</div>

### Description

PHP, Forms, EMail, OH MY! Learn how to use all 3 of them together.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Josh Sherman](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/josh-sherman.md)
**Level**          |Intermediate
**User Rating**    |4.4 (31 globes from 7 users)
**Compatibility**  |PHP 3\.0, PHP 4\.0
**Category**       |[Validation/ Processing](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/validation-processing__8-16.md)
**World**          |[PHP](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/php.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/josh-sherman-php-forms-and-email__8-575/archive/master.zip)





### Source Code

```
<P align="justify">
So you've finished up our tutorial, PHP 101, and now you want more of the meat and potatoes of making PHP work for you. One of the easiest and most effective ways to utilize PHP is my using forms. If you haven't read PHP 101, then please go back and do so, because you may run into some problems with this tutorial and the previous will give you some more insight than this tutorial,
</p>
<P align="justify">
Forms? Yeah, those nifty little things on web pages, which collect data from you, and either email it off to someone, or throw your information in a database for future reference, or something like that. Forms are one of the easiest ways to collect data from your visitors. Either by having them sign up for a mailing list, or collecting data for research or a poll, forms are what you will need to use.
</p>
<P align="justify">
Now, I'm going on the assumption that you don't know anything about forms. If you do, you may want to skip this section and move on to more of the PHP coding aspect of this tutorial.
</p>
<P align="justify">
To start off, we will need to create a new file on your system, which we will call "form.html". Open the file up and you will need to type in the following code:
</p>
<TABLE align="center"><TR><TD><FONT size="2"><B><I>
<HTML><BR>
   <HEAD><BR>
     <TITLE>Form</TITLE><BR>
   </HEAD><BR>
   <BODY><BR>
     <FORM action="processform.php" method="POST" name="form" id="form"><BR>
        What is your name? <INPUT type="text" name="name" id="name"><BR>
        <BR><BR><BR>
        <INPUT type="submit" value="Submit" name="submit" id="submit"><BR>
        <INPUT type="reset" value="Reset" name="reset" id="reset"><BR>
     </FORM><BR>
   </BODY><BR>
</HTML><BR>
</i></b></font></td></tr></table>
<P align="justify">
Nothing all that complicated, this will create a single text box, asking the user what his / her name is. Along with Submit and Reset buttons.
</p>
<P align="justify">
To start the in depth explanation of the code, let me just straight down to the opening <B>FORM</b> tag.
</p>
<P align="center">
<B><I><FORM action="processform.php" method="POST" name="form" id="form"></i></b>
</p>
<P align="justify">
The first part of the tag is <B>action=</b>, this is where you specify what file you are going to use to analyze the contents of the form. In this instance, we are going to be calling upon <B>"processform.php"</b> which we will be creating later.
</p>
<P align="justify">
The next thing to specify is the <B>method</b>. There are two methods which you can use, either POST or GET. In a nutshell, GET assigns the form data to the environment variable of <B>QUERY_STRING</b>, then submits it, while POST simply sends the data. POST is slightly more stealth, as the user will never see the data being passed to the script. GET is most commonly used when sending information between two different windows.
</p>
<P align="justify">
Following the method, there are two additional variables. <B>name</b> and <B>id</b>, which are used for identification purposes, especially with such languages as JavaScript. I usually set the two variables to equal the same thing, just for convenience purposes, and make them fairly descriptive, like this instance where we call it "form".
</p>
<P align="justify">
Now we have our <B>FORM</b> tag, we now have to build the components in the form, and then close it all out. After the prompt, "What is your name?", we have our first of 3 <B>INPUT</b> tags. The first one is the box that the user will type his / her name into. <B>INPUT</b> tags can represent many input types, including text boxes, buttons, radio buttons and check boxes. In this instance, it is going to be a text box, so we set the type variable to be "text". The last two fields are id and name, and hold the same purpose as before. We will set their values to "name" because that is what the text box will be holding the value of, the user's name.
</p>
<P align="justify">
After a couple of line breaks, we throw in the last 2 <B>INPUT</b> tags. The first of the two is going to be our submit button, the second will be a reset button. For submit buttons, we set the <B>type</b> to be "submit", and we will set the <B>name</b> and <B>id</b> to be the same, just to make things uniform. We are now going to set a new variable, value. value specifies what the button says when it is displayed on the screen. We have the value set to Submit, but you can call it whatever you want. The perk of the submit type, is that when the user clicks on it, it will perform the action specified in the <B>FORM</b> tag. Therefore, the submit button is what will execute the form.
</p>
<P align="justify">
The next button is the reset button. It will be the same as the previous button, but we will set all the variables (<B>type</b>, <B>value</b>, <B>name</b> and <B>id</b>) to be reset. reset, like our good friend submit has a special purpose as well. When the user clicks on this button, the contents of all the fields on the form will be reset back to their initial value, which in this case, the name text box will be reset back to being blank, because there is no value set for it.
</p>
<P align="justify">
Our form is now complete, so we will close it off with the closing FORM tag, and upload this bad boy to our host.
</p>
<P align="justify">
Now that we have "form.html" complete, and up on our server, let’s go ahead and pull it up in a web browser. It shouldn't be anything spectacular, just a basic form, with a single field, and 2 buttons. Type in your name and click on "Submit", you should get a page cannot be displayed error. If not, you must have a file called processform.php already in that directory. What happened is the form tried to send the information from the form, to a file that doesn't exist yet, hence the error.
</p>
<P align="justify">
On that note, I want you to create another file, and name it "processform.php". Immediately, I want you to upload it to the server, and try to submit your form again. Wow, a blank screen. Yeah, the file now exists, and doesn't give us an error. Only problem with that is that the script is not doing anything with the data being received, and our form is worthless.
</p>
<P align="justify">
Enough fun and games, lets get down to coding. Close out of your web browser, and open up the "processform.php" file for editing. What we're going to do is write a script that will take the user's name and give them a simple greeting, like "Hey [name], how are you doing?” Since I'm assuming you know a thing or two about PHP, why not give it a try, and then come back to the tutorial. I'll give you a hint, start your file with <B><?</b> and end it with <B>?></b> ;).
</p>
<P align="justify">
Hopefully you figured it out on your own; if not, that's cool, that's why I'm writing this tutorial.
</p>
<P align="justify">
I would hope your file looks at least like this:
</p>
<P align="center">
<B><I><?<BR>
<BR>
?></i></b>
</p>
<P align="justify">
If not, may I suggest my PHP 101 tutorial? If you did get that far, let me say, good job, you're 66% of the way done. Within the delimiters, you will need to add the following line:
</p>
<P align="center">
<B><I>echo "Hey $name, what's shakin'?";</i></b>
</p>
<P align="justify">
Or whatever lame greeting you want. To call the name of the person from the form, you just have to use the <B>$name</b> variable. The name of the variable came from the name of the field on the form. If the name of the field was blah, then the variable that holds the data for that field would be called <B>$blah</b>.
</p>
<P align="justify">
Congratulations, you just completed your first form and PHP script to process it.
</p>
<P align="justify">
Now for my next topic, form validation with PHP. Open up "processform.php" again, and insert a few line breaks after the first delimiter (after the echo statement). In that white space, we are going to add an if structure, to check to see if the user actually inputted a name.
</p>
<TABLE align="center"><TR><TD><FONT size="2"><B><I>
if ($name=="") {<BR>
   echo "I thought I said to type in your name?";<BR>
} else {
</i></b></font></td></tr></table>
<P align="justify">
You can indent the second <B>echo</b> statement, and then add a <B>}</b> on the next line to complete the structure. Upload this new copy of the script, and pull up your form again. Try to submit the form without a name. Now you get the message "I thought I said to type in your name?" instead of "Hey , what's shakin'?" You could also check for certain values, like if the name is equal to your name, you could spit out "Hey, what's my name too!", or something like that. The possibilities are endless.
</p>
<P align="justify">
On a side note, you could use a simple JavaScript form validation routine to accomplish the same, but if the user's browser doesn't handle JavaScript, then you're pretty much SOL.
</p>
<P align="justify">
So we built are form, we are validating that the value isn't null, and now we're going to optimize what we have. Yep, optimize it. How? Well we're going to ditch the 2 files, and combine it into a single PHP file.
</p>
<P align="justify">
Let’s create a new file, and call it "allinone.php". Open it up, and input the following code:
<TABLE align="center"><TR><TD><FONT size="2"><B><I>
<?<BR>
<BR>
if ($name=="") {<BR>
<BR>
?><BR>
<BR>
   <HTML><BR>
     <HEAD><BR>
        <TITLE>Form</TITLE><BR>
     </HEAD><BR>
     <BODY><BR>
        <FORM action="allinone.php" method="POST" name="form" id="form"><BR>
          What is your name? <INPUT type="text" name="name" id="name"><BR>
          <BR><BR><BR>
          <INPUT type="submit" value="Submit" name="submit" id="submit"><BR>
          <INPUT type="reset" value="Reset" name="reset" id="reset"><BR>
        </FORM><BR>
     </BODY><BR>
   </HTML><BR>
<BR>
<? <BR>
<BR>
} else {<BR>
<BR>
   echo "Hey $name, what's shakin'?";<BR>
<BR>
}<BR>
<BR>
?>
</i></b></font></td></tr></table>
<P align="justify">
That code should look familiar for the most part. All we're doing is adding in a giant <B>if</b> structure. If the variable <B>$name</b> is null, then display the form, if not, analyze the data. The form will keep looping if the user doesn't enter in a name, but if they do, it will give them the greeting.
</p>
<P align="justify">
In case you have multiple fields on your form, this method won't be that efficient. In that situation, you will want to use a different <B>if () {</b> statement. The appropriate statement would be either <B>if ($REQUEST_METHOD=="POST") {</b> or <B>if ($REQUEST_METHOD=="GET") {</b> depending on if you use POST or GET for your form method. This will check the environment variable, <B>REQUEST_METHOD</b>, to see if the form is being sent via the POST or GET method.
</p>
<P align="justify">
Well, that's the first part of the tutorial; you should now have a basic understanding of HTML forms, and how to utilize PHP to analyze the data. Now it's time to learn how to do something a bit more functional than just redisplaying the form contents back to the user.
</p>
<P align="justify">
Have you ever seen a site that has a form that gives you the opportunity to contact the people who run the site? If not, please go <A href="http://www.bombthebox.com/index.php?page=contactus" target="_blank" class="NAVITEM">here</a> for an example. What these forms do, is link to a PHP script (or ASP, Perl...) and that script emails the data to who ever is set up as the recipient, usually webmaster@.
</p>
<P align="justify">
PHP has the perfect little function for such a thing, it's called <B>mail()</b>. If you want to check out PHP.net's manual page on <B>mail()</b> then by all means, check it out <A href="http://www.php.net/manual/en/function.mail.php" target="_blank" class="NAVITEM">here</a>. Their site will give you some in depth information about using <B>mail()</b> and some of the problems and pitfalls and what not.
</p>
<P align="justify">
The most simplistic use of <B>mail()</b> is like this:
</p>
<P align="center">
<B><I>mail ($to, $subject, $message);</i></b>
</p>
<P align="justify">
Very basic, all you do is specify the recipient, the subject and the message. You can also add more complex things such as additional header information,
Cc:, Bcc:, and even who the email is from (good for spoofing messages against people who are too dumb to check the header information).
</p>
<P align="justify">
Well, let's try this idea out, and throw up our own contact form. First thing we need to do, as always, is create a new file. This time we will call it
"contactform.php" We will be using just a single file for this, as explained previously.
</p>
<P align="justify">
I am going to give you a basic overview of what you will need to do, and you can try it on your own. If you crash and burn, you can go further into the
tutorial, and use the code provided.
</p>
<P align="justify">
We are going to use an if structure like in the previous bit of code we did, but we will need to check the <B>REQUEST_METHOD</b> variable to see if it's value is
POST. Under the start of the <B>if</b> structure, we will place the code for our form. Our form should have the following fields: name, email address, subject,
message, and 2 buttons, send and reset. After we build our form, we will need throw an else into the structure, put in some code to send the email, and then
close it all off.
</p>
<P align="justify">
Did you get all that? Probably, not, but that's ok.
</p>
<P align="justify">
The first thing mentioned, was starting an if structure that checked the REQUEST_METHOD variable.
</p>
<TABLE align="center"><TR><TD><FONT size="2"><B><I>
<?<BR>
<BR>
if ($REQUEST_METHOD=="POST") {
<BR>
?>
</i></b></font></td></tr></table>
<P align="justify">
That should look familiar, if not, go back and start at the beginning of this tutorial again, and take notes!
</p>
<P align="justify">
Next up is our form, with 4 different boxes, and 2 buttons.
</p>
<TABLE align="center"><TR><TD><FONT size="2"><B><I>
<HTML><BR>
   <HEAD><BR>
     <TITLE>Contact Form</TITLE><BR>
   </HEAD><BR>
   <BODY><BR>
   <FORM action="contactform.php" method="POST" name="form" id="form"><BR>
        Your Name?<BR><INPUT type="text" name="name" id="name"><BR>
        Your Email?<BR><INPUT type="text" name="email" id="email"><BR>
        Subject?<BR><INPUT type="text" name="subject" id="subject"><BR>
        Message?<BR><TEXTAREA name="message" id="message"></TEXTAREA><BR>
        <BR><BR><BR>
        <INPUT type="submit" value="Send Email" name="submit" id="submit"><BR>
        <INPUT type="reset" value="Reset Form" name="reset" id="reset"><BR>
     </FORM><BR>
   </BODY><BR>
</HTML>
</i></b></font></td></tr></table>
<P align="justify">
This script is a bit more complex than our original form, but not too far from being the same. The only new thing there is the use of the <B>TEXTAREA</b> tag.
<B>TEXTAREA</b> is basically a multi-lined input box. We use this for the message, so the user can more room to type and see what they are typing and all that good
stuff. The <B>TEXTAREA</b> tag makes use of a closing tag as well, in case you wanted to put text in the box, you would put it between the tags, instead of using
<B>value=</b>. Everything else is old information from earlier in the tutorial. Note, we used different <B>name</b>’s and <B>id</b>'s for each component on the form, and we
changed the <B>value=</b> for the submit and reset buttons, so that they have different text when the form is viewed.
</p>
<TABLE align="center"><TR><TD><FONT size="2"><B><I>
<? <BR>
<BR>
} else {<BR>
<BR>
   $to = "your@email.address";<BR>
   $from = "From: \"$name\" <$email>";<BR>
   mail($to, $subject, $message, $from);<BR>
   echo "Hey $name, thanks for emailing us, you should get a reply in 3-5 business days.";<BR>
<BR>
}<BR>
<BR>
?>
</i></b></font></td></tr></table>
<P align="justify">
Here is the <B>else</b> portion of the structure. We assign two variables before we do anything. <B>$to</b> is where you put your email address in, so you receive the
emails being sent, <B>$from</b> contains the formatting for the additional header information. <B>From:</b> isn't a standard built into <B>mail()</b>, so you have to define it
in the extra header portion of the function.
</p>
<P align="justify">
The next line contains the <B>mail()</b> function, calling our 2 variables we just defined, as well as the <B>$subject</b> and <B>$message</b> information from the form. This line
will send the information to whatever email address you put in for <B>$to</b>.
</p>
<P align="justify">
The last line is a simple <B>echo</b> statement, to let the user know that their email was sent, and that it should be replied to shortly.
</p>
<P align="justify">
That's all there is to it! You can add additional if structures within the else portion to check to see if any fields were left blank, or to block people
from a certain email address from using the form, et cetera.
</p>
<P align="justify">
That pretty much wraps up using forms, and using the <B>mail()</b> function of PHP. What I'd like to do now, is take our last example, and give you a more complex
version of it. This new code will contain some error checking, as well as utilize HTML encoded email. The previous examples of using <B>mail()</b> sent plain text
messages, lame.
</p>
<P align="justify">
We are going to create one last file, and call it "contactform2.php", and input the following code:
<TABLE align="center"><TR><TD><FONT size="2"><B><I>
<?<BR>
<BR>
if ($REQUEST_METHOD=="POST") {<BR>
<BR>
?><BR>
<BR>
<HTML><BR>
   <HEAD><BR>
     <TITLE>Contact Form, the Sequel</TITLE><BR>
   </HEAD><BR>
   <BODY><BR>
     <FORM action="contactform2.php" method="POST" name="form" id="form"><BR>
        Your Name?<BR><INPUT type="text" name="name" id="name"><BR>
        Your Email?<BR><INPUT type="text" name="email" id="email"><BR>
        Subject?<BR><INPUT type="text" name="subject" id="subject"><BR>
        Message?<BR><TEXTAREA name="message" id="message"></TEXTAREA><BR>
        <BR><BR><BR>
        <INPUT type="submit" value="Send Email" name="submit" id="submit"><BR>
                       <INPUT type="reset" value="Reset Form" name="reset" id="reset"><BR>
     </FORM><BR>
   </BODY><BR>
</HTML><BR>
<BR>
<? <BR>
<BR>
} else {<BR>
	<BR>
   if ($name=="" or $email=="" or $subject="" or $message="") {<BR>
		<BR>
     echo "You have to fill out the entire form, go back and try again.";<BR>
<BR>
   } else {<BR>
<BR>
     $to = "your@email.address";<BR>
     $from = "From: \"$name\" <$email>";<BR>
     $subject = "[via form] " . $subject;<BR>
<BR>
     $additional = "$from\r\nReply-To: $email\r\nContent-Type: text/html; charset=iso-8859-1;<BR>
     $message = "	<HTML><BR>
             <HEAD><BR>
             <TITLE>$subject</TITLE><BR>
             </HEAD><BR>
             <BODY><BR>
               <P align=LEFT>$message</P><BR>
             </BODY><BR>
          </HTML>";<BR>
<BR>
     mail($to, $subject, $message, $additional);<BR>
<BR>
     echo "Hey $name, thanks for emailing us, you should get a reply in 3-5 business days.";<BR>
<BR>
   }<BR>
<BR>
}<BR>
<BR>
?>
</i></b></font></td></tr></table>
<P align="justify">
Hopefully that wasn't too overwhelming. The initial form was not altered at all, so there is no need to discuss it. The first amendment is the new <b>if</b>
structure under the <b>else</b> statement. That particular <b>if</b> structure checks to see if any of the fields on the form were left blank, and if so, it advises the
user accordingly.
</p>
<P align="justify">
If all the fields are filled in, it then goes on to send the email. Our <b>$to</b> and <b>$from</b> variables are still the same, but I threw in a <b>$subject</b> variable.
<b>$subject</b>? Isn't that one of the fields on the form? Yep, it is, but, we aren't changing what the subject is, we're just appending "[via form]" to the front
of the subject line. Then, when the email hits your box, you can see who's using your form.
</p>
<P align="justify">
After appending the subject line, we define another new variable, <b>$additional</b>. This variable contains the additional header information in it, separated by
<b>\r\n</b>. We start the variable off with the <b>$from</b> variable, and then add <b>Reply-To:</b> and <b>Content-Type:</b>. <b>Reply-To</b> simply tells your email client to reply to a
certain address. It isn't truly necessary, but it's in good practice to use it. The last bit of header information is the most important. <b>Content-type:</b> is
used to tell an email client to read the message as HTML and not plain text.
</p>
<P align="justify">
The last variable is our <b>$message</b>. This time, the message won't be displayed as plain text, so we are going to utilize HTML. As you can see, <b>$message</b> is
now formatted like a web page, using <b>$subject</b> for the title, and the original <b>$message</b> in the <b>BODY</b> tag. You can put whatever HTML you want in here, change
the font, or make the background different, whatever floats your boat.
</p>
<P align="justify">
The next line is the <b>mail()</b> function. Nothing too special here, we simply changed the <b>$from</b> variable to the <b>$additional</b> variable to utilize the additional
header information we wanted to use. After that, we have the same echo line as before, just letting the user know what's going on.
</p>
<P align="justify">
That's it, after reading this, you should be able to form with forms, and the <b>mail()</b> function of PHP. If not, read it again. If so, then try using the
information to your advantage, and have fun with you. If you're really adventurous, you could start having emails sent to you when people visit a certain
page on your site, or if you're malicious, and have a site that gets a lot of traffic, you could set up a function that will email your victim every time
that page (or all your pages) is loaded. You could even generate random subject lines, senders, and messages to avoid a mass delete. Remember though kids,
the header information never lies, and even though your email says "From: JoMamma@FudgeYou.com", the header will still say it came from your server.
</p>
<P align="justify">
Hope you found this informative, and thanks for reading!
</p>
```


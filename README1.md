```cmd

1. creating website for book store

File Name - home.html


<frameset rows="40%,*">
<frame src="top.html" noresize scrolling="NO" name="topframe">
<frameset cols="15%,*">
<frame src="left.html" noresize scrolling="NO" name="leftframe">
<frame src="right.html" noresize name="rightframe" scrolling="auto">
</frameset>
</frameset>





File Name - top.html




<html>
<head>
<title>Top Frame</title>
</head>
<body bgcolor="YellowGreen ">
<img src="C:\Users\Asus\OneDrive\Desktop\wt\download.jpg" width="125" height="115" align="left">
<img src="C:\Users\Asus\OneDrive\Desktop\wt\images.jpg" width="125" height="115" align="right">
<center>
<marquee bgcolor="yellow" width="650" behavior="alternate">
<font face="Brush Script MT" size="8" color="green"><b><i>Online Book Store</i></b>
</font>
</marquee> <br>
<font	face="Brush Script" size="6" color="white"><b>Created &	Maintained By DR AIT</b></font>
</center>
<br>
<table width="100%" height="50%" cellspacing=10>
<tr align="center">
<td>	<a href="Home.html" target="_parent"><font face="Brush Script" size="6" color="navy">HOME </a> </td>
<td> <a href="login.html" target="rightframe"><font face="Brush Script" size="6" color="navy">LOGIN</a> </td>
<td> <a href="registration.html" target="rightframe"> <font face="Brush Script" size="6" color="navy">REGISTER </a> </td>
<td> <a href="catalogue.html" target="rightframe"> <font face="Brush Script" size="6" color="navy">CATALOGUE</a> </td>
</tr>
</table>
</body>
</html>




File Name - left.html




<html>
<body align="center" bgcolor="bisque"> <br>
<a href="ise.html" target="rightframe"><font size="6">ISE</font></a><br><br>
<a href="ece.html" target="rightframe"><font size="6">ECE</font></a><br><br>
<a href="eee.html" target="rightframe"><font size="6">EEE</font></a><br><br>
<a href="mech.html" target="rightframe"><font size="6">MECH</font></a><br>
</body>
</html>




File Name - right.html




<html>
<body bgcolor="orange">
<center>
<img src="C:\Users\Asus\OneDrive\Desktop\wt\book.jpg" height="170"><br>
<font face="Brush Script MT" size="5" color="blue">
<h1><b>Welcome to the Online Book Store!!!</b></font><br />
<font face="Brush Script MT" size="5" color="red">
<h2><b> "A Huge Collection Of Engineering E-Books"</b></h2></font>
</center>
</body>
</html>





File Name - ise.html





<html>
<head><title>ISE</title></head>
<body bgcolor="cyan">
<center><font color="blue"><h1>Information Science and Engineering</h1></font></center>
<br>
<table align="center">
<tr>
<td>Text Books</td>
<td>
<select >
<option value="select the book" selected>Select the book
<option value="C&Ds">C&Ds
<option value="Ads">Ads
<option value="Java">Java
<option value="Oracle">Oracle
<option value="Ms SQL Server">Ms SQL Server
<option value="MySql">MySql
</select>
</td></tr>
<tr>
<td>Quantity</td>
<td><input type="text" id="q"></td>
</tr>
<tr>
<td></td>
<td>
<form method=post action="order.html">
<input type="submit" value=ok />
</form>
</td>
</tr>
</table>
<center>
<pre> Cost of one book is"500" + shipping "100" </pre>
</center>
</body>
</html>




File Name - ece.html




<html>
<body bgcolor="Plum">
<h1><font color="blue">Electronics and Communication Engineering</font></h1>
<h2>
<ul>
<li>Digital Circuits</li> <li>Signals and Systems</li> <li>Digital Communication</li>
</ul>
</h2>
</body>
</html>




File Name - eee.html




<html>
<body bgcolor="Plum">
<h1><font color="blue">Electrical and Electronics Engineering</font></h1>
<h2>
<ul type="square">
<li>Concepts in Electric Circuits</li>
<li>Introduction to Electronic Engineering</li>
<li>Electrical Power</li>
</ul>
</h2>
</body>
</html>




File Name - mech.html




<html>
<body bgcolor="Plum">
<h1><font color="blue">Mechanical Engineering</font></h1>
<h2>
<ol type="I">
<li>Theory of Machines</li>
<li>Automation and Robotics</li>
<li>Engineering Fluid Mechanics</li>
</ol>
</h2>
</body>
</html>




File Name - login.html





<html>
<body bg color="pink">
<center>
<img src="C:\Users\Asus\OneDrive\Desktop\wt\login.jpg" width="385" height="135" ><br >
<font face="Brush Script MT" size="7" color="purple">
<b>Enter Login Details:</b>
</font>
<p>Login ID:<input type="text" name="loginid" placeholder="Your Login ID"></p>
<p>Password:<input type="password" name="password"></p>
<input type="submit" value="Submit">
<input type="reset" value="Reset">
</center>
</body>	
</html>





File Name - register.html




<html>
<head><title>Registration Form</title></head>
<body bgcolor="#E4F0F8">
<center><font color="blue" size="6" face="arial">Registration Form</font>
<form action="right.html">
<p>First Name: *<input type="text" name="name" placeholder="Minimum 6 character"></p>
<p>Last Name: *<input type="text" name="lastname"></p>
<p>Email Address: *<input type="email" id="email"></p>
<p>Password: *<input type="password" name="password"></p>
<p>Address: *<textarea rows="2" cols="20" id='addr' /></textarea></p>
<p>Mobile No: *<input type='text' id='mobileno' /></p>
<p>Gender: *
<input type='radio' name="gender">male
<input type='radio' name="gender">female</p>
<input type='Submit' value="Submit">
<input type='Reset' value="Reset">
</center>
</form>	
</body>	
</html>





File Name - catalogue.html





<html>
<head>
<title> Catalogue </title>
</head>
<body bgcolor="pink">
<form action="order.html">
<table border="1" width="100%">
<tr>
<td>
<img src="images/wt.jpg" width=100 height=100/>
</td>
<td> Book: Web Technologies <br> Author: Uttam K. Roy <br> Publication:Oxford University Press</td> 
<td>531 &nbsp;&nbsp;&nbsp;</td>
<td> <input type="submit" value="Add to cart"/></td> 
</tr>
<tr>
<td> <img src="images/php.jpg" width=100 height=100/></td>
<td> Book: PHP & MySQL Web Development <br> Author:Luke Welling & Laura Thompson <br> Publication:PEARSON</td> <td> 898 &nbsp;&nbsp;&nbsp; </td>
<td> <input type="submit" value="Add to cart"/></td> </tr>
</table> </form>
</body>
</html>





File Name - order.html





<html>
<head><title>order conformation</title></head>
<body bgcolor="cyan">
<center>
<pre><strong>
<b>Your order Is Conformed
</strong></pre>
<h2><b>THANK YOU...Visit Again</h2>
</center>
</body>
</html>




```

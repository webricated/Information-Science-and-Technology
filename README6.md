```cmd


6. JS(POP-UP BOX)


File Name - multable.html



<html>
<head><title> Multiplication Table </title></head>
<body>
<script type="text/javascript">

var n=prompt("Enter positive value for n: "," "); 
if(!isNaN(n)) {
var table=""; 
var number="";
for(i=1;i<=10;i++) {
number = n * i;
table += n + " * " + i + " = " + number + "\n"; 
}
alert(table);
}
else {
alert("Enter positive value"); 
n=prompt("Enter positive value for n: "," ");
}
document.write(n+" table values displayed using alert ..<br />");

</script>
</body>
</html>


sumofnums.html
<html>
<head>
  <title>Sum of n numbers using popup boxes</title>
  <script language='javascript'>
    function addSum() {
      alert("You're going to give me a list of numbers. I'm going to add them together for you.");
      var keepGoing = true;
      var sumOfNums = 0;

      while (keepGoing) {
        var nextNumber = parseInt(prompt("What's the next number to add?", ""));

        // Check if the input is a valid number
        if (isNaN(nextNumber)) {
          alert("Invalid input. Please enter a valid number.");
          continue;
        }

        sumOfNums = sumOfNums + nextNumber;
        keepGoing = confirm("Add another number?");
      }

      alert("The sum of all your numbers is " + sumOfNums);
    }
  </script>
</head>
<body>
  <form name="frm">
    <input type="button" value="Sum of n numbers" onclick="addSum()">
  </form>
</body>
</html>



```

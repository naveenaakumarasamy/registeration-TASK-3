# registeration-TASK-3
## Develop a registration form for a website or app, complete with input validation and error messages.

## code:

### index.php

```
<?php  
// define variables to empty values  
$nameErr = $emailErr = $mobilenoErr = $genderErr = $websiteErr = $agreeErr = "";  
$name = $email = $mobileno = $gender = $website = $agree = "";  

if ($_SERVER["REQUEST_METHOD"] == "POST") {  
      
//String Validation  
    if (empty($_POST["name"])) {  
         $nameErr = "Name is required";  
    } else {  
        $name = input_data($_POST["name"]);  
            // check if name only contains letters and whitespace  
            if (!preg_match("/^[a-zA-Z ]*$/",$name)) {  
                $nameErr = "Only alphabets and white space are allowed";  
            }  
    }
      if (empty($_POST["email"])) {  
            $emailErr = "Email is required";  
    } else {  
            $email = input_data($_POST["email"]);  
            // check that the e-mail address is well-formed  
            if (!filter_var($email, FILTER_VALIDATE_EMAIL)) {  
                $emailErr = "Invalid email format";  
            }  
     }
     if (empty($_POST["mobileno"])) {  
            $mobilenoErr = "Mobile no is required";  
    } else {  
            $mobileno = input_data($_POST["mobileno"]);  
            // check if mobile no is well-formed  
            if (!preg_match ("/^[0-9]*$/", $mobileno) ) {  
            $mobilenoErr = "Only numeric value is allowed.";  
            }  
        //check mobile no length should not be less and greator than 10  
        if (strlen ($mobileno) != 10) {  
            $mobilenoErr = "Mobile no must contain 10 digits.";  
            }  
    }
      if (empty($_POST["website"])) {  
        $websiteErr = "Website URL is required";  
    } else {  
            $website = input_data($_POST["website"]);  
            // check if URL address syntax is valid  
            if (!preg_match("/\b(?:(?:https?|ftp):\/\/|www\.)[-a-z0-9+&@#\/%?=~_|!:,.;]*[-a-z0-9+&@#\/%=~_|]/i",$website)) {  
                $websiteErr = "Invalid URL";  
            }      
    }
     if (empty ($_POST["gender"])) {  
            $genderErr = "Gender is required";  
    } else {  
            $gender = input_data($_POST["gender"]);  
    }
     if (!isset($_POST['agree'])){  
            $agreeErr = "Accept terms of services before submit.";  
    } else {  
            $agree = input_data($_POST["agree"]);  
    } 
}
function input_data($data) {  
  $data = trim($data);  
  $data = stripslashes($data);  
  $data = htmlspecialchars($data);  
  return $data;  
}

?>
<!DOCTYPE html> 
<html>  
	<head>  
		<style>  
		.error {
			color: #FF0001;}  
		</style>  
	</head>  
	<body>
	<fieldset>
	<legend><h1><b><i>Registration Form</b></i></h1></legend>  
	<span class="error">* required field </span>  
	<br><br>  
	<form method="post" action="<?php echo htmlspecialchars($_SERVER["PHP_SELF"]); ?>" >      
    		Name:  
    		<input type="text" name="name">
		<span class="error">* <?php echo $nameErr; ?> </span>
  
    		<br><br>  
    		E-mail:  
    		<input type="text" name="email"> 
		<span class="error">* <?php echo $emailErr; ?> </span>
 
    		<br><br>  
    		Mobile No:  
    		<input type="text" name="mobileno">
		<span class="error">* <?php echo $mobilenoErr; ?> </span>
  
    		<br><br>  
    		Website:  
    		<input type="text" name="website">  
		<span class="error"><?php echo $websiteErr; ?> </span>

    		<br><br>  
    		Gender:  
    		<input type="radio" name="gender" value="male"> Male  
    		<input type="radio" name="gender" value="female"> Female  
    		<input type="radio" name="gender" value="other"> Other
		<span class="error">* <?php echo $genderErr; ?> </span>  
    		<br><br>  
    		Agree to Terms of Service:  
   		<input type="checkbox" name="agree">
		<span class="error">* <?php echo $agreeErr; ?> </span>
 
    		<br><br>                            
    		<input type="submit" name="submit" value="Submit">  
    		<br><br>                            
	</form>
	</fieldset>
	</body>  

<?php  
    if(isset($_POST['submit'])) {  
    if($nameErr == "" && $emailErr == "" && $mobilenoErr == "" && $genderErr == "" && $websiteErr == "" && $agreeErr == "") {  
        echo "<h3 color = #FF0001> <b>You have sucessfully registered.</b> </h3>";  
        echo "<h2>Your Input:</h2>";  
        echo "Name: " .$name;  
        echo "<br>";  
        echo "Email: " .$email;  
        echo "<br>";  
        echo "Mobile No: " .$mobileno;  
        echo "<br>";  
        echo "Website: " .$website;  
        echo "<br>";  
        echo "Gender: " .$gender;  
    } else {  
        echo "<h3> <b>You didn't filled up the form correctly.</b> </h3>";  
    }  
    }  
?>
</html>
```
## Output:
![image](https://github.com/naveenaakumarasamy/registeration-TASK-3/assets/113497406/9ff38ea4-b19b-434f-ac61-22671a3c2179)

![image](https://github.com/naveenaakumarasamy/registeration-TASK-3/assets/113497406/1f9bfe03-988d-4e68-8e4b-4fed7abb45ba)

![image](https://github.com/naveenaakumarasamy/registeration-TASK-3/assets/113497406/eb05f276-279f-4d01-a1d1-bb423587aa0a)

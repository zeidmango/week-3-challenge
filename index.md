<html lang="en">
<head>
  <title>Password Generating Application</title>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.16.0/umd/popper.min.js"></script>
  <script src="https://maxcdn.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"></script>
  <style>
    .card {
      height: 150px;
    }

    .secure-password {
      padding-top: 20px;
      padding-bottom: 20px;
    }
  </style>
</head>
<body>

<div class="container pt-4 mt-4">
  <h1 class="text-center">Password Generator</h1>
  <p class="text-center lead">Generate a password</p>

  <hr>
  <div class="card">
    <p class="text-center display-4 secure-password">Your Secure Password</p>
  </div>
  <hr>


  <div class="row">
    <div class="col text-center">
      <button class="btn btn-primary btn-lg gp-btn">Generate Password</button>
    </div>
  </div>
</div>

<script>

$(document).ready(function() {

  function getRandomInt(min, max) {
    min = Math.ceil(min);
    max = Math.floor(max);
    return Math.floor(Math.random() * (max - min + 1)) + min;
  }

  $('.gp-btn').click(function() {

    var op_length;
    var op_lower_case;
    var op_upper_case;
    var op_numeric;
    var op_special_characters;
    var secure_password = '';
    var random_number;

    var lower_case_letters = 'abcdefghijklmnopqrstuvwxyz';
    var upper_case_letters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ';
    var numeric_characters = '0123456789';
    var special_characters = '!@#$%^&*)(+=.<>{}[]:;\'"|~`_-';

    do {

      op_length = prompt('Enter length for password (between 8 and 128)');

    } 
    while (op_length < 8 || op_length > 128);

    do {

      op_lower_case = confirm('Password must have lowercase letters?');
      op_upper_case = confirm('Password must have uppercase letters?');
      op_numeric = confirm('Password must have numeric chracters?');
      op_special_characters = confirm('Password must have special characters?');

    }
    while(!op_lower_case && !op_upper_case && !op_numeric && !op_special_characters);

    for (var i = 0; secure_password.length < op_length; i++) {

      if (op_special_characters) {
        random_number = getRandomInt(0, 27);
        secure_password += special_characters[random_number];
      }

      if (op_numeric && secure_password.length < op_length) {
        random_number = getRandomInt(0, 9);
        secure_password += numeric_characters[random_number];
      }

      if (op_upper_case && secure_password.length < op_length) {
        random_number = getRandomInt(0, 25);
        secure_password += upper_case_letters[random_number];
      }

      if (op_lower_case && secure_password.length < op_length) {
        random_number = getRandomInt(0, 25);
        secure_password += lower_case_letters[random_number];
      }

    }
    
    $('.secure-password').text(secure_password);

  });

});

</script>
</body>
</html>

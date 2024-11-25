# phpmiller


```php
<?php
use PHPMailer\PHPMailer\PHPMailer;
use PHPMailer\PHPMailer\Exception;
require 'PHPMailer/src/Exception.php';
require 'PHPMailer/src/PHPMailer.php';
require 'PHPMailer/src/SMTP.php';

function sendOtp($email, $otp) {
$mail = new PHPMailer(true);

try {
    $mail->isSMTP();
    $mail->Host       = 'Your Host';
    $mail->SMTPAuth   = true;
    $mail->Username   = 'username'; 
    $mail->Password   = 'password'; 
    $mail->SMTPSecure = PHPMailer::ENCRYPTION_STARTTLS;
    $mail->Port       = 587; 
    $mail->setFrom('your sender', 'Company Name');
    $mail->addAddress($email);
    $mail->isHTML(true);
    $mail->Subject = 'Registration Confirm OTP';
    
    $bodyContent = "
    <html>
    <head>
        <style>
            body {
                font-family: Arial, sans-serif;
                background-color: #f4f4f9;
                margin: 0;
                padding: 0;
            }
            .email-container {
                max-width: 600px;
                margin: 0 auto;
                background-color: #ffffff;
                padding: 20px;
                border-radius: 10px;
                box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            }
            .header {
                text-align: center;
                color: #333;
            }
            .otp-box {
                margin: 20px 0;
                padding: 15px;
                background-color: #f7f7f7;
                border-radius: 5px;
                text-align: center;
                font-size: 30px;
                font-weight: bold;
                color: #4CAF50;
            }
            .footer {
                text-align: center;
                margin-top: 30px;
                font-size: 14px;
                color: #777;
            }
            .footer a {
                color: #4CAF50;
                text-decoration: none;
            }
        </style>
    </head>
    <body>
        <div class='email-container'>
            <div class='header'>
                <h2>Welcome to TechRahman!</h2>
                <p>We're happy to help you with your verification process.</p>
            </div>
            <div class='otp-box'>
                <p>Your OTP code is: <b>$otp</b></p>
            </div>
            <div class='footer'>
                <p>If you did not request this code, please ignore this email.</p>
                <p>Need assistance? <a href='mailto:support@techrahman.xyz'>Contact Support</a></p>
            </div>
        </div>
    </body>
    </html>
    ";

    $mail->Body    = $bodyContent;
    $mail->send();
    echo '100';

    } catch (Exception $e) {
        echo "Please Provide valid Email";
    }
}
?>
```

<?php
    if ($_SERVER["REQUEST_METHOD"] == "POST") {

        $mail_to = "hiral.patel201@gmail.com";
        
        # Sender Data
        $subject = "Get in Touch";
        $name = str_replace(array("\r","\n"),array(" "," ") , strip_tags(trim($_POST["name"])));
        $email = filter_var(trim($_POST["email"]), FILTER_SANITIZE_EMAIL);
        $message = trim($_POST["message"]);
        
        if ( empty($name) OR empty($email) OR empty($subject) OR empty($message)) {
            # Set a 400 (bad request) response code and exit.
            http_response_code(400);
            echo "Please complete the form and try again.";
            exit;
        }
        
        # Mail Content
        $content = "Name: $name\n";
        $content = "Email: $email\n\n";
        $content = "Details:\n$message\n";

        # email headers.
        $headers = "From: $name &lt;$email&gt;";
        # Send the email.
        $success = mail($mail_to, $subject, $content, $headers);
        
        if ($success) {
            # Set a 200 (okay) response code.
            http_response_code(200);
            echo "Thank You! Your message has been sent.";
        } else {
            # Set a 500 (internal server error) response code.
            http_response_code(500);
            echo "Oops! Something went wrong, we couldn't send your message.";
        }

    } else {
        # Not a POST request, set a 403 (forbidden) response code.
        http_response_code(403);
        echo "There was a problem with your submission, please try again.";
    }
?>
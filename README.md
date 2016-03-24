# Data-Scraper-ATBS-Python
#! /usr/bin/env python3

import re, pyperclip

# Create a regex for phone numbers
phoneRegex = re.compile (r'''
((\d\d\d)|(\(\d\d\d)))?        #area code (optional)
(\s|-)                           #first seperator
\d\d\d                           #first 3 Digits
-                                #seperator
\d\d\d\d                        #last 4 digits
(((ext(\.)?\s) |x)                 #extenstion
(\d{2,5}))?                      #extension number
''', re.VERBOSE)

# Create a regex for email addresses
emailRegex = re.compile (r'''
#some.+_thing@(\d{2,5}))?.com
[a-zA-Z0-9_+.]    # name part
@    # @ part
[a-zA-Z0-9_+.]     # domain name part

''', re,VERBOSE)

# Get the text off the clipboard
text = pyperclip.paste()
# Extract the email and phone from the text
extractedPhone = phoneRegex.findall(text)
extractedEmail = emailRegex.findall(text)

print(extractedPhone)
print(extractedEmail)
# Todo: Copy the extracted phone and email to the clipboard


import subprocess
from typing_extensions import ParamSpec
# get wifi details
data = subprocess.check_output(['netsh', 'wlan', 'show', 'profile'])
data = data.decode('utf-8').split('\n')

# list of wifi names
wifi_names = []
# iterate through data
for profile in data:

    # find all user profile in each item
    if "All User Profile" in profile:
        # spilt profile item
        profile = profile.split(":")

        # get wifi name
        profile = profile[1]
        profile = profile[1:-1]

        # append all wifi names in wifi_names list
        wifi_names.append(profile)

print("{:<20}| {:}\n".format("wi-fi Names", "passwords"))

# iterate through wifi names
for name in wifi_names:

    # get password details 
    data = subprocess.check_output(['netsh', 'wlan', 'show', 'profile', name, 'key=clear'])
    data = data.decode('utf-8').split('\n')

    # list of passwords
    passwords = []

    # iterate through passwords
    for passw in data:
        password = passw.split(":")

        password = password[1]
        password = password[1:-1]

        # append passwords in password list
        passwords.append(password)
    try:
        # return wifi name and password
        print('{: < 20} | {:}'.format(name, password[0]))
    except IndexError:
        print("{:<20}| {:}".format(name,""))





# Unofficial IServ API

This Python module allows you to interact with IServ school servers using only login data for authentication. No API key is required.

![GitHub commit activity](https://img.shields.io/github/commit-activity/m/Leo-Aqua/IServAPI) ![GitHub Downloads (all assets, all releases)](https://img.shields.io/github/downloads/Leo-Aqua/IServAPI/total?label=GitHub%20Downloads)
![PyPI - Downloads](https://img.shields.io/pypi/dm/IServAPI?label=PyPi%20Downloads)
![PyPI - Python Version](https://img.shields.io/pypi/pyversions/IServAPI) ![PyPI - Wheel](https://img.shields.io/pypi/wheel/IServAPI) ![GitHub repo size](https://img.shields.io/github/repo-size/Leo-Aqua/IServAPI) ![PyPI - Version](https://img.shields.io/pypi/v/IServAPI?label=version)
![GitHub Repo stars](https://img.shields.io/github/stars/Leo-Aqua/IServAPI)



## Installation

```bash
pip install IServAPI
```


## Basic usage

```python
from IServAPI import IServAPI

# Initialize IServ instance with login credentials
api = IServAPI(username="YOUR_ISERV_USERNAME",password="YOUR_ISERV_PASSWORD", iserv_url="some_iserv_url.de")

# Example: Get the current user's information
user_info = api.get_own_user_info()

print(user_info)
```


## Table of contents

- [Unofficial IServ API](#unofficial-iserv-api)
  - [Installation](#installation)
  - [Basic usage](#basic-usage)
  - [Table of contents](#table-of-contents)
  - [Supported Functionality](#supported-functionality)
    - ### Own account
      - [1. Get own User Information](#1-get-own-user-information)
      - [2. Set own User Information](#2-set-own-user-information)
      - [3. Fetch notifications](#3-fetch-notifications)
      - [4. Get badges](#4-get-badges)
      - [5. Read all notifications](#5-read-all-notifications)
      - [6. Read a specific Notification](#6-read-a-specific-notification)
      - [7. Get disk space](#7-get-disk-space)
    - ### Users
      - [8. Get user avatar](#8-get-user-avatar)
      - [9. Search users](#9-search-users)
      - [10. Search users autocomplete](#10-search-users-autocomplete)
      - [11. Get other users information](#11-get-other-users-information)
    - ### Email
      - [12. Get emails](#12-get-emails)
      - [13. Get general Information about emails](#13-get-general-information-about-emails)
      - [14. Get email source](#14-get-email-source)
      - [15. Get all mail folders](#15-get-all-mail-folders)
      - [16. Send Email](#16-send-email)
    - ### Calendar
      - [17. Get upcoming events](#17-get-upcoming-events)
      - [18. Get all eventsources](#18-get-all-eventsources)
    - ### Misc
      - [19. Get conference health](#19-get-conference-health)
      - [20. Files](#20-files)
      - [21. Get folder size](#21-get-folder-size) #TODO add doc section
      - [22. Get groups](#22-get-groups) #TODO add doc section
    - [Logging](#logging)
    - [To-Do List](#to-do-list)
  - [Contribution](#contribution)
  - [Credits](#credits)
  - [License](#license)



## Supported Functionality

### Own account

#### 1. Get own User Information

```python
user_info = get_own_user_info()
```

This method retrieves information about the currently logged-in user.

#### 2. Set own User Information

```python
set_own_user_info(key=value)
```

This method sets your personal information

Available keys are:

`title`

`company`

`birthday`

`nickname`

`_class`

`street`

`zipcode`

`city`

`country`

`phone`

`mobilePhone`

`fax`

`mail`

`homepage`

`icq`

`jabber`

`msn`

`skype`

`note`


#### 3. Fetch notifications

```python
notifications = get_notifications()
```

Retrieves notifications from the specified URL and returns them as a JSON object.


#### 4. Get badges

```python
badges = get_badges()
```

Retrieves the badges from the IServ server. (Badges=numbers on sidebar)


#### 5. Read all notifications

```python
read_all_notifications()
```

Marks all Notification as read.


#### 6. Read a specific Notification

```python
read_notification(notification_id)
```

Marks a single notification as read.


#### 7. Get disk space

```python
get_disk_space()
```
Returns information, like free disk space, label and color about all storage volumes accessible to you. (Windows account, Cloud, etc.)

---

### Users

#### 8. Get user avatar

```python
get_user_profile_picture(user, output_folder)
```

This method retrieves the avatar of any user on the network

It saves the avatar in the folder followed by the username,


#### 9. Search users

```python
search_users(query)
```


#### 10. Search users autocomplete

```python
users = search_users_autocomplete(query, limit=50)
```

Faster than `search_users()` but may not display all users


#### 11. Get other users information

```python
get_user_info(user)
```

Get someone else's public information this includes everything they heve set in 'Personal Information'


---

### Email

#### 12. Get emails

```python
emails = get_emails(path = 'INBOX', length = 50, start = 0, order = 'date', dir = 'desc')
```

Retrieves emails from a specified path with optional parameters for length, start, order, and direction.


#### 13. Get general Information about emails

```python
email_info = get_email_info(path="INBOX", length=0, start=0, order="date", dir="desc")
```

Retrieves email information from the specified path in the mailbox. For example: unread emails.


#### 14. Get email source

```python
email_source = get_email_source(uid, path="INBOX")
```

Retrieves the source code of an email message from the specified email path and message ID.


#### 15. Get all mail folders

```python
mail_folders = get_mail_folders()
```

Retrieves the list of mail folders.


#### 16. Send Email

```python
send_email(receiver_email:str, subject:str, body:str, html_body:str=None, smtp_server:str=None, smtps_port:int=465, attachments:list=None)
```

Sends an email. Note all variables defaulting to none get defined later so don't worry.

sender_email must be a valid name present in the iserv network.


---

### Calendar

#### 17. Get upcoming events

```python
events = get_upcoming_events()
```

Retrieves the upcoming events from the IServ calendar API.


#### 18. Get all eventsources

```python
eventsources = get_eventsources()
```

Retrieves the event sources from the calendar API.


---

### Misc

#### 19. Get conference health

```python
health = get_conference_health()
```

Get the health status of the conference API endpoint.


#### 20. Files

```python
client = file()
```

Possible functions:

**Synchronous methods**

```python
# Checking existence of the resource

client.check("dir1/file1")
client.check("dir1")
```

```python
# Get information about the resource

client.info("dir1/file1")
client.info("dir1/")
```

```python
# Check free space

free_size = client.free()
```

```python
# Get a list of resources

files1 = client.list()
files2 = client.list("dir1")
```

```python
# Create directory

client.mkdir("dir1/dir2")
```

```python
# Delete resource

client.clean("dir1/dir2")
```

```python
# Copy resource

client.copy(remote_path_from="dir1/file1", remote_path_to="dir2/file1")
client.copy(remote_path_from="dir2", remote_path_to="dir3")
```

```python
# Move resource

client.move(remote_path_from="dir1/file1", remote_path_to="dir2/file1")
client.move(remote_path_from="dir2", remote_path_to="dir3")
```

```python
# Move resource

client.download_sync(remote_path="dir1/file1", local_path="~/Downloads/file1")
client.download_sync(remote_path="dir1/dir2/", local_path="~/Downloads/dir2/")
```

```python
# Unload resource

client.upload_sync(remote_path="dir1/file1", local_path="~/Documents/file1")
client.upload_sync(remote_path="dir1/dir2/", local_path="~/Documents/dir2/")
```

```python
# Publish the resource

link = client.publish("dir1/file1")
link = client.publish("dir2")
```

```python
# Unpublish resource

client.unpublish("dir1/file1")
client.unpublish("dir2")
```

```python
# Get the missing files

client.pull(remote_directory='dir1', local_directory='~/Documents/dir1')
```

```python
# Send missing files

client.push(remote_directory='dir1', local_directory='~/Documents/dir1')
```

**Asynchronous methods**

```python
# Load resource

kwargs = {
 'remote_path': "dir1/file1",
 'local_path':  "~/Downloads/file1",
 'callback':    callback
}
client.download_async(**kwargs)

kwargs = {
 'remote_path': "dir1/dir2/",
 'local_path':  "~/Downloads/dir2/",
 'callback':    callback
}
client.download_async(**kwargs)
```

```python
# Unload resource

kwargs = {
 'remote_path': "dir1/file1",
 'local_path':  "~/Downloads/file1",
 'callback':    callback
}
client.upload_async(**kwargs)

kwargs = {
 'remote_path': "dir1/dir2/",
 'local_path':  "~/Downloads/dir2/",
 'callback':    callback
}
client.upload_async(**kwargs)
```

For further informations visit [CloudPolis/webdav-client-python](https://github.com/CloudPolis/webdav-client-python)


#### 21. Get folder size

```python
get_folder_size(path)
```

Returns the size of a folder in human readable form.

#### 22. Get groups

```python
get_goups()
```
Returns a JSON object with all the group names as key and their ID as value.

---

## Logging

Add this
```python
IServAPI.setup_logging("app.log")
```
after your `from IServAPI import IServAPI`


---

## To-Do List

- [x] add search users
- [x] more functionality
- [ ] make wiki
- [ ] Add calendar modification capabilities 


---

## Contribution

Contributions are welcome! If you'd like to contribute to this project, please fork the repository and submit

a pull request. Make sure to follow the existing code style and add appropriate tests for new functionality.


---

## Credits

- Author @Leo-Aqua  
- Author of [WebDAV client Python](https://github.com/CloudPolis/webdav-client-python) @CloudPolis


---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.


> [!IMPORTANT]
> ## DISCLAIMER
> 
> I HOLD NO RESPONSIBILITY FOR ANY DAMAGES OR DATALOSS DONE BY THIS PACKAGE.
> 
> YOU ARE RESPONSIBLE FOR WHAT YOU DO!

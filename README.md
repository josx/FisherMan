# FisherMan

[![GitHub license](https://img.shields.io/github/license/Godofcoffe/FisherMan)](https://github.com/Godofcoffe/FisherMan/blob/main/LICENSE)
![badge](https://img.shields.io/badge/version-3.5.0-blue)
![badge](https://img.shields.io/badge/python-%3E%3D3.8-orange)

### Search for public profile information on Facebook

![screenshot](template.png)

## Installation

```
# clone the repo
$ git clone https://github.com/Godofcoffe/FisherMan

# change the working directory to FisherMan
$ cd FisherMan

# install the requeriments
$ python3 -m pip install -r requeriments.txt

# dependency:
 you need to install geckodriver on your machine,
 download the binary from the official mozilla repo:
 https://github.com/mozilla/geckodriver/releases/latest
 extract and copy the binary, i recommend placing it in /usr/bin
```

## Usage

```
$ python3 fisherman.py --help
usage: fisherman.py [-h] [--version] [-u USERNAME [USERNAME ...] | -i ID
                    [ID ...] | --use-txt TXT_FILE | -S USER] [-sf]
                    [--specify {0,1,2,3,4,5} [{0,1,2,3,4,5} ...]] [-s]
                    [--filters] [-work WORK] [-education EDUCATION]
                    [-city CITY] [-b] [--email EMAIL] [--password PASSWORD]
                    [-o] [-c] [-v | -q]

FisherMan: Extract information from facebook profiles. (Version 3.5.0)

optional arguments:
  -h, --help            show this help message and exit
  --version             Shows the current version of the program.
  -u USERNAME [USERNAME ...], --username USERNAME [USERNAME ...]
                        Defines one or more users for the search.
  -i ID [ID ...], --id ID [ID ...]
                        Set the profile identification number.
  --use-txt TXT_FILE    Replaces the USERNAME parameter with a user list in a
                        txt.
  -S USER, --search USER
                        It does a shallow search for the username. Replace the
                        spaces with '.'(period).
  -b, --browser         Opens the browser/bot.
  -v, -d, --verbose, --debug
                        It shows in detail the data search process.
  -q, --quiet           Eliminates and simplifies some script outputs for a
                        simpler and more discrete visualization.

search options:
  --filters             Shows the list of available filters.
  -work WORK            Sets the work filter.
  -education EDUCATION  Sets the education filter.
  -city CITY            Sets the city filter.

profile options:
  -sf, --scrape-family  If this parameter is passed, the information from
                        family members will be scraped if available.
  --specify {0,1,2,3,4,5} [{0,1,2,3,4,5} ...]
                        Use the index number to return a specific part of the
                        page. about: 0, about_contact_and_basic_info: 1,
                        about_family_and_relationships: 2, about_details: 3,
                        about_work_and_education: 4, about_places: 5.
  -s, --several         Returns extra data like profile picture, number of
                        followers and friends.

credentials:
  --email EMAIL         If the profile is blocked, you can define your
                        account, however you have the search user in your
                        friends list.
  --password PASSWORD   Set the password for your facebook account, this
                        parameter has to be used with --email.

output:
  -o, --file-output     Save the output data to a .txt file.
  -c, --compact         Compress all .txt files. Use together with -o.
```

To search for a user:

* User name: `python3 fisherman.py -u name name.profile name.profile2`
* ID: `python3 fisherman.py -i 000000000000`

The username must be found on the facebook profile link, such as:

```
https://facebook.com/name.profile/
```

It is also possible to load multiple usernames from a .txt file, this can be useful for a brute force output type:

```
python3 fisherman.py --use-txt filename.txt
```

Some profiles are limited to displaying your information for any account, so you can use your account to extract. Note:
this should be used as the last hypothesis, and the target profile must be on your friends list:

```
python3 fisherman.py --email youremail@email.com --password yourpass
```

### Some situations:

* For complete massive scrape:
  ```
  python3 fisherman.py --use-txt file -o -c -sf
  ```
  With a file with dozens of names on each line, you can make a complete "scan" taking your information and even your
  family members and will be compressed into a .zip at the output.


* For specific parts of the account:
    * Basic data: `python3 fisherman.py -u name --specify 0`
    * Family and relationship: `python3 -u name --specify 2`
    * It is still possible to mix: `python3 fisherman.py -u name --specify 0 2`


* To get additional things like profile picture, how many followers and how many friends:
  ```
  python3 fisherman.py -u name [-s | --several]
  ```
  
* For a short search by people's name:
  ```
  python3 fisherman.py [-S | --search] foo
  ```
  Replace the spaces in the name with "."(periods).
  The script returns around 30 profiles.

* To filter the search:
  ```
  python3 fisherman.py -S name -work fisherman
  ```
  If the filter has spaces, enclose it in quotes.
  
* For a minimalist execution:
  ```
  python3 fisherman.py [-q | --quiet]
  ```
  Considerably reduces the script's output texts and, by convention, improves performance.

## Contributing
I would love to have your help in developing this project.

Some things you can help me with:
  * Add more search filters.

Please look at the Wiki entry on [Adding filters to the search argument](https://github.com/Godofcoffe/FisherMan/wiki/Adding-filters-to-the-search-argument) to understand the issues.

## *This tool only extracts information that is public, not use for private or illegal purposes.*

## LICENSE

BSD 3-Clause © FisherMan Project

Original Creator - [Godofcoffe](https://github.com/Godofcoffe)

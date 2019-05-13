# web-scraping-forum-vBulletin
## Overview
This repository includes a web scraper written in Python for self-development of a collection of the posts (incl. usernames, titels and dates). Its core features uses python modules requests, re and BeautifulSoup. It has been tailored for the vBulletin-Software forum.pcgames.de. The spider can easily be updated for other sites.
The script has a built-in delay of average 1 second between two requests. This limit was defined in direct conversation with the operator of forum.pcgames.de
## What is Python?
"Python is a high-level programming language that has been developed since 1991 with the goal of easy learning and applicability. Python is open source. The application is widely used, for example, in the field of data science and in the analysis of scientific research data. Numerous extension libraries make Python attractive beyond these fields of application, especially since scripts in comparatively compact written code can be flexibly referenced to specific automation requirements." (translation of German text by Lennarzt 2018)
## What is Python not?
"A universal tool that can be used easily and without deeper training." (translation of German text by Lennarzt 2018)
## How to run
Follow these steps to become owner of the .html and .xml files of every post of your vBulletin-forum of choice.
1. `1_generate URLs.py` generates URLs of every site of every forum and subforum of forum.pcgames.de and saves the list of URLs in `threadurls_new.txt` (will be created or overwritten in the same directory as the script). You can 
2. Download the HTML-files of every URL in `threadurls_new.txt`. For example you could use the basic unix command `wget` as follows: `sudo nohup wget -i threadurls_new.txt -P htmls/ -o wget.log > nohup.out`
3. `2_transform html to xml` transforms all HTML-files in directory `directory_in_str` to xml and takes caution to their filenames. Date, title (where existing), username and content of a post will be extracted. Quotes will be excluded.

At the end you will have one .html (print-version) and one .xml file of every webpage that includes posts in the forum. Also there will be a detailled log with all process steps of every file.
## Requirements
install pip and then python:
```
sudo su
wget https://bootstrap.pypa.io/get-pip.py
python3 get-pip.py
quit()
```
Python 3.5+
Python module requests (install e.g. with `sudo python -m pip install requests` on your python instance)
Python module BeautifulSoup (install e.g. with `sudo python -m pip install bs4` on your python instance)
## Usage
No installation needed. Simply have a look at all the markdown in the .py-files, copy them to your python instance of choice and run them using e.g. `sudo nohup python3 [script-name] > nohup.out` where `[script-name]` stands for the file's name. Keep in mind that scraping a big forum needs a lot of time. Performing both scripts on forum.pcgames.de took 120 hours.
## Common issues
Sometimes (as in the forum that the scraper was tailered for) post titles are not mandatory. Everytime a post doesn't include a title, it will generate an error.
## Sources
Lennartz, Stephan. Aufbereitung Und Bewertung Digitaler Sammlungen Mit Python. Edited by nestor - Kompetenznetzwerk Langzeitarchivierung. Vol. 10. NESTOR THEMA. Frankfurt am Main, 2018. https://d-nb.info/1159799318/34.

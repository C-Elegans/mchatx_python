# MChatX/MChad Archive Downloader and API
This tool provides an easy way to download subtitles from an MChad/MChatX archive.

## Installation

To use this program, you need to have Python 3 installed.

#### Recommended - Pip

Run the following command in your terminal:

```console
pip install mchatx-python
download_tl -h
```

#### Alternative - Build from source

1. Clone the repository by doing the following

	``` console
	$ git clone https://github.com/C-Elegans/mchatx_python.git

	```
	OR by downloading the [zip](https://github.com/C-Elegans/mchatx_python/archive/refs/heads/master.zip) and unzipping it somewhere convenient

	Note: using `git` is recommended as it makes updating easier

1. It is recommended to install the program under a python virtual environment, as this means the program and dependencies aren't installed globally on the system. The downside is you'll need to activate the environment to use the program
   - Create the environment by doing the following in a convenient folder:

   ``` console
   $ python -m venv .env
   ```
   Note: depending on the age of your system, you may need to replace `python` with `python3`
   - Activate the environment by doing the following:

   ``` console
   $ . .env/bin/activate
   ```
   - Note: You can deactivate the environment by typing `deactivate` into the terminal

1. Install the program's dependencies by doing the following:

   ``` console
   $ pip install -e .
   ```
   Note: depending on the age of your system, you may need to replace `pip` with `pip3`

1. Install the program by doing the following:

   ``` console
   $ python setup.py install
   ```
   Note: depending on the age of your system, you may need to replace `python` with `python3`

1. Test that the program has been installed correctly by running the following:

   ``` console
   $ download_tl -h
   ```
   It should output something like this:
   ```console
   usage: download_tl [-h] [room_link]

   positional arguments:
     room_link   The room link of the MChad archive you want to download

   optional arguments:
     -h, --help  show this help message and exit
   ```



## Usage

To download archives, simply enter the following command in your shell

```console
download_tl
```

The tool should print out a list of the most recent "rooms", where a translator has provided translations for a stream. It should look something like this:

```
id   room/user            room name
0    vtange               freechattest
1    Kamishiro Taishi     [2021.07.25] Reddit Shitpost Review
2    Kamishiro Taishi     [2020.07.24] Reddit Shitpost Review
3    Kamishiro Taishi     [2021.07.24] Haachama Return
4    Kamishiro Taishi     [2021.07.24] Oga 3D Reveal
5    Kamishiro Taishi     [2021.07.24] Kanata RPG

Please enter the ids of the archives you'd like to download, separated by ','
ids (ex. 1,2,9):
```

If for instance you wanted to download the subtitles for Haachama's Return and the 2021-07-25 Reddit shitpost review, you would enter their corresponding numbers at the prompt like this, followed by the `Enter` key:

```
1,3
```

The tool will then download the corresponding translation archives and place them in a file with the same name as the `room name`. In this case it will create `[2021.07.25] Reddit Shitpost Review.json` and `[2021.07.24] Haachama Return.json`

### Downloading a single archive from the room name

As an alternative to the prompt described above, the tool also accepts the room name of a stream as a command line argument. For instance, if you've found an archive on the Mchatx page that you want to download, first click on the buttom marked `Archive Page`.

Clicking this will take you to a url such as `https://mchatx.org/archivecard/Kamishiro Taishi_2021-07-24_15-53-01`. Copy the last portion of the URL (in this case `Kamishiro Taishi_2021-07-24_15-53-01`) and use it as an argument to the tool like so:

```
download_tl 'Kamishiro Taishi_2021-07-24_15-53-01'
```

The tool will then download that room's translation archive and save it just like above.

## Further Usage

Once you have a subtitle archive, you can either use it to generate subtitles with [stream_archive_subtitler](https://github.com/C-Elegans/stream_archive_subtitler) or write a program to parse the data.

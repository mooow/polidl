# polidl
Download PoliTo video lessons!

## Description
This software allows you to download video lessons from polito.it

## Disclaimer
Please note the following statement:

    I contenuti del presente sito sono soggetti al diritto d'autore.
    Tutti i diritti su di essi sono espressamente riservati. 
    I contenuti medesimi possono essere utilizzati solo per lo studio e la 
    consultazione da parte dei singoli studenti del Politecnico di Torino, con 
    espressa esclusione di ogni tipo di commercializzazione, modifica, 
    pubblicazione in rete o altro utilizzo non autorizzato per iscritto. Ogni 
    abuso verra' punito ai sensi di legge.

**By using this software you take full resposibility for whatever you do with the
lessons.**
As such, you are required to log-in with a valid polito.it account.

## Dependencies
This program needs the following packages to be installed:
 * Python 3.x
 * Selenium for Python 3.x
 * geckodriver
 * Firefox

### Installation on ArchLinux
The following command will take care of everything
    
    pacman -S python python-selenium geckodriver firefox --needed

### Installation on Mac
Assuming you have already installed Firefox:
 
    brew install python3 geckodriver
    pip3 install --user selenium

## Configuration
If you don't provide a configuration file, the required information shall be
asked interactively. For your own convenience, you can create a configuration
file `config.json` (in the current working directory) so that you can achieve
maximum automation.

The format is a JSON object which must contain (at least) the following fields:
*  `username`: your school ID, sXXXXXX
*  `password`: your password (in plain-text until we find a better solution)
*  `url`: the URL to the course you want to download (should be something like
`https://didattica.polito.it/portal/pls/portal/sviluppo.videolezioni.vis?cor=<id>`)

The following optional fields are recognized:
*  `output_file`: the file which will contain the link list (default: `links.txt`)

### Example configuration file
This is a valid, bogus configuration file:
```json
{
  "username": "s123456",
  "password": "this is not very clever!",
  "url": "https://didattica.polito.it/portal/pls/portal/sviluppo.videolezioni.vis?cor=123",
  "output_file": "output.txt"
}
```

## Usage
From any given directory (an empty directory is recommended), run:

    python3 /path/to/polidl

If you didn't provide a [configuration file](#example-configuration-file) you
will be asked some questions (interactive mode). After that, the corresponding 
configuration file will be automatically generated.

When the program completes you will have a file called `links.txt` (if you didn't
configure another name) which will contain the links which are to be downloaded.

You can download them, for example (as suggested by the program itself), using
wget:

    wget -nc -ci links.txt


## License
This program is released with the terms of the MIT License.
You can read the terms by running:
    
    polidl --copyright

## Author
polidl is Copyright © 2016-2019 of Lorenzo Mureu

-----

# See also
If your video lessons meet the requisites, you might try 
[a better downloader](https://github.com/mooow/videolez2)


## asciinema2mp4

Generate MP4's from asciinema terminal recordings. All credit to those in the credits, I've just hacked their work to make my life a little easier.

### Motivation

The [`asciinema`] tool is a wonderful way to record and share terminal sessions.
Unfortunately, it's not [currently possible] to embed the output in places like
README files on GitHub repos. This tool provides a solution for that.

### Usage

```bash
asciinema2mp4 [options] <asciinema_number|asciinema_api_url>

  options:
    -s <size>, --size <size>      	One of 'small', 'medium', 'big'
    -p <speed>, --speed <speed>   	Any integer (whole number) to multiply regular speed by
    -t <theme>, --theme <theme>   	One of 'asciinema', 'tango', 'solarized-dark', 'solarized-light', 'monokai'
    -o <file>, --output <file>    	File to write to (defaults to 'asciicast.gif' in current directory)
    -b <bucket>, --bucket <bucket>	Name of S3 bucket to write the file to
    -h, --help                   	Show this help.
```

Examples:

```bash
$ asciinema2mp4 --size small --speed 2 --theme solarized-dark 8332
```

An `asciicast.mp4` file will then be generated for you to embed and share.

```bash
$ asciinema2mp4 --theme solarized-light -o "${HOME}/Desktop/another.mp4" https://asciinema.org/api/asciicasts/8332
```

In this case an `another.mp4` file will be generated on your Desktop. Using the full URL is useful if you want to get an asciicast not from the official website.

#### URL Format

`asciinema2mp4` works by visiting the given webpage, starting the asciicast, screenshotting it repeatedly, and finally stitching it together. The `/api/asciicasts/` format of an asciinema website (e.g. https://asciinema.org/api/asciicasts/8332), as opposed to the main `/a/` format (e.g. https://asciinema.org/a/8332), makes this operation easier (see [usage](#usage)), hence why it is a requirement.

### Requirements

#### Ubuntu

```bash
sudo apt-get install npm ffmpeg 
sudo npm install --global phantomjs2
sudo pip install awscli --upgrade
```

### Credits

* [@blueyed], Daniel Hahler
* [@iblech], Ingo Blechschmidt
* [@tav]
* [@VojtechVitek], Vojtech Vitek
* [@wong2], Wang Dàpéng — **maintainer**
* [@vitorgalvao], Vítor Galvão

### License

Public domain.

—
Enjoy, tav <<tav@espians.com>>


[`asciinema`]: https://asciinema.org/
[asciinema terminal recordings]: https://asciinema.org/
[currently possible]: https://github.com/asciinema/asciinema.org/issues/152

[@blueyed]: https://github.com/blueyed
[@iblech]: https://github.com/iblech
[@tav]: https://github.com/tav
[@VojtechVitek]: https://github.com/VojtechVitek
[@wong2]: https://github.com/wong2
[@vitorgalvao]: https://github.com/vitorgalvao

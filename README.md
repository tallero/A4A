# A4A

A4A (*Asyncio 4chan Archiver* or *Asyncio 4 Archiving*, depending on how much the reader cares about the 4chan API ToS) is a Python script to download all images/videos of a 4chan thread.

## Usage

```
usage: inb4404.py [-h] [-f] [-p PATH] [-a FILE] [--connections N]
                  [--retries N]
                  thread [thread ...]

A4A is a Python script to download all files from 4chan(nel) threads.

positional arguments:
  thread                url of the thread

optional arguments:
  -h, --help            show this help message and exit
  -f, --filenames       use original filenames instead of UNIX timestamps
  -p, --path PATH       set output directory (def: <script location>/downloads)
  -a, --archive FILE    keep track of downloaded files by logging MD5 hashes
  --connections N       number of connections to use (def: 10)
  --retries N           how often to retry a thread if errors occur (def: 5)
                          N<0 to retry indefinitely (not recommended)
```

## Requirements

* Python >= 3.7
* [aiohttp](https://aiohttp.readthedocs.io/en/stable/)

## Paths

The final output directory is assembled according to the following structure

```
<base path>/<board>/<directory name>
```

`<base path>` and `<directory name>` are variable components, which can be changed by the user.

 * `<base path>` can be changed with `-p/--path` (defaults to `<path to inb4404.py>/downloads`)
 * `<directory name>` can be set by adding the desired name to the thread link separated by another "/" (defaults to thread number)

For example:

```
https://boards.4channel.org/abc/thread/12345678        -> <path to inb4404.py>/downloads/abc/12345678
https://boards.4channel.org/abc/thread/12345678/my_dir -> <path to inb4404.py>/downloads/abc/my_dir
```
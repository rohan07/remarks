# remarks

`remarks`: Extract your marks (highlights, scribbles, annotations) and convert them to `Markdown`, `PDF`, `PNG`, and `SVG`. remarks works with PDFs annotated on reMarkable™ paper tablets.

Highlight and annotate PDFs with your Marker on your reMarkable device: 

<!-- How to host images on GitHub but outside your repository? Open an issue, upload your images, and voila! Trick learned from http://felixhayashi.github.io/ReadmeGalleryCreatorForGitHub/ -->

<img width="300" alt="IMG_0642-low.jpg" src="https://user-images.githubusercontent.com/1920195/88480247-3d776680-cf2b-11ea-9c30-061ec0e5cc60.jpg">

Use `remarks` to export annotated pages to `Markdown`, `PDF`, `PNG`, and `SVG` on your computer:

<img width="300" alt="demo-remarks-png.png" src="https://user-images.githubusercontent.com/1920195/88480249-410aed80-cf2b-11ea-919b-22fb550ed9d7.png">

> <mark>WHAT IS LIFE?</mark>
>
> Based on lectures delivered under the auspices of the <mark>Dublin Institute for</mark> <mark>Advanced Studies at Trinity College,</mark> Dublin, in February 1943
>
> <mark>To</mark>
> <mark>the memory of My</mark> <mark>Parents</mark>

Because `remarks` depends only on [PyMuPDF](https://github.com/pymupdf/PyMuPDF) and on [Shapely](https://github.com/Toblerity/Shapely), it should be good to go on macOS, Linux, and Windows. There is no need to install `imagemagick`, `opencv`, or any other image library.

## Install and usage

### 1. Copy files from `xochitl` directory to your computer

There is no need of USB cables nor any connection to your reMarkable Cloud account. You can use the good, old `scp`.

On your reMarkable device, go to `Menu > Settings > About`, then under the `Copyrights and Licenses` tab, scroll down the `General Information` text. Right after the paragraph titled "GPLv3 Compliance", there will be the username (`root`), password and IP address needed for `SSH`.

Using these credentials, `scp` the contents of `/home/root/.local/share/remarkable/xochitl` from your reMarkable to a directory on your computer. It may take a while depending on the size of your document collection and the quality of your wifi network.

You probably want to switch off the Auto sleep feature in `Menu > Settings > Power` before transfering the files to prevent an unintented interruption.

### 2. Run `remarks`

```sh
git clone https://github.com/lucasrla/remarks.git

cd remarks

pyenv virtualenv remarks && pyenv local remarks
# or your choice for managing environments / dependencies

poetry install
# or pip install -r requirements.txt

# note that requirements.txt in this repo was created with:
# poetry export --without-hashes -f requirements.txt -o requirements.txt

# run the demo
python -m remarks demo/xochitl demo/output
```

For usage info, run `python -m remarks --help`.

Note that this is highly experimental software. So far, it has tested only with version 2.2.0.48 of reMarkable software and on macOS Catalina.


## Credits and Acknowledgements

- [@JorjMcKie](https://github.com/JorjMcKie) who wrote and maintains the great [PyMuPDF](https://github.com/pymupdf/PyMuPDF)

- [u/stuculu](https://www.reddit.com/r/RemarkableTablet/comments/7c5fh0/work_in_progress_format_of_the_lines_files/) who wrote the first online post (that I could find) about reverse engineering `.rm` files

- [@ax3l](https://github.com/ax3l) who wrote [lines-are-rusty](https://github.com/ax3l/lines-are-rusty) / [lines-are-beautiful](https://github.com/ax3l/lines-are-beautiful) and also [contributed to reverse engineering of `.rm` files](https://plasma.ninja/blog/devices/remarkable/binary/format/2017/12/26/reMarkable-lines-file-format.html)

- [@edupont, @Liblor, @florian-wagner, and @jackjackk for their contributions to rM2svg](https://github.com/reHackable/maxio/blob/33cdc1706b29698c15aac647619374e895ed3869/tools/rM2svg)

- [@ericsfraga, @jmiserez](https://github.com/jmiserez/maxio/blob/ee15bcc86e4426acd5fc70e717468862dce29fb8/tmp-rm16-ericsfraga-rm2svg.py), [@peerdavid](https://github.com/peerdavid/rmapi/blob/master/tools/rM2svg), [@phill777](https://github.com/phil777/maxio) and [@lschwetlick](https://github.com/lschwetlick/maxio/blob/master/rm_tools/rM2svg.py) for updating rM2svg to the most recent `.rm` format

- [@lschwetlick](https://github.com/lschwetlick) also wrote [rMsync](https://github.com/lschwetlick/rMsync) and two blog posts about reMarkable-related software [[1](http://lisaschwetlick.de/blog/2018/03/25/reMarkable/), [2](http://lisaschwetlick.de/blog/2019/06/10/reMarkable-Update/)]

- [@soulisalmed](https://github.com/soulisalmed) who wrote [biff](https://github.com/soulisalmed/biff)

- [@benlongo](https://github.com/benlongo) who wrote [remarkable-highlights](https://github.com/benlongo/remarkable-highlights)

For more reMarkable resources, check out the great [awesome-reMarkable](https://github.com/reHackable/awesome-reMarkable) and [remarkablewiki.com](https://remarkablewiki.com/).

## Disclaimers

This is free open source software from hobby project of an enthusiastic reMarkable user. 

There is no warranty whatsoever. Use it at your own risk.

> The author(s) and contributor(s) are not associated with reMarkable AS, Norway. reMarkable is a registered trademark of reMarkable AS in some countries. Please see https://remarkable.com for their products.
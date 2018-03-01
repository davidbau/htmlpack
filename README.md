Webcrush
========

Webcrush is a simple utility for minifying and compressing HTML.

Crushing an HTML file discourages casual inspection of the code,
which may be useful, for example, for posting an interactive puzzle
or a student problem-set project without broadcasting spoilers
in cleartext in the HTML.

## Usage

Webcrush can be used at [this][1] page which itself is a crushed
version of [this cleartext page][2]. The web interface provides
two options:

  * LZ compression is optional, on by default.  Unchecking this
    can result in smaller files when LZ overhead dominates.
  * Absolute-url scripts (such as CDN scripts) can be pulled
    out of the LZ compressed code, on by default.  Chrome
    warns about performance penalties when CDN scripts are
    generated by document.write, and this avoids that warning.

There is also a [nodejs API][3] and a nodejs [command-line interface][4]
that provide more options which can be read about in the source.

[1]: https://rawgit.com/davidbau/webcrush/master/crushed.html
[2]: https://github.com/davidbau/webcrush/blob/master/webcrush.html
[3]: https://github.com/davidbau/webcrush/blob/master/lib/webcrush.js
[4]: https://github.com/davidbau/webcrush/blob/master/bin/webcrush

## Caveats

Note that crushing is not good for hiding serious secrets in HTML,
because it is not difficult to decompress and reveal the code.
Also, crushing can grow short documents, because the code is
expressed in base64 (which grows 25%) and LZ decompression code
must be packaged in the document (which adds 473 bytes). It
is better to rely on HTTP gzip encoding for saving bandwidth.

## Credits

Compression is by Sam Hocevar's lz-string.  Minification is by
Juriy Zaytsev's HTML minifier, which in turn relies on the awesome
UglifyJS by Mihai Bazon and CleanCss by Jakub Pawlowicz.

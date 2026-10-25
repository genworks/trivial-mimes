Genworks fork
-------------
This is the Genworks fork of trivial-mimes, kept on Genworks' GitLab
(gitlab.genworks.com, genworks/trivial-mimes) and mirrored to
https://github.com/genworks/trivial-mimes.  It differs from upstream
(https://codeberg.org/shinmera/trivial-mimes) in one way: `T`, `NIL` and
`OTHERWISE` are written in lower case in the code, so the library also
loads under a case-sensitive reader, such as Allegro CL's modern mode.
Nothing changes under an upper-casing reader.

About Trivial-Mimes
-------------------
This is a teensy library that provides some functions to determine the mime-type of a file. As I've had a need for this kind of functionality more than once now and haven't found any suitably lightweight alternative I quickly whipped this up.

How To
------
```
(mimes:mime #p"~/something.png")
```

Upon loading, trivial-mimes builds a mime-type database from the local `mime.types` file or a copy thereof from its own source directory. This database is a simple association of file extension to mime-type (see `mime-lookup`). If the mime lookup in the database fails, it will instead try to consult the `file` shell utility on unix systems (see `mime-probe`). If that too doesn't work, it falls back onto a default.

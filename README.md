# sensitive.el --- A dead simple way to load sensitive information

CC BY Tim Visher

Author: Tim Visher <tim.visher@gmail.com>  
Keywords: convenience  
Package-Requires: ((emacs "24") (sequences "0.1.0))  
Version: 1.0.0

This file is not part of GNU Emacs.

This work is licensed under the Creative Commons Attribution 3.0
Unported License. To view a copy of this license, visit
<http://creativecommons.org/licenses/by/3.0/> or send a letter to
Creative Commons, 444 Castro Street, Suite 900, Mountain View,
California, 94041, USA.

## Commentary:

This package is intended to make it dead simple to include
sensitive information in your public .emacs file. More people
publishing their .emacs file is a good thing for the world of Emacs
users and the more facilities people have for hiding the
information they need to load without having to jump through hoops
to load it should make that easier.

## Usage:

To use sensitive, place directories and files in `sensitive-root`
that correspond to modes and variables.

For instance. If the contents of `sensitive-root` (by default
`~/sensitive`) are as follows:

    {sensitive-root}
    ├── erc
    │   └── erc-password -> "password as a string"
    └── pivotal-tracker
        └── pivotal-api-token -> "api token as a string"

`sensitive` will cause the forms

    (eval-after-load 'erc
      '(setq 'erc-password "password as a string"))
    
    (eval-after-load 'pivotal-api-token
      '(setq pivotal-api-token "api token as string"))

to be evaled.

It's important to note that the contents of the variable files
should be exactly what you would have used if you were to write the
`eval-after-load` form yourself. In other words, there is no
defaulting to strings or something; the form is actually read via
the elisp reader and inserted into the `eval-after-load` form.

That's all there is to it. Happy hunting!

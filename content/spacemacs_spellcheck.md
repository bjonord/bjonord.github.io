+++
title = "Spacemacs - spell-checking with hunspell(OS X)"
date = 2021-03-07
+++

Sometimes it is nice to have some spellchecking squiggles even in your code editor.

## Steps to get up and running

1. Add the `spell-checking` layer in your dotfile.
1. Install `hunspell` using your package manager(brew in my case)
1. download some .aff and .dic files, found this repository to be a useful source: <https://github.com/wooorm/dictionaries>

You could have any number of dictionaries you would like and alter between them as you see fit, but to start out I suggest picking what you are hoping to use as a default.
I chose to use `en`, which you can download like so:

```
> wget https://github.com/wooorm/dictionaries/blob/main/dictionaries/en/index.dic -O en.dic
> wget https://github.com/wooorm/dictionaries/blob/main/dictionaries/en/index.aff -O en.aff
```

*I named my files`en.dic` and `en.aff`, but you could name them whatever you prefer, just remember to set your `DICTIONARY` env appropriately(if you need to do that).*
*Best practice is to use the language codes i.e. en_GB, sv_SE*

I made sure to soft link these files as follows as well:

```
> ln -s en.dic default.dic
> ln -s en.aff default.aff
> ln -s en.dic english.dic
> ln -s en.aff english.aff
```

The default is what hunspell uses if you do not pick a dictionary(`hunspell -d /dev/null` and you'll see), however this does not transfer to `ispell` in emacs.
`ispell` will use what matches your `LANG` or `DICTIONARY` environment variables so I personally set `DICTIONARY` to match up with my choice, but you could do one of the following:

- Change your emacs `LANG` env
- Rename the dictionary files to match you `LANG` env.
- Change your `DICTIONARY` env

I went with the latter, as my knee jerk feeling to alter the `LANG` felt wrong.
To set your `DICTIONARY` env, the easiest is to open up your `~/.spacemacs.env` file and just add: `DICTIONARY=<preferred lang>`; in my case: `DICTIONARY=en`.

A swift: `SPC + f + e + R` and you should be getting all the red squiggles you could hope for!


# Resources

<https://develop.spacemacs.org/layers/+checkers/spell-checking/README.html>
<https://www.emacswiki.org/emacs/InteractiveSpell>

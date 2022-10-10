# Banner

A standard for making color palettes. An extension of
[base16](https://github.com/chriskempson/base16). Primarily for use in GUI
programs where the text-related style specifications of base16 don't cut it.

## How To Make a Banner Palette

You first need your base16 palette colors. They will be referred to as
``base0X`` where ``X`` is the hexadecimal index of the color. These are all you
will need. Eight shades and eight accents. The base16 [styling specifications](https://github.com/chriskempson/base16/blob/main/styling.md)
should serve as good guidelines.
Additionally, the following requirements are added:

- ``base03-base07`` should be readable against ``base00`` and vice-versa.
- ``base00-base02`` should be readable against ``base05`` and vice-versa.
- ``base00-base03`` should be readable against ``base06`` and vice-versa.
- ``base00-base04`` should be readable against ``base07`` and vice-versa.

You will then specify the following special colors:

- ``highlight`` : primary highlight color.
- ``hialt0``    : secondary highlight color.
- ``hialt1``    : another secondary highlight color.
- ``hialt2``    : *another* secondary highlight color.
- ``urgent``    : usually red.
- ``warn``      : usually yellow.
- ``confirm``   : usually green.
- ``link``      : usually blue.

If you are making a monochromatic colorscheme, make ``hi*`` colors similar or
the same. ``highlight`` should be used the most, and all other highlights
should appear equally often, and not much less often than highlight. This means
that most coherent color schemes will have hi2-4 set to the same thing. Three
or more different highlights can lead to unexpected random contrasts in things
that are not functionally different.

You will then specify preferred foreground colors for those special colors.
Referred to by the prefix ``pfg-``. These are colors that are readable when
written in text over the original colors. For example, if ``warn`` is
``f6c177``, and ``base00`` is ``191724``, then you might make ``pfg-warn``
equal to ``191724``, because dark purple (``base00``) is readable on yellow
(``warn``).

Almost there. Now you need to specify ``ansiXX``, values 0-8. These are used
in applications that use ansi colors, namely terminal emulators. These are
meant for use *only* in these programs and nowhere else, if possible. Part of
the idea of banner is that programs respect ``highlight``, and I don't want
programs to have hardcoded use of certain colors. That being said, here are
the names and expected values of these colors:

- ``ansi00``: black
- ``ansi01``: red
- ``ansi02``: green
- ``ansi03``: yellow
- ``ansi04``: blue
- ``ansi05``: magenta
- ``ansi06``: cyan
- ``ansi07``: white

It's okay to take some liberty with these colors, especially black and white
which just need to be percieved as dark and light colors respectively and can
have some hue.

See [example.yaml](example.yaml) for the banner palette of rosepine.

## Motivations

Base16 tends to reliably produce decent looking programs, given a good palette.
However, if you are making your own palette, it can be a nightmare: you have to
change certain entries in the palette so that just one program using the
palette can look good or even just be readable. I believe this is because
the base16 styling specifications are for code/terminals, and don't always
carry over well to GUI programs. In theory, this could be fixed
by simply applying a different template to that program's base16 builder. In
practice, though, most programs don't offer multiple templates, if base16
support at all. Banner seeks to solve this by semantically naming colors, so
that the functionality of templates can be embedded in the palette.

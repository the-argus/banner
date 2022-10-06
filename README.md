# Banner

A standard for making color palettes and templates. An extension of
[base16](https://github.com/chriskempson/base16). Primarily for use in GUI
programs where the text-related style specifications of base16 don't cut it.

## How To Make a Banner Palette

You first need your base16 palette colors. They will be referred to as
``base0X`` where ``X`` is the hexadecimal index of the color. These are all you
will need. Eight shades and eight accents. The base16 [styling specifications](https://github.com/chriskempson/base16/blob/main/styling.md)
should serve as good guidelines, although the colors may not be used for the
purposes after the next steps. Additionally, the following requirements are
added:

- ``base03-base05`` should be readable against ``base00`` and
vice-versa.
- ``base05`` should be readable against ``base01`` and vice-versa.
- ``base06`` should be readable against ``base02`` and vice-versa.
- ``base07`` should be readable against ``base03`` and vice-versa.

You will then specify preferred foreground colors for ``base08`` through
``base0F``. Referred to by the prefix ``pfg``. These are colors that are
readable when written in text over the original colors. For example, if
``base08`` is ``f6c177``, and ``base00`` is ``191724``, then you might make
``pfg8`` equal to ``base00``, because dark purple (``base00``) is readable on
yellow (``base08``).

You will then specify the following special colors:

- ``highlight``: primary highlight color.
- ``hialt0``: secondary highlight color.
- ``hialt1``: another secondary highlight color.
- ``hialt2``: *another* secondary highlight color.
- ``urgent``: usually red.
- ``warn``: usually yellow.
- ``confirm``: usually green.
- ``link``: usually blue.

If you are making a monochromatic colorscheme, make ``hi*`` colors similar or
the same. ``hi1`` should be used the most, and all other highlights should
appear equally often, and not much less often than hi1. This means that most
coherent color schemes will have hi2-4 set to the same thing. Three or more
different highlights can lead to unexpected random contrasts in things that are
not functionally different.

See [example.yaml](example.yaml) for the banner palette of rosepine.

## Motivations

Base16 tends to reliably produce decent looking programs, given a good palette.
However, if you are making your own palette, it can be a nightmare: you have to
change certain entries in the palette so that just one program using the
palette can look good or even just be readable. I believe this is because
the base16 styling specifications are for code/terminals, and don't alwaysI
carry over well to GUI programs. In theory, this could be fixed
by simply applying a different template to that program's base16 builder. In
practice, though, most programs don't offer multiple templates, if base16
support at all. Banner seeks to solve this by semantically naming colors, so
that both creating palettes and using them in programs is intuitive.

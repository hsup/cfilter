# cfilter
Unix grep like perl script utility that adds color highlights to filtered text

```
Usage:
    cfilter [options] [+|-[<color>]:]<pattern> ...

    Takes input from stdin, applies color to, and filters out, lines of text
    that match specified patterns, and prints output to stdout.

Options:
    -I        : Case sensitive pattern matching.
    -c NUM    : Show context (NUM lines) before & after matched patterns.
                Default set to 1.
    +0        : Print all non pattern matching lines in normal text color.
                Turns off default context.
    -0        : Filter & remove all non pattern matching lines.
                Turns off default context.
    +         : Includes lines that contain specified pattern.
    -         : Excludes lines that contain specified pattern.
    <color>   : 1-8 for level of color intensity:
                red, magenta, blue, cyan, green, yellow, white, black.
    <pattern> : May be in regexp.

    -t, --tee <out_file> : also saves unmodified stdin to <out_file>.
    --config (TODO)      : Configure default color settings.
    -h, --help, --usage  : Print usage.

Examples:
    adb logcat | cfilter +3:"ActivityManager.*Intent"
        Hi-lite in blue logs of ActivityManager processing intents.

    adb logcat | cfilter +1:exception +1:"E/" +2:warning +2:"W/"
        Hilite all errors / exceptions in red, and warnings in magenta.

    adb logcat | cfilter photo sync
```

## What is this thing?

progressbar is a C-class (it's a convention, dammit) for displaying attractive
progress bars on the command line. It's heavily influenced by the ruby ProgressBar
gem, whose api and behaviour it imitates.

## Ok, what the hell is a C-class, and how do I use one?

progressbar is implemented in pure C99, but using a vaguely object-oriented convention.

Example usage:

```c
progressbar *progress = progressbar_new("Loading",100);
for(int i=0; i < 100; i++)
{
  // Do some stuff
  progressbar_inc(progress);
}
progressbar_finish(progress);
```

## Why did you do this?

One of the things I miss most when I'm writing C instead of Ruby is the
how ridiculously easy it is to write user-friendly, informative CLI apps
in Ruby. A big part of that, at least for me, is the ProgressBar gem --
and since most of the time when I'm writing C I'm doing so because I need
a tool to handle some long-running, processor-intensive task, I'd really
like to have a way of seeing at a glance how much time is remaining and
how far along we've gotten. Enter progressbar!

## Can I use it?

Of course, if you're so inclined. progressbar is licensed under a simplified BSD license,
so feel free to take it and run with it. Details can be found in the `LICENSE` file.

## Why doesn't it compile?

If progressbar fails to build because `termcap.h` isn't found, you're probably missing the ncurses dev libraries.

```
gcc -c -std=c99 -Iinclude lib/progressbar.c
lib/progressbar.c:13:45: fatal error: termcap.h: No such file or directory
compilation terminated.
```

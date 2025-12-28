# Regular Expression Dialects 

Regular expressions have evolved over the years, and the various tools
that handle regular expressions have different capabilities and slightly
different syntax.

In particular, the original Unix search tool *grep* came in three
varieties:

- `fgrep`, which could search only for fixed text patterns
- `grep`, which handled basic regular expressions
- `egrep`, which handled an extended form of regular expressions

The GNU project originally shipped all three commands, but fgrep and
egrep were never fully standardized, so they were removed from the Posix
standard in 2001. They were recently also removed from the GNU project.

Unlike the original Unix grep, the GNU grep can handle the full extended
regular expression syntax, in either of two ways:

- To use the special characters (called "meta-characters") 
preceed them with a backslash. In other words, while a backslash makes 
special characters like . or ordinary, it also makes ordinary 
characters into special characters.

- Alternately, use the `-E` option to make grep understand extended 
regular expressions, which causes metacharacters to become special characters.

Other tools, such as sed, similarly require backslashes in front of some
of the extended regexp meta-characters (or, if you're using a GNU
version of sed, you can use the -E option to enable extended regular
expressions, just like GNU grep).

The Perl language introduced one of the most powerful and consistent
versions of the regular expression language. There has been increasing
consensus around "Perl-Compatible Regular Extensions" (aka PCRE) and
that dialect is available in many tools (including GNU grep via the `-P`
option, as well as the [PCRE/PCRE2
library](https:*www.pcre.org/ "wikilink") for C and C++ programs, which
is used in many software packages including Safari and Apache httpd).

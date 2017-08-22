On Arch Linux, I use the following command to print documents:

```Bash
PRINTER="the_printer_name" lpr ~/my_doc.pdf
```

It was always working yet broken with the latest version. A mysterious error appears:

```Bash
$ PRINTER="the_printer_name" lpr ~/my_doc.pdf
lpr: Error - scheduler not responding.
```

By tracing the codes, seems ```$PRINTER``` does not work. Now I have to use another pattern to specify the printer:

```Bash
$ lpr -P "the_printer_name" ~/my_doc.pdf
```

After debugging and tracing codes, it turns out that the bug is already fixed upstream [1]. I applied the package and rebuild CUPS. Now everything is fine :)

[1] https://github.com/apple/cups/commit/c536b6c583abd9ea1b750f15e887b313ed7ad951

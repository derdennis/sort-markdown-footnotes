## Sort Markdown Footnotes

This is a Python script to sort Markdown footnote markers like `[^fn1]` into
their order of appearance in the text.

It reads a Markdown file via standard input and tidies the containing
Multimarkdown footnotes. The footnote texts will also be numbered in
the order they appear in the text and placed at the bottom
of the file.

The needed Markdown footnotes syntax can be easily created by using Vim and
[my fork of the vim-markdownfootnotes plugin][1].


### Function

Basically, it looks a lot like this:

![Screenshot](https://raw.github.com/derdennis/sort-markdown-footnotes/master/footnote-sorting.gif)


Markdown does not care a bit about the order in which the footnotes appear in
the text. Both texts above render to the exact same HTML. But it is just *much*
nicer looking, isn't it?

#### Commandline usage

Just place the script somewhere in your path , `~/bin` comes to mind, and use
it in a standard Unix pipe way:

    cat ugly-text.markdown | sort_footnotes > beautiful-text.markdown

#### Usage with Vim

I defined the following mapping in my `.vimrc`:

    " Sort footnotes into order of appearance
    nnoremap <leader>fs mm :%! ~/bin/sort_footnotes<CR> `m :delmarks m<CR>

And now just call `<Leader>fs` whenever I feel my footnotes should get sorted.

### Credits

The whole script is based on the post [Tidying Markdown reference links][2] by
Dr. Drang.

### Caveats

Do *not* place footnote reference links at the start of a line, bad things will
happen, your footnotes will be eaten by a grue.


[1]: https://github.com/derdennis/vim-markdownfootnotes
[2]: http://www.leancrew.com/all-this/2012/09/tidying-markdown-reference-links/

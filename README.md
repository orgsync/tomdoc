TomDoc
======

TomDoc is a flexible code documentation specification with human readers in
mind. Using a few simple rules and zero special syntax you can produce
great looking documentation for both humans and machines.

Just follow these four easy steps:

1. Describe your method
2. Optionally list and describe its arguments
3. Optionally list some examples
4. Explain what your method returns

Like this:

    # Duplicate some text an abitrary number of times.
    #
    # text  - The String to be duplicated.
    # count - The Integer number of times to duplicate the text.
    #
    # Examples
    #   multiplex('Tom', 4)
    #   # => 'TomTomTomTom'
    #
    # Returns the duplicated String.
    def multiplex(text, count)
      text * count
    end

See [the manual][man] or [the spec][spec] for a more in-depth
analysis.

It's important to note that TomDoc is complimentary to most existing
documentation systems. Because it introduces no syntax of its own,
merely conventions, you can use it with Ruby's RDoc or any other
existing documentation format.

More than anything it's a guide for documenting methods and
classes.


tomdoc.rb
---------

This repository also contains tomdoc.rb, a Ruby library for parsing
TomDoc and generating pretty documentation from it.


Installation
------------

    easy_install Pygments
    gem install ruby_parser -v 2.0.4
    gem install colored
    git clone git@github.com:defunkt/tomdoc.git
    cd tomdoc
    rake gem:install

This will generate a RubyGem and run `gem install GEM` to install
it. You can uninstall it at any time:

    gem uninstall tomdoc

tomdoc.rb has been tested with Ruby 1.8.7-p173 and REE 1.8.7-p248.


Usage
-----

    $ tomdoc file.rb
    # Prints colored documentation of file.rb.

    $ tomdoc file.rb -n STRING
    # Prints methods or classes in file.rb matching STRING.

    $ tomdoc fileA.rb fileB.rb ...
    # Prints colored documentation of multiple files.

    $ tomdoc -f html file.rb
    # Prints HTML documentation of file.rb.

    $ tomdoc -i file.rb
    # Ignore TomDoc validation, print any methods we find.

    $ tomdoc -h
    # Displays more options.


Ruby API
--------

Fully TomDoc'd. Well, it will be.

For now:

    $ tomdoc lib/tomdoc/source_parser.rb


Formats
-------

### Console

    tomdoc lib/tomdoc/source_parser.rb -n token

![pattern](http://img.skitch.com/20100408-mnyxuxb4xrrg5x4pnpsmuth4mu.png)

### HTML

    tomdoc -f html lib/tomdoc/source_parser.rb | browser

or

    tomdoc -f html lib/tomdoc/source_parser.rb > doc.html
    open doc.html

![html](http://img.skitch.com/20100408-dbhtc4mef2q3ygmn63csxgh14w.png)

[man]: https://github.com/defunkt/tomdoc/blob/tomdoc.rb/man/tomdoc.5.ronn
[spec]: https://github.com/defunkt/tomdoc/blob/tomdoc.rb/tomdoc.md

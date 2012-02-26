# bibtex-utils

This is just a few simple tools to make it easier to work with BibTeX files. These have been extracted from [researchr](http://github.com/houshuang/folders2web), a [research workflow](http://reganmian.net/wiki/researchr:start).

I am planning to expand this, but currently there are just two tools. I would welcome any improvements. Feel free to raise issues if something is not working, or you have questions.

## anyparse
Two different tools for turning selected text into a BibTeX citation, one looks up the [DOI](http://www.doi.org/) reference in [CrossRef](http://crossref.org/), and the other uses the AnystyleParser library to try to heuristically generate a BibTeX citation. 

Usage:

````ruby
txt = "doi:10.1503/cmaj.110218"
result = BibTeX-Utils::Anyparse.parse(txt)
=> 

txt = "Arguello, J., Butler, B.S., Joyce, E., Kraut, R., Ling, K.S., and Wang, X. Talk to me: foundations for successful individual- group interactions in online communities. Proc. CHI 2006, ACM (2006), 959-968."
result = BibTeX-Utils::Anyparse.parse(txt)
=>
```

You can also specify the doi parser or the anystyle parser.

```ruby
result = BibTeX-Utils::Anyparse.parse(txt, :anystyle)
result = BibTeX-Utils::Anyparse.parse(txt, :doi)
```

And you can directly parse the contents of the clipboard

```ruby
result = BibTeX-Utils::Anyparse.parse(:clipboard)
result = BibTeX-Utils::Anyparse.parse(:clipboard, :doi)
```

If you specify :clipboard, you can also use Anyparse.parse!, which writes the changes back to the clipboard (useful if you are going to paste the text into a citation manager, etc.)

```ruby
BibTeX-Utils::Anyparse.parse!(:clipboard)
BibTeX-Utils::Anyparse.parse!(:clipboard, :anystyle)
```

# Contributing to bibtex-utils
 
* Check out the latest master to make sure the feature hasn't been implemented or the bug hasn't been fixed yet.
* Check out the issue tracker to make sure someone already hasn't requested it and/or contributed it.
* Fork the project.
* Start a feature/bugfix branch.
* Commit and push until you are happy with your contribution.
* Make sure to add tests for it. This is important so I don't break it in a future version unintentionally.
* Please try not to mess with the Rakefile, version, or history. If you want to have your own version, or is otherwise necessary, that is fine, but please isolate to its own commit so I can cherry-pick around it.

# Copyright

Copyright (c) 2012 Stian Håklev. BSD License.
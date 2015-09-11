---
layout: default
title: Projects

projects:
  - name: Programming Languages
    items:
      - name: Apricot
        href: http://github.com/apricot-lang/apricot
        info: Ruby, 2012–2013
        desc: Bytecode-compiled Lisp on [Rubinius](http://rubini.us) with Ruby
              interop

      - name: Fiddle
        href: http://github.com/tsion/fiddle
        info: C++11, 2014–2015
        desc: Statically-typed imperative language compiled with
              [LLVM](http://llvm.org/)

      - name: Stako
        href: http://github.com/tsion/stako
        info: ooc, 2010–2011
        desc: "[Stack-based](https://en.wikipedia.org/wiki/Stack-oriented_programming_language)
              language compiled with LLVM"

      - name: Rasp
        href: http://github.com/tsion/rasp
        info: Ruby, 2010
        desc: Interpreter for a Lisp-like language with Ruby interop

      - name: rbf
        href: http://github.com/tsion/rbf
        info: Ruby, 2012
        desc: Simple [Brainfuck](https://en.wikipedia.org/wiki/Brainfuck)
              interpreter

  - name: Research
    items:
      - name: FastTap
        href: http://github.com/tsion/FastTap
        info: Android, 2013
              \[[pdf](http://hci.usask.ca/uploads/341-CHI-paper-988.pdf)\]
              \[[video](http://youtu.be/1Yz-qQ8RA5g)\]
        desc: Fast multi-touch selection technique for tablets

      - name: Pinta CommandMaps
        href: http://github.com/tsion/Pinta
        info: C#, 2013
              \[[pdf](http://joey.scarr.co.nz/pdf/realworldcommandmaps.pdf)\]
        desc: New interface for [Pinta](http://pinta-project.com/)
              taking advantage of spatial memory

  - name: Operating Systems
    items:
      - name: spideros
        href: https://github.com/tsion/spideros
        info: C++11, 2011–2014
        desc: Basic kernel written in C++11

      - name: porcupine
        href: https://github.com/tsion/porcupine
        info: Clay, 2010–2011
        desc: Basic kernel written in [Clay](http://claylabs.com/clay)

      - name: oos
        href: http://github.com/tsion/oos
        info: ooc, 2009–2010
        desc: Basic kernel written in [ooc](https://ooc-lang.org/)

  - name: Web
    items:
      - name: solson.me
        href: http://github.com/tsion/tsion.github.io
        info: Jekyll, 2013–2015
        desc: This website right here

      - name: What Are They Doing?
        href: https://github.com/tsion/watd
        info: Node.js, 2015
        desc: Live status dashboard for a set of users across many web
              services

  - name: IRC
    items:
      - name: enfin
        href: https://github.com/tsion/enfin
        info: C, 2012
        desc: Basic IRC bot in C

      - name: reggie
        href: https://github.com/tsion/reggie
        info: Ruby, 2011–2012
        desc: IRC bot for Perl-style regex replacement

      - name: frinkbot
        href: https://github.com/tsion/frinkbot
        info: Ruby, 2011–2012
        desc: IRC bot for [Frink](http://futureboy.us/frinkdocs/) code
              evaluation

      - name: on_irc
        href: http://github.com/tsion/on_irc
        info: Ruby, 2008–2012
        desc: Event-driven Ruby IRC client library

  - name: Miscellaneous
    items:
      - name: dotfiles
        href: http://github.com/tsion/dotfiles
        desc: My configuration files for
              [vim](http://www.vim.org/),
              [fish](http://fishshell.com/),
              [i3](http://i3wm.org/), etc.

      - name: do_stuff
        href: http://github.com/tsion/do_stuff
        info: Ruby, 2011
        desc: Minimalistic command line todo-list manager
---

<h2 class="text-center">Projects</h2>

{% for category in page.projects %}
  <h3>{{ category.name }}</h3>

  <div class="project-category">
    {% for project in category.items %}
      <div class="project">
        <h4><a href="{{ project.href }}">{{ project.name }}</a></h4>
        {% if project.info %}
          <small>{{ project.info | markdownify }}</small>
        {% endif %}
        {{ project.desc | markdownify }}
      </div>
    {% endfor %}
  </div>
{% endfor %}

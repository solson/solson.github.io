---
layout: default
title: Projects

projects:
  - name: Programming Languages
    items:
      - name: Apricot
        href: http://github.com/apricot-lang/apricot
        info: Ruby, 2012–2013
        desc: Clojure-like Lisp on Rubinius

      - name: Stako
        href: http://github.com/tsion/stako
        info: ooc, 2010–2011
        desc: Stack-based language using LLVM

  - name: Research
    items:
      - name: FastTap
        href: http://hci.usask.ca/publications/view.php?id=341
        info: Android, 2013
        desc: A faster selection technique for tablets
              \[[video](http://youtu.be/1Yz-qQ8RA5g)\]

      - name: Pinta Thing
        href: #
        info: C#, 2013
        desc: Lorem ipsum dolor sit amet

      - name: Kinect Arms Thing
        href: #
        info: C#, 2013
        desc: Lorem ipsum dolor sit amet

  - name: Miscellaneous
    items:
      - name: do_stuff
        href: http://github.com/tsion/do_stuff
        info: Ruby, 2011
        desc: Minimalistic command line todo-list manager

      - name: oos
        href: http://github.com/tsion/oos
        info: ooc, x86 ASM, 2009–2011
        desc: Operating system written in ooc and assembly

      - name: on_irc
        href: http://github.com/tsion/on_irc
        info: Ruby, 2008–2012
        desc: Event-driven Ruby IRC client library

      - name: solson.me
        href: http://github.com/tsion/tsion.github.io
        info: Jekyll, 2013–present
        desc: This website right here

      - name: dotfiles
        href: http://github.com/tsion/dotfiles
        desc: My configuration files for vim, fish, i3, etc.
---

<h2 class="text-center">Projects</h2>

{% for category in page.projects %}
  <h3>{{ category.name }}</h3>

  <div class="project-category">
    {% for project in category.items %}
      <div class="project">
        <h4><a href="{{ project.href }}">{{ project.name }}</a></h4>
        <small>{{ project.info }}</small>
        {{ project.desc | markdownify }}
      </div>
    {% endfor %}
  </div>
{% endfor %}

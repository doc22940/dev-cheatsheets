---
layout: home
---
# Home


> {{ site.description }}

Welcome to **Dev Cheatsheets** - a quick reference for showing you how to use a CLI tool, language or library by focusing on syntax and real world examples. While keeping explanation paragraphs to a minimum.

<div align="center" style="padding-bottom: 1em;">
    <a href="{{ site.baseurl }}{% link cheatsheets/index.md %}">
        <img src="https://img.shields.io/badge/all_cheatsheet_topics-blue?style=for-the-badge"
            alt="Go to cheatsheets"/>
    </a>
</div>


## Featured topics

### Scripting

<div class="flex-container">
    <a href="{{ site.baseurl }}{% link cheatsheets/python/index.md %}">
        <div>
            {% include logo.html name="python" %}
            <span>Python</span>
        </div>
    </a>
    <a href="{{ site.baseurl }}{% link cheatsheets/javascript/index.md %}">
        <div>
            {% include logo.html name="javascript" %}
            <span>JavaScript</span>
        </div>
    </a>
</div>

### Static sites and docs

<div class="flex-container">
    <a href="{{ site.baseurl }}{% link cheatsheets/markdown/index.md %}">
        <div>
            {% include logo.html name="markdown" %}
            <span>Markdown</span>
        </div>
    </a>
    <a href="{{ site.baseurl }}{% link cheatsheets/jekyll/index.md %}">
        <div>
            {% include logo.html name="jekyll" %}
            <span>Jekyll</span>
        </div>
    </a>

</div>

### Command-line

<div class="flex-container">
    <a href="{{ site.baseurl }}{% link cheatsheets/version-control/git/index.md %}">
        <div>
            {% include logo.html name="git" %}
            <span>Git</span>
        </div>
    </a>
    <a href="{{ site.baseurl }}{% link cheatsheets/shell/index.md %}">
        <div>
            {% include logo.html name="gnubash" %}
            <span>Shell</span>
        </div>
    </a>

</div>


## Quick reference

A few commands or code snippets that I want to keep all in one place, instead of within each category like Shell or Grep.

```sh
grep -r TERM .
# find alias
fn TERM
```

```ruby
group :jekyll_plugins do
  # ...
end
```


## About

These are all in one place so you don't have to look at docs, man pages, tutorials. Sometimes, there are links to other Cheatsheet guides which do a good job.

This is not comprehensive, but, it covers definitions and usage examples which cover the basics and some common flows (leaving out the obscure things I'll probably never need and can always lookup if I need to).

There are a lot of tools and languages on this site here for my own reference and I hope you find something useful here too, by looking for something specific or just discovering what is here.

---
layout: custom_post
title: "Why I like Go: Porting Ruby's State Jacket"
date: 2013-03-23 09:51
comments: true
categories: [ruby, go, state machine]

author: Joshua Bowles
gravatar: 9608da7db688950cfd161f51feb648ba
github: jbowles
twitter: bowlescompling
---
I'm fairly new to professional software engineering and my start was not typical. I first started in acadmeia with Prolog and Lisp; my background is in formal/mathematical philosophy and linguistics. In the last few months I have spent concentrated blocks of time on learning Nodejs, Clojure, Scala, and now Go.

Beside the academic and professional development benefits of doing this, I have a practical reason: I dream of building a very fast, efficient, "smart", and easy to use logging tool. By "smart" I mean applying machine learning and natural language processing to the semi-structured data found in production logs. This means I need support for large matrix multiplication, among other things. Ruby and Python simply do not fit the bill (for me).

<!-- more -->

Don't get me wrong, I would love to do this in Ruby. I tried a couple times and did not like it. Additionally, I do not want to invest in Python given that it's so similar to Ruby. I'm not going to compare all the pros and cons of the different langauges mentioned in this post (you can find enough of that fud on HackerNews), instead, let's just explain my choices as highly personal and motivated by what felt like was the right way for me.

I was initially drawn to Clojure because it is virtually the only chance a developer has of getting paid to work with a Lisp, and then switched efforts to Scala because it's more realistic to convince your team to do something in Scala than it is Clojure. Nodejs is great and V8 is blazing, but once I read through a [Go Codewalk for Markov Chain random text generation](http://golang.org/doc/codewalk/markov/) I was hooked. It seemed to strike the right balance between:
* High level API of Ruby **AND** low level concerns of C
* *the right thing* Lisp **AND** *worse is better* C/Unix
  * See, for example [The Rise of "Worse is Better"](http://www.jwz.org/doc/worse-is-better.html)
* Feeling excited about **AND** responsible for good engineering decisions

## Porting Ruby to Go
[State Jacket](https://github.com/hopsoft/state_jacket) is a Ruby library for helping to "Intuitively define state machine like states and transitions".

{% blockquote Nate Hopkins, State Jacket https://github.com/hopsoft/state_jacket/blob/master/README.md README %}
StateJacket simplifies things by isolating the management of states & transitions. Events are left out, making it much easier to reason about what states exist and how they transition to other states.
{% endblockquote %} 

I spent about 6 hours initially porting 70 lines of Ruby to 70 lines of Go. Much of my time was spent in figuring out the right structure for the data/object; the rest with familiarizing myself with Go idioms. It is a simple project but I want to spend more time refining it until I create a Go package for it, for now you can see my initial work here:

{% gist 5228042 %}

!SLIDE
# The Move to Ruby 1.9.x #

![Siyelo](siyelo.png)

!SLIDE bullets incremental
# Ruby 1.9 #

* Why Upgrade
* Changes
* Gotchas
* Tasty Treats


!SLIDE bullets incremental
# Why upgrade #

* Syntax improvements
* Performance
* Encoding/Unicode
* Fibers (Threads)

!SLIDE  bullets incremental
# But I'm in a relationship...
* Most 1.8 gems now upgraded
* 1.8.7 support [only til 2012](http://www.ruby-lang.org/en/news/2011/10/06/plans-for-1-8-7/)



!SLIDE
# (Nice) Changes #

!SLIDE bullets incremental
# Interpreter #

* Uses faster YARV (Yet Another Ruby Interpreter)
* So will Ruby 2.0+

* Ruby 1.8; old MRI (Matz Ruby Interpreter)


!SLIDE bullets incremental
# String Encoding/Transcoding #

* Every string can have an associated coding
* E.g. ACSCII, UTF-8 etc
* Strings can be transcoded
* E.g convert UTF-8 to UTF-16


!SLIDE bullets incremental
# Fibers

    @@@ruby 
    require 'fiber'
    fiber = Fiber.new { Fiber.yield }
    fiber.resume while fiber.alive?

Courtesy [Tenderlove](https://gist.github.com/1318493)


!SLIDE bullets incremental
# RubyGems integration #

* you will not need to require 'rubygems'


!SLIDE bullets incremental
# Single Character Strings #

    ruby-1.9.2> ?a
     => "a"

    ruby-1.8.7> ?a
     => 97 


!SLIDE bullets incremental
# String Index #

    ruby-1.9.2> 'dog'[1]
     => "o" 

    ruby-1.8.7> "dog"[1]
     => 111 



!SLIDE
# Gotchas (from 1.8.7) #


!SLIDE bullets incremental
# Hash.index deprecated #

    ruby-1.9.2> {1=>2}.key(2)
     => 1 

    ruby-1.8.7> {1=>2}.index(2)
     => 1 


!SLIDE bullets incremental
# Hash Keys now unordered#

    ruby-1.9.2> {1=>1, 3=>3, 2=>2}
     =>  {1=>1, 3=>3, 2=>2} 

    ruby-1.8.7>  {1=>1, 3=>3, 2=>2}
     =>  {1=>1, 2=>2, 3=>3} 


!SLIDE smaller
# instance_methods() gives array of syms#

    ruby-1.9.2> {}.methods
     => [:rehash, :to_hash, ...

    ruby-1.8.7> {}.methods
     => ["find", "[]=", ...


!SLIDE smaller bullets incremental
# Block params now block-local #

    ruby-1.9.2> i=0; [1,2,3].each {|i|}; i
     => 0 
    
    ruby-1.8.7> i=0; [1,2,3].each {|i|}; i
     => 3 

!SLIDE smaller incremental
# No colon in Case statements #

    ruby-1.9.2> case true; when true: puts 'yeah'; end
    SyntaxError: (irb):3: syntax error, unexpected ':', 
    expecting keyword_then or ',' or ';' or '\n'

    ruby-1.8.7> case true; when true: puts 'yeah'; end
    yeah



!SLIDE
# Tasty Treats! #

!SLIDE
# .js style hashes #

    ruby-1.9.2> {key: 'someval'}
     => {:key=>"someval"} 

    ruby-1.8.7> {:key => 'someval'}


!SLIDE
# Shorthand inject #

    ruby-1.9.2> [1,2].inject(:+)
     => 3 


    ruby-1.8.7> [1,2].inject {|a,b| a+b}
     => 3 


!SLIDE smaller
# Shorthand Lambda #

    ruby-1.9.2> l = -> a,b {a+b}
     => #<Proc...

    ruby-1.9.2> puts l.(1,2)
    3
    
    ruby-1.9.2> puts l[1,2]
    3


    ruby-1.8.7>   l = lambda {|a,b| a+b}
     => #<Proc...
    
    ruby-1.8.7> puts l.call(1,2)
    3
   

!SLIDE
# Block local variables #

    > [1,2].each {|val; t| t=val; puts t}
    1
    2

!SLIDE bullets
# And much more...

* [Ruby-Lang.org](http://www.ruby-lang.org/)
* [Ruby 1.9: What to Expect](http://slideshow.rubyforge.org/ruby19.html#1)
* [Upgrading from 1.8.7 to 1.9.2](http://www.engineyard.com/blog/2011/upgrading-from-ruby-1-8-7-to-1-9-2-on-appcloud/)



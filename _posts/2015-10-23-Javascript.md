---
layout: post
section-type: post
title: Ruby Classes vs JavaScript Constructor Functions
category: JavaScript
tags: [ 'ruby', 'dbc' ]
---
So if you have been following along with my blog posts. Last week I wrote a blog post about Ruby classes. So I am gonna continue with the example that I used last week. If you look at the code below, you will see a Ruby class of Money.

~~~ruby
class Money
def initialize(denomination,serial_number,country)
  @denomination = denomination
  @serial_number = serial_number
  end
end
~~~

The same object would created in JavaScript like so:


{% highlight js %}
function Money(denomination,serial,country){
this.denomination = denomination,
this.serial_number = serial_number,
this.country = country
}
{% endhighlight %}

For review one would create a new Money class in Ruby like so:.

{% highlight js %}
jackson = Money.new(100,"1234","US")
{% endhighlight %}

In JavaScript this would be achieved by doing the following:
{% highlight js %}
jackson = new Money(100,"1234","US")
{% endhighlight %}
Now lets take the valid method for the Money class in Ruby, seen below.
{% highlight ruby linenos %}
    def valid
        if @serial_number.size = 10
            true
        else
            false
        end
    end
 {% endhighlight %}

  This is where one of the major differences between Ruby classes and the JavaScript Constructor Function differ between the languages. One can create a function that is available to all of the Money objects in JavaScript however it can't be done within the Constructor function. This would be achieved by creating a prototype in Javascript. A prototype is a JavaScript function that is available to all objects of that type. It can be done like so:

  {% highlight js %}
  Money.prototype.valid = function() {
      if(this.serial_number.length == 10)
          return true;
      }
  };
  {% endhighlight %}
  This will give every Money JS object the ability to check whether its valid or not.

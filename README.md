# learning-ruby
my learning notes on ruby



# sources
* https://www.ruby-lang.org/en/documentation/quickstart/
* https://www.codecademy.com/learn/learn-ruby


# comment

```ruby
#i'm a sinlg eline comment

=begin
I'm a 
multiline
comment!
=end

```


# puts(writeln)
ruby way of console out/print

```ruby
puts "hello world"
```
writes hello world and returns nil

# print(write)

# string methods: length, reverse, upcase, downcase
```ruby
puts "doruk".length
#5


puts "doruk".reverse
#kurod

puts "doruk".upcase
# DORUK
puts "doruk".downcase
#doruk

```

# nil
ruby equivalent of null

# math power
```ruby
3**3
```

means 3 to the power of 3. and returns 27 in this case.

# sqrt

```ruby
Math.sqrt(16)
# 4
```


# function
```ruby
def hi
puts "hello world"
end

```

call by hi or hi()


## with param and string interpolation
```ruby
def hi(name)
puts "Hello #{name}!"
end

```

again, call by **hi "doruk"** or **hi("doruk")**

## make param optional
```ruby
def hi(name="World")
puts "Hello #{name}!"
end

```



# capitalize a string
```ruby
"doruk".capitalize
# Doruk
```


# a class

```ruby
class Greeter
    def initialize(name = "World")
    @name = name
    end
    def say_hi
    puts "Hi #{@name}!"
    
    end
    def say_bye
    puts "Bye #{@name}, come back soon."
    end
    end


g = Greeter.new("Doruk")
g.say_hi
g.say_bye
```


# instance_methods

```ruby
Greeter.instance_methods

Greeter.instance_methods(false)

greeter.respond_to?("name")
```

try and see

# attr_accessor, attr_reader, attr_writer
* attr_reader :getter
* attr_writer   :setter
* attr_accessor :ikisi birlikte

biraz daha derin bir mevzu olabilir. kurcalamam lazım.



## attr_accessor
```ruby
class Greeter
attr_accessor :name
end

g = Greeter.new()

g.respond_to?("name")
#true

g.respond_to?("name=")
#true
```

## attr_reader
```ruby
class Greeter
attr_reader :name
end

g = Greeter.new()

g.respond_to?("name")
#true

g.respond_to?("name=")
#false
```

## attr_writer
```ruby
class Greeter
attr_writer :name
end

g = Greeter.new()

g.respond_to?("name")
#false

g.respond_to?("name=")
#true
```

# iteration
```ruby

5.times { puts "doruk" }
```
easy as that

# chain methods 
```ruby
name = "Doruk".downcase.reverse.upcase
```


# gets.chomp

gets is the Ruby method that gets input from the user. When getting input, Ruby automatically adds a blank line (or newline) after each bit of input; chomp removes that extra line. (Your program will work fine without chomp, but you’ll get extra blank lines everywhere.) - *codecademy*


# string interpolation/formatting

# last_name.capitalize!
* capitalize and assign. yani ! in-place assignment yapıyor.


# instance var, class var and accessor sample

```ruby
class Single
    @@count = 0

    def initialize(desc)
        @desc= desc
        @@count += 1
        puts "number: #{@@count} - desc: #{@desc}"
    end
    
    attr_accessor :desc

end

s1 = Single.new "class 1"
s2 = Single.new "class 2"
s3 = Single.new "class 3"

puts s1.desc

# accessing class variables from outside is not advised in ruby world as far as i got to know.
# therefore, below line throws error. 
#puts s3.count 
```

# thread un-safe singleton

```ruby
class SimpleSingleton

    def initialize()
        @count = 0
    end

    @instance = new             # create an instance of object
    private_class_method :new   # then make new method private

    def self.instance
        @instance               # return instance variable named instance when called
    end

    def Increment
        @count +=  1
    end

    attr_reader :count
end


# throws exc since no public new method is available
# s1 = SimpleSingleton.new 

s1 = SimpleSingleton.instance
s2 = SimpleSingleton.instance

s1.Increment
s1.Increment
s1.Increment

puts s1.count == s2.count
# true
```


# user input, string interpolation
```ruby
print "What's your first name?"
first_name = gets.chomp

print "What's your last name?"
last_name = gets.chomp

print "What's your city?"
city = gets.chomp


print "What's your state/province ?"
state = gets.chomp

print "#{first_name.capitalize!} #{last_name.capitalize!} is from #{city.capitalize!}, #{state.upcase!}"
```


# if, else, elsif
```ruby
if ( 1== 1)
puts "one equals one"
elsif (1==2)
puts "one equals two"
else 
puts "one equals anything else but one or two"
end
```

# include?
```ruby
if user_input.include? "s"
  puts "user input has s in it"
end
```


# gsub

replaces substrings. below replaces s with th

```ruby

user_input.gsub!(/s/, "th")

```



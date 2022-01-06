## Sources
- https://www.learnenough.com/ruby-on-rails-6th-edition-tutorial
- https://www.tutorialspoint.com/ruby/

## New Project

- `echo "gem: --no-document" >> ~/.gemrc`
- `gem install rails -v 6.1.4.1`
- `rails _6.1.4.1_ new hello_app`

## Project directory structure

- `app/` Core application (app) code, including models, views, controllers, and helpers
- `app/`assets Applications assets such as Cascading Style Sheets (CSS) and images
- `bin/` Binary executable files
- `config/` Application configuration
- `db/` Database files
- `doc/` Documentation for the application
- `lib/` Library modules
- `log/` Application log files
- `public/` Data accessible to the public (e.g., via web browsers), such as error pages
- `bin/rails` A program for generating code, opening console sessions, or starting a local server
- `test/` Application tests
- `tmp/` Temporary files
- `README.md` A brief description of the application
- `Gemfile` Gem requirements for this app
- `Gemfile.lock` A list of gems used to ensure that all copies of the app use the same gem versions
- `config.ru` A configuration file for Rack middleware
- `.gitignore` Patterns for files that should be ignored by Git

## Project files

- `config/routes.rb`: maps endpoints to controller methods
  - Add an entry like this: `{path} '{controller name without the '_controller part}#{method name}'`
  - - GET /users `index` page to list all users
    - GET /users/1 `show` page to show user with id 1
    - GET /users/new `new` page to make a new user
    - POST /users `create` create a new user
    - GET /users/1/edit `edit` page to edit user with id 1
    - PATCH /users/1 `update` update user with id 1
    - DELETE /users/1 `destroy` delete user with id 1

## Commands

- `rails generate scaffold {ModelName} {prop}:{type}`
- `rails db:migrate`


## Ruby

- Print to console: `puts {value}`

- New lines or semi-colons are considered the end of a statement. Use `\` to continue the statement in a new line

- Reserved keywords 
  ```
  BEGIN	do	next	then
  END	else	nil	true
  alias	elsif	not	undef
  and	end	or	unless
  begin	ensure	redo	until
  break	false	rescue	when
  case	for	retry	while
  class	if	return	while
  def	in	self	__FILE__
  defined?	module	super	__LINE__
  ```

- Create multi-line strings by using `<<{identifier}`, like so:
  ```ruby
  print <<foo
   This is the first way of creating
   here document ie. multiple line string.
  foo
  ```

- `BEGIN` and `END` run before and after the program's regular code
  ```ruby
  BEGIN {
   puts "Initializing Ruby Program"
  }
  ```

- 
  ```ruby
  # comment
  ```
-
  ```ruby
  =begin
  Multi-line comment
  =end
  ```

- Functions
  - All Ruby functions return a value. If not specified, it will be the value from the last expression
    ```ruby
    # Returns width
    def get_width
      width
    end
    ```

  ```ruby
  def hello
    puts "Hello Ruby!"
  end

  def hello_with_args(arg_1, arg_2)
    puts "Hello Ruby, but with arguments!"
  end

  hello
  hello_with_args("arg1", "arg2")
  hello_with_args "arg1", "arg2"
  ```

  ```ruby
  # arrow functions
  add_one_lambda = -> x { x + 1 }
  ```
- Classes
  - Static properties are always declared and read with `@@`
  - Instance properties are always declared and read with `@`

  ```ruby
  class Class
    CONSTANT = "Hello from constant"

    # Static property / class property
    @@prop = "static prop value"

    def hello
      puts "Hello Ruby!"
    end

    def hello_with_args(arg_1)
      put "Hello Ruby, but with arguments!"
    end

    def Class.static_method
      put "A static method"
    end

    def self.another_static_method
      put "Another static method"
    end
  end

  instance = Class. new

  puts Class::CONSTANT
  ```

  ```ruby
  class Class
    def initialize(prop_1, prop_2)
      # instance properties
      @prop_1 = prop_1
      @prop_2 = prop_2
    end

     # Called when object is converted to string
    def to_s
      "(#@prop_1,#@prop_2)"
    end
  end

  instance = Class.new("prop1 value", "prop2 value")
  puts "String representation of object is : #{instance}"
  ```

  - Inheritance
    ```ruby
    class BigBox < Box

    end
    ```

- Global Variables
  ```ruby
  $global_variable = "value"
  ```

- Pseudo variables
  - `self` − The object that is running the method
  - `true` − Value representing true.
  - `false` − Value representing false.
  - `nil` − Value representing undefined.
  - `__FILE__` − The name of the current source file.
  - `__LINE__` − The current line number in the source file

- Strings
  - Escape characters with `\`
  - Template strings
    ```ruby
    some_variable = "Hello"
    "Log #some_variable"
    ```

    ```ruby
    class SomeClass
      CONSTANT = "Hello from constant"

      @@static_property = "Hello from static propery"

      def initialize
        @instance_property = "Hello from instance property"
      end

      def log_constant
        puts  "Log #{CONSTANT}"
      end

      def log_static_property
        puts  "Log #@@static_property"
      end

      def log_instance_property
        puts  "Log #@instance_property"
      end
    end
    ```

    ```ruby
      # concatenate expressions
      puts "Multiplication Value : #{24 * 60 * 60}"
    ```

- Arrays
  ```ruby
  array = [  "fred", 10, 3.14, "This is a string", "last element", ]
  array.each do |i|
    puts i
  end
  ```

- Hashes
  ```ruby
  hash = { "red" => 0xf00, "green" => 0x0f0, "blue" => 0x00f }
  hash.each do |key, value|
    print key, " is ", value, "\n"
  end
  ```

- Ranges
  ```ruby
  range = (10..15)
  
  range.each do |n| 
    print n, ' ' 
  end

  range === 12 # true
  ```

- Operators
  - The usual ones: `+`, `-`, `*`, `/`, `%`, `**`
  - Methods that return booleans are prefixed with `?` (example: `1.eql?`)
  - `a <=> b`
    - Returns 0 if operands are equal
    - Returns 1 if first operand is greater
    - Returns -1 if first operand is smaller
  - `==`: loose equality (`1 == 1.0` is true)
  - `===`: test a specific case like ranges, regexes or check the instance of an object
    ```ruby
    (1..10) === 5
    (1..10).include?(5)

    /abc/ === 'abcdef'
    /abc/.match?('abcdef')
    
    String === 'foo'
    'foo'.is_a?(String)
    ```
  - `eql?`: strict equality (`1.eql?(1.0)` is false)
  - `equal?`: checks if object instances are the same
  - `=~` and `!~` are for pattern matching (Regex) and cannot be overrided

  - Operator overloading
    ```ruby
    class Box
      def initialize(w,h)     # Initialize the width and height
          @width,@height = w, h
      end

      def +(other)       # Define + to do vector addition
          Box.new(@width + other.width, @height + other.height)
      end

      def -@           # Define unary minus to negate width and height
          Box.new(-@width, -@height)
      end

      def *(scalar)           # To perform scalar multiplication
          Box.new(@width*scalar, @height*scalar)
      end
    end
    ```

- Assignments
  ```ruby
  # parallel assignment
  a, b, c = 10, 20, 30
  ```

- Conditions
  ```ruby

  x = 1
  if x > 2
    puts "x is greater than 2"
  elsif x <= 2 and x!=0
    puts "x is 1"
  else
    puts "I can't guess the number"
  end
  ```

  ```ruby
  # Switch case
  case expr0
  when expr1, expr2
    stmt1
  when expr3, expr4
    stmt2
  else
    stmt3
  end
  ```

- Loops
  ```ruby
  # while true
  while conditional do
    code
  end
  ```

  ```ruby
  # until it becomes true
  until conditional do
    code
  end
  ```

  ```ruby
  for i in 0..5
    if i.eql?(2)
      # same as 'continue' in other languages
      next
    end

    if i.eql?(3)
      # will run current iteration again
      retry
    end

    if i.eql?(4)
      # restarts loop and i is set back to zero
      redo
    end

    puts "Value of local variable is #{i}"
  end

  (0..5).each do |i|
    puts "Value of local variable is #{i}"

    if i.eql?(2)
      break
    end
  end
  ```

- Exceptions
  ```ruby
  begin
    do_something # exception raised
  rescue
    # handles error
    retry  # restart from beginning
  end
  ```

- Threads
  ```ruby
    def func1
      
    end

    t = Thread.new{
      func1()
      }
    t.join
    t.abort_on_exception = true # The program will exit if an uncaught exception is raised on the thread
    Thread.current["my_count"] = 1 # Set variables in the thread
  ```
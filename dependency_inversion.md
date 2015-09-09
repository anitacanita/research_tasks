[Source](http://blog.siyelo.com/solid-principles-in-ruby/)

## Dependency Inversion - Class

example without DI:

````
class Report  
  def initialize
    @body = "whatever"
  end

  def print
    XmlFormatter.new.generate @body
  end
end

class XmlFormatter  
  def generate(body)
    # convert the body argument into XML
  end
end
````

example with DI:

````
class Report  
  def initialize
    @body = "whatever"
  end

  def print(formatter)
    formatter.generate @body
  end
end

class XmlFormatter  
  def generate(body)
    # convert the body argument into XML
  end
end
````

Our Report class is no longer concerned with the specific type of format but rather can take a generic ‘generate’ method and convert the ‘body’ into the required format. This negates the need to instantiate the XmlFormatter (or any other Format) within our Report class and therefore makes this less dependant on specific details of another class. This in itself describes the principle of Dependency Inversion.

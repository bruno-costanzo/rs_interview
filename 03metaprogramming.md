# Metaprogramming in Ruby

# Metaprogramming is a technique for creating objects that can be used to extend the functionality of other objects.

# Example with Ruby

``` ruby
module Animal
  def eat
    ...
  end

  module ClassMethods
    def setup
      scope :disabled, -> { where(disabled: true) }
    end
  end
end

class Dog
  # Inject the instance methods
  include Animal

  # Inject the class methods
  extend Animal::ClassMethods

  # Run any setup code.
  setup
end
´´´


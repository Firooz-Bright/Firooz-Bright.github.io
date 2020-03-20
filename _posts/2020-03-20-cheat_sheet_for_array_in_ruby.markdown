---
layout: post
title:      "Cheat sheet for Array in Ruby "
date:       2020-03-20 04:00:08 +0000
permalink:  cheat_sheet_for_array_in_ruby
---


### ***Today I am going to talk about some array's functions in Ruby langauge.***

*The best way to learn about the array is to review the Ruby document and practice those funcionality. Here I am just going to address some of the most useful array functions. 
*
![](https://cdn-media-1.freecodecamp.org/images/1*HmGUFmEI1w7ClqD6YCSmJQ.pnghttp://)

Create a new array with values:
```
arr_with_stuff = ["value", "other_value"] 
arr_with_stuff2 = Array.new(["a", "b", "c"])
range_to_arr = (1..100).to_a 
```

Create an array of duplicate values: Sometimes it’s helpful to have an array filled with multiple, duplicates:
```
arr = Array.new(4, " ")
# -> [" ", " ", " ", " "]
```

Create an array of strings with a shortcut: use the %w shortcut to create an array of strings without quotes or commas:
```
arr = %w(Ruby JS Python  SQL)
# -> ["Rubyt", "JS", "Python", "SQL"]
```

Get the value at an index or a default value:  fetch will return the value at the index, or it will give the default argument, or code block value.
```
a = [ 11, 22, 33, 44 ]
a.fetch(1)               #=> 22
a.fetch(-1)              #=> 44
a.fetch(4, 'cat')        #=> "cat"
a.fetch(100) { |i| puts "#{i} is out of bounds" }
```
Check if a value is in the array: 
We need to find out sometimes the data we are dealing with is in the array we are working on it or not!
```
a = [ "a", "b", "c" ]
a.include?("b")   #=> true
a.include?("z")   #=> 
```

Add a value to the end of an array: The << is called a “shovel operator”, but you can also use  push. These methods modify the original array:

```
a = [ "a", "b", "c" ]
a.push("d", "e", "f")
        #=> ["a", "b", "c", "d", "e", "f"]
[1, 2, 3].push(4).push(5)
        #=> [1, 2, 3, 4, 5]
arr = %w(cat dog mouse)
arr << "cobra" 
# returns changed array
# -> ["cat", "dog", "mouse", "cobra"]
```

Add a value to the start of the array:
 These methods also modify the content of the original array.
```
a = [ "b", "c", "d" ]
a.unshift("a")   #=> ["a", "b", "c", "d"]
a.unshift(1, 2)  #=> [ 1, 2, "a", "b", "c", "d"]
```
Add a value to the middle of the array:
Sometimes we need to add data to the specific index of an array, in this case we can easily use insert with the selected indexs to modify our array.

```
a = %w{ a b c d }
a.insert(2, 99)         #=> ["a", "b", 99, "c", "d"]
a.insert(-2, 1, 2, 3)   #=> ["a", "b", 99, "c", 1, 2, 3, "d"]
```

Delete by value: 

```
a = [ "a", "b", "b", "b", "c" ]
a.delete("b")                   #=> "b"
a                               #=> ["a", "c"]
a.delete("z")                   #=> nil
a.delete("z") { "not found" }   #=> "not found"
```
Delete by any index:

```
a = ["ant", "bat", "cat", "dog"]
a.delete_at(2)    #=> "cat"
a                 #=> ["ant", "bat", "dog"]
a.delete_at(99)   #=> nil

```
Remove last value:
```
a = [ "a", "b", "c", "d" ]
a.pop     #=> "d"
a.pop(2)  #=> ["b", "c"]
a         #=> ["a"]
```
Combination of other arrays with each index of the first array:

```
[1,2,3].product([4,5])     #=> [[1,4],[1,5],[2,4],[2,5],[3,4],[3,5]]
[1,2].product([1,2])       #=> [[1,1],[1,2],[2,1],[2,2]]
[1,2].product([3,4],[5,6]) #=> [[1,3,5],[1,3,6],[1,4,5],[1,4,6],
                           #     [2,3,5],[2,3,6],[2,4,5],[2,4,6]]
[1,2].product()            #=> [[1],[2]]
[1,2].product([])          #=> []
```

Obtaining Information about an Array:
 We can easily find out about the length of our array in Ruby.
```
browsers = ['Chrome', 'Firefox', 'Safari', 'Opera', 'IE']
browsers.length #=> 5
browsers.count #=> 5
browsers.empty? #=> false
browsers.include?('Konqueror') #=> false
```
Iterating over Arrays:
```
arr = [1, 2, 3, 4, 5]
arr.each { |a| print a -= 10, " " }
# prints: -9 -8 -7 -6 -5
#=> [1, 2, 3, 4, 5]
``` 
we can use reverse on iterator:
```
words = %w[first second third fourth fifth sixth]
str = ""
words.reverse_each { |word| str += "#{word} " }
p str #=> "sixth fifth fourth third second first "
```
There are some other iterator methods , which are so fun to use them I am going to give some exampls of those methods.
The inject and reduce methods are aliases. There is no performance benefit to either
Convert an Array of Arrays to a Hash using inject, this practice is great when you want to make a data histogram.
```
array = [['A', 'a'], ['B', 'b'], ['C', 'c']]

hash = array.inject({}) do |memo, values|
  memo[values.first] = values.last
  memo
end

hash
# => {'A' => 'a', 'B' => 'b', 'C' => 'c'}
```

The syntax can be improved as changing the second parameter of the block (values) and using an array of two variables instead, which will be used by Ruby as the key and value of “array”.
```

array = [['A', 'a'], ['B', 'b'], ['C', 'c']]

hash = array.inject({}) do |memo, (key, value)|
  memo[key] = value
  memo
end

hash
# => {'A' => 'a', 'B' => 'b', 'C' => 'c'}
```

Inject and reduce  can easily be used to sum an enumerable or to get the product of it:

```
[100, 200, 1000].inject(0) { |sum, value| sum += value } # => 1300
[100, 200, 1000].inject(1) { |sum, value| sum *= value } # => 20000000

[100, 200, 1000].reduce :+ # => 1300
[100, 200, 1000].reduce :* # => 20000000

```

The map method can be used to create a new array based on the original array, but with the values modified by the supplied block:
```
arr.map { |a| 2*a }   #=> [2, 4, 6, 8, 10]
arr                   #=> [1, 2, 3, 4, 5]
arr.map! { |a| a**2 } #=> [1, 4, 9, 16, 25]
arr                   #=> [1, 4, 9, 16, 25]
```
Selecting Items from an Array:
Here are some other useful methods we can use to  modify our data in arrays.
Elements can be selected from an array according to criteria defined in a block:
```
arr = [1, 2, 3, 4, 5, 6]
arr.select { |a| a > 3 }     #=> [4, 5, 6]
arr.reject { |a| a < 3 }     #=> [3, 4, 5, 6]
arr.drop_while { |a| a < 4 } #=> [4, 5, 6]

arr                          #=> [1, 2, 3, 4, 5, 6]
arr.delete_if { |a| a < 4 } #=> [4, 5, 6]
arr                         #=> [4, 5, 6]

arr = [1, 2, 3, 4, 5, 6]
arr.keep_if { |a| a < 4 } #=> [1, 2, 3]
arr                       #=> [1, 2, 3]

```
 As I mentioned there are many other methods to address and again it is a good practice to refere back to the Ruby Doc.
 
 Happy Coding........ 


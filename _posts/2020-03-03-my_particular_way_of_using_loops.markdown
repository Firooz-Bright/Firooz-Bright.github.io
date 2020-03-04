---
layout: post
title:      "My Particular Way of Using Loops"
date:       2020-03-03 20:13:31 -0500
permalink:  my_particular_way_of_using_loops
---



The way I used the loop first started in C++ since Java core is kind of close to C++, I felt more comfortable working with loops in Java, but when I started to learn Ruby I found loops more convenient and easy.  below is one of the examples I had fun with it when I tried to use loops to solve with Ruby , I liked the way I solved the palindrom with loops when I just started to learn Ruby.

```

def palindrome?(string)
  i = 0
  while i < string.length
    if string[i] != string[(string.length - 1) - i]
      return false
    end

    i += 1
  end

  return true
end

def longest_palindrome(string)
  
  substr_start = 0
  substr_length = string.length
  while substr_length > 0 # 1 is a trivial palindrome and the end case

    while substr_start <= string.length - substr_length

      if palindrome?(string.slice(substr_start,substr_length))
        puts 'found palindrome: ' + string.slice(substr_start,substr_length)
        return string.slice(substr_start,substr_length)
      end
      substr_start += 1
    end
    substr_start = 0 # inner loop ctr reset
    substr_length -= 1
  end
  puts 'null string tested?'
  return ''
end



puts(
  'longest_palindrome("abcbd") == "bcb": ' +
  (longest_palindrome('abcbd') == 'bcb').to_s
)
puts(
  'longest_palindrome("abba") == "abba": ' +
  (longest_palindrome('abba') == 'abba').to_s
)
puts(
  'longest_palindrome("abcbdeffe") == "effe": ' +
  (longest_palindrome('abcbdeffe') == 'effe').to_s
)

```



 






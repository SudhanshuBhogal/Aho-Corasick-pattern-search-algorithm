# Aho-Corasick-pattern-search-algorithm
***

Aho-corasick pattern search algorithm that will search a given list of patterns in a given string.

[Execute Online](https://colab.research.google.com/drive/1W3SE4BUsypYPNzgd1ZoiDtPvcsJR14RG)
*(After getting redirected to google Colab,Open playground mode and sign in to google to run)*

### Introduction
  ###### Given a block of text and list of patterns strings 'patterns[]', we need to find all the occurences of all the patterns in the given text. Let 'n' be the size of the text and 'k' be the total number of patterns and 'm' be the total number of characters in all the patterns.Aho-Corasick Algorithm finds all words in O(n+m+z) time where 'z' is total number of occurrences of words in text.

### Example:

          Input:
                patterns = ['a','ab','bc','bca','c','caa']
                text = "abccab"
                
          Output:
                'a' found at index 0
                'ab' found at index 0
                'bc' found at index 1
                'c' found at index 2
                'c' found at index 3
                'a' found at index 4
                'ab' found at index 4

### Short Explanation:
The algorithm first takes the 'm' characters from the patterns to build a trie data structure(Intuitively a dictionary). We construct a special way to traverse this trie. Then the algorithm processes the text sequentially so once it processes a character at an index, it will not processes at this index again. As the text is being processed, as soon as any one of the patterns is matched, it will output the pattern matched and then continues to find others patterns like so. The trie data structure for the above example will be formed as follows:
   
<img src="https://upload.wikimedia.org/wikipedia/commons/9/90/A_diagram_of_the_Aho-Corasick_string_search_algorithm.svg" alt="Trie structure for the given example" width="300" height="500"/>

Whenever we try to append a letter into the string processed and if as a result, our string is not a node in the trie, we have to move to a different node which marks the end of the next largest suffix of the scanned string before we can append the letter again. The transition from our current node to the node of the next largest suffix is called a 'failure transition' from our current node to its fail state node. For example, when 'abc' doesn't match, the fail state of 'ab' is the 'b' which descends from the root.The black arrows in the above diagram represent success transitions, blue arrows represent failure transitions to strict suffices and green arrows represent transition to other free suffices.

This way of assigning failure states is the special feature of the Aho-Corasick algorithm which allows the text to be processed in one pass: we keep updating our matched string, outputting a word and index whenever the matched string matches one of the words in the dictionary. When our matched string is no longer a prefix of any word in the dictionary, we truncate the matched string from the front until it is, and keep reading in more characters from the text input. 

At the termination of the Aho-Corasick algorithm, we will have outputted all keywords present and their respective indices.

### Applications of the algorithm
1) The Aho–Corasick string matching algorithm formed the basis of the original Unix command fgrep.
2) Detecting Plagiarism
3) Bioinformatics - DNA matching
  

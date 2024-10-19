# Watching Computer Science Courses

### CS50

- **Info**
  
  - In `binary` the *numbers* work by
    - `[16]` `[8]` `[4]` `[2]` `[1]`
    - `[1]` `[0]` `[0]` `[1]` `[1]`
      - This number is `19` (* 16 + 2 + 1*)
    - The *numbers* are `doubled` with each new `index`
    - When `[1]` the corresponding number is `added` to the `sum`
    - When `[0]` the corresponding number is not `added` to the `sum`
  - When looking on a `sorted` `list` by
    - Slicing half of a `sorted` *list*
    - Continue to the the *upper* or *lower* `half` part depending if the *item* is `lower` or `higher`
    - Is of `log2` *Time Complexity*
  - `C` is first compiled to `assembly` ?
  - `assembly` is *instructions* for the `cpu`
    - That look similar to this:
      - `movb $0 %al`
      - `callq get_string` ...
    - Different `cpu` brands might have `different` instructions
  - `transistors` are keeping `0s` and `1s`
- **Arrays Lecture 2**
  
  - `strings` are actually `arrays`
    
    - When a *string* is *stored* in `memory` we actually *store* each *characters* `ascii` code in 1 `byte` each
      
      - `[104]` `[105]` `[33]` `[\0]` ----> `hi!`
        
      - `[\0]` means `null` and is to *denote* the `end` of the `string`
        
  - Reading from `memory` is `context` *specific*
    
    - Which means that the `program` depends on `context` on how to `translate` these *numbers*
    - For example in `photosop` one *number* might mean something else, than in`excel`
      - For *reference* checkout the `mappings` for [ascii code](http://sticksandstones.kstrom.com/appen.html)
  - In `ascii` code the `uppercase` and the `lowercase` have `fixed` distance between them,
    
- **Algorithms Lecture 3**
  
  - In `c` the parameters on the main `function` can be taken from the `cli`
  
  ```c
  ./someExe param1 param2
  ```
  

```c
main(int argc, string argv) //argv -> [param1,param2], argc -> 2
 ...
```

- - `argc` is the number of `arguments` passed
  - `argv` keyword is similar to `arguments` in *javascript*
- In `c` returning `0` means *all went well*
  
- In algorithm efficiency notation
  
  - Big `O` means the `most` *possible steps*
  - Big `Ω` means the `least` *possible steps*
  - `Θ` means `O` and `Ω` are *the same*
- Imagine in `c` that you made a *data structure* for `media` like `pixels` of *image* which has `rgb` *properties*
  
  ```c
  typedef struct {
    red:...,
    green:...,
    blue:...
  }pixel;
  ```
  
- - Same principle for *video, music, etc*
- 2 *dimensional arrays* simply means an *array* of *arrays*
  

- **Memory Lecture 4**
  
  - In `c` a `pointer` is a *variable* that stores a location `address` in *memory*
  - Syntax
  
  ```c
  int varName = 20;
  int *pointer1 = &varName
  ```
  
  - - `&` means get `address` of *"varName"*
    - `*` means of *type* *pointer*
  - When *prefixing* a `*` to a `pointer` variable it `dereferences` and returns the `value`
    
  
  ```c
  printf("%i", *pointer1)
  //It *dereferences* and returns the *value* *e.x* 20
  ```
  
  - When the *cs50* *library* adds the *type* `string`
    - It created the type 'string' like this: `typedef char *string`
  
  ```c
  typedef char *string
  
  string str1 = "hi!"
  // So in C type "string" is essentially this:
  char *str2 = "hi!"
  ```
  
  - `*str` returns the `address` of the `1st` `char` in *"hi!"* `array`
    - And there is a *similarity* to *normal* `arrays` in `c`
    - So:
  
  ```c
  char *str3 = str2;
  toUpperCase(str[0]) // will also uppercase str2[0]
  ```
  
  - `printf` `%s ` *prints* untill it sees `\0` `null`, to stop
  - In `c` `addresses` can be `mathed` (*address + 1*)
  - `malloc` stands for `memory` `allocation`
    - And it `allocates` memory on request
  
  ```c
  char str* = malloc(8) // allocates 8 *bytes* for 'str'
  ```
  
  - `free(str)` will `clear` the *allocated memory* for `str`
    
  - You can use `sizeof(int)` to find the `size` of a `type` in `bytes`
    
  - `valgrind` is a program that *finds* `memory` `issues` in a *compiled* *C .e.t.c?* program
    
    - If you have it type `valgrind` `./name` to use it on *name*
  - When running a program the computer will `organize` the `memory` like this:
    
    - `machine code`
    - `Globals` - `global` *variables* will go here
    - `Heap` - whenever `malloc` is used, it gets from here
    - `Stack` - `local` *variables* in a `function` go here
  - `0x0` in `hexadecimal` *memory* is 0 and is used the same as `null`
    
- **Data Structures 5**
  
  - To *increase* `array1` `size` we can use `realloc`
  
  ```c
  int *array3 = realloc(array1,20)
  ```
  
  - - Will `allocate` a new space in *memory* of *20* `bytes` in size, and `copy` the `array1` in there
    - Now we have the `bigger` *array* `array3` with all the *previous data*
  - To create a `linked` `list` in `c` use
  
  ```c
  typedef struct node {
      int number;
      struct node *next; // using itself (node) as the type is possible by declaring the name at the top
  }
  ```
  
  - - To edit a value of node use the `dereferencing`
  
  ```c
  (*node1).number = 1; // or
  node1->number = 1;
  ```
  
  - - `for` *loop* for a `linked` `list` looks like this
  
  ```c
  for(node *temp = node1; temp->next != NULL; temp = temp->next;){
  ```
  
  - - `Free` a *linked list* by
  
  ```c
  while (list->next != NULL){
      node *temp = list->next;
      free(list);
      list = temp;
  }
  ```
  
  - For `binary` `tree`, *linked list*
    - While adding to it
      - If `smaller` *value* we add at `left`
      - If `bigger` *value* we add at `right`
  
  ```c
  typedef struct node{
      int number;
      struct node *left;
      struct node *right;
  }node
  ```
  
  - - `binary` `tree` looks something like this:
      - *binary* *tree* needs to be `balanced` or else it might resolve to simply a `linked` `list`
  
  ```c
        4 // Balanced scenario
      2  6
     1 3 5 7 
  
        1 // Unbalanced scenario
          2
            3
            ...
  ```
  

- For `binary` `search` on a *binary tree* using `recursion`
  
  - If `searched` is *bigger* than *current* *node*, we *call* with the `left` *node* as `param`
  - If `searched` is *smaller* than *current* *node*, we *call* with the `right` *node* as `param`
  
  ```c
  boolean binarySearch(node *currNode,int searched){
    if(currNode->next == NULL){
        return false
    }
    else if(searched > currNode->number){  // if number is bigger than current 
        return binarySearch(currNode->right,searched)
    }
    else if(searched < currNode->number){  // if number is smaller than current 
        return binarySearch(currNode->left,searched)
    }
    else {  // number is same as node
        return currNode
    }
  }
  ```
  

- A simple `hash` `table` which is *different* from a `hashmap` can be implemented like this:
  
  - We create an `array` of size *n*, and to `insert` a `value` in it
    - We create an *algorithm* that *converts* the `value` to an `index` in that `array`
    - And we put the `value` there, inside a `hashNode` that has also stores the `address` of the next element
    - When we have two *different* `values` that generate the `same` `hash` `table`, we either
      - `increase` our `hashNode` *divisions*, or *connect* them as a `linked` `list`
  - There also must be a more `efficient` way of implementing a `hash` `table`
  
  ```c
  typedef struct hashNode {
    char value[OfTheLargestLikelyWord + 1]
    node *next
  }
  
  [A] [0] -> ["America",[nextA_HashNode1]],["Average",[nextHashNode2]],..
  [B] [1] -> ["Because",[nextB_HashNode1]]
  [C] [2] -> ["Country",[nextC_HashNode1]]
  ...
  ```
  

- Checkout the `trie` *data structure* which is a `tree` of `arrays`
  
- Some `abstract` *data types* are
  
  - `Queue` - `FIFO`
  - `Stack` - `LIFO`

- **Python 6 **
  
  - *Python* uses `identation` instead of `parenthesis`
  
  ```python
  def function1 :
      print("nice")
  ```
  
  - *Template Literals* are used with `f""`
  
  ```python
  string = f"{var1}"
  ```
  
  - Comments start with `#`
  - `conditionals`
  
  ```python
  if (x > y):
      print(True)
  elif(x < y):
      print(False)
  else :
      print("nice")
  ```
  
  - `Booleans` are *capitalized*
  - `loops`
  
  ```python
  while i < 3:
      print(f"counter is on {i}")
      i+=1
  ```
  
  ```python
  for i in list:
  
  for i in [0,1,2]
  
  for i in range(3)
  ```
  
  - No `i++` in *python*
  - `importing`
    - Default import
  
  ```python
  import lib1
  ```
  
  - - Named Import
  
  ```python
  from cs50 import getString,getInt
  ```
  
  - Running the code
    
    - `python file1.py`
      - Will run the code with the `interpreter`
  - `true`/`false` resolves to `1` and `0`
    
  - Ternary Operators
    
  
  ```python
  res = "yay!" if 0 > 1 else "nay!"
  ```
  
  * **Lecture 8 Object Oriented Programming**
    - In Python
      * `Tuple` is a *data structure* similar to `list`(*array*) and is immutable
        - ```python
              a,b = get_stuf()
              def get_stuff():
              a = 1
              b = 2
                return a,b
                Or
                return (a,b)
          ```

### CJ

- **Javascript Engine - Under the Hood**
  
  - Engine Optimizations
    
    - An `array` of
      
      - `numbers` corresponds to a `c++` array of `ints`
        
      - `doubles` ...etc corresponds to a `c++` array of `ints`
        
      - `objects`, ...etc with other corresponds to a `c++` array of `pointers`

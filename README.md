# NanoRescueSquad 纳米救援小子 🚁
&emsp;&emsp; -- Chaoqi LIU (chaoqil2@illinois.edu) \
&emsp;&emsp; -- Jiahui LIN (jiahui9@illinois.edu) 

<br />

## Intro to Huffman Coding

* __Background Information__ \
In 1951, while enrolled in an Information Theory class at MIT, David A. Huffman and his classmates were given a choice by professor Robert M. Fano: they could either take the final exam or find the most efficient binary code. Huffman chose the less traveled path, and the rest, as they say, is history. The [Huffman coding](https://en.wikipedia.org/wiki/Huffman_coding) algorithm is a fundamental data compression algorithm. Data compression is a powerful tool that allows a given set of information to be represented in less space, allowing for more efficient data transfer. JPG (lossy) and PNG image formats use various types of compression (lossless). It is also used to compress multiple files in ZIP files. Communication Networks, which deal with transferring large amounts of data, and Computer Security, which deals with data encoding for a layer of privacy, both use the concept of data encoding.


* __Huffman Tree Visualization__ \
Huffman tree built from the text "The Huffman encoding algorithm is a fundamental data compression algorithm" was shown below
```
                                                                                                ______________________________ 74 _____________________________                                                                                                  
                                                                 ______________________________/                                                               \______________________________                                                                   
                                                ______________ 31 _____________                                                                                                ______________ 43 _____________                                                   
                                 ______________/                               \______________                                                                  ______________/                               \______________                                    
                        ______ 14 _____                                                ______ 17 _____                                                 ______ 20 _____                                                ______ 23 _____                            
                 ______/               \______                                  ______/               \______                                   ______/               \______                                  ______/               \______                     
            __ 6 __                          a:8                           __ 8 __                          _:9                            __ 10 _                        __ 10 _                         __ 11 _                        __ 12 _                 
         __/       \__                                                  __/       \__                                                   __/       \__                  __/       \__                   __/       \__                  __/       \__              
      l:3            d:3                                             h:4            e:4                                               5             t:5             m:5            o:5              i:5             6              n:6             6             
                                                                                                                                    /   \                                                                         /   \                          /   \           
                                                                                                                                 c:2    f:3                                                                    g:3     3                      r:3    s:3         
                                                                                                                                                                                                                      / \                                        
                                                                                                                                                                                                                    p:1u:2                                       

```
<br />

## Technical Overview

* __Data Structure__
  * The Huffman Trees' left paths represent a '0' in the binary message and taking a right path as a '1'
    <pre>
              root
             0/  \1
             /    \ 
           'E'   _---_
               0/     \1
              _/       \_
            0/ \1     0/ \1
            /   \     /   \
          'S'   'R' 'C'   'T'
    </pre>
  * The numbers in each node represent character frequencies. The number on each edge represent the direction taken on the tree. For insteance to encode 'S', the value is '100'
<br />

* __I/O__
  * Implemented the [serialization and deserialization](https://en.wikipedia.org/wiki/Serialization) of huffman tree
  * Implemented reading/writing for both .txt and .dat file
<br />
  
* __Coding Algorithms__
  * Added one extra byte which represnets the number of complementary 0s followed by complementary 0s, then encoded content (bits) to prevent loss of information/bits due to binary files being quantified as bytes -- bits that are insufficient to form a byte will be lost
    <pre>
    actual valid bits:                  11100 10101100
    bits written to file:   00000011 00011100 10101100
    </pre>
<br />

* __Optization__
  * Implemented [MapReduce](https://en.wikipedia.org/wiki/MapReduce) algorithm (multi-threaded mapper) to improve the efficiency of building a huffman tree
  * Builded robust exception (panic) handling system
<br />

## Possible Challenges

&emsp;&emsp; __N/A__
<br />

## User Guide

&emsp;&emsp; __[Demo Video](https://www.youtube.com/watch?v=VuxoMrkrdvw)__

* Clone the repo ```git clone https://github.com/Chaoqi-LIU/Huffman_Coding```
* Move to the dir ```cd huffman```
* To see all operations provided ```cargo run -- help```

  <pre>
    -- help                                                 print this help message
    -- encode input_file -o output_file huffman_tree        encode the content in 'input_file'[.txt], write encoded content to 'output_file'[.dat], and save the huffman tree to 'huffman_tree'[.crab]
    -- encode input_file huffman_tree -o output_file        encode the content in 'input_file'[.txt] with 'huffman_tree'[.crab] provided, write encoded content to 'output_file'[.dat]
    -- decode input_file huffman_tree -o output_file        decode the content in 'input_file'[.txt] with 'huffman_tree'[.crab] provided, write decoded content to 'output_file'[.txt]
    -- compress input_file -o output_file huffman_tree      compress the image in 'input_file'[.ppm], write compressed image to 'output_file'[.dat] and save the huffman tree to 'huffman_tree'[.crab]
    -- compress input_file huffman_tree -o output_file      compress the image in 'input_file'[.ppm] with 'huffman_tree'[.crab] provided, write compressed image to 'output_file'[.dat]
    -- depress intput_file huffman_tree -o output_file      depress the image in 'input_file'[.dat] with 'huffman_tree'[.crab] provided, write depressed image to 'output_file'[.ppm]
    -- print huffman_tree                                   print the 'huffman_tree'[.crab]
  </pre>
<br />

## Reference
&emsp;&emsp; This project is inspired by [lab_huffman](https://courses.engr.illinois.edu/cs225/fa2022/labs/huffman/) of CS225(2022fall) @ UIUC

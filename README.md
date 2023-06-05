# Huffman-Coding

## Aim:

To implement Huffman coding to compress the data using Python.

## Software Required:

Anaconda - Python 3.7

## Algorithm:

### Step 1:

Assign the input string.

### Step 2:

Create the required tree nodes.

### Step 3:

Create a function to implement the huffman coding.

### Step 4:

Calculate the frequency of occurence of each characters.

### Step 5:

Print the characters with its equivalent Huffman code.

### Step 6:

End the program.
 
## Program:

```python

# Get the input String:

string = 'Silambarasan 212221230101'

```

```python

# Create tree nodes:

class NodeTree(object):
    
    def __init__(self, left=None, right=None): 
        self.left = left
        self.right=right
        
    def children(self):
        return (self.left,self.right)

```

```python

# Main function to implement huffman coding:

def huffman_code_tree (node, left=True, binString=''):
    if type(node) is str:
        return {node: binString}
    (l, r) = node.children()
    d = dict()
    d.update(huffman_code_tree (l, True, binString + '0'))
    d.update(huffman_code_tree (r, False, binString + '1'))
    return d

```

```python

# Calculate frequency:

freq = {}
for c in string:
    if c in freq:
        freq[c] += 1
    else:
        freq[c] = 1
        
freq = sorted(freq.items(), key=lambda x: x[1], reverse=True)

nodes = freq

```

```python

# Calculating frequency of occurence:

while len(nodes)>1:
    (key1,c1)=nodes[-1]
    (key2,c2)=nodes[-2]
    nodes = nodes[:-2]
    node = NodeTree (key1, key2)
    nodes.append((node,c1 + c2))
    
    nodes = sorted (nodes, key=lambda x: x[1], reverse=True)

```

```python

# Print the characters and its huffman_code:

huffmanCode = huffman_code_tree(nodes[0][0])
print('#*#*#*#*#*#*#*#*#*#*#*#')
print(' Char | Huffman code ') 
print('#*#*#*#*#*#*#*#*#*#*#*#')
for (char, frequency) in freq:
    print('%-4r |%12s' %(char,huffmanCode[char]))

```


## Output:

### Print the characters and its huffmancode:

![img1](https://github.com/simbu07/Huffman-Coding/assets/94525786/dc02e833-13ca-4378-b9fc-62209caa0871)

## Result:

Thus the huffman coding was implemented to compress the data using python programming.


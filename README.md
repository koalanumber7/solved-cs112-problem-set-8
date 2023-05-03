Download Link: https://assignmentchef.com/product/solved-cs112-problem-set-8
<br>
<strong>Problem Set 8</strong>

<strong>Binary Tree, Huffman Coding</strong>

<ol>

 <li><strong>*</strong> Answer the following questions in terms of <em>h</em>, the height of a binary tree:

  <ol>

   <li>What is the <strong>minimum</strong> possible number of nodes in a binary tree of height <em>h</em>?</li>

   <li>A <em>strictly</em> binary tree is one in which every node has either no children or two children; in other words, there is <strong>no</strong> node that has exactly one child. What is the <strong>minimum</strong> possible number of nodes in a strictly binary tree of height <em>h</em>?</li>

   <li>A <em>complete</em> binary tree is one in which every level <strong>but</strong> the last has the maximum number of nodes possible at that level; the last level may have any number of nodes. What is the <strong>minimum</strong> possible number of nodes in a complete binary tree of height <em>h</em>?</li>

  </ol></li>

 <li>Two binary trees are <em>isomorphic</em> if they have the same shape (i.e. they have identical structures.) Implement the following <strong>recursive</strong> method:</li>

</ol>

public static &lt;T&gt; boolean isomorphic(BTNode&lt;T&gt; T1, BTNode&lt;T&gt; T2) {

/* your code here */

}

that returns <strong>true</strong> if the trees rooted at T1 and T2 are isomorphic, and false otherwise. BTNode is defined as follows:

public class BTNode&lt;T&gt; {

T data;

BTNode&lt;T&gt; left, right;

BTNode(T data, BTNode&lt;T&gt; left, BTNode&lt;T&gt; right) {              this.data = data;              this.left = left;              this.right = right;

}

}




<ol start="3">

 <li>The <em>radix tree</em> data structure shown below stores the bit strings 0,1,01,010,100, and 1011 in such a way that each left branch represents a 0 and each right branch represents a 1.</li>

</ol>




X

/   

0     1

   /

01  X

/   /  

010  100  X



1011

Nodes that do not have any stored bit strings will have a dummy value ‘X’ instead.

To find whether a bit string exists in this radix tree, start from the root, and scanning the bits of the string left to right, take a left turn if the but is 0, and a right turn if the bit is 1. If a node can be reached using this sequence of turns, and it does not contain the dummy value ‘X’, then the bit string is found, else it is not found.

<ol>

 <li>Given the following bit strings:</li>

</ol>

1011, 01, 0010, 1010, 011, 1000, 0101

Starting with an empty radix tree, build it up to store these strings, showing the radix tree after <em>each</em> bit string is inserted.

(To insert a new string you may have to insert more than one new node in the tree built thus far.)

<ol start="2">

 <li>How many units of time did it take to build this tree? Treat taking a turn at an existing branch, and inserting a new branch as basic unit time operations.</li>

 <li>How many units of time would it take to <em>lexicographically sort</em> the bit strings in this radix tree, after all the strings have been inserted? Use the same basic operations as in the previous question. The output of the sort should be:</li>

</ol>

0010  01  0101  011  1000  1010  1011

(Lexicographic sort is like alphabetic sort, 0 precedes 1)

<ol start="4">

 <li>How many units of time would it take in the worst case to insert a new <em>k</em>-bit string into a radix tree? (ANY radix tree, not the specific one above.)</li>

 <li>How many units of time would it take in the worst case to insert an arbitrary number of bit strings whose total length is <em>n </em>bits?</li>

</ol>

<ol start="4">

 <li>A general tree is one in which a node can have any number of children. General trees are used to model hierarchies. Think of a company hierarchy with a CEO at the root, then presidents of various units that report to her at the next level, then various vicepresidents who report to the presidents at the next level, and so on. Computer file systems are hierarchies as well, with a root folder, with other folders and files recursively nested under the root.</li>

</ol>

Every general tree can be represented as a binary tree. Here’s an example of how:

<h3>       A</h3>

____|_____               A

|  |  |  |              /

B  C  D  X              B

/     |               

E  F   G                C

/   

<h2>                          E     D</h2>

     

F      X

/                                 G

For every node in the general tree:

The first child of the node becomes the left child of the same node in the binary tree

The second child of the node becomes the right child of the first

The third child of the node becomes the right child of the second, and so on

<ol>

 <li>Exercise 9.8 of text</li>

</ol>

Draw the binary tree representations of the following general trees:

(a)                  (b)                  (c)

A                    A                    A

_____|_____          _____|_____          _____|______

|     |     |        |     |     |        |   |    |   |

G     H     K        G     H     K        G   H    K   Z

|    /              |     |     |        |   |    |   |

<ul>

 <li>X P            X     P     Q        B   X    P   E</li>

</ul>

____|____                |     |     |       /       / 

|  |   |  |               R     T     S      O   L    N   R   O  L   R  E

<ol start="2">

 <li>Exercise 9.9 of text</li>

</ol>

Draw the general trees represented by the following binary trees:

(a)                  (b)                  (c)

A                    T                    A

/                    /                    /

G                    D                    B

/                   /                       

<ul>

 <li>L G     R                    C</li>

</ul>

<h1>       /                 /     /                   /       O   R    E          P    Q  E  X                D</h1>

/   /                       

A  C  B  D                      E

<ol start="5">

 <li>Suppose the equivalent binary tree for a general tree is built out of the following binary tree nodes:</li>

</ol>

public class BTNode&lt;T&gt; {

T data;

BTNode&lt;T&gt; left, right, parent;

…

}

Complete the following methods

<ol>

 <li>Given a pointer to a node x, find and return the node that would be x’s parent in the general tree:</li>

</ol>

public static &lt;T&gt; BTNode&lt;T&gt; genTreeParent(BTNode&lt;T&gt; x) {

/* COMPLETE THIS METHOD */

}

<ol start="2">

 <li><strong>*</strong> Given a pointer to a node x, and an integer k, find and return the node that would be the k-th child of x (k=1 if first child, etc.), in the general tree. The method should thrown an exception if there is no k-th child:</li>

</ol>

public static &lt;T&gt; BTNode&lt;T&gt; genTreekthChild(BTNode&lt;T&gt; x, int k)        throws NoSuchElementException {            /* COMPLETE THIS METHOD */

}

<ol start="6">

 <li><strong>*</strong> Suppose you are given the following binary tree class definition, which uses the BTNode&lt;T&gt; class of the previous exercise.</li>

</ol>

public class BinaryTree&lt;T&gt; {         private BTNode&lt;T&gt; root;

…     }

Add the following methods to this class so that applications can do an inorder traversal one node at a time:

// returns the first node that would be visited in an inorder traversal;

// returns null if tree is empty        public BTNode&lt;T&gt; firstInorder() {

/* COMPLETE THIS METHOD */

} and

// returns the next node that would be visited in an inorder traversal;

// returns null if there is no next node

public BTNode&lt;T&gt; nextInorder(BTNode&lt;T&gt; currentNode) {

/* COMPLETE THIS METHOD */        }

For instance, an application would call these methods like this to do the inorder traversal:

BinaryTree&lt;String&gt; strBT = new BinaryTree&lt;String&gt;();      // insert a bunch of strings into strBST

…

// do inorder traversal, one node at a time      BTNode&lt;String&gt; node = strBST.firstInorder();      while (node != null) {

node = strBST.nextInorder(node);      }

1111011  1010111  1101110  0010011  111000

<ol start="7">

 <li>Exercise 9.4 of text</li>

 <li>Build a Huffman tree for the following set of characters, given their frequencies:</li>

</ol>

R   C   L   B   H   A   E

6   6   6  10  15  20  37

<ol start="2">

 <li>Using this Huffman tree, encode the following text:</li>

</ol>

CLEARHEARBARE

<ol start="3">

 <li>What is the average code length?</li>

 <li>If it takes 7 bits to represent a character without encoding, then for the above text, what is the ratio of the encoded length to the unencoded?</li>

 <li>Decode the following (the string has been broken up into 7-bit chunks for readability):</li>

</ol>
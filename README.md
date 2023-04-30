Download Link: https://assignmentchef.com/product/solved-cs2420-program-7graphs-wordnet
<br>
<h1>History:  WordNet</h1>

Suppose you had a graph between sets of nouns in which an arc A -&gt; B indicates that the set of nouns A is a more specific case of the set of nouns B.  Such a graph would allow us to reason about similarities and differences.   The graph below is an example of what this might look like.

<strong>Measuring the semantic relatedness of two nouns</strong>. Semantic relatedness refers to the degree to which two concepts are related. Measuring semantic relatedness is a challenging problem. For example, you consider <em>Ronald Reagan</em> and <em>John F. Kennedy</em> (two U.S. presidents) to be more closely related than <em>Ronald Reagan</em> and <em>chimpanzee</em> (two primates). It might not be clear whether <em>Ronald Reagan</em> and <em>Eric Arthur Blair</em> are more related than two arbitrary people.  However, both <em>Ronald Reagan</em> and <em>Eric Arthur Blair</em> (aka George Orwell) are famous communicators and, therefore, closely related.

<a href="http://wordnet.princeton.edu/">WordNet</a> is a semantic lexicon for the English language that computational linguists and cognitive scientists use extensively. For example, WordNet was a key component in IBM’s Jeopardy-playing <a href="https://en.wikipedia.org/wiki/Watson_(computer)">Watson</a> computer system.




<h1>Your Assignment:</h1>

For simplicity, we’ll just use nodes that have a numeric name (rather than a set of strings), but the principle is the same.  Given a directed acyclic graph, find the shortest path between any two nodes, the length of the path, and the shortest common ancestor.

You have been given starter code which has the test cases provided.  As long as you keep the same test cases, you can change anything you want about the code.

<strong>Shortest common ancestor.</strong> An <em>ancestral path</em> between two vertices (<em>v</em> and <em>w)</em> in a rooted DAG (directed acyclic graph) is a directed path from <em>v</em> to a common ancestor <em>x</em>, together with a directed path from <em>w </em>to the same ancestor <em>x</em>. A <em>shortest ancestral path</em> is an ancestral path of minimum total length. We refer to the common ancestor in a shortest ancestral path as a <em>shortest common ancestor</em>. Note that a shortest common ancestor always exists because the root is an ancestor of every vertex. Note also that an ancestral path is a path, but not a directed path.







Hint (you do NOT need to do it this way):

Every ancestor of a node v (in the above example) needs to know

(1) the length of the shortest path to it from v

(2) the predecessor responsible for that shortest path. Storing the predecessor helps you in recreating the best path.

In my code, I called that information (known by each node) PathInfo.

Since we need to find the shortest path to a node from two different nodes, the code has two PathInfo variables.   p1 stores the best path from one node and p2 stores the best path from another node.

So for example, for digraph1, lca(5,6) may store the following information:

digraph1.txt Best lca 5 6 Distance: 3 Ancestor 1 Path:5 1 3 6

The Graph digraph1.txt

0[2 Pred:1] [99 Pred:-1]

1[1 Pred:5] [2 Pred:3] 1-&gt;0

2[99 Pred:-1] [99 Pred:-1] 2-&gt;0

3[99 Pred:-1] [1 Pred:6] 3-&gt;1

4[99 Pred:-1] [99 Pred:-1] 4-&gt;1

5[0 Pred:5] [99 Pred:-1] 5-&gt;1

6[99 Pred:-1] [0 Pred:6] 6-&gt;3

7[99 Pred:-1] [99 Pred:-1] 7-&gt;3

8[99 Pred:-1] [99 Pred:-1] 8-&gt;5

9[99 Pred:-1] [99 Pred:-1] 9-&gt;5

10[99 Pred:-1] [99 Pred:-1] 10-&gt;9

11[99 Pred:-1] [99 Pred:-1] 11-&gt;9

<strong>Outcast detection.</strong> Given a list of nodes <em>x</em><sub>1</sub>, <em>x</em><sub>2</sub>, …, <em>x<sub>n</sub></em>, which node is the least related to the others? To identify <em>an outcast</em>, compute the sum of the path lengths between each node and every other one:

<em>d<sub>i</sub></em>   =   pathL<em>ength</em>(<em>x<sub>i</sub></em>, <em>x</em><sub>1</sub>)   +   pathL<em>ength</em> (<em>x<sub>i</sub></em>, <em>x</em><sub>2</sub>)   +   …   +   pathL<em>ength( x<sub>i</sub></em>, <em>x<sub>n</sub></em>)

and return the node <em>x<sub>t</sub></em> for which <em>d<sub>t</sub></em> is maximum.







<strong>Input:</strong>

The input will be the number of nodes followed by the edges. Each edge A-&gt; B is represented by A  B.




<table>

 <tbody>

  <tr>

   <td width="313">There are the two provided  input files:digraph1.txt12     //Number of nodes6  3  // an edge from 6 to 37  33  14  15  18  59  510  911  91  02  0 </td>

   <td width="313"></td>

  </tr>

 </tbody>

</table>







<table>

 <tbody>

  <tr>

   <td width="137">digraph2.txt 251 02 03 14 15 26 27 38 39 310 110 511 512 512 613 714 715 916 917 1018 1019 1220 1221 1622 1623 2024 2013 39 423 4 </td>

   <td width="535"></td>

  </tr>

 </tbody>

</table>

<strong> </strong>

<strong>Testing:</strong>

Run the tests shown in Graph.java.




The lca computation does the following.  Given two nodes in the graph, find the shortest common ancestor, shortest ancestral path, and associated length.

The outcast computation prints the outcast (and, as debug, shows all the lengths that were computed in order to compute an outcast)










Sample Output:

(I printed the graph name so I didn’t get confused)




digraph1.txt Best lca 3 7 Distance: 1 Ancestor 3 Path:3 7

digraph1.txt Best lca 5 6 Distance: 3 Ancestor 1 Path:5 1 3 6

digraph1.txt Best lca 9 1 Distance: 2 Ancestor 1 Path:9 5 1







(I showed the computations involved in computing the Outcast)

digraph1.txt Best lca 7 10 Distance: 5 Ancestor 1 Path:7 3 1 5 9 10

digraph1.txt Best lca 7 2 Distance: 4 Ancestor 0 Path:7 3 1 0 2

digraph1.txt Best lca 10 2 Distance: 5 Ancestor 0 Path:10 9 5 1 0 2

digraph1.txt For [7, 10, 2] Outcast is 10 with distance sum of 10
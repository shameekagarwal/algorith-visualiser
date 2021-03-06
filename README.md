<b>

# algorithms_visualiser

the website is about simulating algorithms. algorithms are best understood when there is a step by step visualisation, which helps provide an intuition about all the moving pieces.

[link to the website](https://algorithms-visualiser.herokuapp.com/)

<br />

# features and their implementation

the algorithms it simulates are - 

1. sorting
   1. [merge sort](demo-images/Mergesort.png)
   2. [quick sort](demo-images/Quicksort.png)
   3. [heap sort](demo-images/Heapsort.png)
2. graph
   1. [kruskal](demo-images/Kruskal.png)
   2. [dijkstra](demo-images/Dijkstra.png)
3. [convex hull](demo-images/ConvexHull.png)
4. [sudoku](demo-images/Sudoku.png)

*the complexities mentioned below do not take into account the delays used in simulation - in order for the simulations to work, random delays here and there might have altered the algorithm's complexity, but the algorithm's flow doesn't change.*

## sorting

user can enter / generate a random array of elements. vanilla js simulates the sorting algorithm on html canvas. the speed of the simulation is fast for array lengths > 100. the bars too are responsive i.e. scale according to viewport size. all three algorithms [merge sort](https://www.geeksforgeeks.org/merge-sort/), [quick sort](https://www.geeksforgeeks.org/quick-sort/), [heap sort](https://www.geeksforgeeks.org/heap-sort/) have complexity `O(Nlog(N)`.

## graph

graph algorithms are simulated using [visjs](https://github.com/visjs/vis-network). user inputs the number of nodes, edges and the orientation of these edges. in case of [kruskal](https://www.geeksforgeeks.org/kruskals-minimum-spanning-tree-algorithm-greedy-algo-2/), the user is directed to a page with the mst. complexity of this algorithm is `O(Elog(E) + Elog(V)) = O(Elog(EV))`. however, in case of [dijkstra](https://www.geeksforgeeks.org/dijkstras-shortest-path-algorithm-greedy-algo-7/) the user is directed to a page with a graph showing the shortest distance from the source vertex to all other vertices. though achievable in `Elog(V)` , my implementation has a complexity of `O(V^2)`.

## convex hull

it uses [p5js](https://p5js.org/) to draw the convex hull incrementally based on the markers placed by the user. it uses [jarvis algorithm](https://www.geeksforgeeks.org/convex-hull-set-1-jarviss-algorithm-or-wrapping/), leading to a complexity of `O(n^2)`.

## sudoku

uses [backtracking](https://www.geeksforgeeks.org/sudoku-backtracking-7/) to solve the sudoku, in `O(9^(n^2))` complexity. with each decision that is taken by the algorithm, a delay is associated which helps in visualising the algorithm.

## role of nodejs

the user can only view the simulation of the algorithm if authenticated. oauth is achieved using [passportjs](http://www.passportjs.org/packages/passport-google-oauth2/).
<br />
after google "validates" the user, their details (name and email id) are saved to the database ([mongodb atlas](https://www.mongodb.com/cloud/atlas))
<br />
once successfully logged in, the user can view all simulations and also send feedback about the website.
<br />
the feedback is directly sent over to the admin, and an acknowledgement is delivered to the user, with the help of [nodemailer](https://nodemailer.com/about/).

<br />

# stack used

1. node
2. express
3. mongodb
4. javascript
5. bootstrap

</b>


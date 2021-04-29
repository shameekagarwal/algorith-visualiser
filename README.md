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
   2. [dijikstra](demo-images/Dijkstra.png)
3. [convex hull](demo-images/ConvexHull.png)
4. [sudoku](demo-images/Sudoku.png)

*the complexities mentioned below do not take into account the delays used in simulation - in order for the simulations to work, random delays here and there might have altered the algorithm's complexity, but the algorithm's flow doesn't change.*

## sorting

user can enter / generate a random array of elements. vanilla js simulates the sorting algorithmon on html canvas. the speed of the simulation is fast for array lengths > 100. the bars too are responsive i.e. scale according to viewport size. all three algortihms have complexity `O(N*log(N)`.

## graph

graph algorithms are simulated using [visjs](https://github.com/visjs/vis-network). user inputs the number of nodes, edges and the orientation of these edges. in case of [kruskal](https://www.geeksforgeeks.org/kruskals-minimum-spanning-tree-algorithm-greedy-algo-2/), the user is directed to a page with the mst. complexity of this algorithm is `O(Elog(E) + Elog(V)) = O(Elog(EV))`. however, in case of [dijkstra](https://www.geeksforgeeks.org/dijkstras-shortest-path-algorithm-greedy-algo-7/) the user is directed to a page with a graph showing the shortest distance from the source vertex to all other vertices. though achievable in `Elog(V)` , my implementation has a complexity of `O(V^2)`.

## convex hull

it uses [p5js](https://p5js.org/) to draw the convex hull incrementally based on the markers placed by the user. it uses [jarvis algortihm](https://www.geeksforgeeks.org/convex-hull-set-1-jarviss-algorithm-or-wrapping/), leading to a complexity of `O(n^2)`.

## sudoku

uses [backtracking](https://www.geeksforgeeks.org/sudoku-backtracking-7/) to solve the sudoku, in `O(9^(n*n))` complexity. with each decision that is taken by the algortihm, a delay is associated which helps in visualising the algorithm.

## role of nodejs

1. the user can only view the simulation of the algorithm if authenticated using oauth. oauth is achieved using [passportjs](http://www.passportjs.org/packages/passport-google-oauth2/). the flow of oauth in the application is described in the next few steps.
2. user enters the website, and on clicking the signin button, the user is directed to the consent screen
3. since passport has all the admin's api key
4. when the user grants permission, the google api redirects to the "redirect uri" with a code.
5. after this, passport middleware intervenes. this middleware can use the code of the previous step, send it to google, in a reply to which google sends the user details like email, name, profile phot, etc.
6. now after getting access to the user details, it is saved to mongodb, after which the user is redirected to the homepage of the website.
7. once successfully logged in, the user can view all simulations and also send feedback about the website.
8. the feedback is directly sent over to the admin, and an acknowledgement is delivered to the user, with the help of [nodemailer](https://nodemailer.com/about/).

<br />

# stack used

1. node
2. express
3. mongodb
4. javascript
5. bootstrap
6. nodemailer

</b>


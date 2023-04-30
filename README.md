# cross_stitch

One of my hobbies is cross stitching, and I have noticed that when stitching from a pattern I spend a lot of time staring at the pattern, planning the best route to stitch in such that I use the least thread and have the least large jumps on the back. This gave me the idea to try and create an algorithm which can find the most efficient route.

I am writing this algorithm in python.

My first attempt at this will only consider that both strokes of the cross are done one after the other (as opposed to doing one diagonal, doing at least one other stitch in between, and then completing the original cross with the second stitch). I have decided this in order to make the problem simpler to start with, but I hope to eventually include this case too as it can certainly increase the efficiency of the path.

I will be considering the each cross having the first stitch (the under stitch) from the top right to bottom left and then the second (top) stitch to be from top left to bottom right, as this is the traditional direction. In cross stitching it is conventional for all the crosses to have the same top stitch / bottom stitch direction and thus that is what I will be working in in this algorithm.

At this point the program will accept text files representing the cross stitch pattern with the rows represented on separate lines, the columns represented by commas, and the colours represented by numbers. 
Each input file will have the number of rows, newline, the number of columns, newline, the number of colours, newline and then the pattern as described above. Here is an example:
```
3
3
4
1,1,3
1,2,2
2,2,4
```
The numbers do not have to be 1-n as in the example, they can be any integers.

In future it would be great to be able to interpret actual cross stutch patterns (usually in pdf form and displayed in a grid) without having to manually put them in this csv form.


Current approach:
Of course one could do a brute force algorithm, finding all possible paths to find the most efficient. I hope to make a more time efficient algorithm that this.

My current approach is prioritizing minimizing the distances that, if not chosen, will result in the largest increase in length. Specifically, for each cross we order all other crosses based on distance and priritize the routes where the second smallest distance to get to that cross is most different to the first.

I have considered also a method where we define clusters of crosses using a clustering algorithm. One would then find the most efficient path of each cluster and the best way to join clusters.

Another possible method is combining the brute force algorithm with another approach - searching all possible paths within certain restraints.

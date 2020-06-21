# N-Queens
Implementation of N-Queens Problem in C language:

Since the number of queens equals the number of rows, each queen can be represented by the row number where it can be placed. So, we can define a position[] vector  where the indices represent the rows (ie. the queens)  and the value of position[] represents the column number  where the queen can be safely placed. Thus, any cell in the chessboard has the coordinates as (i,position[i]).

We need then a function place(k) to check if a queen k can be safely placed at a specific column represented by position[k] :

➔	Two queens cannot be placed in the same row: Since we are proceeding row-wise we know that all the rows above the current row k are filled but not the current row and thus, there is no need to check for row k.
The function place(k) checks all the attacks of queens from i=1 to i=k-1:

➔	Two queens cannot be in the same column: for each row i, place(k) function checks if the column number of i equals the column of queen k ie: position[k]==position[i] ?

➔	Two queens cannot be in the same diagonal: if two cells (i,j) and (m,n) are in the same right diagonal they verify: i+j=m+n . Also, if they are in the same left diagınal they verify: i-j=m-n.
From the first equation: n-j=i-m and from the second equation: n-j=m-i
Therefore, two cells are in the same diagonal if and only if abs(m-i)=abs(n-j) For our algorithm, place(k) checks if: abs(position[i]-position[k])==abs(i-k)) for the cells (i,position[i]) and (k,position[k])

The main() function asks for the queens number n and calls two functions:

•	queen(k,n) returns one if there is a possible arrangement and prints it.
• analysis() which computes the time complexity of different inputs and plots results as a bar chart

queen(k,n) function places the queens one by one strating from the leftmost column of each row k ( position[k] is initilized with zero for all rows). To check if this column is valid, the function place(k) is called. If the column is not safe we check the next column (making sure that there still columns left to check ie: position[k]<=n)

•	If the queen k is safely placed we check if it is the last queen to place (k==n)?

     	If yes, we print the arrangement by calling the function print_sol(n)  and stop.

     	Else, we move to the queen k+1 and repeat the process.

•	If no safe column is found backtrack to the previous queen queen(k-1,n)  and change its position.

The queen(k,n) function stops running when k==0 This means there is no valid arrangement for the n queens.

In the analysis() function, we plot the time complexity (that will be discussed in the next section) of different inputs In[] (chessboard dimensions) as a bar chart. First we calculate time complexity by calling the function  fact(n) that returns n! 


Results are saved in the vector T[] . Since the results are quite large numbers that exceed 1000 for n>=7, our bar chart values Range[] will be : 100k,10k,1k,100,10. 
The bar chart is printed as 2D vector. Each line represents a value of Range[], each column represents one dimension In[j]  of the chessboard.

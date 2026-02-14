/*Problem: Write a program to check whether a given square matrix is an Identity Matrix. An identity matrix is a square matrix in which all diagonal elements are 1 and all non-diagonal elements are 0.

Input:
- First line: integer n representing number of rows and columns
- Next n lines: n integers each representing the matrix elements

Output:
- Print "Identity Matrix" if the matrix satisfies the condition
- Otherwise, print "Not an Identity Matrix"

Example:
Input:
3
1 0 0
0 1 0
0 0 1

Output:
Identity Matrix*/
#include<stdio.h>
int main()
    {   int r,c;
        printf("enter no of row and columns:");
        scanf("%d %d",&r,&c);

        int arr[r][c];
        for(int i=0;i<r;i++)
        {
            for(int j=0;j<c;j++)
            {
                printf("arr[%d][%d]",i,j);
                scanf("%d",&arr[i][j]);
            }
        }
        if(r!=c)
        {
            printf("not an identity matrix");
        }
        else
        {   int k=0;
            for(int i=0;i<r;i++)
            {
                if(arr[i][i]==1)
                {
                   k += 1;
                }
                else
                k = 0;
            }
            if(k==3){
                printf("identity matrix");
            }
            else
            printf("not an identity matrix");
        }
        return 0;
    }

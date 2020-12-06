# Matrices

## Q1. Find the transpose of a matrix.
```
class Main 
{
    public static void main(String[] args) 
    {
        int og[][]={{1,8,9},{7,2,3},{2,4,6}};       
        int transpose[][]=new int[3][3]; 
            
        for(int i=0;i<3;i++)
        {   
            for(int j=0;j<3;j++)
                transpose[i][j]=og[j][i]; 
        }   
            
        System.out.println("Original Matrix:"); 
        for(int i=0;i<3;i++)
        {   
            for(int j=0;j<3;j++)
                System.out.print(og[i][j]+" ");   
            System.out.println();
        }   
        
        System.out.println("Transpose Matrix:"); 
        for(int i=0;i<3;i++)
        {   
            for(int j=0;j<3;j++)
                System.out.print(transpose[i][j]+" ");   
            System.out.println();
        }   
    }
}
```
## Q2. Find the sum of two matrices.
```
class Main 
{
    public static void main(String[] args) 
    {
        int a[][]={{2,3,8},{2,7,3},{4,4,5}};   
        int b[][]={{1,3,8},{2,6,3},{1,1,4}};   
        int c[][]=new int[3][3]; 
            
        for(int i=0;i<3;i++)
        {   
            for(int j=0;j<3;j++)
            {   
                c[i][j]=a[i][j]+b[i][j];  
                System.out.print(c[i][j]+" ");   
            }   
            System.out.println(); 
        }   
    }
}
```
## Q3. Find the product of two matrices.
```
class Main 
{
    public static void main(String[] args) 
    {
        int row1 = 3, col1 = 3, row2 = 3, col2 = 3;   
        int a[][] = {   
                        {1, 2, 2},   
                        {3, 1, 1},   
                        {1, 2, 2}   
                        };   
        int b[][] = {   
                        {2, 1, 1},   
                        {1, 1, 1},   
                        {1, 3, 1}   
                    };   
            
        int prod[][] = new int[row1][col2];   
            
        for(int i = 0; i < row1; i++)
        {   
            for(int j = 0; j < col2; j++)
            {   
                for(int k = 0; k < row2; k++)
                {   
                    prod[i][j] = prod[i][j] + a[i][k] * b[k][j];    
                }   
            }   
        }   
                
        System.out.println("Product of two matrices: ");   
        for(int i = 0; i < row1; i++)
        {   
            for(int j = 0; j < col2; j++)
            {   
                System.out.print(prod[i][j] + " ");   
            }   
            System.out.println();   
        }   
    }
}
```
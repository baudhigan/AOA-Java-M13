
# EX 3D Sudoku solver - Backtracking.

## AIM:
To write a Java program to solve a Sudoku puzzle by filling the empty cells.

For example:
<img width="357" height="322" alt="image" src="https://github.com/user-attachments/assets/334b8c39-d547-4743-aca0-de92e38bdd1c" />



## Algorithm
Start the program and read a 9×9 Sudoku board input, where empty cells are represented by 0.
Define a function isSafe() to check if a number can be placed in a cell without violating Sudoku rules (row, column, and 3×3 box).
Use the recursive function solveSudoku() to fill empty cells one by one using backtracking.
If the number placement leads to a valid configuration, continue recursively; otherwise, backtrack by resetting the cell to 0.
After solving, print the completed Sudoku board if a solution exists; otherwise, display "No solution exists." 

## Program:
```
import java.util.Scanner;

public class SudokuSolver {

    static boolean isSafe(int[][] board, int row, int col, int num) {
        for (int i = 0; i < 9; i++) {
            if (board[row][i] == num || board[i][col] == num)
                return false;
        }
        int startRow = row - row % 3;
        int startCol = col - col % 3;
        for (int i = 0; i < 3; i++)
            for (int j = 0; j < 3; j++)
                if (board[startRow + i][startCol + j] == num)
                    return false;
        return true;
    }

    static boolean solveSudoku(int[][] board, int row, int col) {
        if (row == 9)
            return true;
        if (col == 9)
            return solveSudoku(board, row + 1, 0);
        if (board[row][col] != 0)
            return solveSudoku(board, row, col + 1);

        for (int num = 1; num <= 9; num++) {
            if (isSafe(board, row, col, num)) {
                board[row][col] = num;
                if (solveSudoku(board, row, col + 1))
                    return true;
                board[row][col] = 0;
            }
        }
        return false;
    }

    static void printBoard(int[][] board) {
        for (int[] row : board) {
            for (int val : row)
                System.out.print(val + " ");
            System.out.println();
        }
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int[][] board = new int[9][9];
        for (int i = 0; i < 9; i++)
            for (int j = 0; j < 9; j++)
                board[i][j] = sc.nextInt();

        if (solveSudoku(board, 0, 0)) {
            System.out.println("Solved Sudoku:");
            printBoard(board);
        } else {
            System.out.println("No solution exists.");
        }
        sc.close();
    }
}
```

## Output:

<img width="716" height="598" alt="image" src="https://github.com/user-attachments/assets/da489f3d-0d2a-4c0c-9102-dde7348cd06f" />


## Result:
The program successfully implemented and the expected output is verified.

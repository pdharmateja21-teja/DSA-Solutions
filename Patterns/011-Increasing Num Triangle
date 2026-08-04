public class Solution {

    public static void nNumberTriangle(int n) {

        // Variable to keep track of the current number to be printed.
        // It starts from 1 and increases after every print.
        int count = 1;

        // Outer loop controls the number of rows.
        // It runs from 1 to n.
        for (int i = 1; i <= n; i++) {

            // Inner loop prints numbers in the current row.
            // Row 1 prints 1 number.
            // Row 2 prints 2 numbers.
            // Row 3 prints 3 numbers.
            // ...
            // Row n prints n numbers.
            for (int j = 1; j <= i; j++) {

                // Print the current value of count.
                System.out.print(count + " ");

                // Increment count so that the next number
                // printed is one greater than the current number.
                count++;
            }

            // Move to the next line after completing the current row.
            System.out.println();
        }
    }
}

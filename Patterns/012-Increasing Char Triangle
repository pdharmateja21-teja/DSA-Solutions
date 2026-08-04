public class Solution {

    public static void nLetterTriangle(int n) {

        // The outer loop controls the number of rows.
        // It runs from 0 to (n - 1).
        for (int i = 0; i < n; i++) {

            // The inner loop prints characters from 'A'
            // up to the current row.
            //
            // Row 0 -> A
            // Row 1 -> A B
            // Row 2 -> A B C
            // ...
            for (int j = 0; j <= i; j++) {

                // Convert the character using ASCII values.
                //
                // 'A' has an ASCII value of 65.
                //
                // Examples:
                // j = 0 -> 'A' + 0 = 'A'
                // j = 1 -> 'A' + 1 = 'B'
                // j = 2 -> 'A' + 2 = 'C'
                //
                // The result is explicitly typecast to 'char'
                // because ('A' + j) produces an integer value.
                System.out.print((char) ('A' + j) + " ");
            }

            // Move to the next line after completing the current row.
            System.out.println();
        }
    }
}

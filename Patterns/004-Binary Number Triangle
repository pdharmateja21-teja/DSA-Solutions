public class Solution {
    public static void nBinaryTriangle(int n) {

        // Loop through each row
        for (int i = 0; i < n; i++) {

            // Print elements in the current row
            // Number of elements = i + 1
            for (int j = 0; j <= i; j++) {

                // If the sum of row and column indices is even,
                // print 1; otherwise, print 0.
                // This creates the alternating binary pattern.
                if ((i + j) % 2 == 0) {
                    System.out.print("1 ");
                } else {
                    System.out.print("0 ");
                }
            }

            // Move to the next line after completing the current row
            System.out.println();
        }
    }
}


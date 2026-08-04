public class Solution {

    public static void numberCrown(int n) {

        // The outer loop controls the number of rows.
        // It runs from 1 to n.
        for (int i = 1; i <= n; i++) {

            // ---------------- Left Increasing Numbers ----------------
            // Print numbers from 1 to the current row number.
            //
            // Example (n = 4):
            // Row 1 : 1
            // Row 2 : 1 2
            // Row 3 : 1 2 3
            for (int j = 1; j <= i; j++) {
                System.out.print(j + " ");
            }

            // ---------------- Middle Spaces ----------------
            // Print spaces between the left and right halves.
            //
            // Number of spaces decreases as the row number increases.
            //
            // Formula:
            // 2 × (n - i)
            //
            // Example (n = 4):
            // Row 1 → 6 spaces
            // Row 2 → 4 spaces
            // Row 3 → 2 spaces
            // Row 4 → 0 spaces
            for (int j = 1; j <= 2 * (n - i); j++) {
                System.out.print(" ");
            }

            // ---------------- Right Decreasing Numbers ----------------
            // Print numbers from the current row number back to 1.
            //
            // Example:
            // Row 3 → 3 2 1
            // Row 4 → 4 3 2 1
            for (int j = i; j >= 1; j--) {
                System.out.print(j + " ");
            }

            // Move to the next row.
            System.out.println();
        }
    }
}

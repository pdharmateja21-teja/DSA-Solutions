import java.util.Scanner;

class GFG {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Read the number of rows
        int n = sc.nextInt();

        // -------------------- Upper Half --------------------
        // Print stars in increasing order from 1 to n
        for (int i = 0; i < n; i++) {

            // Print (i + 1) stars in the current row
            for (int j = 0; j <= i; j++) {
                System.out.print("* ");
            }

            // Move to the next line after each row
            System.out.println();
        }

        // -------------------- Lower Half --------------------
        // Print stars in decreasing order from n-1 to 1
        // Start from n-2 to avoid printing the middle row twice
        for (int i = n - 2; i >= 0; i--) {

            // Print (i + 1) stars in the current row
            for (int j = 0; j <= i; j++) {
                System.out.print("* ");
            }

            // Move to the next line after each row
            System.out.println();
        }
    }
}

## Code 

public class GFG { 
    // Function to return the minimum number of delete operations
    static int findMinimumDeletion(int l, int r, int dp[][], String s) {
        if (l > r) {
            return 0;
        }
        if (l == r) {
            return 1;
        }
        if (dp[l][r] != -1) {
            return dp[l][r];
        }

        // When a single character is deleted
        int res = 1 + findMinimumDeletion(l + 1, r, dp, s);

        // When a group of consecutive characters are deleted if any of them matches
        for (int i = l + 1; i <= r; ++i) {
            // When both the characters are same then delete the letters in between them
            if (s.charAt(l) == s.charAt(i)) {
                res = Math.min(res, findMinimumDeletion(l + 1, i - 1, dp, s)
                        + findMinimumDeletion(i, r, dp, s));
            }
        }

        // Memoize
        return dp[l][r] = res;
    }

    // Driver code
    public static void main(String[] args) {
        String s = "kjslaqpwoereeeeewwwefifjdksjdfhjdksdjfkdfdlddkjdjfjfjfjjjjfjffnefhkjgefkgjefkjgkefjekihutrieruhigtefhgbjkkkknbmssdsdsfdvneurghiueor";
        int n = s.length();
        int dp[][] = new int[n][n];
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                dp[i][j] = -1;
            }
        }
        System.out.println(findMinimumDeletion(0, n - 1, dp, s));
    }
}


## Output

78

## Code

import java.util.Arrays;

public class MinTaskCost {
    public static int minTaskCost(int[] workers) {
        int n = workers.length;
        int minCost = Integer.MAX_VALUE;
        int[] sortedWorkers = Arrays.copyOf(workers, n);
        Arrays.sort(sortedWorkers);
        for (int i = 0; i < n; i++) {
            int[] remainingWorkers = new int[n - 1];
            System.arraycopy(sortedWorkers, 0, remainingWorkers, 0, i);
            System.arraycopy(sortedWorkers, i + 1, remainingWorkers, i, n - i - 1);
            int cost = 0;
            for (int j = 0; j < n - 2; j += 2) {
                cost += Math.abs(remainingWorkers[j] - remainingWorkers[j+1]);
            }
            if (cost < minCost) {
                minCost = cost;
            }
        }
        return minCost;
    }

    public static void main(String[] args) {
        int[] workers = {1, 3, 54, 712, 52, 904, 113, 12, 135, 32, 31, 56, 23, 79, 611, 123, 677, 232, 997, 101, 111, 123, 2, 7, 24, 57, 99, 45, 666, 42, 104, 129, 554, 335, 876, 35, 15, 93, 13};
        int minCost = minTaskCost(workers);
        System.out.println(minCost);
    }
}

## output

475
![Challenge-4](https://github.com/dalawai01/algo-challenge/assets/130344323/09eba791-0a79-4520-bf1c-a702a14de52a)

## Code

import java.util.ArrayList;
import java.util.List;

public class Permutations {
    public static void main(String[] args) {
        String input = "1867";
        List<String> perms = generatePermutations(input);
        List<Integer> divisiblePerms = findDivisiblePermutations(perms);
        
        if (!divisiblePerms.isEmpty()) {
            int min = findMin(divisiblePerms);
            int max = findMax(divisiblePerms);
            double avg = (double) (min + max) / 2;
            System.out.println(avg);
        } else {
            System.out.println("No permutations are divisible by 7");
        }
    }
    
    public static List<String> generatePermutations(String input) {
        List<String> permutations = new ArrayList<>();
        permute("", input, permutations);
        return permutations;
    }
    
    private static void permute(String prefix, String suffix, List<String> permutations) {
        if (suffix.length() == 0) {
            permutations.add(prefix);
            return;
        }
        
        for (int i = 0; i < suffix.length(); i++) {
            char current = suffix.charAt(i);
            String newPrefix = prefix + current;
            String newSuffix = suffix.substring(0, i) + suffix.substring(i + 1);
            permute(newPrefix, newSuffix, permutations);
        }
    }
    
    public static List<Integer> findDivisiblePermutations(List<String> permutations) {
        List<Integer> divisiblePerms = new ArrayList<>();
        
        for (String perm : permutations) {
            int num = Integer.parseInt(perm);
            if (num % 7 == 0) {
                divisiblePerms.add(num);
            }
        }
        
        return divisiblePerms;
    }
    
    public static int findMin(List<Integer> numbers) {
        int min = numbers.get(0);
        for (int i = 1; i < numbers.size(); i++) {
            int current = numbers.get(i);
            if (current < min) {
                min = current;
            }
        }
        return min;
    }
    
    public static int findMax(List<Integer> numbers) {
        int max = numbers.get(0);
        for (int i = 1; i < numbers.size(); i++) {
            int current = numbers.get(i);
            if (current > max) {
                max = current;
            }
        }
        return max;
    }
}

  ## Output
  
  5152.0

    ![Challenge-3](https://github.com/dalawai01/algo-challenge/assets/130344323/a0df51e9-3be0-42f8-8e81-0a67432e534f)

    

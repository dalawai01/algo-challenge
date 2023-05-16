## Code

import java.util.HashMap;
import java.util.Map;

public class DecodeString {
    public static String decode(String encoded, Map<String, String> codebook) {
        StringBuilder decoded = new StringBuilder();
        StringBuilder currentCode = new StringBuilder();
        String[] validCodes = codebook.values().toArray(new String[0]);

        for (char bit : encoded.toCharArray()) {
            currentCode.append(bit);

            if (containsCode(validCodes, currentCode.toString())) {
                String symbol = getKeyByValue(codebook, currentCode.toString());
                decoded.append(symbol);
                currentCode.setLength(0);
            }
        }

        String decodedString = decoded.toString();
        decodedString = decodedString.replace("yab", " ");
        return decodedString;
    }

    private static boolean containsCode(String[] validCodes, String code) {
        for (String validCode : validCodes) {
            if (validCode.equals(code)) {
                return true;
            }
        }
        return false;
    }

    private static String getKeyByValue(Map<String, String> map, String value) {
        for (Map.Entry<String, String> entry : map.entrySet()) {
            if (entry.getValue().equals(value)) {
                return entry.getKey();
            }
        }
        return null;
    }

    public static void main(String[] args) {
        Map<String, String> codebook = new HashMap<>();
        codebook.put(" ", "11111111110001");
        codebook.put("z", "11111111110000");
        codebook.put("y", "1111111111");
        codebook.put("x", "1111111110");
        codebook.put("w", "1111111101");
        codebook.put("v", "1111111100");
        codebook.put("u", "1111111011");
        codebook.put("t", "1111111010");
        codebook.put("s", "1111111001");
        codebook.put("r", "1111111000");
        codebook.put("q", "1111110111");
        codebook.put("p", "1111110110");
        codebook.put("o", "1111110101");
        codebook.put("n", "1111110100");
        codebook.put("m", "1111110011");
        codebook.put("l", "1111110010");
        codebook.put("k", "1111110001");
        codebook.put("j", "1111110000");
        codebook.put("i", "111110");
        codebook.put("h", "111101");
        codebook.put("g", "111100");
        codebook.put("f", "1110");
        codebook.put("e", "1101");
        codebook.put("d", "1100");
        codebook.put("c", "10");
        codebook.put("b", "01");
        codebook.put("a", "00");

        String encodedString = "11111011111111110001111111001011111101011111111100110111111111110001001111110100111100110111111100101111010010111111000111111111110001101111110101110011011111111111000110111101001111110010111111001011011111110100111100110111111111110001011101100011111110111111111001110111111111110001111110111111101011111111110001111110111111100111111111110001111011111110111111110100111111111100010011111101001100111111111100011101111111111010111110111111101011111011111101001111001111111111000100111111010011001111111111000111111011111111110001110011111011111110011111110010111110111111000111011111111111000111111110101111011101111111111100011111111101111111010111111110001100111111111100011111111111000111111111110001111111101011110100111111101011111111110001001111110110111111011011010011111110001111111001111111111100011111101111110100111111111100011111111010111101110111111111110001111111011011110111111110000011111110011101";

String decodedString = decode(encodedString, codebook);
System.out.println(decodedString);
}
}


## Output

i love angelhack code challenge because it is fun and exciting and i dislike the word   that appears in the phrase

![Challenge-5](https://github.com/dalawai01/algo-challenge/assets/130344323/2284b24e-14ff-4d0c-95d5-1ad832bec969)

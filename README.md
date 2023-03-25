# Hackerrank Java (Basic) Certification Solutions

## Shapes
Below is the solution to the problem:
```
import java.io.*;
import java.util.*;
import java.text.*;
import java.math.*;
import java.util.regex.*;

class Shape {
    int length, breadth;

    public Shape(int length, int breadth) {
        this.length = length;
        this.breadth = breadth;
    }

    public void area() {
        System.out.println(length + " " + breadth);
    }
}

class Rectangle extends Shape {
    public Rectangle(int length, int breadth) {
        super(length, breadth);
    }

    @Override
    public void area() {
        System.out.println(length * breadth);
    }
}

public class Solution {
    public static void main(String args[] ) throws Exception {
        Scanner sc = new Scanner(System.in);
        int l = sc.nextInt();
        int b = sc.nextInt();

        Shape shape = new Shape(l,b);
        shape.area();

        Shape rectangle = new Rectangle(l,b);
        rectangle.area();
    }
}
```

## Encryption Decryption
Below is the solution to the problem:
```
import java.io.*;
import java.math.*;
import java.security.*;
import java.text.*;
import java.util.*;
import java.util.concurrent.*;
import java.util.function.*;
import java.util.regex.*;
import java.util.stream.*;
import static java.util.stream.Collectors.joining;
import static java.util.stream.Collectors.toList;

class Result {
    
    public static String decryptMessage(String encryptedMessage) {
        // Split the encrypted message into individual words
        String[] words = encryptedMessage.split("\\s+");
        
        // Reverse the order of the words
        Collections.reverse(Arrays.asList(words));
        
        // Iterate through each word and decrypt it
        StringBuilder decryptedMessage = new StringBuilder();
        for (String word : words) {
            // Check if the word has been compressed
            if (word.matches("\\w+\\d+")) {
                // Decrypt the compressed word
                StringBuilder decryptedWord = new StringBuilder();
                for (int i = 0; i < word.length(); i++) {
                    char c = word.charAt(i);
                    if (Character.isDigit(c)) {
                        int count = Character.getNumericValue(c);
                        for (int j = 0; j < count; j++) {
                            decryptedWord.append(word.charAt(i - 1));
                        }
                    } else {
                        decryptedWord.append(c);
                    }
                }
                decryptedMessage.append(decryptedWord).append(" ");
            } else {
                // Add the word to the decrypted message
                decryptedMessage.append(word).append(" ");
            }
        }
        
        // Remove the trailing space and return the decrypted message
        return decryptedMessage.toString().trim();
    }

}

public class Solution {
    
    public static void main(String[] args) throws IOException {
        BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bufferedWriter = new BufferedWriter(new FileWriter(System.getenv("OUTPUT_PATH")));

        String encryptedMessage = bufferedReader.readLine();

        String result = Result.decryptMessage(encryptedMessage);

        bufferedWriter.write(result);
        bufferedWriter.newLine();

        bufferedReader.close();
        bufferedWriter.close();
    }
}
```

# filereading
# We are going to read the file and than calculate the sales

import java.io.File;
import java.io.FileNotFoundException;
import java.util.ArrayList;
import java.util.Scanner;

  public class Newclass {
    public static void main(String[] args) {
        ArrayList<Integer> Arr = new ArrayList<>();
        int total = 0;
        int E011total = 0;
        int E012total = 0;
        int E013total = 0;
        int E014total = 0;

        try {
            File f1 = new File("sample.txt");
            Scanner s1 = new Scanner(f1);
            s1.nextLine(); // skip header

            while (s1.hasNextLine()) {
                String line = s1.nextLine();
                String[] sets = line.split("\t");

                int price = Integer.parseInt(sets[2]);
                int qty = Integer.parseInt(sets[3]);
                total = qty * price;
                String item = sets[5];

                if (item.equals("E011")) {
                    E011total += total;
                }
                if (item.equals("E012")) {
                    E012total += total;
                }
                if (item.equals("E013")) {
                    E013total += total;
                }
                if (item.equals("E014")) {
                    E014total += total;
                }
            }

        } catch (FileNotFoundException e) {
            System.out.println("File not found");
            return; // Exit if file is not found
        }

        Arr.add(E011total);
        Arr.add(E012total);
        Arr.add(E013total);
        Arr.add(E014total);
        System.out.println(Arr);
    }
}

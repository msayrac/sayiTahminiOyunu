# sayiTahminiOyunu
import java.lang.reflect.Array;
import java.util.Arrays;
import java.util.Random;
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Random rand = new Random();

        int number = rand.nextInt(100);

        System.out.println(number);


        // int number = (int)(Math.random()*100);
        Scanner input = new Scanner(System.in);

        int right = 0;
        int selected;
        int[] wrong = new int[5];

        boolean isWin = false;
        boolean isWrong = false;

        while (right < 5) {
            System.out.println("Lutfen tahmininizi giriniz : ");
            selected = input.nextInt();
            if (selected < 0 || selected > 99) {
                System.out.println("0 ile 100 arasi sayi giriniz");
                if(isWrong){
                    right++;
                    System.out.println("Cok fazla hatali giris yaptiniz. Hakan hak : "+ (5-right));
                } else{
                    isWrong=true;
                    System.out.println("Bir daha hatada can hakkinizdan dusulecektir");

                }
                continue;

            }
            if (selected == number) {
                System.out.println("Tebrikler dogru tahmin : " + number);
                isWin = true;
                break;
            } else {
                wrong[right] = selected;
                right++;
                System.out.println("Hatali sayi girdiniz");
                if (selected > number) {
                    System.out.println(selected + " sayisi gizli saiydan buyuktur.");
                } else {
                    System.out.println(selected + " sayisi gizli sayidan kucuktur.");
                }
                System.out.println("Kalan hakkiniz : " + (5 - right));
            }
        }


        if (!isWin && !isWrong) {
            System.out.println("Kaybettiniz ");
        }
        System.out.println("Yalis sayilar : " + Arrays.toString(wrong));


    }
}

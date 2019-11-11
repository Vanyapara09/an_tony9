package com.company;

public class Atm {

    private int kup20;
    private int kup50;
    private int kup100;
    private int e;
    private int s;
    private boolean b = true;

    public Atm(int kup20, int kup50, int kup100) {
        this.kup20 = kup20;
        this.kup50 = kup50;
        this.kup100 = kup100;

    }

    public void refill20(int amount) {
        kup20 += amount / 20;
    }

    public void refill50(int amount) {
        kup50 += amount / 50;
    }

    public void refill100(int amount) {
        kup100 += amount / 100;
    }

    public boolean withdrawMoney(int amount1) {
        e = amount1;
        s = kup20 * 20 + kup50 * 50 + kup100 * 100;
        if (amount1 <= s) {
            if (amount1 % 100 >= 50) {
                kup100 = amount1 / 100;
                if (amount1 % 100 % 20 == 0) {
                    kup50 = 0;
                    kup20 = amount1 % 100 / 20;
                } else {
                    kup50 = amount1 % 100 / 50;
                    kup20 = amount1 % 50 / 20;
                }

            } else {
                kup100 = amount1 / 100 - 1;
                if (amount1 % 100 % 20 != 0) {
                    kup50 = 1;
                    kup20 = (amount1 - kup100 * 100 - kup50 * 50) / 20;
                } else {
                    kup50 = 0;
                    kup20 = (amount1 - kup100 * 100) / 20;
                }

            }
        } else b = false;

        return b;
    }

    public void printAmount() {
        if (b) {
            System.out.println("Summa= " + e);
            System.out.println("Купюр po 100= " + kup100 + "\nKupur po 50= " + kup50 + "\nKupur po 20= " + kup20);
            System.out.println("Operaciya odobrena");
        } else System.out.println("Otkloneno");
    }
}

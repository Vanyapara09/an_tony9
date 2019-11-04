# an_tony9
public class Bankomat {

        int kup20,kup50,kup100,e,ostatok,s;
        boolean b=true;
        public Bankomat(int kup20, int kup50, int kup100){
            this.kup20=kup20;
            this.kup50=kup50;
            this.kup100=kup100;
            s=kup20*20+kup50*50+kup100*100;
        }
        public boolean Popolnenie(int Summa){
            kup100+=Summa/100;
            kup50+=Summa%100/50;
            kup20+=Summa%50/20;
            s+=Summa;
            return  b;
        }
        public boolean Snyatie(int Summa1) {
            e=Summa1;

            if(Summa1<s) {
                if(Summa1%100>=50){
                kup100=Summa1/100;
                if(Summa1%100%20==0){kup50=0;
                    kup20=Summa1%100/20;}
                else{
                    kup50=Summa1%100/50;
                    kup20=Summa1%50/20;
                }

            }else{
                    kup100=Summa1/100-1;
                    kup50=1;
                    kup20=(Summa1-kup100*100-kup50*50)/20;
                }
            }

            else b=false;

           return b;
        }
        public void printSumma(){
            if(b){
            System.out.println("Summa= "+e);
            System.out.println("Купюр po 100= "+kup100+"\nKupur po 50= "+kup50+"\nKupur po 20= "+kup20);
                System.out.println("Operaciya odobrena");
        }
            else System.out.println("Otkloneno");
        }
}

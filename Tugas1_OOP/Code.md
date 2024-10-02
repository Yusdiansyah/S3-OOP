```java
public class pesawat{
    private final String warna;
    private int ketinggian;
    private int kecepatan;
    private int energi;
    private String arah;
    private static final int MAX_KETINGGIAN = 24000;
    private static final int MAX_KECEPATAN = 3000;

    public pesawat (String warna){
        this.warna = warna;
        this.ketinggian = 0;
        this.kecepatan = 0;
        this.energi = 100;
        this.arah = "barat";
    }

    public void nyalakanMesin() throws InterruptedException{
        System.out.println("Menyalakan mesin Pesawat... ");
        System.out.println("Pesawat memulai terbang... ");
    }

    public void mulaiTerbang(){
        if (this.kecepatan > 0) {
            if (this.energi >= 10) {
                this.energi -= 10;
                System.out.println("Pesawat berhasil terbang ");
            } 
            else {
                System.out.println("Energi tidak cukup untuk terbang! ");
            }
            
        }
        else {
            System.out.println("Pesawat harus memiliki kecepatan untuk terbang. ");
        }
    }
    
    public void tambahKecepatan(int kecepatan){
        this.kecepatan += kecepatan;
        if (kecepatan > MAX_KECEPATAN) {
            this.kecepatan = MAX_KECEPATAN;
        }
        System.out.println("kecepatan pesawat bertambah menjadi "+ this.kecepatan +"km/jam");
    }

    
    public void kurangiKecepatan(int kecepatan){
        this.kecepatan -= kecepatan;
        if (kecepatan < 0 ) {
            this.kecepatan = 0;
        }
        System.out.println("kecepatan pesawat berkurang menjadi "+ this.kecepatan +"km/jam");
    }

    public void belok(String arah) {
        this.arah = arah;
        System.out.println("Pesawat berbelok ke "+this.arah);
    }

    public void turun(){
        if (this.ketinggian - 100 >= 0) {
            this.ketinggian -= 100;

            System.out.println("Pesawat turun ke ketinggian "+ this.ketinggian +"mdpl.");
        } else { 
            System.out.println("Pesawat telah mendarat.");
        }
    }

    public void naik(){
        if (this.ketinggian + 100 <= MAX_KETINGGIAN) {
            this.ketinggian += 100;
        } else {
            System.out.println("DANGER! Pesawat telah mencapai ketinggian maksimum!");
            System.out.println("Melanjutkan akan menempatkan Pesawat dalam bahaya.");
        }
    }

    public void infoPesawat(){
        System.out.println("=========================");
        System.out.println("Informasi Pesawat");
        System.out.println("Warna: "+this.warna);
        System.out.println("Ketinggian: "+this.ketinggian+" mdpl");
        System.out.println("Kecepatan; "+this.kecepatan+" km/j");
        System.out.println("Energi: "+this.energi+"%");
        System.out.println("Arah: "+this.arah);
        System.out.println("=========================");
    }

    public static void main(String[] args) throws InterruptedException {
        pesawat SR71_Blackbird = new pesawat("Hitam");
        SR71_Blackbird.infoPesawat();
        SR71_Blackbird.nyalakanMesin();
        SR71_Blackbird.mulaiTerbang();
        SR71_Blackbird.tambahKecepatan(200);
        SR71_Blackbird.mulaiTerbang();
        SR71_Blackbird.naik();
        SR71_Blackbird.belok("Kiri");
        SR71_Blackbird.kurangiKecepatan(100);
        SR71_Blackbird.turun();
        SR71_Blackbird.kurangiKecepatan(100);
        SR71_Blackbird.turun();
        SR71_Blackbird.infoPesawat();
    }
}
```

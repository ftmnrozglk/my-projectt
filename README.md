# my-projectt
import java.util.Scanner;

public class ${NAME} {
    private static String kullaniciAdi;
    private static String sifre;
    private static double bakiye = 5000.0;

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.println("Kullanıcı adınızı giriniz:");
        kullaniciAdi = scanner.nextLine();

        System.out.println("Şifrenizi giriniz:");
        sifre = scanner.nextLine();

        if (girisYap()) {
            System.out.println("Giriş başarılı!");
            anaMenuGoster(scanner);
        } else {
            System.out.println("Hatalı kullanıcı adı veya şifre!");
        }
    }

    private static boolean girisYap() {
        return "fatma".equals(kullaniciAdi) && "3644".equals(sifre);
    }

    private static void anaMenuGoster(Scanner scanner) {
        int secim;

        do {
            System.out.println("\nAna Menü:");
            System.out.println("1 - Kullanıcı adını değiştir");
            System.out.println("2 - Şifreyi değiştir");
            System.out.println("3 - Para çek");
            System.out.println("4 - Para yatır");
            System.out.println("0 - Çıkış");
            System.out.print("Seçiminizi yapınız: ");
            secim = scanner.nextInt();

            switch (secim) {
                case 1 -> kullaniciAdiDegistir(scanner);
                case 2 -> sifreDegistir(scanner);
                case 3 -> paraCek(scanner);
                case 4 -> paraYatir(scanner);
                case 0 -> System.out.println("Çıkış yapılıyor...");
                default -> System.out.println("Geçersiz seçim! Lütfen tekrar deneyin.");
            }
        } while (secim != 0);
    }

    private static void kullaniciAdiDegistir(Scanner scanner) {
        System.out.print("Yeni kullanıcı adını giriniz: ");
        String yeniKullaniciAdi = scanner.next();
        System.out.println("Kullanıcı adı" + yeniKullaniciAdi + " olarak değiştirildi");
        kullaniciAdi = yeniKullaniciAdi;
    }

    private static void sifreDegistir(Scanner scanner) {
        System.out.print("Yeni şifreyi giriniz: ");
        String yeniSifre = scanner.next();
        System.out.println("Şifreniz " + yeniSifre + " olarak değiştirildi");
        sifre = yeniSifre;
    }

    private static void paraCek(Scanner scanner) {
        System.out.print("Çekmek istediğiniz tutarı giriniz: ");
        double cekilecekTutar = scanner.nextDouble();

        if (cekilecekTutar <= bakiye) {
            bakiye -= cekilecekTutar;
            System.out.println("Para çekme işlemi başarılı. Kalan bakiye: " + bakiye);
            if (cekilecekTutar > 10000) {
                System.out.println("Dikkat! Çekilen tutar " + bakiye + " 'nin üzerinde.");
            } else if (cekilecekTutar == 5000) {
                System.out.println("Çekilen tutar 5000 TL.");
            }
        } else {
            System.out.println("Yetersiz bakiye! İşlem gerçekleştirilemedi.");
        }

        anaMenuGoster(scanner);
    }

    private static void paraYatir(Scanner scanner) {
        System.out.print("Yatırmak istediğiniz tutarı giriniz: ");
        double yatirilacakTutar = scanner.nextDouble();
        bakiye += yatirilacakTutar;
        System.out.println("Para yatırma işlemi başarılı. Yeni bakiye: " + bakiye);

        anaMenuGoster(scanner);
    }
}

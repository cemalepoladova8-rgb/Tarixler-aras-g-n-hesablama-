#include <stdio.h>

int gun_hesabla(int gun, int ay, int il) {
    int aylar[] = {31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31};
    int cem = 0;

    // Ayların günlərini toplamaq
    for (int i = 0; i < ay - 1; i++) {
        cem += aylar[i];
    }

    // Günləri əlavə etmək
    cem += gun;

    // Uzun il yoxlanışı (sadə)
    if (il % 4 == 0 && ay > 2) {
        cem++;
    }

    // Keçmiş illərin günləri
    cem += (il - 1) * 365 + (il - 1) / 4;

    return cem;
}

int main() {
    int g1, a1, i1;
    int g2, a2, i2;

    printf("Birinci tarixi daxil edin (gun ay il): ");
    scanf("%d %d %d", &g1, &a1, &i1);

    printf("Ikinci tarixi daxil edin (gun ay il): ");
    scanf("%d %d %d", &g2, &a2, &i2);

    int ferq = gun_hesabla(g2, a2, i2) - gun_hesabla(g1, a1, i1);

    if (ferq < 0) {
        ferq = -ferq;
    }

    printf("Tarixler arasindaki gunlerin sayi: %d\n", ferq);

    return 0;
}

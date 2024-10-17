#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <math.h>
void kiemtrasonguyen() {
    float x;
    printf("Nhap 1 so bat ky: ");scanf("%f",&x);
    if (x==(int)x)
        printf("%.2f la so nguyen\n",x);
    else printf("%.2f la so thuc\n",x);
    if(x>1 && x==(int)x) {
        int KtraSNT =1;
        for(int i=2;i<=sqrt(x);i++) {
            if((int)x%i==0) {
                KtraSNT=0;
                break;
            }
        }
        if(KtraSNT==1)
            printf("%.2f la so nguyen to\n",x);
        else printf("%.2f khong phai la so nguyen to\n",x);
    }else printf("%.2f khong phai  la so nguyen to\n",x);
}
void USCLNvaBSCNN() {
    int a,b,USCLN,BSCNN;
    nhaplai:
    printf("Nhap 2 so A va B: ");scanf("%d%d",&a,&b);
    if (a==0 && b==0) {
        printf("du lieu khong hop le\n");
        goto nhaplai;
    }
    int so1=a,so2=b;
    if (a==0 || b==0) {
        USCLN=a+b;
    }else
        while(a!=b) {
            if (a>b) a=a-b;
            else b=b-a;
        }
    USCLN=a;
    printf("USCLN( %d , %d )= %d\n",so1,so2,USCLN);
    BSCNN=so1*so2/USCLN;
    printf("BSCNN( %d , %d )= %d\n",so1,so2,BSCNN);
}
void tinhtienkaraoke() {
    float giovao,giora;
    nhaplai:
    printf("nhap gio vao: ");scanf("%f",&giovao);
    printf("nhap gio ra: ");scanf("%f",&giora);
    if(giovao>=giora || giovao <12 || giora>23) {
        puts("gio vao va gio ra khong hop le! xin vui long nhap lai!!!");
        goto nhaplai;
    }
    const int gia=150000;
    int TongTG=0;
    int TienTra=0;
    if (giovao>14 && giora<17) {
        TongTG=giora-giovao;
        TienTra=TongTG*gia*0.9;
    }else {
        TongTG=giora-giovao;
        if (TongTG>3) {
            TienTra=3*gia+(TongTG-3)*0.9*gia;
        }else TienTra=TongTG*gia;
    }
    printf("Tien phai tra: %d\n",TienTra);
}
void tinhtiendientieuthuhogiadinh() {
    float d,t;
    printf("nhap so dien tieu thu hang thang: ");scanf("%f",&d);
    if(d<0) {
        printf("nhap sai so dien ieu dung! vui long nhap lai!");
    }else if (d>=0 && d<=50) {
        t=d*1.678;
        printf("so tien dien can phai dong la: %.2f\n",t);
    }else if (d>=51 && d<=100) {
        t=50*1.678+(d-50)*1.734;
        printf("so tien dien can phai dong la: %.2f\n",t);
    }else if (d>=101 && d<=200) {
        t=50*1.678+50*1.734+(d-100)*2.014;
        printf("so tien dien can phai dong la: %.2f\n",t);
    }else if (d>=201 && d<=300) {
        t=50*1.678+50*1.734+100*2.014+(d-200)*2.536;
        printf("so tien dien can phai dong la: %.2f\n",t);
    }else if (d>=301 && d<=400) {
        t=50*1.678+50*1.734+100*2.014+100*2.536+(d-300)*2.834;
        printf("so tien dien can phai dong la: %.2f\n",t);
    }else if (d>=401) {
        t=50*1.678+50*1.734+100*2.014+100*2.536+100*2.834+(d-400)*2.927;
        printf("so tien dien can phai dong la: %.2f\n",t);
    }
}
void tienlaivayNH() {
    float Sotienvay;
    float Laisuatvay;
    int Kyhan;
    float Sotienconlai;
    float Laiphaitra;
float Sotienphaitra;
    printf("Nhap so tien vay: ");scanf("%f",&Sotienvay);
    printf("Nhap lai thang: ");scanf("%f",&Laisuatvay);
    printf("Nhap ky han: ");scanf("%d",&Kyhan);
    const float Gocphaitra = Sotienvay / Kyhan;
    Sotienconlai = Sotienvay;
    printf("Ky han\t lLai phai tra\t Goc phai tra\t So tien phai tra\t So tien con lai\n");
    for(int i= 1;i <= Kyhan;i++){
    Laiphaitra = Laisuatvay*Sotienconlai;
    Sotienphaitra = Gocphaitra + Laiphaitra;
    Sotienconlai = Sotienconlai - Gocphaitra;
    printf(" %d\t%.0f\t\t%.0f\t\t%.0f\t\t\t%.0f\n",i,Laiphaitra,
    Gocphaitra,Sotienphaitra,Sotienconlai);
    }
}
struct Sinhvien {
    char hoten[50];
    float diem;
    char hocluc[10];
};
void nhapsv(struct Sinhvien sv[], int n);
void xuatsv(struct Sinhvien sv[], int n);
void hocluc(struct Sinhvien sv[], int n);
void sapxepdiem(struct Sinhvien sv[], int n);
int sapxepTSV() {
    struct Sinhvien sv[100];
    int n;
    printf("Nhap so sinh vien: ");
    scanf("%d", &n);
    getchar();
    nhapsv(sv, n);
    puts("Danh sach chua sap xep: ");
    hocluc(sv, n);
    xuatsv(sv, n);
    sapxepdiem(sv, n);
    puts("Danh sach sau sap xep: ");
    xuatsv(sv, n);
}
void nhapsv(struct Sinhvien sv[], int n) {
    for (int i = 0; i < n; i++) {
        printf("Nhap sinh vien thu %d\n", i + 1);

        printf("Nhap ho ten: ");
        gets(sv[i].hoten);
        printf("Nhap diem: ");
        scanf("%f", &sv[i].diem);
        getchar();
    }
}
void xuatsv(struct Sinhvien sv[], int n) {
    for (int i = 0; i < n; i++) {
        printf("Sinh vien thu %d:\n", i + 1);
        printf("Ho ten: "); puts(sv[i].hoten);
        printf("Diem: %.2f\n", sv[i].diem);
        printf("Hoc Luc: "); puts(sv[i].hocluc);
    }
}
void hocluc(struct Sinhvien sv[], int n) {
    for (int i = 0; i < n; i++) {
        if (sv[i].diem >= 9 && sv[i].diem <= 10)
            strcpy(sv[i].hocluc, "Xuat Sac");
        else if (sv[i].diem >= 8 && sv[i].diem < 9)
            strcpy(sv[i].hocluc, "Gioi");
        else if (sv[i].diem >= 6.5 && sv[i].diem < 8)
            strcpy(sv[i].hocluc, "Kha");
        else if (sv[i].diem >= 5 && sv[i].diem < 6.5)
            strcpy(sv[i].hocluc, "Trung Binh");
        else
            strcpy(sv[i].hocluc, "Yeu");
    }
}
void sapxepdiem(struct Sinhvien sv[], int n) {
    for (int i = 0; i < n - 1; i++) {
        for (int j = i + 1; j < n; j++) {
            if (sv[i].diem < sv[j].diem) {
                struct Sinhvien tam = sv[i];
                sv[i] = sv[j];
                sv[j] = tam;
            }
        }
    }
}
void tinhtoanphanso() {
	float a,b,c,d;
    printf("moi ban nhap vao (tu so) thu nhat : ");scanf("%f",&a);
    printf("moi ban nhap vao (mau so) thu nhat: ");scanf("%f",&b);
    printf("moi ban nhap vao (tu so) thu hai : ");scanf("%f",&c);
    printf("moi ban nhap vao (mau so) thu hai : ");scanf("%f",&d);
    int tongt,tongm,hieut,hieum,thuongt,thuongm,ticht,tichm;
    tongt=(a*d)+(c*b);
    tongm=b*d;
    printf("tong cua hai phan so la :%d/%d\n",tongt,tongm);
    hieut=(a*d)-(c*b);
    hieum=b*d; 
    printf("hieu cua hai phan so la : %d/%d\n",hieut,hieum);
    ticht=a*c;
    tichm= b*d; 
    printf("tich cua 2 phan so la  : %d/%d\n",ticht,tichm);
    thuongt=a*d;
    thuongm=b*c; 
    printf("thuong cua 2 phan so la :%d/%d\n",thuongt,thuongm);
}
int main() {
    tieptuc:
        printf("******************************************\n");
        printf("* 1. Kiem tra so nguyen                  *\n");
        printf("* 2. USCLN va BSCNH cua 2 so             *\n");
        printf("* 3. Tinh tien quan karaoke              *\n");
        printf("* 4. Tinh tien dien tieu thu ho gia dinh *\n");
printf("* 5. Tinh tien lai vay tra gop ngan hang *\n");
        printf("* 6. Sap xep thong tin sinh vien         *\n");
        printf("* 7. Tinh toan phan so                   *\n");
        printf("******************************************\n");
        int op;
        printf("hay chon 1 menu: ");scanf("%d",&op);
        switch (op) {
            case 1:
                printf("Noi goi ham kiem tra so nguyen\n");
                kiemtrasonguyen();
                break;
            case 2:
                printf("Noi goi ham tim USCLN va BSCNH cua 2 so\n");
                USCLNvaBSCNN();
                break;
            case 3:
                printf("Noi goi ham tien quan karaoke\n");
                tinhtienkaraoke();
                break;
            case 4:
                printf("Noi goi ham tinh tien dien tieu thu ho gia dinh\n");
                tinhtiendientieuthuhogiadinh();
                break;
            case 5:
                printf("Noi goi ham tinh tien lai vay tra gop ngan hang\n");
                tienlaivayNH();
                break;
            case 6:
                printf("Noi goi ham sap xep thong tin tan sinh vien\n");
                sapxepTSV();
                break;
            case 7:
                printf("Noi goi ham tinh toan phan so\n");
                tinhtoanphanso();
                break;
            default:
                printf("Lua chon khong hop le vui long nhap lai!\n");
                break;
        }
    char ct[2];
    printf("Ban muon dung chuong trinh ? (go Y|N) ");scanf("%s",ct);
    if (stricmp(ct,"Y")==0) exit(0);
    else goto tieptuc;
}

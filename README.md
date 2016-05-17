# ogrenciotomasyonu
C programlama diinde öğrenci otomasyonu

#include<stdio.h>
#include<conio.h>
#include<string.h>
#include<stdlib.h>

    typedef struct ogrenci {
    	char ad[20], soyad[20];
    	int no,durum;
	}XX;
    XX yeni,bilgi,gecici;
 void menu();
 void ekle();
 void goster();
 void sil(int);
 void yenile(int);
 int  ekle (XX add){
 	FILE *dosya,*dosya2;
 	char satir[100],*ptr,dizi[10],dizi1[2],isim1[30],isim2[30];
 	dosya=fopen("ögrenciler1.txt","a+");
 	if(fgetc(dosya)<0){
 		fprintf(dosya," %d#%s#%s#%d\n",add.no,add.ad,add.soyad,add.durum);
 		fclose(dosya);
		 }
		 else{
	  int sayac=0,sayac2=0;
	  dosya2=fopen("ögrenciler2.txt","a+");
	  while(!feof(dosya)){
	  	char *ptr;
	  fscanf(dosya,"%s\n",satir);
 	  ptr = strtok(satir,"#");
 	  strcpy(dizi,satir);
 	  yeni.no=atoi(dizi);
 	  ptr=strtok(NULL,"#");
 	  strcpy(yeni.ad,ptr);
 	  ptr=strtok(NULL,"#");
 	  strcpy(yeni.soyad,ptr);
 	  ptr=strtok(NULL,"#");
 	  strcpy(dizi1,ptr);
 	  yeni.durum=atoi(dizi1);
 	  strcpy(isim1,yeni.ad);
 	  strcat(isim1,yeni.soyad);
 	  strcpy(isim2,add.ad);
 	  strcat(isim2,add.soyad);
 	  if(add.no==yeni.no){
 	  	sayac2++;
	   }
 	  if(strcmp(isim1,isim2)>0){
 	  	sayac++;
	   } 
	   	if(sayac==1){
	   	fprintf(dosya2," %d#%s#%s#%d\n",add.no,add.ad,add.soyad,add.durum);
		   }
	   	fprintf(dosya2," %d#%s#%s#%d\n",yeni.no,yeni.ad,yeni.soyad,yeni.durum);
			 }
			 if(sayac==0){
			 	fprintf(dosya2," %d#%s#%s#%d\n",add.no,add.ad,add.soyad,add.durum);
			 }
			 if(sayac2>0){
		printf("Ayni Numaradan 2 kayit olamaz\n ");
 	  	fclose(dosya);
 	  	fclose(dosya2);
 	  	remove("ögrenciler2.txt");
 	  	return -1;
			 }
			 else{
			 fclose(dosya2);
			 fclose(dosya);
			 remove("ögrenciler1.txt");
           	 rename("ögrenciler2.txt","ögrenciler1.txt");
           }
		 }
 }
 void goster(){
 	FILE *dosya;
 	dosya=fopen("ögrenciler1.txt","a+");
 	char satir[100],*ptr,dizi[10],dizi1[2];
 	if(fgetc(dosya)<0){
 		printf("Dosya bos\n");
 		fclose(dosya);
		 }
		 else{
	  while(!feof(dosya)){
	  fscanf(dosya,"%s\n",satir);
 	  ptr = strtok(satir,"#");
 	  strcpy(dizi,satir);
 	  yeni.no=atoi(dizi);
 	  ptr=strtok(NULL,"#");
 	  strcpy(yeni.ad,ptr);
 	  ptr=strtok(NULL,"#");
 	  strcpy(yeni.soyad,ptr);
 	  ptr=strtok(NULL,"#");
 	  strcpy(dizi1,ptr);
 	  yeni.durum=atoi(dizi1);
 	  if(yeni.durum!=0){
 	  	printf("Numara=%d\nIsim=%s\nSoyisim=%s\n",yeni.no,yeni.ad,yeni.soyad);
	   }
 }
 fclose(dosya);
		 }
 }
 void sil(int numara){
 	FILE *dosya,*dosya2;
 	dosya=fopen("ögrenciler1.txt","a+");
 	dosya2=fopen("ögrenciler2.txt","a+");
 	char satir[100],*ptr,dizi[10],dizi1[2];
 	if(fgetc(dosya)<0){
 		printf("Dosya bos\n");
 		fclose(dosya);
		 }
		 else{
	  while(!feof(dosya)){
	  fscanf(dosya,"%s\n",satir);
 	  ptr = strtok(satir,"#");
 	  strcpy(dizi,satir);
 	  yeni.no=atoi(dizi);
 	  ptr=strtok(NULL,"#");
 	  strcpy(yeni.ad,ptr);
 	  ptr=strtok(NULL,"#");
 	  strcpy(yeni.soyad,ptr);
 	  ptr=strtok(NULL,"#");
 	  strcpy(dizi1,ptr);
 	  yeni.durum=atoi(dizi1);
 	  if(numara==yeni.no){
 	  	yeni.durum=0;
 	  	fprintf(dosya2," %d#%s#%s#%d\n",yeni.no,yeni.ad,yeni.soyad,yeni.durum);
	   }
	   else{
	   	fprintf(dosya2," %d#%s#%s#%d\n",yeni.no,yeni.ad,yeni.soyad,yeni.durum);
	   }
 }
             fclose(dosya2);
			 fclose(dosya);
			 remove("ögrenciler1.txt");
           	 rename("ögrenciler2.txt","ögrenciler1.txt");
		 }
 }
 void yenile(int numara){
 	FILE *dosya,*dosya2;
 	int sayac=0;
 	dosya=fopen("ögrenciler1.txt","a+");
 	dosya2=fopen("ögrenciler2.txt","a+");
 	char satir[100],*ptr,dizi[10],dizi1[2];
 	if(fgetc(dosya)<0){
 		printf("Dosya bos\n");
 		fclose(dosya);
		 }
		 else{
	  while(!feof(dosya)){
	  fscanf(dosya,"%s\n",satir);
 	  ptr = strtok(satir,"#");
 	  strcpy(dizi,satir);
 	  yeni.no=atoi(dizi);
 	  ptr=strtok(NULL,"#");
 	  strcpy(yeni.ad,ptr);
 	  ptr=strtok(NULL,"#");
 	  strcpy(yeni.soyad,ptr);
 	  ptr=strtok(NULL,"#");
 	  strcpy(dizi1,ptr);
 	  yeni.durum=atoi(dizi1);
 	  if(numara==yeni.no){
 	  	char secim;
 	  	printf("Numara=%d\nIsim=%s\nSoyisim=%s\n",yeni.no,yeni.ad,yeni.soyad);
 	  	strcpy(gecici.ad,yeni.ad);
 	    strcpy(gecici.soyad,yeni.soyad);
 	    gecici.no=yeni.no;
 	    gecici.durum=yeni.durum;
 	  	printf("güncellemek istediginize eminmisiniz? (E),(e))");
 	  	scanf(" %c",&secim);
 	  	if(secim=='E'||secim=='e'){
 	  	printf("Yeni Adinizi giriniz...\n"); fflush(stdin);gets(bilgi.ad);
 	  	strlwr(bilgi.ad);
 	    printf("Yeni Soyadinizi giriniz...\n"); fflush(stdin);gets(bilgi.soyad);
 	    strlwr(bilgi.soyad);
 	    printf("Yeni Numaranýzý giriniz...\n"); scanf("%d",&bilgi.no);
 	    bilgi.durum=1;
 	  		sayac++;
		   }
	   }
	   else{
	   	fprintf(dosya2," %d#%s#%s#%d\n",yeni.no,yeni.ad,yeni.soyad,yeni.durum);
	   }
	  
 }       if(sayac==0){
 			 printf("Boyle Bir kayit Yoktur");
 	         fclose(dosya2);
			 fclose(dosya);
			 remove("ögrenciler1.txt");
           	 rename("ögrenciler2.txt","ögrenciler1.txt");
                     }
                     else{
                     	fclose(dosya2);
			 			fclose(dosya);
						remove("ögrenciler1.txt");
           	 			rename("ögrenciler2.txt","ögrenciler1.txt");
           	 			if(ekle(bilgi)==-1){
           	 				ekle(gecici);
							}
					 }
		 }
 }
 void arama(){
	FILE *dosya;
 	char satir[100],*ptr,dizi[10],dizi1[2],isim1[30],arama[30];
 	int sayac=0;
 	printf("Aranacak Karekterleri Giriniz");
 	scanf("%s",&arama);
 	strlwr(arama);
 	dosya=fopen("ögrenciler1.txt","a+");
 	if(fgetc(dosya)<0){
 		printf("Dosya bos\n");
 		fclose(dosya);
		 }
		 else{
	  while(!feof(dosya)){
	  fscanf(dosya,"%s\n",satir);
 	  ptr = strtok(satir,"#");
 	  strcpy(dizi,satir);
 	  yeni.no=atoi(dizi);
 	  ptr=strtok(NULL,"#");
 	  strcpy(yeni.ad,ptr);
 	  ptr=strtok(NULL,"#");
 	  strcpy(yeni.soyad,ptr);
 	  ptr=strtok(NULL,"#");
 	  strcpy(dizi1,ptr);
 	  yeni.durum=atoi(dizi1);
 	  strcpy(isim1,yeni.ad);
 	  strcat(isim1,yeni.soyad);
 	  if(strstr(isim1,arama)>0){
 	  	printf("Numara=%d\nIsim=%s\nSoyisim=%s\n",yeni.no,yeni.ad,yeni.soyad);
 	  	sayac++;
	   }
	   
}
if(sayac==0){
	printf("Aranan eleman bulunamadi\n");
}
	fclose(dosya);
}
}
 int main() {

    while (true) {
        menu();
    }

    return 0;
}
void menu() {
    int secim,sil_num;
    printf("************************\n"); 
    printf("**********MENU********** \n");
    printf("************************\n"); 
    printf("1-)Kayit Ekleme\n");
    printf("2-)Kayit Gösterme\n");
	printf("3-)Kayit Silme\n");
    printf("4-)Kayit Guncelleme\n");
    printf("5-)Kayit Arama\n");
    printf("0-)Cikis\n");
    printf("Secim Giriniz: ");
    scanf("%d", &secim);

    switch (secim) {
        case 0:
            exit(1);
            break;
        case 1: 
		printf("Adinizi giriniz...\n"); fflush(stdin);gets(bilgi.ad);
		strlwr(bilgi.ad);
 	    printf("Soyadinizi giriniz...\n"); fflush(stdin);gets(bilgi.soyad);
 	    strlwr(bilgi.soyad);
 	    printf("Numaranizi giriniz...\n"); scanf("%d",&bilgi.no);
 	    bilgi.durum=1;
	    ekle(bilgi);
            break;
        case 2: goster();
            break;
        case 3: printf("Silinecek Numarayi Giriniz\n");
		scanf("%d",&sil_num);
		sil(sil_num);
            break;
        case 4:
		printf("Güncellencek Numarayi Giriniz\n");
		scanf("%d",&sil_num);
		yenile(sil_num);
            break;
        case 5: arama();
            break;
        default:
            printf("Yanlis secim!!!\n");

    }
}

# Membuat-Virtual-Machine-IDCloudHost

__IDCloudHost__ merupakan provider lokal pertama yang menyediakan layanan cloud VPS dengan biaya berdasarkan pemakaian (Pay as you go), dimana biaya pemakaian dihitung per jam, tidak seperti VPS klasik biasa yang biayanya dihitung per bulan.

1. Silahkan login terlebih dahulu >> https://console.idcloudhost.com/

2. Setelah login, silahkan klik __Compute__ atau __Virtual Mechine__ -> Pilih Sistem Operasi -> Tentukan Spek 

   ![Screenshot from 2022-09-06 17-16-45](https://user-images.githubusercontent.com/40049149/188613957-e8a9f529-a7e7-4a8d-a722-c9f063c7fc24.png)

3. Kemudian _Virtual Mechine__ -> __Pilih Sistem Operasi__

   ![Screenshot from 2022-09-06 17-21-57](https://user-images.githubusercontent.com/40049149/188612318-7e1cb90f-8d41-4574-88dc-bf8eaf8db76b.png)

4. Tentukan Spesifikasi kemudian masukan username dan password serta masukan nama resourcenya. Untuk kolom SSH sendiri apabila sudah memahami SSH lebih jauh bisa diisi, tetapi dikosongkan juga tidak apa-apa.

   ![Screenshot from 2022-09-06 17-30-33](https://user-images.githubusercontent.com/40049149/188613437-b345c6dd-b55c-4bec-bd9a-8c85d4f95bd9.png)

5. Setelah selesai, maka akan tampil seperti dibawah ini.

   ![Screenshot from 2022-09-06 17-38-16](https://user-images.githubusercontent.com/40049149/188620762-a9438522-41da-4717-8328-2f24856f320f.png)


### Deploy Aplikasi

1. Ambil aplikasi yang ingin di deply dengan git clone

       git clone https://github.com/dumbwaysdev/dumbflix-frontend
       
   ![image](https://user-images.githubusercontent.com/40049149/188661659-d49fe5d7-8c63-4068-a0d4-cfe4bda4e5af.png)

2. Install NVM untuk menjalankan nodejs

       wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash

   ![image](https://user-images.githubusercontent.com/40049149/188662726-848e8706-d8ba-45b3-aebb-ed40417ee9cc.png)  

       exec bash
       nvm i 16
       
   ![image](https://user-images.githubusercontent.com/40049149/188664811-dab122f2-97b5-4254-a57d-ee05a1d604f1.png)

3. Install PM2

       npm install -g pm2

   ![image](https://user-images.githubusercontent.com/40049149/188670880-3c0149b9-6e3a-4ee7-b30f-48d8ebfdfe33.png)

4. Install NPM di directori aplikasi

       cd dumbflix-frontend
       npm install

   ![Screenshot from 2022-09-06 21-49-36](https://user-images.githubusercontent.com/40049149/188666961-bbb4edea-fd8b-406f-b199-48590e416f32.png)


























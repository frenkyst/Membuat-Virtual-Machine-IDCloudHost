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


## Deploy Aplikasi

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

5. Inisialisasi PM2

       pm2 init simple

   ![image](https://user-images.githubusercontent.com/40049149/188674233-0b61bdc1-eaf5-4968-bedc-c017c7a68f91.png)

6. Edit file ecosystem.config.js dan edit seperti gambar di bawah

       nano ecosystem.config.js

   ![image](https://user-images.githubusercontent.com/40049149/188674064-ef002382-33d5-449a-9832-267737950ceb.png)

7. Sekarang coba kita jalankan

       pm2 start ecosystem.config.js

   ![image](https://user-images.githubusercontent.com/40049149/188675021-07516296-6a0a-41f3-b38b-17e4342807d6.png)

8. Jika sudah sekarang coba buka web browser kalian setelah itu coba akses __ip kalian:3000__

   ![image](https://user-images.githubusercontent.com/40049149/188679859-635423c0-74bf-4b7d-9dcd-de6baf588263.png)


## Reverse Proxy dan Setup Domain Cloudflare

1. Install nginx di server

       sudo apt install nginx

   ![image](https://user-images.githubusercontent.com/40049149/188860497-cf3440e1-7568-4a2a-aaa5-c323fdc604af.png)

2. Buat folder configurasi di directory nginx dan juga buat file configurasi juga

       cd /etc/nginx/
       sudo mkdir config
       cd config
       sudo nano reverse-proxy.conf

   ![image](https://user-images.githubusercontent.com/40049149/188862055-a061e149-37bf-479a-af85-d7c3515c48db.png)

3. Masukan configurasi berikut 

         server { 
            server_name frenky.studentdumbways.my.id; 
    
            location / { 
                     proxy_pass http://103.186.1.127:3000;
            }
         }

   .

         INFO
         pastikan port 3000 di ganti sesuai aplikasi yang digunakan dan sesuaikan server_name dan IP addres kalian.

4. Untuk domainya dari cloudflare, kita login dulu ke cloudflare

   ![image](https://user-images.githubusercontent.com/40049149/188867978-1d496ca4-b458-4e2f-a78c-da24998b791e.png)

5. Pilih DNS pada side menu dan klik Add record

   ![image](https://user-images.githubusercontent.com/40049149/188868291-404818b6-3f99-45a9-9c3e-9405061dcbe4.png)

6. Masukan Name dan IP kemudian jangan lupa Save

   ![image](https://user-images.githubusercontent.com/40049149/188868720-436a1a0a-f8c9-45bc-8ed7-97592347e948.png)

7. Lanjut setelah Step 3 kita simpan config yang kita bikin

       cd ..
       sudo nano nginx.conf
       
       jangan lupa Save

   ![image](https://user-images.githubusercontent.com/40049149/188871765-7869e838-d5f8-442a-936d-f2c20524befe.png)






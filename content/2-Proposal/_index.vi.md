---
title: "Báº£n Ä‘á» xuáº¥t"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

Táº¡i pháº§n nÃ y, báº¡n cáº§n tÃ³m táº¯t cÃ¡c ná»™i dung trong workshop mÃ  báº¡n **dá»± tÃ­nh** sáº½ lÃ m.

# IoT Weather Platform for Lab Research  
## Giáº£i phÃ¡p AWS Serverless há»£p nháº¥t cho giÃ¡m sÃ¡t thá»i tiáº¿t thá»i gian thá»±c  

### 1. TÃ³m táº¯t Ä‘iá»u hÃ nh  
IoT Weather Platform Ä‘Æ°á»£c thiáº¿t káº¿ dÃ nh cho nhÃ³m *ITea Lab* táº¡i TP. Há»“ ChÃ­ Minh nháº±m nÃ¢ng cao kháº£ nÄƒng thu tháº­p vÃ  phÃ¢n tÃ­ch dá»¯ liá»‡u thá»i tiáº¿t. Ná»n táº£ng há»— trá»£ tá»‘i Ä‘a 5 tráº¡m thá»i tiáº¿t, cÃ³ kháº£ nÄƒng má»Ÿ rá»™ng lÃªn 10â€“15 tráº¡m, sá»­ dá»¥ng thiáº¿t bá»‹ biÃªn Raspberry Pi káº¿t há»£p cáº£m biáº¿n ESP32 Ä‘á»ƒ truyá»n dá»¯ liá»‡u qua MQTT. Ná»n táº£ng táº­n dá»¥ng cÃ¡c dá»‹ch vá»¥ AWS Serverless Ä‘á»ƒ cung cáº¥p giÃ¡m sÃ¡t thá»i gian thá»±c, phÃ¢n tÃ­ch dá»± Ä‘oÃ¡n vÃ  tiáº¿t kiá»‡m chi phÃ­, vá»›i quyá»n truy cáº­p giá»›i háº¡n cho 5 thÃ nh viÃªn phÃ²ng lab thÃ´ng qua Amazon Cognito.  

### 2. TuyÃªn bá»‘ váº¥n Ä‘á»  
*Váº¥n Ä‘á» hiá»‡n táº¡i*  
CÃ¡c tráº¡m thá»i tiáº¿t hiá»‡n táº¡i yÃªu cáº§u thu tháº­p dá»¯ liá»‡u thá»§ cÃ´ng, khÃ³ quáº£n lÃ½ khi cÃ³ nhiá»u tráº¡m. KhÃ´ng cÃ³ há»‡ thá»‘ng táº­p trung cho dá»¯ liá»‡u hoáº·c phÃ¢n tÃ­ch thá»i gian thá»±c, vÃ  cÃ¡c ná»n táº£ng bÃªn thá»© ba thÆ°á»ng tá»‘n kÃ©m vÃ  quÃ¡ phá»©c táº¡p.  

*Giáº£i phÃ¡p*  
Ná»n táº£ng sá»­ dá»¥ng AWS IoT Core Ä‘á»ƒ tiáº¿p nháº­n dá»¯ liá»‡u MQTT, AWS Lambda vÃ  API Gateway Ä‘á»ƒ xá»­ lÃ½, Amazon S3 Ä‘á»ƒ lÆ°u trá»¯ (bao gá»“m data lake), vÃ  AWS Glue Crawlers cÃ¹ng cÃ¡c tÃ¡c vá»¥ ETL Ä‘á»ƒ trÃ­ch xuáº¥t, chuyá»ƒn Ä‘á»•i, táº£i dá»¯ liá»‡u tá»« S3 data lake sang má»™t S3 bucket khÃ¡c Ä‘á»ƒ phÃ¢n tÃ­ch. AWS Amplify vá»›i Next.js cung cáº¥p giao diá»‡n web, vÃ  Amazon Cognito Ä‘áº£m báº£o quyá»n truy cáº­p an toÃ n. TÆ°Æ¡ng tá»± nhÆ° Thingsboard vÃ  CoreIoT, ngÆ°á»i dÃ¹ng cÃ³ thá»ƒ Ä‘Äƒng kÃ½ thiáº¿t bá»‹ má»›i vÃ  quáº£n lÃ½ káº¿t ná»‘i, nhÆ°ng ná»n táº£ng nÃ y hoáº¡t Ä‘á»™ng á»Ÿ quy mÃ´ nhá» hÆ¡n vÃ  phá»¥c vá»¥ má»¥c Ä‘Ã­ch sá»­ dá»¥ng ná»™i bá»™. CÃ¡c tÃ­nh nÄƒng chÃ­nh bao gá»“m báº£ng Ä‘iá»u khiá»ƒn thá»i gian thá»±c, phÃ¢n tÃ­ch xu hÆ°á»›ng vÃ  chi phÃ­ váº­n hÃ nh tháº¥p.  

*Lá»£i Ã­ch vÃ  hoÃ n vá»‘n Ä‘áº§u tÆ° (ROI)*  
Giáº£i phÃ¡p táº¡o ná»n táº£ng cÆ¡ báº£n Ä‘á»ƒ cÃ¡c thÃ nh viÃªn phÃ²ng lab phÃ¡t triá»ƒn má»™t ná»n táº£ng IoT lá»›n hÆ¡n, Ä‘á»“ng thá»i cung cáº¥p nguá»“n dá»¯ liá»‡u cho nhá»¯ng ngÆ°á»i nghiÃªn cá»©u AI phá»¥c vá»¥ huáº¥n luyá»‡n mÃ´ hÃ¬nh hoáº·c phÃ¢n tÃ­ch. Ná»n táº£ng giáº£m bá»›t bÃ¡o cÃ¡o thá»§ cÃ´ng cho tá»«ng tráº¡m thÃ´ng qua há»‡ thá»‘ng táº­p trung, Ä‘Æ¡n giáº£n hÃ³a quáº£n lÃ½ vÃ  báº£o trÃ¬, Ä‘á»“ng thá»i cáº£i thiá»‡n Ä‘á»™ tin cáº­y dá»¯ liá»‡u. Chi phÃ­ hÃ ng thÃ¡ng Æ°á»›c tÃ­nh 0,66 USD (theo AWS Pricing Calculator), tá»•ng cá»™ng 7,92 USD cho 12 thÃ¡ng. Táº¥t cáº£ thiáº¿t bá»‹ IoT Ä‘Ã£ Ä‘Æ°á»£c trang bá»‹ tá»« há»‡ thá»‘ng tráº¡m thá»i tiáº¿t hiá»‡n táº¡i, khÃ´ng phÃ¡t sinh chi phÃ­ phÃ¡t triá»ƒn thÃªm. Thá»i gian hoÃ n vá»‘n 6â€“12 thÃ¡ng nhá» tiáº¿t kiá»‡m Ä‘Ã¡ng ká»ƒ thá»i gian thao tÃ¡c thá»§ cÃ´ng.  

### 3. Kiáº¿n trÃºc giáº£i phÃ¡p  
Ná»n táº£ng Ã¡p dá»¥ng kiáº¿n trÃºc AWS Serverless Ä‘á»ƒ quáº£n lÃ½ dá»¯ liá»‡u tá»« 5 tráº¡m dá»±a trÃªn Raspberry Pi, cÃ³ thá»ƒ má»Ÿ rá»™ng lÃªn 15 tráº¡m. Dá»¯ liá»‡u Ä‘Æ°á»£c tiáº¿p nháº­n qua AWS IoT Core, lÆ°u trá»¯ trong S3 data lake vÃ  xá»­ lÃ½ bá»Ÿi AWS Glue Crawlers vÃ  ETL jobs Ä‘á»ƒ chuyá»ƒn Ä‘á»•i vÃ  táº£i vÃ o má»™t S3 bucket khÃ¡c cho má»¥c Ä‘Ã­ch phÃ¢n tÃ­ch. Lambda vÃ  API Gateway xá»­ lÃ½ bá»• sung, trong khi Amplify vá»›i Next.js cung cáº¥p báº£ng Ä‘iá»u khiá»ƒn Ä‘Æ°á»£c báº£o máº­t bá»Ÿi Cognito.  

![Smart Healthcare Appointment System Architecture](/images/2-Proposal/so-do.jpg)

*Dá»‹ch vá»¥ AWS sá»­ dá»¥ng*  
- *AWS IoT Core*: Tiáº¿p nháº­n dá»¯ liá»‡u MQTT tá»« 5 tráº¡m, má»Ÿ rá»™ng lÃªn 15.  
- *AWS Lambda*: Xá»­ lÃ½ dá»¯ liá»‡u vÃ  kÃ­ch hoáº¡t Glue jobs (2 hÃ m).  
- *Amazon API Gateway*: Giao tiáº¿p vá»›i á»©ng dá»¥ng web.  
- *Amazon S3*: LÆ°u trá»¯ dá»¯ liá»‡u thÃ´ (data lake) vÃ  dá»¯ liá»‡u Ä‘Ã£ xá»­ lÃ½ (2 bucket).  
- *AWS Glue*: Crawlers láº­p chá»‰ má»¥c dá»¯ liá»‡u, ETL jobs chuyá»ƒn Ä‘á»•i vÃ  táº£i dá»¯ liá»‡u.  
- *AWS Amplify*: LÆ°u trá»¯ giao diá»‡n web Next.js.  
- *Amazon Cognito*: Quáº£n lÃ½ quyá»n truy cáº­p cho ngÆ°á»i dÃ¹ng phÃ²ng lab.  

*Thiáº¿t káº¿ thÃ nh pháº§n*  
- *Thiáº¿t bá»‹ biÃªn*: Raspberry Pi thu tháº­p vÃ  lá»c dá»¯ liá»‡u cáº£m biáº¿n, gá»­i tá»›i IoT Core.  
- *Tiáº¿p nháº­n dá»¯ liá»‡u*: AWS IoT Core nháº­n tin nháº¯n MQTT tá»« thiáº¿t bá»‹ biÃªn.  
- *LÆ°u trá»¯ dá»¯ liá»‡u*: Dá»¯ liá»‡u thÃ´ lÆ°u trong S3 data lake; dá»¯ liá»‡u Ä‘Ã£ xá»­ lÃ½ lÆ°u á»Ÿ má»™t S3 bucket khÃ¡c.  
- *Xá»­ lÃ½ dá»¯ liá»‡u*: AWS Glue Crawlers láº­p chá»‰ má»¥c dá»¯ liá»‡u; ETL jobs chuyá»ƒn Ä‘á»•i Ä‘á»ƒ phÃ¢n tÃ­ch.  
- *Giao diá»‡n web*: AWS Amplify lÆ°u trá»¯ á»©ng dá»¥ng Next.js cho báº£ng Ä‘iá»u khiá»ƒn vÃ  phÃ¢n tÃ­ch thá»i gian thá»±c.  
- *Quáº£n lÃ½ ngÆ°á»i dÃ¹ng*: Amazon Cognito giá»›i háº¡n 5 tÃ i khoáº£n hoáº¡t Ä‘á»™ng.  

### 4. Triá»ƒn khai ká»¹ thuáº­t  
*CÃ¡c giai Ä‘oáº¡n triá»ƒn khai*  
Dá»± Ã¡n gá»“m 2 pháº§n â€” thiáº¿t láº­p tráº¡m thá»i tiáº¿t biÃªn vÃ  xÃ¢y dá»±ng ná»n táº£ng thá»i tiáº¿t â€” má»—i pháº§n tráº£i qua 4 giai Ä‘oáº¡n:  
1. *NghiÃªn cá»©u vÃ  váº½ kiáº¿n trÃºc*: NghiÃªn cá»©u Raspberry Pi vá»›i cáº£m biáº¿n ESP32 vÃ  thiáº¿t káº¿ kiáº¿n trÃºc AWS Serverless (1 thÃ¡ng trÆ°á»›c ká»³ thá»±c táº­p).  
2. *TÃ­nh toÃ¡n chi phÃ­ vÃ  kiá»ƒm tra tÃ­nh kháº£ thi*: Sá»­ dá»¥ng AWS Pricing Calculator Ä‘á»ƒ Æ°á»›c tÃ­nh vÃ  Ä‘iá»u chá»‰nh (ThÃ¡ng 1).  
3. *Äiá»u chá»‰nh kiáº¿n trÃºc Ä‘á»ƒ tá»‘i Æ°u chi phÃ­/giáº£i phÃ¡p*: Tinh chá»‰nh (vÃ­ dá»¥ tá»‘i Æ°u Lambda vá»›i Next.js) Ä‘á»ƒ Ä‘áº£m báº£o hiá»‡u quáº£ (ThÃ¡ng 2).  
4. *PhÃ¡t triá»ƒn, kiá»ƒm thá»­, triá»ƒn khai*: Láº­p trÃ¬nh Raspberry Pi, AWS services vá»›i CDK/SDK vÃ  á»©ng dá»¥ng Next.js, sau Ä‘Ã³ kiá»ƒm thá»­ vÃ  Ä‘Æ°a vÃ o váº­n hÃ nh (ThÃ¡ng 2â€“3).  

*YÃªu cáº§u ká»¹ thuáº­t*  
- *Tráº¡m thá»i tiáº¿t biÃªn*: Cáº£m biáº¿n (nhiá»‡t Ä‘á»™, Ä‘á»™ áº©m, lÆ°á»£ng mÆ°a, tá»‘c Ä‘á»™ giÃ³), vi Ä‘iá»u khiá»ƒn ESP32, Raspberry Pi lÃ m thiáº¿t bá»‹ biÃªn. Raspberry Pi cháº¡y Raspbian, sá»­ dá»¥ng Docker Ä‘á»ƒ lá»c dá»¯ liá»‡u vÃ  gá»­i 1 MB/ngÃ y/tráº¡m qua MQTT qua Wi-Fi.  
- *Ná»n táº£ng thá»i tiáº¿t*: Kiáº¿n thá»©c thá»±c táº¿ vá» AWS Amplify (lÆ°u trá»¯ Next.js), Lambda (giáº£m thiá»ƒu do Next.js xá»­ lÃ½), AWS Glue (ETL), S3 (2 bucket), IoT Core (gateway vÃ  rules), vÃ  Cognito (5 ngÆ°á»i dÃ¹ng). Sá»­ dá»¥ng AWS CDK/SDK Ä‘á»ƒ láº­p trÃ¬nh (vÃ­ dá»¥ IoT Core rules tá»›i S3). Next.js giÃºp giáº£m táº£i Lambda cho á»©ng dá»¥ng web fullstack.  

### 5. Lá»™ trÃ¬nh & Má»‘c triá»ƒn khai  
- *TrÆ°á»›c thá»±c táº­p (ThÃ¡ng 0)*: 1 thÃ¡ng lÃªn káº¿ hoáº¡ch vÃ  Ä‘Ã¡nh giÃ¡ tráº¡m cÅ©.  
- *Thá»±c táº­p (ThÃ¡ng 1â€“3)*:  
    - ThÃ¡ng 1: Há»c AWS vÃ  nÃ¢ng cáº¥p pháº§n cá»©ng.  
    - ThÃ¡ng 2: Thiáº¿t káº¿ vÃ  Ä‘iá»u chá»‰nh kiáº¿n trÃºc.  
    - ThÃ¡ng 3: Triá»ƒn khai, kiá»ƒm thá»­, Ä‘Æ°a vÃ o sá»­ dá»¥ng.  
- *Sau triá»ƒn khai*: NghiÃªn cá»©u thÃªm trong vÃ²ng 1 nÄƒm.  

### 6. Æ¯á»›c tÃ­nh ngÃ¢n sÃ¡ch  
CÃ³ thá»ƒ xem chi phÃ­ trÃªn [AWS Pricing Calculator](https://calculator.aws/#/estimate?id=621f38b12a1ef026842ba2ddfe46ff936ed4ab01)  
Hoáº·c táº£i [tá»‡p Æ°á»›c tÃ­nh ngÃ¢n sÃ¡ch](../attachments/budget_estimation.pdf).  

*Chi phÃ­ háº¡ táº§ng*  
- AWS Lambda: 0,00 USD/thÃ¡ng (1.000 request, 512 MB lÆ°u trá»¯).  
- S3 Standard: 0,15 USD/thÃ¡ng (6 GB, 2.100 request, 1 GB quÃ©t).  
- Truyá»n dá»¯ liá»‡u: 0,02 USD/thÃ¡ng (1 GB vÃ o, 1 GB ra).  
- AWS Amplify: 0,35 USD/thÃ¡ng (256 MB, request 500 ms).  
- Amazon API Gateway: 0,01 USD/thÃ¡ng (2.000 request).  
- AWS Glue ETL Jobs: 0,02 USD/thÃ¡ng (2 DPU).  
- AWS Glue Crawlers: 0,07 USD/thÃ¡ng (1 crawler).  
- MQTT (IoT Core): 0,08 USD/thÃ¡ng (5 thiáº¿t bá»‹, 45.000 tin nháº¯n).  

*Tá»•ng*: 0,7 USD/thÃ¡ng, 8,40 USD/12 thÃ¡ng  
- *Pháº§n cá»©ng*: 265 USD má»™t láº§n (Raspberry Pi 5 vÃ  cáº£m biáº¿n).  

### 7. ÄÃ¡nh giÃ¡ rá»§i ro  
*Ma tráº­n rá»§i ro*  
- Máº¥t máº¡ng: áº¢nh hÆ°á»Ÿng trung bÃ¬nh, xÃ¡c suáº¥t trung bÃ¬nh.  
- Há»ng cáº£m biáº¿n: áº¢nh hÆ°á»Ÿng cao, xÃ¡c suáº¥t tháº¥p.  
- VÆ°á»£t ngÃ¢n sÃ¡ch: áº¢nh hÆ°á»Ÿng trung bÃ¬nh, xÃ¡c suáº¥t tháº¥p.  

*Chiáº¿n lÆ°á»£c giáº£m thiá»ƒu*  
- Máº¡ng: LÆ°u trá»¯ cá»¥c bá»™ trÃªn Raspberry Pi vá»›i Docker.  
- Cáº£m biáº¿n: Kiá»ƒm tra Ä‘á»‹nh ká»³, dá»± phÃ²ng linh kiá»‡n.  
- Chi phÃ­: Cáº£nh bÃ¡o ngÃ¢n sÃ¡ch AWS, tá»‘i Æ°u dá»‹ch vá»¥.  

*Káº¿ hoáº¡ch dá»± phÃ²ng*  
- Quay láº¡i thu tháº­p thá»§ cÃ´ng náº¿u AWS gáº·p sá»± cá»‘.  
- Sá»­ dá»¥ng CloudFormation Ä‘á»ƒ khÃ´i phá»¥c cáº¥u hÃ¬nh liÃªn quan Ä‘áº¿n chi phÃ­.  

### 8. Káº¿t quáº£ ká»³ vá»ng  
*Cáº£i tiáº¿n ká»¹ thuáº­t*: Dá»¯ liá»‡u vÃ  phÃ¢n tÃ­ch thá»i gian thá»±c thay tháº¿ quy trÃ¬nh thá»§ cÃ´ng. CÃ³ thá»ƒ má»Ÿ rá»™ng tá»›i 10â€“15 tráº¡m.  
*GiÃ¡ trá»‹ dÃ i háº¡n*: Ná»n táº£ng dá»¯ liá»‡u 1 nÄƒm cho nghiÃªn cá»©u AI, cÃ³ thá»ƒ tÃ¡i sá»­ dá»¥ng cho cÃ¡c dá»±Â Ã¡nÂ tÆ°Æ¡ngÂ lai.

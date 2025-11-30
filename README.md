# Fraud_Risk_Analysis
---

# 🌐 Fraud Riskinin Analizi — SQL Layihəsi

Bu layihə bank sektorunda fırıldaqçılıq əməliyyatlarını aşkar etmək və riskləri qiymətləndirmək məqsədi ilə SQL üzərində qurulmuş analitik araşdırmadır. Real bank tranzaksiyalarına uyğun məlumatlar əsasında müxtəlif SQL metodları tətbiq edilərək dərin analiz aparılmışdır.

## 📌 Layihənin Məqsədi

- Bank müştəriləri və kartları üzrə fraud risk faktorlarını təyin etmək  
- Tranzaksiyalarda davranış anomaliyalarını aşkar etmək  
- Yüksək riskli müştəri/kart seqmentlərini müəyyənləşdirmək  
- Fraud davranışından sonra reaksiyanın nə qədər kritik olduğunu göstərmək  
- Bank üçün real biznes dəyəri yaradan proaktiv qaydalar təklif etmək

---
##  İstifadə Olunan Datasetlər

1. **Customers** – Müştəri məlumatları:
   | Sütun Adı        | Tip      | İzahı                       |
   |----------------- |----------|-----------------------------|
   | customer_id      | number   | Unikal müştəri ID           |
   | first_name       | varchar  | Müştərinin adı              |
   | last_name        | varchar  | Müştərinin soyadı           |
   | date_of_birth    | date     | Doğum tarixi                |
   | city             | varchar  | Şəhər                       |
   | country          | varchar  | Ölkə                        |
   | registration_date| date     | Qeydiyyat tarixi            |

2. **Cards** – Kart məlumatları:
   | Sütun Adı       | Tip      | İzahı                            |
   |---------------- |----------|--------------------------------  |
   | card_id         | number   | Unikal kart ID                   |
   | customer_id     | number   | Müştəri ID (Customers ilə əlaqə) |
   | card_number     | varchar  | Kart nömrəsi                     |
   | card_type       | varchar  | Kart növü (Standard, Gold, və s.)|
   | credit_limit    | number   | Kredit limiti                    |
   | card_status     | varchar  | Aktiv/dormant status             |
   | issue_date      | date     | Kartın verilmə tarixi            |

3. **Transactions** – Tranzaksiya məlumatları:
   | Sütun Adı             | Tip      | İzahı                                  |
   |---------------------- |----------|----------------------------------------|
   | transaction_id        | number   | Unikal tranzaksiya ID                  |
   | card_id               | number   | Kart ID (Cards ilə əlaqə)              |
   | merchant_id           | number   | Satıcı ID (Merchants ilə əlaqə)        |
   | transaction_amount    | number   | Məbləğ                                 |
   | transaction_datetime  | datetime | Tranzaksiya vaxtı                      |
   | transaction_location  | varchar  | Tranzaksiya yeri                       |
   | transaction_status    | varchar  | Status (approved, declined və s.)      |
   | is_fraud              | boolean  | Fraud flag (0 = normal, 1 = fraud)     |

4. **Merchants** – Satıcı məlumatları:
   | Sütun Adı         | Tip       | İzahı                         |
   |------------------ |----------|--------------------------------|
   | merchant_id       | number   | Unikal satıcı ID               |
   | merchant_name     | varchar  | Satıcının adı                  |
   | merchant_category | varchar  | Satıcının kateqoriyası         |
   | merchant_country  | varchar  | Satıcının ölkəsi               |


## 📊 Aparılan Analizlər

## 1. Müştəri və kart seqmentasiyası
Müştərilər əməkdaşlıq müddətinə görə, kartlar isə kredit limitinə görə seqmentləşdirilib.
Riskli seqmentlər müəyyən edilib.

## 2. Yatan (dormant) kartların analizi
Fraud əməliyyatlarından əvvəl kartın nə qədər müddət istifadə edilmədiyi ölçülüb.

## 3. Xərcləmə sürəti anomaliyası
Window funksiyaları ilə 24 saatlıq rolling sum və son 3 əməliyyatın ortası hesablanıb.

## 4. “İlk Hücum” (First Attack) analizi
İlk frauddan sonra 1 saat ərzində edilən əməliyyatların sayı və məbləği ölçülüb.

## 5. Fraud zəncirinin xəritələnməsi
1 saatda bir satıcının neçə fərqli oğurlanmış kartdan əməliyyat qəbul etdiyi öyrənilib.
 
## 6. Proaktiv qayda simulyasiyası
"Ağıllı limit" qaydası tətbiq edilərək True Positive / False Positive təsirləri ölçülüb.

## 📝 Əsas Nəticələr

- Ən riskli seqment: Yeni müştərilərin Standard kartları  
- Yatan kartlar fraud ehtimalını artırır  
- Ani böyük məbləğ artımları ciddi risk siqnalıdır  
- İlk frauddan sonra hücumlar qısa vaxtda maksimum zərər vurmağa yönəlib  
- Smart limit rule — 150 fraud-u düzgün aşkar etsə də, çoxlu yanlış pozitivlər yaradır  

##  Layihənin Dəyəri

- Risk komandasına fraud davranışlarını əvvəlcədən görmək imkanı verir  
- Tətbiq edilə bilən biznes qaydaları yaradır  
- Real vaxt bazasında davranış modellərinin avtomatlaşdırılmasına zəmin yaradır  
- Data analitikası, SQL və risk analizi bacarıqlarını nümayiş etdirir  

## 👩‍💻 Layihə müəllifi  

**Məleykəxanım Rəfiyeva**  

[![GitHub Repository](https://img.shields.io/badge/GitHub-Repository-black?style=for-the-badge&logo=github)](https://github.com/Maleykakhanim/Fraud_Risk_Analysis)

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Profile-blue?style=for-the-badge&logo=linkedin)](https://www.linkedin.com/in/maleykakhanim-rafiyeva/)


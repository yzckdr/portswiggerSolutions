# 📘 API (Application Programming Interface) Nedir?

## 🔹 Tanım

**API**, yazılım uygulamalarının birbirleriyle konuşmasını sağlayan bir araçtır.

> 🧠 Düşün ki bir restorandasın. Menüyü inceliyorsun, siparişi garsona veriyorsun.  
> Garson mutfağa gidiyor ve senin siparişini getiriyor.

🍽️ **İşte burada API = garson** gibidir.  
Senin uygulaman, arka plandaki sistemle **API üzerinden iletişime geçer** ve istediğin veriyi getirir.

---

## 🔹 Gerçek Hayattan Örnek

Bir hava durumu uygulaması yaptığımızı düşünelim. Kullanıcı "İstanbul" der ve senin uygulaman şu isteği yapar:

🎯 Örnekle Anlayalım:
Senaryo:
Bir hava durumu uygulaması yapıyorsun. Kullanıcının yaşadığı şehirdeki sıcaklığı göstermek istiyorsun.

Nasıl Olur?
Kullanıcı "İstanbul" der.

Senin uygulaman bir hava durumu API'sine şu isteği gönderir:
GET https://api.weather.com/weather?city=Istanbul

API şu cevabı döner:

<pre><code>```json { "city": "Istanbul", "temperature": 29, "condition": "sunny" } ```</code></pre>



---

## 🧱 API Türleri

| Tür         | Açıklama                                                                 |
|-------------|--------------------------------------------------------------------------|
| REST API    | En yaygın API türüdür. HTTP istekleriyle çalışır. Basit ve hızlıdır.     |
| SOAP API    | Daha katı kurallara sahip, XML tabanlı eski bir yapıdır.                 |
| GraphQL API | İstediğin kadar veri alanını tek seferde çekmeni sağlar. Facebook geliştirmiştir. |

---

## 🔐 API Nerelerde Kullanılır?

| Kullanım Alanı            | Açıklama                                             |
|---------------------------|------------------------------------------------------|
| Hava durumu uygulamaları  | Gerçek zamanlı hava bilgisi almak için               |
| Bankacılık sistemleri     | Bakiye sorgulama, para transferi                     |
| Harita servisleri         | Yol tarifi veya konum verisi almak                   |
| Sosyal medya uygulamaları | Paylaşım yapmak, kullanıcı verisi almak             |
| E-ticaret sistemleri      | Ürün listesi, sipariş oluşturma işlemleri           |

---

## 🧪 API Testine Başlarken

API ile çalışmaya başlamadan önce aşağıdaki adımları izlemelisin:

### ✅ 1. Uç Noktaları (Endpoints) Belirle

Bir API’nin sunduğu veri yollarıdır. Örnek:


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

## 🔍 API Dokümantasyonunu Keşfetmek (Discovering API Documentation)

Bir API’nin dokümantasyonu açıkça yayınlanmamış olabilir. Ancak bu, hiçbir şekilde erişemeyeceğin anlamına gelmez. Aşağıdaki yöntemlerle API dokümantasyonunu keşfetme şansın vardır:

---

### 🧭 1. Uygulamaları Gözlemleyerek Dokümantasyonu Bulmak

API'ler genellikle bir web veya mobil uygulama tarafından zaten kullanılıyordur. Bu durumda:

- Uygulamayı aç
- Tarayıcı geliştirici araçlarını (F12) kullan
- `Network` sekmesinde istekleri izle

Bu isteklerin içinde `/api`, `/swagger`, `/openapi.json` gibi yollar olabilir. Bu yollar dokümantasyon dosyalarına işaret edebilir.

---

### 🛠️ 2. Burp Suite ile API Tarama

Burp Suite, hem manuel hem otomatik olarak API endpoint’lerini ve dokümantasyon yollarını keşfetmek için kullanılabilir.

#### İki yöntem:
- **Burp Scanner**: Uygulamayı otomatik olarak tarar ve API yollarını keşfeder.
- **Burp Tarayıcısı (Manual)**: Uygulamada gezinirken yapılan tüm HTTP isteklerini kaydeder.

Bu yöntemle gizlenmiş dokümantasyon yolları ortaya çıkabilir.

---

### 📄 3. Yaygın Dokümantasyon Yollarını Kontrol Et

Aşağıdaki yollar API dokümantasyonuna işaret edebilir. Bunları manuel olarak veya Burp/Dirsearch gibi araçlarla kontrol edebilirsin:

/api
/swagger/index.html
/swagger-ui.html
/openapi.json
/api-docs
/v2/api-docs


---

### 📎 4. Kaynak Endpoint’ten Base Path’i Tespit Et

Bir kaynak endpoint’i keşfettiysen örneğin:

/api/swagger/v1/users/123


Bunun kök yollarını da incelemelisin:

- `/api/swagger/v1`
- `/api/swagger`
- `/api`

Bu yollar genellikle dokümantasyon ve şema dosyalarını barındırır.

---

### 🧪 5. Yaygın Path Listeleriyle Brute Force Denemesi

Eğer manuel taramayla sonuç alamadıysan, yaygın endpoint yollarından oluşan bir listeyle brute force (deneme-yanılma) taraması yapabilirsin.

Kullanılabilecek araçlar:

- **Burp Intruder**
- **Dirsearch**
- **FFUF**
- **Gobuster**

---

## 🧠 Özet

| Adım | Açıklama |
|------|----------|
| 🔍 Uygulamayı analiz et | Geliştirici araçları veya Burp ile gözlem |
| 🛠️ Burp Scanner ile tarama yap | Otomatik endpoint keşfi |
| 📂 Yaygın yolları dene | `/swagger`, `/api-docs`, `/openapi.json` gibi |
| 📎 Kaynak path'ten base path çıkarımı yap | `/api/users/123` → `/api/` |
| 🧪 Brute force testleri | Dirsearch, FFUF, Gobuster gibi araçlarla |

---

> 🔐 Bu yöntemler, dokümantasyonu yayında olmayan veya özel sistemlerde çalışan API’leri analiz ederken son derece faydalıdır.  
> Özellikle güvenlik araştırmaları, penetration testleri veya tersine mühendislik çalışmalarında sıkça kullanılır.



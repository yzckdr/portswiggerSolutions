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

## 🤖 Makine Tarafından Okunabilir API Dokümantasyonunu Kullanmak

Modern API sistemleri genellikle sadece insanlar için değil, **makineler tarafından da anlaşılabilecek şekilde belgelenir**. Bu tür dokümantasyonlar, yazılım araçları tarafından otomatik olarak analiz edilebilir, test edilebilir ve API istemcileri (client'lar) oluşturulabilir.

---

### 📄 1. Makine Tarafından Okunabilir Dokümantasyon Türleri

| Format | Açıklama |
|--------|----------|
| **OpenAPI (Swagger)** | En yaygın formattır. JSON veya YAML olarak yazılır. Tüm endpoint'leri, parametreleri, veri türlerini içerir. |
| **WSDL (SOAP)**       | XML tabanlı eski bir dokümantasyon biçimi. SOAP servislerinde yaygındır. |
| **RAML / API Blueprint** | Alternatif şema tanım dilleridir. Genelde REST API’ler için kullanılır. |

Bu belgeler genellikle şu yollar üzerinden erişilebilir:

/openapi.json
/swagger.json
/swagger.yaml
/api-docs


---

### 🛠️ 2. Bu Belgeleri İşlemek İçin Kullanabileceğin Araçlar

#### ✅ Burp Suite + Burp Scanner

- Burp Scanner, OpenAPI veya Swagger dosyalarını analiz ederek endpoint'leri çıkartabilir.
- Bu endpoint’lere yönelik otomatik güvenlik testleri çalıştırabilir.
- Swagger/OpenAPI JSON dosyasını verdiğinde tüm rotaları tarayıp açıkları tespit etmeye çalışır.

#### ✅ Burp BApp Store: OpenAPI Parser

- Burp Suite içine **“OpenAPI Parser”** eklentisini kur.
- Bu eklenti `.json` veya `.yaml` uzantılı Swagger/OpenAPI belgelerini ayrıştırır.
- Sonuç olarak: API endpoint’leri Burp Suite’e otomatik olarak eklenir ve taranabilir hale gelir.

---

### 🧪 3. Test İçin Kullanılabilecek Uygulamalar

| Araç     | Açıklama |
|----------|----------|
| **Postman** | Swagger veya OpenAPI dosyasını içe aktararak API çağrıları yapmanı sağlar. |
| **SoapUI**  | Özellikle SOAP servisleri için dokümantasyon ve test amaçlı kullanılır. |
| **Insomnia**| Postman alternatifi, modern ve hafif bir API istemcisi. |

Bu araçlar sayesinde:

- Dokümantasyon içindeki endpoint'leri otomatik olarak çekebilir
- Her endpoint için test isteği oluşturabilir
- JSON body, headers, authentication gibi alanları kolayca yönetebilirsin

---

### 🧠 Neden Önemlidir?

Makine tarafından okunabilir dokümantasyonun avantajları:

- ⚙️ **Otomatik test ve denetim yapılabilir**
- 🚀 **Kod üretimi yapılabilir** (örneğin OpenAPI → Python client)
- 📋 **API dökümantasyonu elle yazmak zorunda kalmazsın**
- 🔐 **Güvenlik açıklarını hızlıca analiz edebilirsin**

---

## 📘 Örnek Senaryo

Bir web sunucusunda aşağıdaki path’i buldun:

https://target.com/openapi.json


Yapabileceklerin:

1. Bu dosyayı indir
2. Postman’e içe aktar → Test et
3. Burp Suite → OpenAPI Parser ile yükle → Endpoint’leri çıkar
4. Burp Scanner ile tarama başlat → Güvenlik açıklarını tespit et

---

> Makine tarafından okunabilir dokümantasyon, bir API'yi **hızlı, doğru ve etkili** şekilde analiz etmenin en güçlü yollarından biridir.

## 🚩 API Uç Noktalarını Belirleme ve HTTP Yöntemleriyle Etkileşim

---

### 🔎 Uç Noktaları Belirleme

Uygulamalarda API endpoint’lerini bulmak için:

- Burp Tarayıcı’yı kullanarak uygulamayı gez
- `/api/`, `.json`, `.js` gibi kalıpları URL’lerde ara
- JavaScript dosyalarını incele (örnek: `main.js`)
- Burp → **JS Link Finder** eklentisi ile daha fazla yol bul
- Bazı endpoint’ler sadece uygulama içinde tetiklenir; manuel gezinme önemlidir

---

### 🔁 API Uç Noktalarıyla Etkileşim Kurma

- **Burp Repeater** → Tekil istekleri test etmek için kullanılır
- **Burp Intruder** → Otomatik olarak farklı parametre/metot denemeleri yapar

Aşağıdaki durumları incele:

- Yanıt mesajları ve hata açıklamaları
- Desteklenen HTTP yöntemleri (GET, POST, PATCH, DELETE, OPTIONS...)
- Desteklenen içerik türleri (`application/json`, `application/xml`, vs)

---

### 🔧 HTTP Yöntemleri

| Metot     | Açıklama                                       |
|-----------|------------------------------------------------|
| GET       | Bir kaynaktan veri alır                        |
| POST      | Yeni bir kaynak oluşturur                      |
| PATCH     | Kaynağın bazı alanlarını günceller             |
| PUT       | Kaynağı tamamen günceller                      |
| DELETE    | Kaynağı siler                                  |
| OPTIONS   | Desteklenen HTTP metotlarını listeler          |

Örnek: `/api/tasks`

GET     /api/tasks        → Görevleri listeler
POST    /api/tasks        → Yeni görev oluşturur
DELETE  /api/tasks/1      → ID=1 olan görevi siler
OPTIONS /api/tasks        → Kullanılabilir metotları gösterir

## 🎯 Intruder ile Gizli API Uç Noktalarını Bulmak

Uygulama üzerinde bazı temel endpoint’leri (örneğin `/api/user/update`) keşfettikten sonra, Burp Suite’in **Intruder** modülü ile görünmeyen (gizli) endpoint’leri ortaya çıkarabilirsin.

---

### 🔍 Amaç

Mevcut bir endpoint şu şekilde olabilir:

PUT /api/user/update


Bu, sistemde şu endpoint’lerin de bulunabileceğini düşündürebilir:


Bu, sistemde şu endpoint’lerin de bulunabileceğini düşündürebilir:

/api/user/delete
/api/user/add
/api/user/disable


---

### 🛠 Uygulama Adımları

#### 1. Burp Intruder'a Bir İstek Gönder

PUT /api/user/§update§ HTTP/1.1
Host: example.com
Authorization: Bearer [TOKEN]






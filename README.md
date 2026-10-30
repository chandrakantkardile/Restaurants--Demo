# स्वामी समर्थ हॉटेल वेबसाइट (Swami Samarth Hotel)

स्वामी समर्थ हॉटेलसाठी तयार केलेली responsive, bilingual (मराठी आणि English)
restaurant website. ग्राहक मेनू पाहू शकतात, पदार्थ शोधू शकतात, Veg/Non-Veg
filter वापरू शकतात, cart मध्ये पदार्थ add करू शकतात आणि WhatsApp द्वारे order
पाठवू शकतात.

## मुख्य Features

### ग्राहकांसाठी

-   मराठी आणि English भाषा बदलण्याची सुविधा.
-   Responsive design --- mobile, tablet आणि desktop साठी.
-   Menu categories:
    -   नाश्ता व स्नॅक्स
    -   Starters
    -   Main Course
    -   भाकरी व भात
    -   पेये
    -   गोड पदार्थ
-   पदार्थ शोधण्यासाठी search.
-   Veg आणि Non-Veg filter.
-   Popular dishes highlight.
-   Cart मध्ये quantity वाढवणे/कमी करणे.
-   Subtotal, 5% GST आणि Total calculation.
-   Dine-in, Takeaway आणि Home Delivery order प्रकार.
-   ग्राहकाचे नाव, मोबाईल नंबर आणि आवश्यकतेनुसार table/time/address माहिती.
-   WhatsApp वर order details पाठवण्याची सुविधा.
-   Order status पाहणे आणि pending order cancel करणे.
-   Bill पाहणे, WhatsApp वर share करणे आणि print करणे.

### हॉटेल मालकासाठी

-   Owner Panel.
-   सध्याच्या browser मध्ये जतन झालेल्या orders पाहणे.
-   Pending orders आणि completed orders पाहणे.
-   Order ला Preparing किंवा Completed status देणे.
-   Order delete करणे.
-   Pending orders, completed orders आणि completed sales यांचा summary.

## वापरलेले तंत्रज्ञान

-   HTML5
-   CSS3
-   JavaScript (Vanilla JS)
-   Tailwind CSS 3.4.17 --- CDN द्वारे
-   Google Fonts
-   Browser LocalStorage
-   WhatsApp Click-to-Chat (`wa.me`)

## Project Structure

सध्या हा single-page frontend project आहे.

``` text
swami-samarth-hotel/
├── index.html
└── README.md
```

`index.html` मध्ये HTML layout, CSS styling, Marathi/English text, menu
data आणि JavaScript functionality समाविष्ट आहे.

## Project चालवण्याची पद्धत

### आवश्यक गोष्टी

-   कोणताही आधुनिक browser --- Chrome, Edge, Firefox इ.
-   Tailwind CSS CDN आणि Google Fonts load होण्यासाठी internet
    connection.

### Steps

1.  Project मधील `index.html` फाइल उघडा.
2.  ती Chrome किंवा इतर browser मध्ये run करा.
3.  Menu मधून पदार्थ निवडून cart मध्ये add करा.
4.  Order type निवडा आणि आवश्यक customer details भरा.
5.  **Place Order** वर click करा.
6.  WhatsApp उघडल्यानंतर message तपासून **Send** दाबा.

Local development साठी VS Code मधील Live Server वापरू शकता.

## महत्त्वाची Configuration

`index.html` मधील JavaScript मध्ये खालील constants/configuration आहेत:

  Configuration      सध्याची value        उपयोग
  ------------------ ------------------- -------------------------------
  WhatsApp number    `919960842249`      Order WhatsApp वर पाठवण्यासाठी
  Hotel phone        `+91 99608 42249`   Call link आणि contact details
  Owner demo PIN     `1234`              Owner Panel उघडण्यासाठी
  GST                `5%`                Bill calculation
  Language default   `mr`                सुरुवातीची भाषा मराठी

### WhatsApp नंबर बदलणे

`PH` constant आणि HTML मधील `tel:` / `wa.me` links मध्ये नवीन नंबर country
code सहित update करा. `wa.me` साठी नंबर digits-only format मध्ये असावा.

### Menu आणि किंमती बदलणे

`M` array मध्ये प्रत्येक पदार्थाची माहिती दिली आहे:

``` javascript
// [category, emoji, English name, Marathi name, price, isVeg, isPopular]
["snack", "🍲", "Misal Pav", "मिसळ पाव", 90, 1, 1]
```

-   `category`: पदार्थाची category.
-   `emoji`: menu card वर दाखवलेले चिन्ह.
-   `English name` / `Marathi name`: दोन्ही भाषांतील नाव.
-   `price`: पदार्थाची किंमत.
-   `isVeg`: `1` = Veg, `0` = Non-Veg.
-   `isPopular`: `1` = Popular, `0` = सामान्य.

## Data Storage आणि मर्यादा

हा सध्याचा frontend demo आहे. Data browser च्या `localStorage` मध्ये साठवला
जातो.

-   Cart: `ss_cart`
-   Language: `ss_lang`
-   Orders: `ss_orders`

**महत्त्वाचे:** LocalStorage मुळे cart आणि orders हे त्याच browser/device मध्ये
उपलब्ध राहतात. वेगवेगळ्या मोबाईल किंवा devices मध्ये orders आपोआप sync होत
नाहीत. Browser data clear केल्यास साठवलेली माहिती जाऊ शकते.

Owner Panel मधील `1234` हा demo PIN आहे. तो production security नाही.
सध्या backend, database, secure authentication, online payment gateway
किंवा centralized order management जोडलेले नाहीत.

WhatsApp order flow मध्ये website message तयार करून WhatsApp उघडते. ग्राहकाने
WhatsApp मध्ये **Send** दाबल्यावरच order हॉटेलला पाठवला जातो.

## Production साठी पुढील सुधारणा

Production मध्ये वापरण्यापूर्वी खालील गोष्टींचा विचार करा:

1.  Spring Boot किंवा इतर backend API तयार करणे.
2.  MySQL/PostgreSQL database मध्ये menu, customers आणि orders साठवणे.
3.  Secure owner/admin login आणि role-based access.
4.  सर्व devices वर orders sync होण्यासाठी real-time किंवा periodic API
    refresh.
5.  Menu आणि prices साठी admin CRUD panel.
6.  Order confirmation आणि status updates.
7.  Payment gateway integration --- आवश्यक असल्यास.
8.  Server-side GST/tax calculation आणि योग्य invoice rules.
9.  Input validation, API security, HTTPS आणि error handling.
10. Production hosting आणि domain configuration.

## संपर्क

**स्वामी समर्थ हॉटेल**\
पत्ता: मु. पो. गेवराई, ता. नेवासा, जि. अहिल्यानगर, महाराष्ट्र\
फोन: +91 99608 42249\
वेळ: दररोज सकाळी ८ ते रात्री ११

------------------------------------------------------------------------

**टीप:** Menu items, prices, GST आणि contact details हे सध्याच्या project
code मधील values आहेत. प्रत्यक्ष वापरापूर्वी हॉटेलकडून त्यांची खात्री करून घ्या.

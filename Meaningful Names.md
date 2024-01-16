# Anlamlı İsimlendirme

* **Anlaşılır isimlendirme yap! Anlamsız kısaltmalardan uzak dur.**
* **Telaffuz etmesi zor kelimeleri kullanma**


* `int d; //elapsed time in days`  
Bunun gibi bir kullanım oldukça hatalıdır.
değişkenlere, fonksiyonlara ve sınıflara anlaşılır isimler verilmelidir.
Eğer bu şekilde yorum satırıyla değişken için açılama yapmamız gerekiyorsa bir sorun var demektir.



* Torba yapısından oluşturulan değişkenlere
  (örn: List) `productList, addresList` gibi isimlendirmeler kullanmana gerek yok.
Zaten bunların liste yapısında olduğu belli olmaktadır.
Bunun yerine `products, addresses` gibi isimlendirmeler kullan.


* Tek harften oluşan isimlendirmeler yapılmamalıdır.
Bu durum anlaşılma zorluna neden olacaktır hem de 
kod içinde aramayı zorlaştıracaktır. Örneğin `a` şeklinde
bir tanımlama yapıldığında a olarak aratıldığunda bir sürü şey çıkacaktır.



* Tek harf değişken kullanımı döngüler içinde sayaç olarak kullanılabilir.
Bu gibi durumlar herkes tarafından bilindiği ve anlaşılması basit olduğu için 
bu şekilde kullanılabilir.


Örnek kötü kullanım:

        for (int j=0; j<34; j++) {
            s += (t[j]*4)/5;
        } 
Doğru kullanım:

    int realDaysPerIdealDay = 4;
    const int WORK_DAYS_PER_WEEK = 5;
    int sum = 0;
    for (int j=0; j < NUMBER_OF_TASKS; j++) {
        int realTaskDays = taskEstimate[j] * realDaysPerIdealDay;
        int realTaskWeeks = (realdays / WORK_DAYS_PER_WEEK);
        sum += realTaskWeeks;
    }

* İsimlendirmede tutarlı olunmalıdır. Örneğin veri getirme görevi olan
fonksiyonları isimlendirirken biri `getProduct`, diğeri `fetchCustomer` 
yapılmamalıdır. Bir yerde get kullanılıyorsa projenin tamamında buna uyarak isimlendirme
yapılmalıdır.


* İsimlendirme yaparken kullanılan kelimeye farklı anlamlar yüklemek karışıklığa neden olabilir.


Örneğin; `add`'e bazen farklı anlamlar yüklenebilmektedir. Hem var olan bir yapıya
ekleme yaparken hemde bir şey yaratırken `add` ile başlayan isimlendirmeler yapılmamalıdır.
Var olana eklemek için `add`, yaratmak için `create` gibi ayrımlar yapılmalıdır.



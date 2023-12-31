# Bilgisayar programlamada tür sistemleri

Bilgisayar programlamada tür/tip sistemi, her "terime" tür adı verilen bir özellik (örneğin, integer, floating point, string) atayan bir dizi kuraldan oluşan mantıksal bir sistemdir. Genellikle terimler, değişkenler, ifadeler, fonksiyonlar veya modüller gibi bir bilgisayar programının çeşitli yapılarıdır. Bir tür sistemi, bir terim üzerinde gerçekleştirilebilecek işlemleri belirler. Değişkenler için, tür sistemi o terim için izin verilen değerlerini belirler. Tür sistemleri programcının cebirsel veri türleri, veri yapıları veya diğer bileşenler için kullandığı örtük kategorileri resmileştirir ve uygular.

Tür sistemleri genellikle programlama dillerinin bir parçası olarak belirtilir ve yorumlayıcılara ve derleyicilere yerleştirilir, ancak bir dilin tür sistemi dilin orjinal tür söz dizimini ve grammar'ini kullanarak ek kontroller gerçekleştiren isteğe bağlı araçlarla genişletilebilir.

Bir programlama dilindeki tür sisteminin temel amacı, bilgisayar programlarında tür hatalarından kaynaklanan hata olasılıklarını azaltmaktır. Söz konusu tür sistemi, neyin tür hatası olduğunu belirler, ancak genel olarak amaç, belirli bir değer bekleyen işlemlerin, bu işlemin mantıklı olmadığı değerlerle kullanılmasını önlemektir (geçerlilik hataları). Tür sistemleri, bir bilgisayar programının farklı parçaları arasındaki arayüzlerin tanımlanmasına ve ardından bu parçaların tutarlı bir şekilde bağlandığının kontrol edilmesine olanak tanır. Bu kontrol etme, statik olarak (compile time'da), dinamik olarak (run time'da) ya da her ikisinin bir kombinasyonu olarak gerçekleşebilir. Tür sistemleri, iş kurallarını ifade etme, belirli derleyici optimizasyonlarını mümkün kılma, çoklu gönderime izin verme ve bir tür dokümantasyon sağlama gibi başka amaçları da vardır.

## Kullanıma Genel Bakış

Basit bir tür sistemine örnek olarak C dili verilebilir. Bir C programının bölümleri fonksiyon tanımlarıdır. Bir fonksiyon başka bir fonksiyon tarafından çağrılır. Bir fonksiyonun arayüzü, fonksiyonun adını ve fonksiyonun koduna aktarılan parametrelerin bir listesini belirtir. Çağrılan bir fonksiyonun kodu, çağrılan fonksiyonun adını ve ona aktarılacak değerleri tutan değişkenlerin adlarını belirtir. Yürütme sırasında değerler geçici depolama alanına yerleştirilir ardından yürütme, çağrılan fonksiyonun koduna atlar. Çağrılan fonksiyonun kodu değerlere erişir ve bunları kullanır. Fonksiyonların içindeki talimatlar bir integer değer alınacağı varsayımıyla yazılmışsa, ancak çağıran kod floating-point bir değer geçtiyse, çağrılan fonksiyon tarafından yanlış sonuç hesaplanacaktır. C derleyicisi, bir fonksiyona aktarılan argümanların türlerini, fonksiyonun tanımında bildirilen parametrelerin türlerine göre kontrol eder. Türler eşleşmezse, derleyici bir compile-time hatası veya uyarısı atar.

Bir derleyici ayrıca bir değerin statik türünü, ihtiyaç duyduğu depolama alanını ve değer üzerindeki işlemler için algoritma seçimini optimize etmek için kullanabilir. Örneğin, birçok C derleyicisinde float veri türü, tek hassasiyetli kayan noktalı sayılar için IEEE spesifikasyonuna uygun olarak 32 bit ile temsil edilir. Dolayısıyla, bu değerler üzerinde kayan noktaya özgü mikroişlemci işlemlerini (kayan noktalı toplama işlemi, çarpma işlemi, vb.) kullanacaklardır.

Tür kısıtlamalarının derinliği ve değerlendirme şekli, dilin türlemesini etkiler. Bir programlama dili, tür polimorfizmi durumunda, bir işlemi her tür için çeşitli çözümlerle ilişkilendirebilir. Tür teorisi, tür sistemlerinin incelenmesidir. Integer ve string'ler gibi bazı programlama dillerinin somut türleri, bilgisayar mimarisi, derleyici uygulaması ve dil tasarımı gibi pratik konulara bağlıdır.

## Temelleri

Resmi olarak tür teorisi, tür sistemlerini inceler. Bir programlama dili, ister compile-time'da ister run-time'da olsun, elle açıklanmış veya otomatik olarak çıkarılmış tür sistemini kullanarak tür kontrolü yapma olanağına sahip olmalıdır. Mark Manasse'nin kısaca ifade ettiği gibi:

Bir tür teorisi tarafından ele alınan temel sorun, programların bir anlamı olmasını sağlamaktır. Bir tür teorisinin neden olduğu temel sorun ise anlamlı programların kendilerine atfedilen anlamlara sahip olmayabilmesidir. Daha zengin tür sistemleri arayışı bu gerilimden kaynaklanmaktadır.

Türleme (typing) olarak adlandırılan bir veri türü atama, bellekteki bir değer gibi, değişken gibi veya bir object gibi bir bit dizisine anlam kazandırır. Genel amaçlı bir bilgisayarın donanımı, örneğin bir bellek adresi ile bir komut kodu arasında ya da bir karakter, bir tamsayı ya da bir kayan noktalı sayı arasında ayrım yapamaz, çünkü bir dizi bitin ifade edebileceği olası değerlerden herhangi biri arasında içsel bir ayrım yapmaz. Bir bit dizisini bir tür ile ilişkilendirmek bu anlamı programlanabilir donanıma aktararak bu donanım ve bazı programlardan oluşan sembolik bir sistem oluşturur.

Bir program her değeri en az bir belirli tür ile ilişkilendirir, ancak bir değerin birçok alt türle ilişkilendirilmesi de söz konusu olabilir. Object'ler, modüller, iletişim kanalları ve bağımlılıklar gibi diğer varlıklar bir tür ile ilişkilendirilebilir. Bir tür bile bir tür ile ilişkilendirilebilir. Bir tür sisteminin uygulanması teoride veri türü olarak adlandırılan tanımlamaları ilişkilendirebilir (bir değerin türü, bir object'in türü, bir türün türü veya metatür).

Bir programlama dili daha ayrıntılı tür sistemi geliştirdiğinde, temel tür denetiminden daha ince taneli bir kural kümesi kazanır, ancak tür çıkarımları (ve diğer özellikler) karar verilemez hale geldiğinde ve programcı tarafından koda açıklama eklemek veya bilgisayarla ilgili işlemleri ve işleyişi dikkate almak için daha fazla dikkat gösterilmesi gerektiğinde bunun bir bedeli vardır. Tüm programlama uygulamalarını tür güvenli bir şekilde karşılayan yeterince etkili bir tür sistemi bulmak zordur.

Bir programlama dili derleyicisi bir tür denetçisi tarafından daha da fazla program spesifikasyonunun doğrulanmasını sağlayan bir bağımlı tür veya bir etki sistemi de uygulayabilir. Basit değer-tür çiftlerinin ötesinde, kodun sanal bir "bölgesi" neyin ne ile yapıldığını açıklayan ve örneğin bir hata raporunun "atılmasını" sağlayan bir "etki" bileşeni ile ilişkilendirilir. Böylece sembolik sistem, bir tür ve etki sistemi olabilir, bu da ona tek başına tür kontrolünden daha fazla güvenlik kontrolü sağlar.

İster derleyici tarafından otomatikleştirilsin ister bir programcı tarafından belirtilsin, bir tür sistemi, tür sistemi kurallarının dışına çıkıldığında program davranışını yasadışı hale getirir.
Programcı tarafından belirtilen tür sistemlerinin sağladığı avantajlar şunlardır:

-   **_Soyutlama (veya modülerlik)_** - Türler, programcıların düşük seviye uygulama ile uğraşmadan, bit veya bayttan daha yüksek bir seviyede düşünmelerini sağlar. Örneğin programcılar bir string'i yalnızca bir bayt array'i yerine bir karakter değerleri kümesi olarak düşünmeye başlayabilir. Daha da yukarıda, türler programcıların herhangi bir boyutlu iki alt sistem arasındaki arayüzleri düşünmelerini ve ifade etmelerini sağlar. Bu, alt sistemlerin birlikte çalışabilirliği için gereken tanımların bu iki alt sistem iletişim kurduğunda tutarlı kalması için daha fazla yerelleştirme düzeyi sağlar.

-   **_Dokümantasyon_** - Daha etkileyici tür sistemlerinde, türler programcının amacını açıklayan bir dokümantasyon biçimi olarak hizmet edebilir. Örneğin, bir programcı bir fonksiyonu timestamp (zaman damgası) türü olarak geri döndürüyor olarak bildirirse, zaman damgası türü kodun daha derinlerinde bir integer türü olarak açıkça bildirilebildiğinde bu fonksiyonu belgeler.

Derleyici tarafından belirtilen tür sistemlerinin sağladğı avantajlar şunlardır:

-   **_Optimizasyon_** - Statik tür denetimi derleme zamanında yararlı bilgiler sağlayabilir. Örneğin, bir tür, bir değerin bellekte dört baytın katları olarak hizanlamasını gerektiriyorsa, derleyici daha verimli makine komutları kullanabilir.

-   **_Güvenlik_** - Bir tür sistemi derleyicinin, anlamsız veya geçersiz kodu tespit etmesini sağlar. Örneğin kurallar bir integer'ın string'e nasıl bölüneceğini belirtmediğinde, `3/"Merhaba, Dünya"` ifadesini geçersiz olarak tanımlayabiliriz. Güçlü türleme daha fazla güvenlik sunar ancak tam tür güvenliğini garanti edemez.

### Tür Hataları

Tür hatası, bir programın geliştirilmesinin birçok aşamasında ortaya çıkabilen istenmeyen bir durumdur. Bu nedenle tür sisteminde hatanın tespiti için bir kolaylığa ihtiyaç vardır. Haskell gibi tür çıkarımının otomatikleştirildiği bazı dillerde, hatanın tespit edilmesine yardımcı olmak için derleyicinin lint'i mevcut olabilir.

Tür güvenliği, program doğruluğuna katkıda bulunur, ancak yalnızca tür kontrolünün kendisini, karar verilemez bir problem haline getirme pahasına doğruluğu garanti edebilir (Halting probleminde olduğu gibi). Otomatik tür denetimine sahip bir tür sisteminde, bir programın hatalı çalıştığı ancak hiçbir derleyici hatası üretmediği ortaya çıkabilir. Sıfıra bölme güvenli olmayan ve yanlış bir işlemdir. ancak yalnızca derleyici zamanında çalışan bir tür denetleyicisi çoğu dilde sıfıra bölme işlemini taramaz. Bu bölme işlemi runtime hatası olarak ortaya çıkar. Bu kusurların yokluğunu kanıtlamak için toplu olarak program analizleri olarak bilinen diğer türden biçimsel yöntemler yaygın olarak kullanılmaktadır. Alternatif olarak, bağımlı olarak türlenen dillerde olduğu gibi yeterince anlamlı bir tür sistemi bu tür hataları önleyebilir (örneğin, sıfır olmayan sayıların türünü ifade etmek). Buna ek olarak yazılım testi, böyle bir tür denetleyicisinin tespit edemeyeceği hataları bulmak için deneysel bir yöntemdir.

[Orjinal Makale](https://en.wikipedia.org/wiki/Type_system)

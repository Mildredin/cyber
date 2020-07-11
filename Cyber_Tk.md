# cyber: Büyük Web bilgisini hesaplamak

[![img](https://github.com/serejandmyself/cyber/raw/master/images/graph.png)](https://github.com/serejandmyself/cyber/blob/master/images/graph.png)

## Soyut

Fikir birliği bilgisayarı, Google, Amazon veya Facebook gibi düşünülmüş bir kara kutu aracı olmadan ispatlanmış alakalı cevapların hesaplanmasına izin verir. IPFS gibi durum bilgisi olmayan, içeriğe adreslenebilir eşler arası iletişim ağları ve Ethereum gibi durumlu fikir birliği bilgisayarları, benzer yanıtlar elde etmek için gereken çözümün sadece bir kısmını sağlayabilir. Bununla birlikte, yukarıda belirtilen uygulamalarla ilişkili en az 3 problem vardır. (A) alaka düzeyinin öznel doğası. (B) konsensüs bilgisayarları aşırı büyüklükteki bilgi grafikleri için ölçeklemede zorluk. (C) bu bilgi grafikleri arasında kalite eksikliği. Sybil saldırıları ve etkileşen ajanların bencil davranışları gibi çeşitli yüzey saldırılarına eğilimlidirler. Bu belgede, fikir birliğindeki GPU'lar kullanılarak hesaplanan siber ~ Rank'ın Tendermint konsensüsüne dayanan IPFS nesneleri arasında uygunluğun kanıtlanabilir konsensüs hesaplaması için bir protokol tanımladık. Tehlikeli kanıt konsensüsü ilk dağıtımda yardımcı olmadığından, ekolojik ve verimli dağıtım oyunlarının tasarımını özetliyoruz. Protokolün minimalist bir mimarisinin, alana özgü bilgi konsensüs bilgisayarlarının bir ağının oluşturulması için kritik olduğuna inanıyoruz. Çalışmamızın bir sonucu olarak, daha önce hiç var olmamış bazı uygulamalar ortaya çıkacaktır. Bu belgeyi olası özellikler ve potansiyel uygulamalar vizyonumuzla genişletiyoruz.

## Büyük Web

İnternetin orijinal protokolleri, örneğin: TCP / IP, DNS, URL ve HTTP / S, web'i şu an bulunduğu eski bir noktaya getirdi. Bu protokollerin web'in ilk gelişimi için yarattığı tüm faydalar göz önünde bulundurularak, masaya önemli engeller getirmişlerdir. Web'in hayati bir özelliği olan globality, kuruluşundan bu yana gerçek bir tehdit altındadır. Her yerde hükümet müdahaleleri nedeniyle ağın kendisi büyümeye devam ederken bağlantının hızı azalmaya devam ediyor. İkincisi, insan haklarına varoluşsal bir tehdit olarak gizlilik endişelerine neden olmaktadır.

Başlangıçta belirgin olmayan bir mülk, İnternet'in günlük kullanımı ile önemli hale gelir: kalıcı bağlantılar alışverişi yapma yeteneği, [zaman geçtikten sonra kırılmayacak](https://ipfs.io/ipfs/QmNhaUrhM7KcWzFYdBeyskoNyihrpHvUEBQnaddwPZigcN). Her seferinde birinin mimarisine güvenmek ISP hükümetlerin paketleri etkili bir şekilde sansürlemesini sağlar. Bu, çocuklarımızın geleceği ile ilgilenen her mühendis için geleneksel web yığınındaki son düşüştür.

Diğer özellikler, bu kadar kritik olmasa da, çok arzu edilir: çevrimdışı ve gerçek zamanlı bağlantı. Ortalama bir internet kullanıcısı, çevrimdışıyken, halihazırda sahip oldukları durumla çalışmaya devam edebilmelidir. Bir bağlantı kurduktan sonra, küresel durumla senkronize edebilmeli ve kendi durumlarının geçerliliğini gerçek zamanlı olarak doğrulamaya devam edebilmelidirler. Şu anda, bu özellikler uygulama düzeyinde sunulmaktadır. Bu özelliklerin alt düzey protokollere entegre edilmesi gerektiğine inanıyoruz.

Ortaya çıkması [yepyeni bir web yığını](https://ipfs.io/ipfs/Qmf2rKkDPSsvdudwSmdDPbZuYae8XRV26c1wAFCCvg8Dhw) üstün bir İnternet için bir fırsat yaratır. Topluluk buna web3 diyor. Biz buna Büyük Web diyoruz. Çeşitli düşük seviyeli iletişim türlerinin değişmez olması ve on yıllar boyunca değişmemesi gerektiğine inanıyoruz, ör. değişmez içerik bağlantıları. Geleneksel protokol yığını sorunlarının giderilmesinde çok umut verici görünüyorlar. Daha fazla hız ekler ve yeni web'e daha erişilebilir bir bağlantı sağlarlar. Bununla birlikte, benzersiz bir şey sunan herhangi bir konseptte olduğu gibi - yeni sorunlar ortaya çıkar. Bu endişelerden biri genel amaçlı aramadır. Mevcut genel amaçlı arama motorları, herkesin güvendiği zorlayıcı ve merkezi veritabanlarıdır. Bu arama motorları öncelikle TCP / IP, DNS, URL ve HTTP / S tabanlı istemci-sunucu mimarileri için tasarlanmıştır. Büyük Web, gelişen teknolojilere dayanan ve bu amaçlar için özel olarak tasarlanmış bir arama motoru için bir zorluk ve fırsat yaratır. Şaşırtıcı bir şekilde, izinsiz blockchain mimarisi, önceki mimarilere erişilemeyecek bir şekilde genel amaçlı bir arama motoru oluşturmaya izin verir.

## Çekişmeli örnekler problemi üzerine

[Arama motorlarının mevcut mimarisi](https://ipfs.io/ipfs/QmeS4LjoL1iMNRGuyYSx78RAtubTT2bioSGnsvoaupcHR6) bazı varlıkların tüm bokları işlediği bir sistemdir. Bu yaklaşım, parlak Google bilim adamları tarafından bile henüz çözülmemiş olan zorlu ve farklı bir sorundan muzdarip: [çekişmeli örnekler problemi](https://ipfs.io/ipfs/QmNrAFz34SLqkzhSg4wAYYJeokfJU5hBEpkT4hPRi226y9). Google'ın kabul ettiği sorun, belirli bir örneğin olumsuz olup olmadığını algoritmik olarak akıl yürütmenin oldukça zor olmasıdır. Bu, eğitim teknolojisinin kendi içinde ne kadar harika olduğu konusunda düşüncesizdir. Kripto-ekonomik bir yaklaşım oyundaki faydalanıcıları değiştirebilir. Sonuç olarak, bu yaklaşım olası sybil saldırı vektörlerini etkili bir şekilde kaldıracaktır. Tek bir varlık tarafından sabit kodlu model taraması ve anlam çıkarması gerekliliğini ortadan kaldırır. Bunun yerine, bu gücü tüm dünyaya verir. Öğrenme yeteneğine dirençli, ajan tarafından üretilen bir model, muhtemelen daha büyük boyutlarda daha öngörücü sonuçlara yol açacaktır.

## Siber protokol

Özünde protokol çok minimalisttir ve aşağıdaki adımlarla ifade edilebilir:

1. Tanımlanan dağılıma göre siber protokolün oluşumunu hesaplar
2. Durumunu tanımlayın [bilgi grafiği](https://github.com/serejandmyself/cyber/blob/master/cyber.md#knowledge-graph)
3. İşlemleri bir [fikir birliği bilgisayarı](https://github.com/serejandmyself/cyber/blob/master/cyber.md#the-notion-of-a-consensus-computer)
4. İmzaların geçerliliğini kontrol etme
5. Kontrol edin [bant genişliği sınırı](https://github.com/serejandmyself/cyber/blob/master/cyber.md#relevance-machine)
6. CID'lerin geçerliliğini kontrol edin
7. İmzalar, bant genişliği sınırı ve CID'lerin tümü geçerliyse uygulayın [Cyberlinks](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyberlinks) ve işlemler
8. Vaüllerini hesaplayın [siber ~ Derece](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyberrank) üzerindeki her tur için [bilgi grafiği](https://github.com/serejandmyself/cyber/blob/master/cyber.md#knowledge-graph)

Bu belgenin geri kalanında, önerilen protokolün gerekçesi ve teknik ayrıntıları tartışılmaktadır.

## Bilgi grafiği

Bir bilgi grafiğini, içerik adresleri arasındaki yönlendirilmiş bağlantıların ağırlıklı bir grafiği olarak temsil ediyoruz. Aka, içerik tanımlayıcılar, CID'ler, IPFS karmaları veya basitçe - IPFS bağlantıları. Bu belgede, yukarıdaki terimleri eş anlamlı olarak kullanacağız.

[![img](https://github.com/serejandmyself/cyber/raw/master/images/knowledge-graph.png)](https://github.com/serejandmyself/cyber/blob/master/images/knowledge-graph.png)

İçerik adresleri aslında web3 bağlantılarıdır. Belirsiz ve değişmez kullanmak yerine:

```
https://github.com/cosmos/cosmos/blob/master/WHITEPAPER.md
```

Nesnenin kendisini kullanıyoruz:

```
Qme4z71Zea9xaXScUi6pbsuTKCCNFp5TAv8W5tjdfH7yuH
```

Kazanacağımız bilgi grafiğini oluşturmak için içerik adreslerini kullanarak [çok ihtiyaç var](https://steemit.com/web3/@hipster/an-idea-of-decentralized-search-for-web3-ce860d61defe5est) [IPFS](https://ipfs.io/ipfs/QmV9tSDx9UiPeWExXEeH6aoDvmihvx6jD5eLb4jbTaKGps) - [like](https://ipfs.io/ipfs/QmXHGmfo4sjdHVW2MAxczAfs44RCpSeva2an4QvkzqYgfR) bir arama motoru için istenen p2p protokollerinin süper güçleri:

- mesh-network geleceğe hazır
- gezegenler arası erişilebilirlik
- sansür direnci
- teknolojik bağımsızlık

Bilgi grafiğimiz harika ustalar tarafından üretildi. Ustalar kendilerini tek bir işlem, bir siber bağlantı yardımıyla bilgi grafiğine eklerler. Böylece, açık anahtarlarının içerik adresleri için özel anahtarlarının varlığını kanıtlarlar. Bu mekaniği kullanarak, [fikir birliği bilgisayarı](https://github.com/serejandmyself/cyber/blob/master/cyber.md#the-notion-of-a-consensus-computer) bir bilgi grafiğinde konular ve nesneler arasında kanıtlanabilir farklılaşma elde edebilir.

Uygulamamız [Go-siber](https://github.com/cybercongress/go-cyber) dayanır [kozmos-SDK](https://github.com/cosmos/cosmos-sdk) kimlikler ve [CIDv0 / CIDv1](https://github.com/multiformats/cid#cidv0) içerik adresleri.

Ustalar uygulayarak bilgi grafiğini oluşturur [cyberlinks](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyberlinks).

## Cyberlinks

Siber bağlantıların nasıl çalıştığını anlamak için bir URL bağlantısı (diğer adıyla köprü) ve IPFS bağlantısı arasındaki farkı anlamamız gerekir. Bir URL bağlantısı, bir IPFS bağlantısının içeriğin kendisini gösterip göstermediğine bakılmaksızın içeriğin konumunu gösterir. Konum bağlantılarına ve içerik bağlantılarına dayalı web mimarileri arasındaki fark radikaldir ve benzersiz bir yaklaşım gerektirir.

Cyberlink, semantik olarak iki içerik adresini veya IPFS bağlantısını bağlamak için bir yaklaşımdır:

```
.md syntax: [QmdvsvrVqdkzx8HnowpXGLi88tXZDsoNrGhGvPvHBQB6sH](Qme4z71Zea9xaXScUi6pbsuTKCCNFp5TAv8W5tjdfH7yuH)    
.dura syntax: QmdvsvrVqdkzx8HnowpXGLi88tXZDsoNrGhGvPvHBQB6sH.Qme4z71Zea9xaXScUi6pbsuTKCCNFp5TAv8W5tjdfH7yuH
```

Yukarıdaki siber bağlantı, [Go-siber](https://github.com/cybercongress/go-cyber) sırasında[cyberc0n](https://etherscan.io/token/0x61B81103e716B611Fff8aF5A5Dc8f37C628efb1E) Cosmos tanıtım belgesine atıfta bulunuyor. Siber bağlantılar kavramı, herhangi bir p2p ağında iletişim formatının basit anlambilimi etrafında bir konvansiyon:

[![img](https://github.com/serejandmyself/cyber/raw/master/images/cyberlink.png)](https://github.com/serejandmyself/cyber/blob/master/images/cyberlink.png)

Bir siber bağlantının iki bağ arasındaki bağlantıyı temsil ettiğini görüyoruz. Tereyağından kıl çeker gibi!

Cyberlink, evrenin öngörülü bir modelini oluşturmak için basit ama güçlü bir anlamsal yapıdır. Bu, köprüler yerine siber bağlantıların kullanılmasının bize önceki genel amaçlı arama motorlarının mimarileri tarafından erişilemeyen süper güçleri sağladığı anlamına gelir.

Siber bağlantılar uzatılabilir, yani bir veya iki siber bağlantı bir master'dan geçerse, birinci siber bağlantıdaki ikinci bağ ikinci siber bağlantıdaki ilk bağlantıya eşitse, bağlantı zincirleri oluşturabilirler:

[![img](https://github.com/serejandmyself/cyber/raw/master/images/linkchain.png)](https://github.com/serejandmyself/cyber/blob/master/images/linkchain.png)

Aracılar yerel IPFS bağlantılarını anlamsal olarak daha zengin bir şeyle genişletirse, örneğin[dura](https://github.com/cybercongress/cyb/blob/dev/docs/dura.md) bağlantılar, daha sonra belirli bir program tarafından yürütme kuralları üzerinde fikir birliğine daha doğal bir yaklaşımla ulaşılabilir.

The [Go-siber](https://github.com/cybercongress/go-cyber) siber bağlantıların uygulanması [.Siber](https://github.com/cybercongress/dot-cyber) deneysel web3 tarayıcımızın uygulaması [cyb](https://cyb.ai/), veya[cyber.page](http://cyber.page/).

Ustalar tarafından gönderilen siber bağlantılar, [RFC-6962 standard](https://ipfs.io/ipfs/QmZpJLmc3T2L1FLUxzvU3P8MBCPe15fEmUyVS7Bz8ZKMhG). Bu, [kanıtı alaka](https://github.com/serejandmyself/cyber/blob/master/cyber.md#proof-of-relevance).

[![img](https://github.com/serejandmyself/cyber/raw/master/images/graph-tree.png)](https://github.com/serejandmyself/cyber/blob/master/images/graph-tree.png)

Siber bağlantıları kullanarak, nesnelerin ve nesnelerin [bilgi grafiği](https://github.com/serejandmyself/cyber/blob/master/cyber.md#knowledge-graph). Ama ihtiyacımız var [fikir birliği bilgisayarı](https://github.com/serejandmyself/cyber/blob/master/cyber.md#the-notion-of-a-consensus-computer).

## Mutabakat bilgisayarı kavramı

Bir konsensüs bilgisayar, ajanlar arasındaki etkileşimden ortaya çıkan soyut bir hesaplama makinesidir. Bir konsensüs bilgisayarın temel hesaplama kaynakları açısından kapasitesi vardır: bellek ve hesaplama. Ajanlarla etkileşim kurmak için bir bilgisayarın bant genişliğine ihtiyacı vardır. İdeal bir fikir birliği bilgisayarı şu durumlarda bir bilgisayardır:

```
the sum of all the computations and memory available to individuals`
`is equal to`
`the sum of all the verified computations and memory of the consensus computer
```

Biz biliyoruz ki:

```
verifications of computations < (computations + verifications of computations)
```

Bu nedenle, asla ideal bir konsensüs bilgisayarı elde edemeyiz. CAP teoremi ve ölçeklenebilirlik trilemması bu ifadeye daha fazla kanıt ekler.

[![img](https://github.com/serejandmyself/cyber/raw/master/images/consensus-computer.png)](https://github.com/serejandmyself/cyber/blob/master/images/consensus-computer.png)

Yine de bu teori bir konsensüs bilgisayarı için bir performans göstergesi olarak çalışabilir. Mutabakat bilgisayarlarına 6 yıl yatırım yaptıktan sonra, [Tendermint](https://ipfs.io/ipfs/QmaMtD7xDgghqgjN62zWZ5TBGFiEjGQtuZBjJ9sMh816KJ) fikir birliği, görevimiz için gerekli olan serinlik ile üretime hazır olma arasında yeterince iyi bir dengeye sahiptir. Bu nedenle, [Siber](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyber-protocol) Cosmos Hub'a çok yakın ayarlara sahip olan Tendermint konsensüsünü kullanarak protokol. [Go-siber](https://github.com/cybercongress/go-cyber) uygulama 64-bit dizge alanı için bir 64-bit Tendermint konsensüs bilgisayarıdır. Bu, en azından 1/146 kadar ideal değildir, çünkü aynı hesaplamaları üreten aynı hesaplamaları doğrulayan 146 doğrulayıcıya sahibiz. [Bilgi-grafiği](https://github.com/serejandmyself/cyber/blob/master/cyber.md#knowledge-graph).

Mutabakat bilgisayarının hesaplanmasını, depolanmasını ve bant genişliği beslemesini sorgulara maksimum bir taleple ilişkilendirmeliyiz. Temel bir durumda hesaplama ve depolama [uygunluk makinesi](https://github.com/serejandmyself/cyber/blob/master/cyber.md#relevance-machine) bant genişliğine göre kolayca tahmin edilebilir. Ancak bant genişliği sınırlayıcı bir mekanizma gerektirir.

## Alaka düzeyi makinesi

Alaka düzeyini belirleyen bir makineyi, [Bilgi-grafiği](https://github.com/serejandmyself/cyber/blob/master/cyber.md#knowledge-graph) öğretmek ve incelemek isteyen ajanların iradesine dayanarak [Bilgi-grafiği](https://github.com/serejandmyself/cyber/blob/master/cyber.md#knowledge-graph). İrade her biri tarafından [cyberlinks](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyberlinks) bir efendi yapar. Daha fazla temsilci[Bilgi-grafiği](https://github.com/serejandmyself/cyber/blob/master/cyber.md#knowledge-graph), bilgi ne kadar değerli olursa. Bu projeksiyonlara dayanarak, içerik adresleri arasındaki ilişki hesaplanabilir. Alaka düzeyi makinesi, cevapları sorgulayıp ileterek arama mekanizması için basit bir yapı sağlar.

Alaka makinesinin bir özelliği çok önemlidir. Tümevarımsal muhakeme özelliklerine sahip olmalı veya kara kutu ilkesine uymalıdır:

```
The machine should be able to interfere with predictions without any knowledge about the objects,`
`except for who, when and what was cyberlinked
```

Eğer bir [fikir birliği bilgisayarı](https://github.com/serejandmyself/cyber/blob/master/cyber.md#the-notion-of-a-consensus-computer) bağlantılı nesneler hakkında bazı bilgilere sahip olmalıdır, o zaman böyle bir modelin karmaşıklığı öngörülemez şekilde büyüyecektir. Bu nedenle işlem bilgisayarının bellek ve hesaplama için yüksek gereksinimleri. Blackbox prensibini takip eden bir alaka makinesine hitap eden içerik sayesinde, verilerin depolanması gerekmez. Ancak, yine de etkili bir şekilde çalışabilir. İçinde anlam çıkarılması [fikir birliği bilgisayarı](https://github.com/serejandmyself/cyber/blob/master/cyber.md#the-notion-of-a-consensus-computer) pahalı. Dolayısıyla, böyle bir tasarım varsayım körlüğüne bağlı olabilir. İçindeki anlamı çıkarmak yerine [fikir birliği bilgisayarı](https://github.com/serejandmyself/cyber/blob/master/cyber.md#the-notion-of-a-consensus-computer), anlam çıkarmanın teşvik edildiği bir sistem tasarladık. Bu, gerektiren ustalar nedeniyle elde edilir [CYB](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyb) alaka düzeyini ifade etmek için jetonlar, alaka makinesinin rütbeyi hesaplayabileceği.

Spam koruma sisteminin merkezinde, yazma işlemlerinin yalnızca alaka düzeyindeki makinenin evrimsel başarısına olan ilgisi olanlar tarafından gerçekleştirilebileceği varsayımı vardır. Etkili bahis miktarının her% 1'i [fikir birliği bilgisayarı](https://github.com/serejandmyself/cyber/blob/master/cyber.md#the-notion-of-a-consensus-computer) olası ağların bant genişliğinin% 1'ini ve bilgi işlem yeteneklerini kullanma yeteneği verir. Basit bir kural aracıların kötüye kullanımını önler: bir çift içerik tanımlayıcı bir adresle yalnızca bir kez siber bağlanabilir.

[![img](https://github.com/serejandmyself/cyber/raw/master/images/algo1.png)](https://github.com/serejandmyself/cyber/blob/master/images/algo1.png)

Bir hesabın etkin bahis tutarını (aktif bahis + tahvil hissesi) değiştirmenin sadece iki yolu vardır: doğrudan jeton transferleri ve bono işlemleri.

[Siber](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyber-protocol) çok basit bir bant genişliği modeli kullanır. Bu modelin temel amacı, günlük ağ büyümesini belirli bir sabite düşürmektir. Bu, kahramanları (doğrulayıcıları) gelecekteki altyapı yatırımlarını tahmin etme yeteneği ile karşılamak için yapılır. Böylece, burada 'watt' veya 'W' yi sunuyoruz. Her mesaj türünün atanmış W maliyeti vardır. Sabit 'DesirableBandwidth', W değeri tarafından harcanan istenen 'RecoveryWindow' değerini belirler. Kurtarma süresi, bir master'ın bant genişliklerini 0'dan maksimum bant genişliğine ne kadar hızlı geri kazanabileceğini tanımlar. Bir üstat, aşağıdaki formülle belirlenen etkili hissesi ile orantılı olarak maksimum W değerine sahiptir:

```
AgentMaxW = EffectiveStake * DesirableBandwidth
```

'AdjustPricePeriod' periyodu, son bloktaki 'RecoveryPeriod' periyodu boyunca ne kadar W harcandığını toplar. 'SpentBandwidth' / 'WanrableBandwidths' oranına kesirli rezerv oranı denir. Ağ kullanımı düşük olduğunda, kısmi rezerv oranı, daha düşük bir hisseye sahip ustaların daha fazla işlem yapmalarını sağlamak için mesaj maliyetini ayarlar. Kaynaklara olan talep arttığında, kısmi rezerv oranı> 1 olur ve bunun sonucunda mesaj maliyetini arttırır ve uzun vadeli bir süre için nihai tx sayısını sınırlar (W geri kazanımı <sonra W harcaması olacaktır). Hiç kimse sahip olduğu tüm bant genişliğini kullanmadığından, bir fiyat yeniden hesaplama hedef süresi içinde 100x'e kadar kesirli rezervi güvenle kullanabiliriz. Bu tür mekanikler oluşturmak için bir indirim sağlar [cyberlinking](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyberlinks), üst düzeye çıkarır. Seçtiğiniz tasarımın alaka gereklilikleri için gerekli banttır.

İnsan zekası, zamanla ilgisiz ve önemsiz anılar unutulmayacak şekilde düzenlenmiştir. Aynı durum alaka makinesine de uygulanabilir. Alaka düzeyi makinesi [agresif budama stratejileri](https://ipfs.io/ipfs/QmP81EcuNDZHQutvdcDjbQEqiTYUzU315aYaTyrVj6gtJb), gibi, budama tarihinin budaması [Bilgi-grafiği](https://github.com/serejandmyself/cyber/blob/master/cyber.md#knowledge-graph), veya daha az alakalı hale gelen bağlantıları unutmak.

Sonuç olarak, uygulanan sibernomik [CYB](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyb) jetonlar aynı ifade ve spam koruma mekanizmaları gibi değil, aynı zamanda kahramanların işlem kapasitesini ve pazarın işleme talebini hizalayabilen bir ekonomi düzenleme aracı işlevi de görür. Uygunluk makinesinin go-siber uygulaması, siber ~ Sıra adı verilen çok basit bir mekanizmaya dayanmaktadır.

## cyber ~ Derece

Kullanarak sıralama [fikir birliği bilgisayarı](https://github.com/serejandmyself/cyber/blob/master/cyber.md#the-notion-of-a-consensus-computer) fikir birliği bilgisayarlarının ciddi kaynak kısıtlamaları olduğu için zor olabilir. İlk olarak kendimize sormalıyız: neden sıralamayı zincir üzerinde hesaplamalı ve saklamalı ve aynı şekilde takip etmemeliyiz? [Koloni](https://ipfs.io/ipfs/QmZo7eY5UdJYotf3Z9GNVBGLjkCnE1j2fMdW2PgGCmvGPj) veya[Truebit](https://ipfs.io/ipfs/QmTrxXp2xhB2zWGxhNoLgsztevqKLwpy5HwKjLjzFa7rnD)?

Rütbe bir [fikir birliği bilgisayarı](https://github.com/serejandmyself/cyber/blob/master/cyber.md#the-notion-of-a-consensus-computer) bu sıralamanın içerik dağıtımına kolay erişim ve [kanıtlanabilir uygulamalar oluşturmak](https://github.com/serejandmyself/cyber/blob/master/cyber.md#apps) bu rütbenin üstünde. Dolayısıyla daha kozmik bir mimari izlemeye karar verdik. Bir sonraki bölümde, [alaka düzeyi kanıtı](https://github.com/serejandmyself/cyber/blob/master/cyber.md#proof-of-relevance) ağın etki alanına özgü yardımıyla ölçeklendirilmesini sağlayan mekanizma [uygunluk makineleri](https://github.com/serejandmyself/cyber/blob/master/cyber.md#relevance-machine). IBC protokolü sayesinde aynı anda çalışırlar.

Sonunda, [uygunluk makineleri](https://github.com/serejandmyself/cyber/blob/master/cyber.md#relevance-machine) (1) sürekli olarak eklenen bir ağda rütbenin hesaplanmasına izin verecek olan deterministik bir algoritma elde etmek gerekir, bu da kendisi, benzerlerinin büyüklüğüne göre ölçeklenebilir [Google](https://google.com/). Ayrıca, mükemmel bir algoritma (2) doğrusal belleğe ve hesaplama karmaşıklığına sahip olmalıdır. En önemlisi, (3) ilgili varlığı için kanıtlanabilir en yüksek tahmin yeteneklerine sahip olmalıdır[cyberlinks](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyberlinks).

Sonra[ayrıntılı araştırma](https://ipfs.io/ipfs/QmTJPJ55ePgR2MS1HoAtyqS1mteVLXUjAS4H8W97EEopxC), gümüş mermi almanın imkansız olduğunu bulduk. Bu nedenle, ağı önyükleyebilen daha temel, kurşun geçirmez bir yol bulmaya karar verdik: [mevki, makam, rütbe](http://ipfs.io/ipfs/QmbuE2Pfcsiji1g9kzmmsCnptqPEn3BuN3BhnZHrPVsiVw) Larry ve Sergey'in önceki ağlarına önyükleme yaparlardı. Orijinal PageRank ile ilgili temel sorun, sybil saldırılarına karşı dayanıklı olmamasıdır. Bununla birlikte, bir token ağırlıklı bant genişliği modeliyle sınırlanan bir token ağırlıklı PageRank, naif PageRank'in temel sorununu miras almaz, çünkü - sybil saldırılarına karşı dayanıklıdır. Şimdilik, daha uygun bir şey ortaya çıkana kadar siber ~ Rank olarak adlandıracağız. Genesis'te uygulanmasında aşağıdaki algoritma uygulanır:

[![img](https://github.com/serejandmyself/cyber/raw/master/images/algo2.png)](https://github.com/serejandmyself/cyber/blob/master/images/algo2.png)

Sıralama mekanizmasının daima kırmızı bir ringa balığı olarak kalacağını biliyoruz. Bu nedenle, belirli bir zamanda en uygun mekanizmayı tanımlayabilen zincirleme yönetişim araçlarına güvenmeyi umuyoruz. Ağın, sadece öznel görüşlere değil, aynı zamanda alana özgü 'sert kaşıklama' ile ekonomik a / b testine dayanarak bir algoritmadan diğerine geçebileceğini düşünüyoruz. [uygunluk makineleri](https://github.com/serejandmyself/cyber/blob/master/cyber.md#relevance-machine).

cyBer ~ Rank, büyük önem taşıyan iki tasarım kararını korur: (1) acentelerin mevcut niyetini açıklar ve (2) [cyberlinks](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyberlinks). İlk özellik, siber ~ Rank'ın oynanamayacağını garanti eder. Bir temsilci transfer etmeye karar verirse [CYB](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyb) belirteçleri hesabından [uygunluk makineleri](https://github.com/serejandmyself/cyber/blob/master/cyber.md#relevance-machine) ayarlayacaktır [cyberlinks](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyberlinks) acentenin mevcut niyetleri uyarınca bu hesap için geçerlidir. Ve bunun tersi, eğer bir ajan transfer ederse [CYB](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyb) kendi hesabına[cyberlinks](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyberlinks) bu hesaptan gönderilenler derhal daha fazla önem kazanacaktır. İkinci özellik, geçmişte çimentolanmamak için esastır. Yeni gibi [cyberlinks](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyberlinks) sürekli eklenirse, mevcut bağlantıların sırasını orantılı olarak seyreltirler. Bu özellik, yeni ve daha iyi içeriğin yalnızca kısa süre önce gönderildiği için daha düşük bir sıraya sahip olduğu bir durumu engeller. Bu kararların, son zamanlarda eklenen içeriğin uzun kuyruğuna çıkarım kalitesi sağlamasını bekliyoruz. [bilgi grafiği](https://github.com/serejandmyself/cyber/blob/master/cyber.md#knowledge-graph).

Oy satın alma sorununu tartışmak isteriz. Bir olay olarak oy satın almak o kadar da kötü değil. Oy satın alımlı ikilemler, oylamanın o sistem enflasyonunun tahsisini etkilediği sistemlerde ortaya çıkar. Örneğin, [Steem](http://ipfs.io/ipfs/QmepU77tqMAHHuiSASUvUnu8f8ENuPF2Kfs97WjLn8vAS3) veya herhangi bir fiat-durumu tabanlı sistem. Oy satın almak, sıfır toplamlı bir oyun kullanan bir rakip için değer katmaya gerek kalmadan kolayca karlı olabilir. Merkezi olmayan bir arama konusundaki orijinal fikrimiz bu yaklaşıma dayanıyordu. Ancak, bu fikri reddettik, [bilgi grafiği](https://github.com/serejandmyself/cyber/blob/master/cyber.md#knowledge-graph) fikir birliği düzeyinde. Her katılımcının tahmin modelini etkilemek için sisteme bir miktar değer katması gereken ortamda oy satın almak NP zor bir sorun haline gelir. Bu nedenle sisteme faydalı olur.

Mevcut uygulama [uygunluk makinesi](https://github.com/serejandmyself/cyber/blob/master/cyber.md#relevance-machine) sıralamayı hesaplamak için GPU'ları kullanır. Makine, 64 baytlık bir CID alanında herhangi bir arama isteği için ilgili sonuçları yanıtlayabilir ve sunabilir. Ancak, etki alanına özgü bir ağ oluşturmak yeterli değildir [uygunluk makinesi](https://github.com/serejandmyself/cyber/blob/master/cyber.md#relevance-machine). [fikir birliği bilgisayarı](https://github.com/serejandmyself/cyber/blob/master/cyber.md#the-notion-of-a-consensus-computer) birbiriyle ilişkisini kanıtlama yeteneğine sahip olmalıdır.

## Alaka kanıtı

Ağı, arama ile ilgili olarak, kötü niyetli davranış gibi bir şeyin olmadığı varsayımı altında tasarladık. Bu, cevapları bulmak amacıyla hiçbir kötü niyetli davranış bulunmadığı için varsayılabilir. Bu yaklaşım tüm yüzey saldırılarını önemli ölçüde azaltır.

```
Ranks are computed based on the fact that something was searched, thus linked, and as a result - affected the predictive model
```

Gözlemin kendisinin davranışı etkilediği kuantum mekaniğinde iyi bir analoji gözlemlenir. Bu yüzden olumsuz oylama gibi bir şeye ihtiyacımız yok. Bunu yaparak, öznelliği protokol dışına çıkarırız ve uygunluk kanıtını tanımlayabiliriz.

[![img](https://github.com/serejandmyself/cyber/raw/master/images/graph-tree.png)](https://github.com/serejandmyself/cyber/blob/master/images/graph-tree.png)

Her yeni CID bir sıra numarası alır. Numaralandırma sıfır ile başlar. Daha sonra her yeni CID için bir artırılır. Bu nedenle, sıralamayı tek boyutlu bir dizide saklayabiliriz, burada indeksler CID sıra numaralarıdır. Merkle ağacı hesaplamaları [RFC-6962 standard](https://ipfs.io/ipfs/QmZpJLmc3T2L1FLUxzvU3P8MBCPe15fEmUyVS7Bz8ZKMhG). Merkle ağaçlarını kullanarak, herhangi bir içerik adresi için rütbeyi etkili bir şekilde kanıtlayabiliriz. Alaka düzeyi hala doğası gereği öznel olsa da, bir şeyin belirli bir toplulukla belirli bir zamanda alakalı olduğunu gösteren ortak bir kanıtımız vardır.

Bu tür kanıtları herhangi bir ikisini kullanarak [IBC uyumlu](https://ipfs.io/ipfs/QmSGbrGAPZtR6Q1jHHe8mmS3bLBehKmfp9ZYvrg5ycaZuk) [consensus computers](https://github.com/serejandmyself/cyber/blob/master/cyber.md#the-notion-of-a-consensus-computer) birbiriyle ilişkisini kanıtlayabilir. Bu, etki alanına özgü [uygunluk makineleri](https://github.com/serejandmyself/cyber/blob/master/cyber.md#relevance-machine) gelişebilir.

Ortak bir kişi için [Go-siber](https://github.com/cybercongress/go-cyber) Merkle ağacı her turda hesaplanır ve kök karması ABCI'ye bağlıdır.

## hız

Kullanıcılara geleneksel bir web uygulaması hissi vermek için anında onay zamanına ihtiyacımız var. Bu, ekonomik topolojiyi ve teknolojinin ölçeklenebilirliğini şekillendiren güçlü bir mimari gereksinimdir.[Siber](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyber-protocol) protokol. Önerilen blockchain tasarımı, [Hassas fikir birliği](https://ipfs.io/ipfs/QmaMtD7xDgghqgjN62zWZ5TBGFiEjGQtuZBjJ9sMh816KJ) 146 doğrulayıcı ile algoritma ve hızlı, 5 saniye tx sonlandırma zamanı vardır. Ortalama onay süresi 1 saniyeye daha yakındır ve karmaşık blockchain etkileşimlerini ajanlar için neredeyse görünmez hale getirebilir.

Belirli bir şeyi belirtiyoruz [Go-siber](https://github.com/cybercongress/go-cyber) hız sıralı hesaplama bağlamında mülkiyet. Fikir birliğinin bir parçası olarak, mermi içindeki işlem validasyonuna paralel olarak gerçekleşir. Tur, paydaşlar tarafından tanımlanan bir konsensüs değişkenidir. Başlangıçta bir tur 20 bloğa ayarlanır. Pratik olarak, bu, ağın her 100 saniyede bir [bilgi grafiği](https://github.com/serejandmyself/cyber/blob/master/cyber.md#knowledge-graph). Bu demektir ki her [cyberlink](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyberlinks) gönderilen [bilgi grafiği](https://github.com/serejandmyself/cyber/blob/master/cyber.md#knowledge-graph) neredeyse anında ve ortalama 50 saniye içinde bir rütbe kazanır. İlk günlerinde [Google](https://google.com/) rütbe kabaca her hafta yeniden hesaplandı. Büyük Web ustalarının sıralama değişikliklerini gerçek zamanlı olarak gözlemlemekten memnuniyet duyacağına inanıyoruz, ancak bu pencerenin yeterli olduğu varsayımıyla ağı başlatmaya karar verdik. Beklentilerin gelişmesiyle birlikte [Siber](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyber-protocol) protokol her turun hızı azalacaktır. Bunun nedeni kahramanlar arasındaki rekabettir. Bu işlev büyüklük sırasını daha hızlı hale getirmek için bazı mekanizmaların farkındayız:

- fikir birliği parametrelerinin optimizasyonu
- rütbe hesaplamasının daha iyi paralelleştirilmesi
- bir[daha iyi saat](https://ipfs.io/ipfs/QmbsKzizZVVVzPbZvg1qSsNMkwmA3MFufgXb3MFqbSnmPs) fikir birliği öncesinde

## Ölçeklenebilirlik

Bu fikri, [Google](https://google.com/). Varsayalım ki, bu düğüm uygulaması, [Cosmos-SDK](https://github.com/cosmos/cosmos-sdk) saniyede 10 bin işlem gerçekleştirebilir. Bu demek oluyor ki, her gün en az 8.64 milyon usta 100 [cyberlinks](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyberlinks) ve arama sonuçlarını aynı anda etkiler. Bu, vahşi ortamdaki tüm varsayımları doğrulamak için yeterlidir, ancak İnternet'in mevcut ölçeğinde çalışacağını söylemek için yeterli değildir. Ekibimiz tarafından yapılan son teknoloji araştırmaları göz önüne alındığında, belirli bir blok zincirinin ihtiyacımız olan boyuta ölçeklenmesine izin verecek bir fikir birliği teknolojisinin mevcut olmadığını güvenle söyleyebiliriz. Bu nedenle, etki alanına özgü kavramını sunuyoruz [bilgi grafiği](https://github.com/serejandmyself/cyber/blob/master/cyber.md#knowledge-graph).

[![img](https://github.com/serejandmyself/cyber/raw/master/images/network.png)](https://github.com/serejandmyself/cyber/blob/master/images/network.png)

Biri kendi etki alanına özgü bir arama motoru çalıştırabilir [Go-siber](https://github.com/cybercongress/go-cyber), \ textit {ortak kamu bilgisi} üzerine odaklanmıştır. Veya basitçe takın [Go-siber](https://github.com/cybercongress/go-cyber) mevcut bir zincire bir modül olarak, ör. Cosmos Merkezi. Bloklar arası iletişim protokolü arasında durum senkronizasyonu için eşzamanlı mekanizmalar sunar [uygunluk makineleri](https://github.com/serejandmyself/cyber/blob/master/cyber.md#relevance-machine). Bu nedenle, önerilen arama mimarisinde, alana özgü [uygunluk makineleri](https://github.com/serejandmyself/cyber/blob/master/cyber.md#relevance-machine) ortak bilgiden öğrenebilecektir. Ortak bilginin etki alanına özgüden öğrenebileceği gibi [uygunluk makineleri](https://github.com/serejandmyself/cyber/blob/master/cyber.md#relevance-machine).

## Browzers

Önerilen ağın bir web3 tarayıcısıyla nasıl çalışacağını hayal etmeyi istedik. Bizim hayal kırıklığımız için [başaramadı](https://github.com/cybercongress/cyb/blob/master/docs/comparison.md) önerilen yaklaşımın serinliğini sergileyen bir web3 tarayıcısı bulmak için. Bu yüzden sıfırdan bir web3 tarayıcısı geliştirmeye karar verdik. [Cyb](https://cyb.ai/) bir örneği olan arkadaş canlısı robotunuz [.Siber](https://cyber.page/) ile etkileşim için başvuru [Siber](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyber-protocol) protokol.

[![img](https://github.com/serejandmyself/cyber/raw/master/images/cyb.jpg)](https://github.com/serejandmyself/cyber/blob/master/images/cyb.jpg)

İyi bir teslimat örneği olarak, [cyber.page](https://cyber.page/). Kahramanların, ustaların ve evangelistlerin bir web2 ağ geçidi üzerinden protokolle etkileşime girmesini sağlar. Siber bağlantılar oluşturun, içeriği doğrudan IPFS'ye sabitleyin, Büyük Web'de arama yapın, siber yönetişime katılın vb. Ayrıca derin bir kaşif, bir cüzdan gibi davranabilir ve Ledger cihazları gibi donanım cüzdanlarını cep haline getirebilir.

Geçerli arama snippet'leri çirkin. Ancak, bunları kullanarak kolayca genişletilebileceğini varsayıyoruz. [IPLD](https://github.com/ipld/specs) farklı içerik türleri için. Sonunda, daha çekici hale gelebilirler. [Google](https://google.com/).

[![img](https://github.com/serejandmyself/cyber/raw/master/images/architecture.png)](https://github.com/serejandmyself/cyber/blob/master/images/architecture.png)

Önerilen mimarinin uygulanması sırasında, en az 3 temel fayda sağladık.[Google](https://google.com/) muhtemelen geleneksel yaklaşımıyla bunu yapamazdı:

- arama sonuçları herhangi bir p2p ağından kolayca iletilebilir: ör. .cyber videoları oynatabilir
- ödeme düğmeleri doğrudan arama snippet'lerine eklenebilir. Bu, aracıların arama sonuçlarıyla, ör. ajanlar .cyber içinde bir ürün satın alabilirsiniz. Bu, kanıtlanabilir bir dönüşüm ilişkilendirmesi sayesinde e-ticaretin oldukça gelişebileceği anlamına gelir
- arama snippet'lerinin statik olması gerekmez, ancak etkileşimli olabilir. Örneğin. .cyber mevcut cüzdan bakiyenizi sağlayabilir

## yayılma

Teknik sınırlamalar nedeniyle, ekosistemi 2 jeton kullanarak başlatmamız gerekiyor: [THC](https://github.com/serejandmyself/cyber/blob/master/cyber.md#thc) ve[CYB](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyb)

- [CYB](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyb) egemenliğin yerel belirteci [Siber](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyber-protocol) Tendermint konsensüs algoritması tarafından desteklenen protokol. 3 ana kullanımı vardır: (1) fikir birliği için bahis, (2) gönderme için bant genişliği sınırlaması [cyberlinks](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyberlinks), ve (3) siber ~ Rank'ın hesaplanması için ustaların iradesinin ifade edilmesi.
- [THC](https://github.com/serejandmyself/cyber/blob/master/cyber.md#thc) (teknoloji olarak telaffuz edilir) yaratıcı bir siber proto maddedir. [THC](https://github.com/serejandmyself/cyber/blob/master/cyber.md#thc) siber ~ Vakıf (DAO'yu yöneten topluluk) ve dağıtım oyunundan ETH üzerinde kontrol şeklinde fayda değeri olan Ethereum ERC-20 uyumlu bir token. [THC](https://github.com/serejandmyself/cyber/blob/master/cyber.md#thc) bir Aragon kuruluşu olarak siber Kuruluşun oluşturulması sırasında yayılır. Yaratıcı güçleri [THC](https://github.com/serejandmyself/cyber/blob/master/cyber.md#thc) almak için yeteneği gelen 1 [CYB](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyb) her biri için jeton 1 [THC](https://github.com/serejandmyself/cyber/blob/master/cyber.md#thc) siber sondan önce verildiğinde jeton ~ Müzayede.

Her iki simge de işlevsel kalır ve doğası gereği çok farklı kullanımları nedeniyle değeri birbirinden bağımsız olarak izler.

Genel olarak, dağıtım işlemi aşağıdaki yapıya sahiptir:

1. cyber ~ Kongre Linkler Oyunu dağıtıyor
2. Topluluk, Bağlantılar Oyununa katılıyor
3. Topluluk, Bağlantılar Oyunundan elde edilen sonuçları içeren bir Genesis bloğunu doğrular ve önerir
4. cyber ~ Kongre siber sözleşmeler devreye ~ Vakıf ve siber ~ Müzayede
5. Topluluk Genesis'ten sonra siber müzayedeye katılır. Bağışçılar hissesi [THC](https://github.com/serejandmyself/cyber/blob/master/cyber.md#thc) almak için jetonlar [CYB](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyb) belirteçleri
6. siber ~ Kongre dağıtıyor [CYB](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyb) siber sırasında sürekli tokenler ~ Müzayede
7. cyber ~ Kongre kalanları yakar [CYB](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyb) ve [THC](https://github.com/serejandmyself/cyber/blob/master/cyber.md#thc) İlk dağıtım sürecinin sonundaki jetonlar ve raporlar

cyber ~ Kongre Ethereum'da [Aragon DAO](https://mainnet.aragon.org/#/cybercongress/0x4feb2bcc5907e7779130c093eef8fb44502c1330). Ayrıca bir [Siber ağda 2'den 3 çoklu görüntüleme](https://cyber.page/network/cyber/contract/cyber1latzme6xf6s8tsrymuu6laf2ks2humqvdq39v8). siber ~ Kongre [Siber](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyber-protocol) protokol. Siber bağlamda, Kongre'nin 2 rolü vardır:

1. Otomatikleştirmek imkansız olan ilk dağıtım programını dağıtmak ve yürütmek. ETH ve ATOM arasında mesaj değişimi için güvenilir bir altyapı olmadığı için, siber Kongre ilk dağıtım sürecinde tek bir başarısızlık noktası ortaya koymaktadır. Göndermeye karar verdik [CYB](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyb) belirteçleri [THC](https://github.com/serejandmyself/cyber/blob/master/cyber.md#thc) manuel olarak zımbalar çünkü yarattığımız ağı başlatmak için doğru zaman olduğunu düşünüyoruz. Ayrıca, devam eden bir açık artırmanın ilk dağıtım süreci için hayati olduğuna inanıyoruz. Siber ~ Kongre herhangi bir olası nedenden ötürü dağıtım açısından yükümlülüklerini yerine getiremezse, topluluğun ağı kesip dağıtabileceğini umuyoruz [CYB](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyb) söz verildiği gibi jetonlar. Umarım, her işlem kanıtlanabilir ve şeffaf bir şekilde tasarlanmıştır. Tüm işlemler bir [Siber ağda özel amaçlı 2'li 3 çoklu hesap](https://cyber.page/network/cyber/contract/cyber147drnke9676972jr3anklkj7pzgwjw47cp2u7j).
2. Büyümesini desteklemek [Siber](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyber-protocol) toplum siber ~ Vakıf şeklinde gelişimi ele geçirene kadar protokol. Bağlantı Oyunu sırasında ATOM'lara yapılan bağışlar [siber ~ Kongre Cosmos 2/3 multisig](https://www.mintscan.io/account/cosmos1latzme6xf6s8tsrymuu6laf2ks2humqv2tkd9a). Siber Kongre çoklu oturumuna yönlendirilen tüm ATOM bağışları mülkiyeti haline gelecektir. ATOM bağışının rolü şöyledir: ATOM sayesinde, hem Cosmos hem de Cyber ekosistemlerinin geliştirilmesinde siber Kongre'ye bağlı kalmak istiyoruz. ATOM bağışları siber ~ Kongre'nin ödüllendirmeyi kullanmasına ve sürdürülebilir bir akışa ulaşmasına izin verecektir. [Siber](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyber-protocol) hiçbirini boşaltmaya gerek kalmadan protokol[CYB](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyb) ne de ATOM belirteçleri.

## CYB

Tehlike kanıtı sistemleri ilk dağıtımda yardımcı olmaz. İlk dağıtımın amaçlı, enerji tasarruflu, kanıtlanabilir ve şeffaf bir şekilde tasarlanması, dolayısıyla erişilebilir olması, [bilgi grafiği](https://github.com/serejandmyself/cyber/blob/master/cyber.md#knowledge-graph) kalite ve boyut kazanacaktır.

Siber protokolün genesis bloğu aşağıdaki gibi parçalanmış 1000 000 000 000 000 CYB (bir petacyb veya 1 PCYB) jetonu içerir:

- 750 000 000 000 000 CYB belirteçlerie [THC](https://github.com/serejandmyself/cyber/blob/master/cyber.md#thc) siber sonuna kadar belirteçler ~ Müzayede (siber katılımcılar ~ Kongre, ETH ve Siber Taht Oyunları ~ Müzayede)
- Linkler Oyunu katılımcıları için 150 000 000 000 000 CYB jetonu
- 100000 000 000 000 Ethereum, Cosmos ve Urbit toplulukları için bir hediye olarak CYB belirteçleri

[![img](https://github.com/serejandmyself/cyber/raw/master/images/CYB.svg?sanitize=true)](https://github.com/serejandmyself/cyber/blob/master/images/CYB.svg)

Genesis'ten sonra CYB jetonları yalnızca bahis ve kısaltma parametrelerine dayanan kahramanlar tarafından oluşturulabilir. Temel fikir birliği, yeni oluşturulan CYB tokenlerinin paydaşların emrinde olmasıdır.

Şu anda maksimum miktarda CYB jetonu diye bir şey yoktur. Bu, ağın kahramanlarına sürekli enflasyonun ödenmesinden kaynaklanmaktadır. CYB jetonu uint64 kullanılarak uygulanır, bu nedenle ek CYB jetonlarının oluşturulması durum değişikliklerini ve sıralamasını hesaplamayı önemli ölçüde daha pahalı hale getirir. CYB tokenlerinin tamamen ilk dağıtımından ve akıllı sözleşmelerin işlevselliğinin etkinleştirilmesinden sonra yönetişim sistemi tarafından yaşam boyu bir parasal strateji oluşturulmasını bekliyoruz. Enflasyonun başlangıç parametreleri, Bağlantılar Oyunu sırasında yönetişim yoluyla tanımlanacaktır.

## THC

Bir alternatif oluşturmak amacı [Google benzeri](https://google.com/) yapı, çeşitli gruplardan olağanüstü çaba gerektirir. Bu nedenle, Aragon DAO gibi merkezi olmayan bir motorla yönetilen bir siber ~ Vakıf fonu kurmaya karar verdik. ETH ile ücretlendirilir ve ilk dağıtıma katılan acenteler tarafından yönetilir. Bu yaklaşım, yerel platform jetonunun aşırı piyasa dökümünden korunmaya izin verecektir - [CYB](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyb) çalışmalarının ilk yıllarında, böylece istikrarlı bir gelişme sağlamak. Ek olarak, bu, böyle bir ihtiyaç ortaya çıktığında, temel platformu çeşitlendirmeye ve protokolü diğer konsensüs hesaplama mimarilerine genişletmeye izin verir.

Bağış için jeton seçerken, üç ana kriteri takip ettik: token (1) en likitlerden biri, (2) en umut verici olmalı, böylece bir topluluk bu tür devlerle karşılaştırıldığında bile sağlam bir yatırım çantasının rekabetçi olmasını sağlayabilir. sevmek [Google](https://google.com/), ve (3) herhangi bir üçüncü tarafa dayanmadan bir açık artırma ve sonuçta ortaya çıkan bir organizasyonu yürütmek için teknik kabiliyete sahip olma. Bu kriterlere uyan tek sistem Ethereum'dur, dolayısıyla bağışların birincil belirteci ETH olacaktır.

Genesis siber ~ Vakıf önce 750 000 000 000 000 THC (yedi yüz elli terathc) aşağıdaki gibi parçaladı:

- Siber ~ Müzayede sözleşmesine 600 000 000 000 000 THC jeton tahsis edilmiştir
- Siber ~ Kongre sözleşmesine 150 000 000 000 000 THC jetonu ayrılmıştır

[![img](https://github.com/serejandmyself/cyber/raw/master/images/THC.svg?sanitize=true)](https://github.com/serejandmyself/cyber/blob/master/images/THC.svg)

Siber Vakfı tarafından alınan tüm kararlar, THC oylarının sonuçlarına göre yürütülecektir. Aşağıdaki parametreler uygulanacaktır:

- Destek:% 51
- Çekirdek: 51%
- Oy süresi: 500 saat

## Hediye

Önerilen yaklaşımı olabildiğince çok temsilciye değerlendirme yeteneği vermek istiyoruz. Ancak, KYC ve / veya captcha gibi karmaşıklık eklemeden. Bu yüzden% 8 hediye etmeyi seçtik [CYB](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyb) tokenlerinin% 8'ini, Ethereum'a% 1'ini, Cosmos'a% 1'ini ve% 1'ini hediye etmeyi seçtik Urbit topluluklarına. Genesis'i yeniden üretmek için aşağıdaki kurallar uygulanır:

- Ethereum vakıf ağındaki her hesap, sözleşme olmayan en az 1 giden işlemle ve 8080808 bloğunda> 0.001 ETH tutarında
- 2000000 bloğunda Cosmos hub-3 içindeki sıfır olmayan her hesap
- Nesne sayısına göre 10677601 bloğunda gökada (% 30), yıldız (% 30) veya gezegen (% 40) bulunan her hesap

Bu hediyenin temel amacı Genesis her hesap en az yapabilmek için 1 [cyberlink](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyberlinks) 24 saat içinde ağ boşaltıldığında. Bu yüzden dağıtım eğrisini biraz daha eşit hale getirmeye ve radikal olarak ikinci dereceden bir eğriye değiştirmeye karar verdik. Bu nedenle, [CYB](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyb) anlık görüntüler sırasında her hesap bakiyesinin karekökü ile orantılı olarak belirteçler. İkinci dereceden bir tasarımın oynaması çok kolay olduğundan, dağıtılan miktarını hesapladık [CYB](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyb) bu gerçek halka açıklanmadan önce önerilen bloklar için jetonlar. İkinci dereceden kuralı Urbit uzaylılarına uygulamıyoruz.

## Linkler Oyunu

ATOM Cosmos hodlers için bir oyun. Katılımcılar CYB karşılığında ATOM bağışında bulunuyorlar. ATOM ne kadar çok bağışlanırsa, CYB fiyatı o kadar yüksek olur. Oyun 1 GCYB başına 1 ATOM'dan başlar. Kalkış bağışlarının başlamasından bu yana 146 gün geçtiğinde veya fiyat başlangıç fiyatından 5 kat arttığında oyun sona erer. Fiyatı [CYB](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyb) Kalkış sırasında aşağıdaki fonksiyon tarafından tanımlanır:

f(c) = 40 * c + 1000

f (c) ATOM'daki TCYB fiyatı ise, c Kalkış sırasında kazanılan TCYB jetonlarının miktarıdır.

Ana fikir şudur: Kalkış bağış turu ne kadar iyi olursa, disiplinlerdeki katılımcıların ödemesi o kadar fazla olur. 100 [TCYB](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyb) Kalkış bağışlarının katılımcılarına tahsis edilir ve 50 [TCYB](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyb) Bağlantılar Oyunu disiplinlerinin katılımcıları için ayrılmıştır. Herşey [CYB](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyb) Kalkıştan kalan jetonlar, oyunun sonunda topluluk havuzuna tahsis edilir. Herşey [CYB](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyb) disiplinlerden kalan jetonlar siber Kongreye tahsis edilir. CYB tokenlerine ek olarak, Game of Links, final için tüm Kalkış donörlerine test EUL tokenlerini tahsis eder. A [ayrıntılı belge](https://cybercongress.ai/game-of-links/) oyun için kurallar ve hükümler ile yayınlanmıştır.



## Cyber ~ Müzayede

ETH'de Ethereum hodlers için bir oyun. Katılımcılar THC karşılığında ETH bağışında bulunurlar. ETH ne kadar çok bağışlanırsa, THC'nin fiyatı o kadar yüksek olur. Oyun ETH'deki Kalkışın 5 katı kapanış fiyatıyla başlıyor. Başlangıcından bu yana 888 gün geçtiğinde veya fiyat başlangıç fiyatından 5 kat arttığında oyun sona erer. Bu aşamada [CYB](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyb) jetonlar siber ~ Kongre tarafından sürekli olarak dağıtılır[THC](https://github.com/serejandmyself/cyber/blob/master/cyber.md#thc) açık artırmanın sonuna kadar jetonlar. kazanılmış [THC](https://github.com/serejandmyself/cyber/blob/master/cyber.md#thc) jetonlar alma yeteneği sağlar [CYB](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyb) buna göre jetonlar ve siber Vakıf içindeki oy yetkileri. Fiyatı [THC](https://github.com/serejandmyself/cyber/blob/master/cyber.md#thc) Cyber ~ Auction sırasında aşağıdaki fonksiyon ile tanımlanır:

g(t)= 1/30 * t * p + 5 * p

burada g (t) ETH'de TTHC fiyatı, t siber ~ Açık Artırma sırasında kazanılan TTHC jetonlarının miktarıdır, p kapanış anında ETH'ye dönüştürülen bir CYB için Kalkış fiyatının sonucudur.

Başlangıç fiyatı, Kalkış katılımcılarına Genesis'ten önce donanım ve yazılım altyapısına yatırım yapma riskleri için 5 kat prim verecek şekilde tasarlanmıştır. cyber ~ Auction erken katılımcılar için önemli teşvikler verir. Dağıtımın sona ermesinden sonra, katılımcılar [THC](https://github.com/serejandmyself/cyber/blob/master/cyber.md#thc) jetonlar ve istedikleri gibi kullanırlar, ör. açık artırma sonucunda, topluluk Aragon organizasyonu içinde bağışlanan tüm ETH'lere erişebilecek. Siber ~ Müzayede sona erdikten sonra [THC](https://github.com/serejandmyself/cyber/blob/master/cyber.md#thc) Açık artırma sözleşmesi kanıtlanabilir şekilde yakılmalıdır. Aşağıdaki kurallar geçerlidir: [CYB](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyb) altında jetonlar [dağıtım için multisig](https://cyber.page/network/cyber/contract/cyber147drnke9676972jr3anklkj7pzgwjw47cp2u7j):

- siber ~ Kongre payını devretmeyecek ve sonuç olarak dağıtılana kadar pasif bir pay olarak kalacaktır.
- siber bittikten sonra ~ Müzayede, kalan [CYB](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyb) jetonlar kanıtla yakılmalıdır

## Uygulamalar

Önerilen algoritmanın varsayılan olarak yüksek kaliteli bilgileri garanti etmediğini varsayıyoruz. Tıpkı yeni doğmuş bir bebek gibi, daha da gelişmesi için bilgi edinmesi gerekir. Protokolün kendisi sadece tek bir basit araç sağlar: [cyberlinks](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyberlinks) iki içerik adresi arasında bir aracı hissesi ile.

Semantik çekirdeğin, davranışsal faktörlerin, temsilcilerin ilgi alanlarına ilişkin anonim verilerin ve arama kalitesini belirleyen diğer araçların analizi, akıllı sözleşmeler ve zincir dışı uygulamalar ile elde edilebilir, örneğin: [web3 tarayıcılar](https://github.com/serejandmyself/cyber/blob/master/cyber.md#browzers),merkezi olmayan sosyal ağlar ve içerik platformları. İlkini inşa etmenin toplumun ve ustaların yararına olduğuna inanıyoruz. [bilgi grafiği](https://github.com/serejandmyself/cyber/blob/master/cyber.md#knowledge-graph) ve onu korumak için. Bu nedenle, grafik için en alakalı arama sonuçlarını sağlamak.

Genel olarak, üç tip başvuruyu [bilgi grafiği](https://github.com/serejandmyself/cyber/blob/master/cyber.md#knowledge-graph):

- Mutabakat uygulamaları. Kendi takdirine bağlı olarak çalıştırılabilir [fikir birliği bilgisayarı](https://github.com/serejandmyself/cyber/blob/master/cyber.md#the-notion-of-a-consensus-computer) akıllı yetenekler ekleyerek
- On-chain apps. Can be run by the [fikir birliği bilgisayarı](https://github.com/serejandmyself/cyber/blob/master/cyber.md#the-notion-of-a-consensus-computer) in exchange for gas
- Zincir dışı uygulamalar. Kullanarak uygulanabilir [bilgi grafiği](https://github.com/serejandmyself/cyber/blob/master/cyber.md#knowledge-graph) yürütme ortamında girdi olarak

Aşağıdaki, akla gelebilecek uygulama listesi, yukarıda belirtilen kategorileri birleştirir:

Web3 tarayıcıları. Gerçekte, tarayıcı ve arama birbirinden ayrılamaz. Web2 aramasına dayanan tam gelişmiş bir web3 tarayıcısının ortaya çıktığını hayal etmek zor. Şu anda, blok zincirleri ve dağıtılmış teknoloji etrafında tarayıcılar geliştirmek için birkaç çaba var. Bunların arasında Beher, Sis, Cesur ve Metamask var. Hepsi web2'yi web3'e gömmeye çalışıyor. Yaklaşımımız biraz farklı. Web2'yi web3 için güvenli olmayan bir alt küme olarak kabul ediyoruz. Bu yüzden, deneysel bir web3 tarayıcısı olan Cyb'i[Siber](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyber-protocol) sorguları daha iyi yanıtlamaya ve içeriği daha hızlı iletmeye yönelik yaklaşım.

Sosyal ağlar. Sosyal ağlar o kadar gizemli değil. Herhangi bir sosyal ağda içerik kraldır. Bu nedenle, kanıtlanabilir sıralama, herhangi bir sosyal ağın temel yapı taşıdır. Tüm sosyal ağ türleri kolayca bir ağ üzerine kurulabilir [bilgi grafiği](https://github.com/serejandmyself/cyber/blob/master/cyber.md#knowledge-graph). Sosyal ağlar da mevcutturbilir.

Programlanabilir anlambilim. Şu anda, devasa semantik çekirdeğin en popüler anahtar kelimeleri [Google](https://google.com/) aşağıdaki gibi uygulamaların anahtar kelimeleridir: [Youtube](https://youtube.com/), [Facebook](https://facebook.com/), [GitHub](https://github.com/), Ancak, bu başarılı uygulamaların geliştiricileri, [Google](https://google.com/) arama sonuçlarının nasıl daha iyi yapılandırılacağı. [Siber](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyber-protocol) yaklaşımı bu gücü geliştiricilere geri verir. Geliştiriciler artık belirli semantik çekirdekleri hedefleyebilir ve uygulamalarını istedikleri gibi dizine ekleyebilir.

Arama işlemleri. Önerilen tasarım, blockchain (ve birbirine benzer) varlıklarla ilgili faaliyetler için yerel destek sağlar. (1) içerik oluşturucuların sahip olduğu, (2) arama sonuçlarında doğru görünen ve (3) bir arama sorgusu için dönüşümün kanıtlanabilir ilişkilendirilmesiyle işlem yapılabilir bir eyleme izin veren uygulamalar tasarlamak önemsizdir. e-Ticaret hiç bu kadar kolay olmamıştı.

Çevrimdışı arama. IPFS, global internet bağlantısı olmayan bir ortamdan kolayca belge almayı mümkün kılar. [Go-siber](https://github.com/cybercongress/go-cyber) IPFS kullanılarak dağıtılabilir. Bu, her yerde bulunan, çevrimdışı arama olanağı yaratır!

Komut araçları. Komut satırı araçları, bir arama motorunun ilgili ve yapılandırılmış yanıtlarına güvenebilir. Pratik olarak, aşağıdaki CLI aracını uygulamak mümkündür:

```
>  go-cyber earn using 100 GB

Enjoy the following predictions:
- apt install go-filecoin:     0.001   BTC p/ month p/ GB
- apt install siad:            0.0007  BTC p/ month p/ GB
- apt install storjd:          0.0005 BTC p/ month p/ GB

According to the most desirable prediction, I decided to try `mine go-filecoin -limit 107374182400`

Git clone ...
Building go-filecoin
Starting go-filecoin
Creating a wallet using @xhipster seed
Your address is ...
Placing bids ...
Waiting for incoming storage requests ...
```

CLI içinden arama araçları kaçınılmaz olarak robotlar için özel bir anlamsal çekirdeğin oldukça rekabetçi bir pazarını yaratacaktır.

Otonom robotlar. Blockchain teknolojisi, dijital varlıkları kendi başlarına yönetebilen cihazların oluşturulmasını sağlar.

```
If a robot can store, earn, spend and invest - they can do everything you can do
```

İhtiyaç duyulan şey basit, ancak belirli şeyleri bulma yeteneğine sahip güçlü bir devlet gerçeklik aracıdır. [Go-siber](https://github.com/cybercongress/go-cyber) ekonomik olarak rasyonel robotları programlamak için gerekli araçları sağlayan minimalist ancak sürekli kendini geliştiren bir veri kaynağı sunar. Göre [top-10,000 İngilizce kelimeler](https://github.com/first20hours/google-10000-english) İngilizcede en popüler kelime, belirli bir öğeye işaretçi anlamına gelen 'the' tanımlayıcı makalesidir. Bu gerçek şu şekilde açıklanabilir: belirli maddeler bizim için çok önemlidir. Bu nedenle, doğamız eşsiz şeyler bulmaktır. Bu nedenle, robotlar için de benzersiz şeylerin anlaşılması şarttır.

Dil yakınsaması. Bir programcı, bir ajanın kullanacağı dili önemsememelidir. Temsilcinin aramalarını hangi dilde yaptığını bilmemize gerek yok. UTF-8 spektrumunun tamamı iş başında. Anlamsal çekirdek açıktır, bu nedenle sorguları yanıtlamak için rekabet farklı alana özgü alanlara dağıtılabilir. Çeşitli diller için anlamsal çekirdekler dahil. Bu birleşik yaklaşım siber ~ Bahasa için bir fırsat yaratır. İnternetin başlangıcından bu yana, hızlı bir yakınsama süreci gözlemliyoruz. Vatandaşlık, dil, ırk, isim veya İnternet bağlantısından bağımsız olarak tüm gezegende gerçekten küresel kelimeler kullanıyoruz. Gerçekten küresel bir dilin hayalini kurmak zordur, çünkü ne anlama geldiğini kabul etmek zordur. Ancak, bu rüyayı gerçekleştirecek araçlara sahibiz. Bir kelime ne kadar kısa olursa, siber ~ Rank'in o kadar güçlü olacağını tahmin etmek zor değildir. Genel, halka açık semboller, kelimeler ve deyimler listesi siber olarak sıralanmıştır ~ tarafından sağlanan ilgili bir bağlantı ile sıralayın [Go-siber](https://github.com/cybercongress/go-cyber) herkesin kabul edebileceği gerçekten küresel bir dilin ortaya çıkışının temeli olabilir. Son [scientific advances](https://ipfs.io/ipfs/QmQUWBhDMfPKgFt3NfbxM1VU22oU8CRepUzGPBDtopwap1) makine çevirisinde nefes kesici ama Google ölçeğinde eğitimli bir model olmadan uygulamak isteyenler için anlamsız. Önerilen siber ~ Sıra tam olarak bunu sunar.

Kendini tahmin etme. bir [fikir birliği bilgisayarı](https://github.com/serejandmyself/cyber/blob/master/cyber.md#the-notion-of-a-consensus-computer) sürekli bir [bilgi grafiği](https://github.com/serejandmyself/cyber/blob/master/cyber.md#knowledge-graph) tek başına varlığını tahmin etmek [cyberlinks](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyberlinks) ve bu tahminleri durumuna uygulamak. Dolayısıyla, [fikir birliği bilgisayarı](https://github.com/serejandmyself/cyber/blob/master/cyber.md#the-notion-of-a-consensus-computer) ekonomik uzlaşmaya katılabilir. [Siber](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyber-protocol) protocol.

Evrensel kehanet. bir [fikir birliği bilgisayarı](https://github.com/serejandmyself/cyber/blob/master/cyber.md#the-notion-of-a-consensus-computer) en alakalı verileri bir anahtar / değer deposunda depolayabilir. Anahtar bir CID ve değerler gerçek içeriğin baytıdır. Bu, temsilcilerin hangi CID değerlerini budamak istedikleri ve hangi değerleri uygulamak istedikleri konusunda her turda bir karar vererek elde edilebilir. İçindeki içerik adreslerinin fayda ölçüsüne dayanarak [bilgi grafiği](https://github.com/serejandmyself/cyber/blob/master/cyber.md#knowledge-graph). Yardımcı program ölçüsünü hesaplamak için, kahramanlar, [bilgi grafiği](https://github.com/serejandmyself/cyber/blob/master/cyber.md#knowledge-graph), daha sonra, CID'lerin boyutuna ve derecesine göre ağırlık. Ortaya çıkan anahtar / değer çifti depolaması, [fikir birliği bilgisayarı](https://github.com/serejandmyself/cyber/blob/master/cyber.md#the-notion-of-a-consensus-computer) sadece ve ajanlar için değil. Ancak, değerler programlarda kullanılabilir.

Konuma duyarlı arama. İnşa etmek mümkündür [cyberlinks](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyberlinks) ile[Kanıt-of-Location](https://ipfs.io/ipfs/QmZYKGuLHf2h1mZrhiP2FzYsjj3tWt2LYduMCRbpgi5pKG) gibi dikkate değer mevcut protokollere dayanarak [Köpük](https://ipfs.io/ipfs/QmZYKGuLHf2h1mZrhiP2FzYsjj3tWt2LYduMCRbpgi5pKG). Sonuç olarak, web3-etmenleri nirengi yapar ve eklerse, konuma dayalı bir arama da kanıtlanabilir hale gelir [kanıtı konumu](https://ipfs.io/ipfs/QmZYKGuLHf2h1mZrhiP2FzYsjj3tWt2LYduMCRbpgi5pKG) bağlı her zincir için.

Bağlantı alaka düzeyi ile ilgili tahmin piyasaları. Bu fikri, [bilgi grafiği](https://github.com/serejandmyself/cyber/blob/master/cyber.md#knowledge-graph) bağlantı alaka düzeyine ilişkin bir tahmin piyasasına dayanmaktadır. Bağlantı alaka üzerine bahis yapılmasına izin veren bir uygulama, terimlerin yönü için benzersiz bir gerçek kaynağı olabilir ve ayrıca ajanları daha fazla bağlantı göndermeye motive edebilir.

Özel siber bağlantılar. Gizlilik esastır. Gizliliğe bağlıyken, özel uygulamaların gerçekleştirilmesi [cyberlinks](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyberlinks) Genesis'e kadar ekibimiz için mümkün değil. Bu nedenle, protokolün üstünde yürütülebilen WASM programları üzerinde çalışmak topluluğa bağlıdır. Sorun siber ~ Rank hesaplamak için,[cyberlinks](https://github.com/serejandmyself/cyber/blob/master/cyber.md#cyberlinks) web3-ustaları tarafından ne açıklama yapmadan gönderilirler: önceki istekleri veya ortak anahtarlar. Sıfır bilgi kanıtları genel olarak çok pahalıdır. Arama gizliliğinin tasarım gereği olması gerektiğine inanıyoruz, ancak bu aşamada nasıl uygulanacağını bildiğimizden emin değiliz. [Koda](https://ipfs.io/ipfs/Qmdje3AmtsfjX9edWAxo3LFhV9CTAXoUvwGR7wHJXnc2Gk) özyinelemeli Snarks gibi ve [MimbleWimble](https://ipfs.io/ipfs/Qmd99xmraYip9cVv8gRMy6Y97Bkij8qUYArGDME7CzFasg) yapılar, teorik olarak, gizlilik endişesinin bir kısmını çözebilir. Ancak, yeni, denenmemiş ve yine de, hesaplamalar açısından şeffaf alternatiflerinden daha pahalı olacaklar.

Bu kesinlikle tüm olası uygulamaların aşırı listesi değil, gerçekten çok heyecan verici bir liste.

## Sonuç

Uygunluk konusunda fikir birliği bilgisayarlar arasında kanıtlanabilir iletişim için bir protokol tanımladık ve uyguladık. Protokol, siber bağlantılar kullanılarak ajanlar tarafından üretilen basit bilgi grafikleri fikrine dayanır. Siber bağlantılar, uygunluk makinesi kavramı kullanılarak bir konsensüs bilgisayarı tarafından işlenir. Siber fikir birliği bilgisayarı CIDv0 / CIDv1'i temel alır ve temel olarak go-IPFS ve Cosmos-SDK kullanır. IPFS, kaynak tüketimi açısından önemli faydalar sağlar. Birincil nesneler olarak CID basitlikleri açısından sağlamdır. Her CID için, siber ~ Rank, tek bir hata noktası olmadan bir konsensüs bilgisayarı tarafından hesaplanır. Cyber ~ Rank, sybil saldırılarına ve bencilce oylamaya karşı ekonomik koruma sağlayan bir CYB token ağırlıklı PageRank'tır. Her tur sıra ve grafik ağaçlarının Merkle kökü yayınlanır. Sonuç olarak, her bilgisayar herhangi bir bilgisayara belirli bir CID için değerin uygunluğunu kanıtlayabilir. Sybil direnci bant genişliği sınırlamasına dayanır. Gömülü programları yürütme yeteneği ilham verici uygulamalar sunar. Başlangıçtaki birincil amaç, IPFS, Swarm, Sia, Git, BitTorrent veya durum bilgisi gibi eşler arası içerik adres sistemlerinin IPX, Ethereum ve diğer blok zincirleri ve düğümler gibi dizinlenmesidir. Siber bağlantının önerilen semantiği, fikir birliği bilgisayarının kendisi tarafından nesneler arasındaki anlamlı ilişkileri tahmin etmek için sağlam bir mekanizma sunar. Alaka makinesinin kaynak kodu açık kaynak kodludur. Mutabakat bilgisayarı tarafından toplanan her veri biti, biri onu işlemek için kaynaklara sahipse herkes tarafından kullanılabilir. Önerilen yazılım uygulamasının performansı kesintisiz etkileşim için yeterlidir. Önerilen uygulamanın ölçeklenebilirliği, günümüzde var olan ve bunları Büyük Web'in milyonlarca temsilcisine sunabilecek tüm kendini doğrulayan verileri dizine eklemek için yeterlidir. Blok zinciri, standart yönetişim modülüyle Tendermint konsensüs algoritması altında çalışan bir Süper Zeka tarafından yönetilir. Sistem, geleneksel bir arama motoru için bir alternatif sunmak için gerekli yardımcı programı sağlamasına rağmen, sadece bu kullanım durumu ile sınırlı değildir. Sistem çok sayıda uygulama için genişletilebilir ve etrafındaki nesneleri özerk bir şekilde anlayabilen ekonomik olarak rasyonel, kendine ait robotlar tasarlamayı mümkün kılar.

## Referanslar

1. [Bilimsel bağlam](https://ipfs.io/ipfs/QmNhaUrhM7KcWzFYdBeyskoNyihrpHvUEBQnaddwPZigcN)
2. [Yepyeni yığın](https://ipfs.io/ipfs/Qmf2rKkDPSsvdudwSmdDPbZuYae8XRV26c1wAFCCvg8Dhw)
3. [Uygulamada arama motorlarına bilgi alma](https://ipfs.io/ipfs/QmeS4LjoL1iMNRGuyYSx78RAtubTT2bioSGnsvoaupcHR6)
4. [Çekişmeli örnek araştırmalar için motive edici oyun](https://ipfs.io/ipfs/QmNrAFz34SLqkzhSg4wAYYJeokfJU5hBEpkT4hPRi226y9)
5. [Merkezi olmayan bir arama fikri](https://ipfs.io/ipfs/QmXNoGTWLQrcFRb66oS4HafpP1vcLKbVkJrQm4DVvihuoq)
6. [IPFS](https://ipfs.io/ipfs/QmV9tSDx9UiPeWExXEeH6aoDvmihvx6jD5eLb4jbTaKGps)
7. [DAT](https://ipfs.io/ipfs/QmXHGmfo4sjdHVW2MAxczAfs44RCpSeva2an4QvkzqYgfR)
8. [Go-siber](https://github.com/cybercongress/go-cyber)
9. [kozmos-sdk](https://github.com/cosmos/cosmos-sdk)
10. [CIDv1](https://github.com/multiformats/cid#cidv1)
11. [cyber.page](http://cyber.page/)
12. [DURA](https://github.com/cybercongress/cyb/blob/dev/docs/dura.md)
13. [Koloni](https://ipfs.io/ipfs/QmZo7eY5UdJYotf3Z9GNVBGLjkCnE1j2fMdW2PgGCmvGPj)
14. [Truebit](https://ipfs.io/ipfs/QmTrxXp2xhB2zWGxhNoLgsztevqKLwpy5HwKjLjzFa7rnD)
15. [Tahminlerin termodinamiği](https://ipfs.io/ipfs/QmP81EcuNDZHQutvdcDjbQEqiTYUzU315aYaTyrVj6gtJb)
16. [PageRank](http://ipfs.io/ipfs/QmbuE2Pfcsiji1g9kzmmsCnptqPEn3BuN3BhnZHrPVsiVw)
17. [RFC 6962](https://ipfs.io/ipfs/QmZpJLmc3T2L1FLUxzvU3P8MBCPe15fEmUyVS7Bz8ZKMhG)
18. [IBC protokolü](https://ipfs.io/ipfs/QmSGbrGAPZtR6Q1jHHe8mmS3bLBehKmfp9ZYvrg5ycaZuk)
19. [Tendermint](https://ipfs.io/ipfs/QmaMtD7xDgghqgjN62zWZ5TBGFiEjGQtuZBjJ9sMh816KJ)
20. [Web3 tarayıcılarının karşılaştırılması](https://github.com/cybercongress/cyb/blob/master/docs/comparison.md)
21. [Cyb](https://cyb.ai/)
22. [SpringRank](https://ipfs.io/ipfs/QmTJPJ55ePgR2MS1HoAtyqS1mteVLXUjAS4H8W97EEopxC)
23. [Siber protokolde doğrulayıcı çalıştır](https://cybercongress.ai/docs/go-cyber/run_validator/)
24. [En iyi 10000 İngilizce kelime](https://github.com/first20hours/google-10000-english)
25. [Çok dilli sinir makinesi çevirisi](https://ipfs.io/ipfs/QmQUWBhDMfPKgFt3NfbxM1VU22oU8CRepUzGPBDtopwap1)
26. [Köpük](https://ipfs.io/ipfs/QmZYKGuLHf2h1mZrhiP2FzYsjj3tWt2LYduMCRbpgi5pKG)
27. [Koda](https://ipfs.io/ipfs/Qmdje3AmtsfjX9edWAxo3LFhV9CTAXoUvwGR7wHJXnc2Gk)
28. [Mimblewimble](https://ipfs.io/ipfs/Qmd99xmraYip9cVv8gRMy6Y97Bkij8qUYArGDME7CzFasg)
29. [Tezos](https://ipfs.io/ipfs/QmdSQ1AGTizWjSRaVLJ8Bw9j1xi6CGLptNUcUodBwCkKNS)
30. [Yazılım 2.0](https://medium.com/@karpathy/software-2-0-a64152b37c35)
31. [Kanıt-of-tarih](https://ipfs.io/ipfs/QmbsKzizZVVVzPbZvg1qSsNMkwmA3MFufgXb3MFqbSnmPs)
32. [IPLD](https://github.com/ipld)
33. [siber ~ Kongre organizasyonu](https://mainnet.aragon.org/#/cybercongress/0x4feb2bcc5907e7779130c093eef8fb44502c1330/)
34. [cyber ~ Siber Kongresi](https://cyber.page/network/cyber/contract/cyber1latzme6xf6s8tsrymuu6laf2ks2humqvdq39v8)
35. [cyber ~ Evren Kongresi](https://www.mintscan.io/account/cosmos1latzme6xf6s8tsrymuu6laf2ks2humqv2tkd9a)
36. [CYB dağıtımı için multisig](https://cyber.page/network/cyber/contract/cyber147drnke9676972jr3anklkj7pzgwjw47cp2u7j)
37. [.Siber](https://github.com/cybercongress/dot-cyber)

## Teşekkür

1. @hleb-albau
2. @arturalbov
3. @jaekwon
4. @ebuchman
5. @npopeka
6. @belya
7. @serejandmyself

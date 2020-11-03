---
title: 密碼編譯服務
description: .NET 所支援的加密方法和作法的總覽。
ms.date: 07/14/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- cryptography [.NET]
- pattern of derived class inheritance
- digital signatures
- asymmetric cryptographic algorithms
- digital signatures, public-key systems
- public keys
- decryption [.NET]
- private keys
- MAC algorithms
- cryptographic algorithms
- private keys, overview
- encryption [.NET]
- security [.NET], encryption
- cryptographic services
- symmetric cryptographic algorithms
- hash
- message authentication codes
- derived class inheritance
- cryptography [.NET], about
- random number generation
ms.assetid: f96284bc-7b73-44b5-ac59-fac613ad09f8
ms.openlocfilehash: 463ccec5f60ff10331d501d39144a979d95eff95
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2020
ms.locfileid: "93281721"
---
# <a name="cryptographic-services"></a>密碼編譯服務

公用網路（例如網際網路）無法在兩實體之間提供一種可安全通訊的方式。 這類網路上的通訊很容易被人讀取，或是被未經授權的協力廠商所修改。 密碼編譯有助於保護資料不受人檢視，可提供一種方式來偵測資料是否已遭修改，比起其他非安全的通道，它有助提供安全的通訊方式。 比方說，可以利用密碼編譯演算法來加密資料，並以加密的狀態傳送，而稍後由指定的一方解密資料。 假使第三方攔截到加密資料，也難以破解。

在 .NET 中，命名空間中的類別 <xref:System.Security.Cryptography> 會為您管理多個密碼編譯的詳細資料。 有些是作業系統執行的包裝函式，而有些則是純粹受管理的實施。 您不用是加密專家才能使用這些類別。 當您在其中一個加密演算法類別中建立新執行個體時，會自動產生金鑰以便於使用，而且預設屬性盡可能以安全為主。

本總覽提供 .NET 所支援的加密方法和作法的概要說明，包括 ClickOnce 資訊清單。

## <a name="cryptographic-primitives"></a>密碼編譯基本類型

通常會使用密碼編譯情況是，兩方 (Alice 和 Bob) 透過不安全的通道通訊時。 Alice 和 Bob 想確保兩人間的通訊，不被可能正在接聽的任何人所理解。 不僅如此，由於 Alice 和 Bob 兩人身處遠端，Alice 必須確保在傳輸期間，她所接收到來自 Bob 的資訊未被任何人竄改。 此外，她必須確保資訊的確來自 Bob，而非假扮成他的人。

密碼編譯的用途為達成下列目標：

- 機密性：協助保護使用者的身分或資料不被他人讀取。

- 資料完整性：協助保護資料不遭人變更。

- 驗證：確保資料來自特定對象。

- 不可否認性：防止特定對象否認自己曾傳送訊息。

若要達成這些目標，您可以將演算法與稱為密碼編譯基本類型的做法搭配組合，以創造密碼編譯的配置。 下表列出密碼編譯基本類型以及它們的用法。

|密碼編譯基本類型|使用|
|-----------------------------|---------|
|私密金鑰加密 (對稱密碼編譯)|執行資料轉換，以防止第三方讀取。 這類加密使用單一共用的私密金鑰來加密和解密資料。|
|公開金鑰加密 (非對稱密碼編譯)|執行資料轉換，以防止第三方讀取。 這類加密使用公開/私密金鑰組來加密和解密資料。|
|密碼編譯簽署|可以透過專屬於該對象數位簽章，確認資料來自特定對象。 此程序也會使用雜湊函式。|
|密碼編譯雜湊|將資料從任何長度對應至固定長度的位元組序列。 雜湊是統計上唯一一種不同兩個位元組序列，而且不會出現相同值的雜湊。|

## <a name="secret-key-encryption"></a>私密金鑰加密

私密金鑰加密演算法使用單一私密金鑰來加密或解密資料。 您必須確認未經授權的代理程式無法存取金鑰，因為任何具有金鑰的一方可用它來解密您的資料或加密自己的資料，並宣告資料來自於您。

私密金鑰加密也稱為對稱式加密，因為加密和解密可用相同的金鑰。 相較於公開金鑰演算法，秘密金鑰加密演算法十分迅速，並且適用於執行大型流量資料的密碼編譯轉換。 例如 RSA 的非對稱式加密演算法，在多少資料可以加密的數學相關方面則受到限制。 對稱式加密演算法通常不具備這些問題。

一種稱為區塊編碼器的私密金鑰演算法，可用來一次加密一個資料區塊。 像是資料加密標準 (DES)、TripleDES、進階加密標準 (AES) 這類區塊編碼器，會以密碼編譯方式將 *n* 個位元組的輸入區塊轉換成加密位元組輸出區塊。 如果您想要加密或解密位元組序列，就必以區塊為單位進行。 因為 *n* 很小 (DES 和 TripleDES 為 8 個位元組；AES 為 16 個位元組 [預設值]、24 個位元組或 32 個位元組)，所以大於 *n* 的資料值必須一次以一個區塊為單位加密。 資料值小於 *n* 必須展開成 *n* 以便進行處理。

有一種簡易的區塊編碼器型式，稱為電子碼書 (ECB) 模式。 ECB 模式並不算安全，因為它不會使用初始化向量來初始化第一個純文字區塊。 對於某個指定的私密金鑰 *k* ，不使用初始化向量的簡單區塊編碼器會將同一個純文字輸入區塊加密成同一個加密文字輸出區塊。 因此，如果您的輸入純文字資料流中有重複的區塊，在輸出加密文字資料流中也會有重複區塊。 這些重複的輸出區塊會警示未經授權的使用者，可能已採用弱式加密之演算法，以及可能的攻擊模式。 因此 ECB Cipher 模式比較容易對分析，以及最終的金鑰探索受到攻擊。

在基底類別程式庫中提供的的區塊編碼器類別會使用稱為 Cipher 區塊鏈結 (CBC) 的預設鏈結模式，但是若您想變更，也可以變更此預設值。

CBC 加密使用初始化向量 (IV) 來加密純文字的第一個區塊，克服了與 ECB 加密相關的問題。 每個後續純文字區塊會經歷位元互斥，或是 (`XOR`) 在加密前與先前的加密文字區塊作業。 因此每個加密文字區塊都會與先前的所有區塊相依。 當使用此系統時，可能會讓未授權使用者知道的通用訊息標頭，不能用來在金鑰上進行反向工程。

可能危及 CBC 加密資料的一種方法是徹底搜索每種可能的金鑰。 依據用來執行加密的金鑰大小而定，即使使用最迅速的電腦，這種搜尋仍然非常耗時，因此並不可行。 較大的金鑰會更難破解。 雖然理論上加密並非可讓對手完全無法擷取加密的資料，但是它卻會增加擷取資料的成本。 如果需要花三個月的時間執行徹底搜尋，卻只擷取到在幾天內才具有意義的資料，則徹底搜尋就變得不切實際。

私密金鑰加密的缺點是，它假設兩方都已同意一個金鑰與 IV，並且通訊過其值。 IV 不算是機密，而且能用訊息以純文字傳輸。 不過，金鑰必須保持機密，不可讓未授權使用者知道。 由於這些問題，私密金鑰加密通常會與公開金鑰加密搭配使用，以利私下通訊金鑰和 IV 的值。

假設 Alice 和 Bob 是想要透過非安全通道進行通訊的兩方，它們可使用私密金鑰加密，如下所示：Alice 和 Bob 同意將特定金鑰和特定 IV 與一種特定演算法 (例如 AES) 搭配使用。 Alice 撰寫一則訊息，並建立網路串流 (可能是指要傳送訊息的具名管道或網路電子郵件) 。 接下來，她使用金鑰和 IV 將文字加密，並透過內部網路傳送加密訊息和 IV 給 Bob。 Bob 收到加密文字，並使用該 IV 和先前同意的金鑰解密文字。 如果正在攔截傳輸，攔截器無法復原原始訊息，因為它們不知道金鑰。 在此案例中，要保持機密的僅有金鑰。 在真實案例中，Alice 或 Bob 兩方都沒有產生私密金鑰，而是使用公開金鑰 (非對稱式) 加密來傳輸私密 (對稱) 金鑰至其他對象。 (如需公開金鑰加密的詳細資訊，請參閱下一節)。

.NET 提供下列可執行秘密金鑰加密演算法的類別：

- <xref:System.Security.Cryptography.Aes>

- <xref:System.Security.Cryptography.HMACSHA256>、<xref:System.Security.Cryptography.HMACSHA384> 和 <xref:System.Security.Cryptography.HMACSHA512>。  (這些都是技術上的秘密金鑰演算法，因為它們代表使用密碼編譯雜湊函式結合秘密金鑰計算而來的訊息驗證碼。 請參閱本文稍後的 [雜湊值](#hash-values)。 ) 

## <a name="public-key-encryption"></a>公開金鑰加密

公開金鑰需要使用一個需對未授權使用者保持機密的私密金鑰，以及一個可以對任何人公開的公開金鑰。 公開金鑰和私密金鑰以數學方式相連，以公開金鑰加密的資料只能用私密金鑰解密，而且以私密金鑰簽署的資料只能以公開金鑰驗證。 公開金鑰可開放給任何人；它是用來加密要傳送給私密金鑰持有者的資料。 公開金鑰密碼編譯演算法也稱為非對稱演算法，因為一個金鑰需要用來加密資料，而另一個金鑰需要用來解密資料。 基本密碼編譯規則禁止重複使用金鑰，而且每個通訊工作階段中應有專屬的兩個金鑰。 不過在實務上，非對稱金鑰通常存留較久。

兩方 (Alice 和 Bob) 可能會使用公開金鑰加密，如下所示：首先 Alice 產生公開/私密金鑰組。 如果 Bob 想要傳送 Alice 加密訊息，他會像她要求她的公開金鑰。 Alice 透過非安全的網路將公開金鑰傳送 Bob，他會使用這個金鑰來加密訊息。 Bob 將加密訊息傳送給 Alice，然後她會使用自己的私密金鑰解密。 如果 Bob 透過非安全的通道收到 Alice 的金鑰，例如在公用網路，Bob 等於開放給攔截攻擊。 因此，Bob 必須與 Alice 確認他有她的公開金鑰正確副本。

在 Alice 使用公開金鑰傳輸的過程中，未經授權的代理程式可能會攔截到此金鑰。 此外，相同的代理程式可能會從 Bob 攔截到加密訊息。 不過，代理程式無法使用公開金鑰解密訊息。 若要解密訊息，只能搭配 Alice 未傳送的私用金鑰。 Alice 並未使用她的私密金鑰來加密回覆訊息給 Bob，因為任何知道公開金鑰的人都能解密訊息。 如果 Alice 想要將訊息回傳給 Bob，她會向他要求他的公開金鑰，並用該公開金鑰加密她的訊息。 然後 Bob 會使用他相關聯的私密金鑰解密訊息。

在此案例中，Alice 和 Bob 使用公開金鑰 (非對稱) 加密来傳送私密 (對稱) 金鑰，並在工作階段的其餘部分使用私密金鑰加密。

下列清單提供公開金鑰和私密金鑰密碼編譯演算法之間的比較：

- 公開金鑰密碼編譯演算法會使用固定的緩衝區大小，而私密金鑰密碼編譯演算法使用可變長度的緩衝區。

- 公開金鑰演算法無法像私密金鑰演算法一樣，可將資料鏈結成資料流，因為只有小量資料可以被加密。 因此，非對稱作業不像對稱作業一樣，可使用相同的資料流模型。

- 公開金鑰加密與私密金鑰加密相比，有一個較大的金鑰空間 (金鑰可能值的範圍)。 因此，公開金鑰加密較不易受到徹底搜索每個可能金鑰的攻擊。

- 公開金鑰不需要受到保護，所以可輕鬆地散發，前提是有已知方法來驗證寄件者。

- 有些公開金鑰演算法 (例如 RSA 和 DSA，但非 Diffie-hellman) 可用來建立數位簽章，以驗證資料寄件者的身份識別。

- 相較於私密金鑰演算法，公開金鑰演算法速度很慢，並非設計來加密大量資料。 公開金鑰演算法只適合傳送非常少量的資料。 通常，公開金鑰加密是用來加密要使用私密金鑰演算法來加密的金鑰和 IV。 金鑰和 IV 傳送之後，其餘的工作階段會使用私密金鑰加密。

.NET 提供下列可執行公開金鑰演算法的類別：

- <xref:System.Security.Cryptography.RSA>

- <xref:System.Security.Cryptography.ECDsa>

- <xref:System.Security.Cryptography.ECDiffieHellman>

- <xref:System.Security.Cryptography.DSA>

RSA 允許加密和簽署，但 DSA 只能用來簽署。 DSA 與 RSA 並不安全，我們建議採用 RSA。 Diffie-Hellman 只能用於金鑰產生。 一般來說，公開金鑰演算法在用途上比私密金鑰演算法更受到限制。

## <a name="digital-signatures"></a>數位簽章

公開金鑰演算法也可用於形成數位簽章。 數位簽章驗證的寄件者的身份識別 (如果您信任該寄件者的公開金鑰)，並協助保護資料的完整性。 使用 Alice 所產生的公開金鑰，Alice 資料的收件者可以藉由比較 Alice 資料與其公開金鑰的數位簽章，確認傳送者為 Alice。

若要使用公開金鑰密碼編譯來數位簽署訊息，Alice 必須先在訊息中套用雜湊演算法來建立訊息摘要。 訊息摘要是資料壓縮和獨特的表示方式。 Alice 接著會使用她的私密金鑰來建立個人簽章，並加密訊息摘要。 收到訊息和簽章後，Bob 會使用 Alice 的公開金鑰來復原訊息摘要，並用與 Alice 所用的相同雜湊演算法來雜湊簽章。 如果 Bob 所計算的訊息摘要符合從 Alice 收到的訊息摘要，Bob 就可以確信訊息來自私密金鑰的擁有人，且資料未被修改。 如果 Bob 信任 Alice 就是私密金鑰的擁有人，他就知道訊息來自 Alice。

> [!NOTE]
> 任何人都可以驗證簽章，因為寄件者的公開金鑰是通用資訊，而且通常包含於數位簽章格式中。 此方法不保留訊息的機密性，對於需要保密的訊息，還是必須經過加密。

.NET 提供下列可執行數位簽章演算法的類別：

- <xref:System.Security.Cryptography.RSA>

- <xref:System.Security.Cryptography.ECDsa>

- <xref:System.Security.Cryptography.DSA>

## <a name="hash-values"></a>雜湊值

雜湊演算法會將任意長度的二進位值對應到固定長度較小的二進位值，又稱為雜湊值。 雜湊值是一段資料的數值表示法。 如果您雜湊純文字段落，但只要變更了段落中的一個字母，後續的雜湊就會產生不同的值。 如果雜湊密碼編譯的強度夠強，其值將會大幅變更。 比方說，如果變更訊息的一小部份，強式雜湊函式可能會產生相異百分之 50 的輸出。 許多輸入的值可雜湊出相同的輸出值。 不過，就運算資源而言，要找到兩個相異的輸入可雜湊處理至相同的值並不可行。

兩方 (Alice 和 Bob) 可以使用雜湊函式以確保訊息的完整性。 他們會選取雜湊演算法來簽署其訊息。 Alice 會寫入訊息，並使用所選的演算法建立該訊息的雜湊。 接著他們會遵循下列方法之一：

- Alice 傳送純文字訊息和雜湊訊息 (數位簽章) 給 Bob。 Bob 收到後雜湊該訊息，並將他從 Alice 接收到的雜湊值與自己的雜湊值相比較。 如果雜湊值完全相同，訊息未遭竄改。 如果值不相同，則 Alice 撰寫訊息後已遭修改。

  可惜這個方法無法確認寄件者的真實性。 任何人都可以模擬 Alice 並傳送訊息給 Bob。 他們可以使用相同的雜湊演算法來簽署訊息，而且 Bob 只能用符合其簽章的訊息來判斷。 這是一種攔截攻擊的形式。 如需詳細資訊，請參閱 [新一代密碼編譯 (CNG) 安全通訊範例](/previous-versions/cc488018(v=vs.100))。

- Alice 透過非安全的公用通道傳送純文字訊息給 Bob。 Alice 透過安全的私用通道傳雜湊送息給 Bob。 Bob 收到純文字訊息，然後進行雜湊，並將該雜湊與私下交換的雜湊相比。 如果雜湊相符，Bob 就知道兩件事：

  - 訊息未經更改。

  - 寄件者的訊息 (Alice) 已經過驗證。

  若要讓此系統成功運作，Alice 必須對 Bob 除外的所有對象隱藏原始雜湊值。

- Alice 透過非安全的公用通道傳送純文字訊息給 Bob，並將已雜湊的訊息放在可讓人公開檢視的網站上。

  此方法藉由防止任何人修改雜湊值來預防訊息遭到竄改。 雖然任何人都可以讀取訊息和其雜湊，但是只有 Alice 可以變更雜湊值。 若攻擊者想要模擬 Alice，就需要存取她的網站。

先前的方法中，沒有一項能防止他人讀取 Alice 的訊息，因為它們會以純文字傳送。 完整的安全性通常需有數位簽章和加密 (訊息簽章)。

.NET 提供下列類別來執行雜湊演算法：

- <xref:System.Security.Cryptography.SHA256>.

- <xref:System.Security.Cryptography.SHA384>.

- <xref:System.Security.Cryptography.SHA512>.

.NET 也提供 <xref:System.Security.Cryptography.MD5> 和 <xref:System.Security.Cryptography.SHA1> 。 但是，MD5 和 SHA-1 演算法發現不安全，現在建議改用 SHA-1。 SHA-1 包含 SHA256、SHA384 和 SHA512。

## <a name="random-number-generation"></a>產生變數

對許多密碼編譯作業而言，亂數產生是不可或缺的項目。 例如，密碼編譯金鑰需要盡可能為隨機產生，以致於其他人無法重現金鑰。 密碼編譯亂數產生器需產生在運算資源上，無法預測的機率必須大於一半之輸出。 因此，任何預測下一個輸出位元的方法，必須不能優於隨機猜測的方式。 .NET 中的類別會使用亂數產生器來產生密碼編譯金鑰。

<xref:System.Security.Cryptography.RandomNumberGenerator> 類別是亂數產生器演算法的一種實作。

## <a name="clickonce-manifests"></a>ClickOnce 資訊清單

下列密碼編譯類別可讓您取得及驗證使用 [ClickOnce 技術](/visualstudio/deployment/clickonce-security-and-deployment)部署之應用程式的資訊清單簽章相關資訊：

- 當您使用它的 <xref:System.Security.Cryptography.ManifestSignatureInformation> 方法多載時， <xref:System.Security.Cryptography.ManifestSignatureInformation.VerifySignature%2A> 類別可取得資訊清單簽章的相關資訊。

- 您可以使用 <xref:System.Security.ManifestKinds> 列舉來指定要確認哪一個資訊清單。 驗證的結果是 <xref:System.Security.Cryptography.SignatureVerificationResult> 的其中一個列舉值。

- <xref:System.Security.Cryptography.ManifestSignatureInformationCollection> 類別提供已驗證簽章的唯讀集合 <xref:System.Security.Cryptography.ManifestSignatureInformation> 物件。

此外，下列類別會提供特定的簽章資訊：

- <xref:System.Security.Cryptography.StrongNameSignatureInformation> 替資訊清單保存強式名稱的簽章資訊。

- <xref:System.Security.Cryptography.X509Certificates.AuthenticodeSignatureInformation> 代表資訊清單的 Authenticode 簽章資訊。

- <xref:System.Security.Cryptography.X509Certificates.TimestampInformation> 包含了在 Authenticode 簽章上的時間戳記相關資訊。

- <xref:System.Security.Cryptography.X509Certificates.TrustStatus> 提供簡單的方法來檢查 Authenticode 簽章是否受到信任。

## <a name="cryptography-next-generation-cng-classes"></a>新一代密碼編譯 (CNG) 類別

新一代密碼編譯 (CNG) 類別提供可在原生 CNG 函式周圍的 Managed 包裝函式。  (CNG 是 CryptoAPI 的取代。 ) 這些類別在其名稱中使用 "Cng"。 CNG 包裝函式類別的中心是 <xref:System.Security.Cryptography.CngKey> 金鑰容器類別，其會擷取儲存體和使用 CNG 金鑰。 這個類別可讓您安全地儲存金鑰組或公開金鑰，並使用簡單的字串名稱參考它。 橢圓曲線基礎 <xref:System.Security.Cryptography.ECDsaCng> 簽章類別和 <xref:System.Security.Cryptography.ECDiffieHellmanCng> 加密類別可以使用 <xref:System.Security.Cryptography.CngKey> 物件。

<xref:System.Security.Cryptography.CngKey> 類別用於各種其他作業，包括開啟、建立、刪除及匯出金鑰。 它也提供存取基礎金鑰控制代碼，以便在直接呼叫原生函式時使用。

.NET 也包含各種支援的 CNG 類別，如下所示：

- <xref:System.Security.Cryptography.CngProvider> 維護金鑰儲存提供者。

- <xref:System.Security.Cryptography.CngAlgorithm> 維護 CNG 演算法。

- <xref:System.Security.Cryptography.CngProperty> 維護常用的金鑰屬性。

## <a name="see-also"></a>另請參閱

- [加密模型](cryptography-model.md) -說明如何在基類庫中執行密碼編譯。
- [跨平臺密碼編譯](cross-platform-cryptography.md)
- [使用填補進行 CBC 模式對稱解密的時間弱點](vulnerabilities-cbc-mode.md)
- [ASP.NET Core 資料保護](/aspnet/core/security/data-protection/introduction)

---
title: .NET Core 和 .NET 5 中的跨平臺密碼編譯
description: 瞭解 .NET 支援的平臺上的密碼編譯功能。
ms.date: 06/19/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- cryptography, cross-platform
- encryption, cross-platform
ms.openlocfilehash: 793a9bc55e5bd660374abd2ae81899e63ce3f36a
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85854005"
---
# <a name="cross-platform-cryptography-in-net-core-and-net-5"></a>.NET Core 和 .NET 5 中的跨平臺密碼編譯

.NET Core 和 .NET 5 中的密碼編譯作業是由作業系統（OS）程式庫所完成。 這項相依性有下列優點：

* .NET 應用程式受益于作業系統可靠性。 將密碼編譯程式庫保持安全不受弱點影響，是作業系統廠商的高優先順序。 若要這麼做，他們會提供系統管理員應該套用的更新。
* 如果作業系統程式庫經過 FIPS 驗證，則 .NET 應用程式可以存取 FIPS 驗證演算法。

作業系統程式庫的相依性也表示 .NET 應用程式只能使用作業系統所支援的密碼編譯功能。 雖然所有平臺都支援特定的核心功能，但 .NET 所支援的某些功能無法在某些平臺上使用。 本文會識別每個平臺上支援的功能。

本文假設您已熟悉如何在 .NET 中使用密碼編譯。 如需詳細資訊，請參閱[.Net 密碼編譯模型](cryptography-model.md)和 .net 密碼編譯[服務](cryptographic-services.md)。

## <a name="hash-algorithms"></a>雜湊演算法

所有雜湊演算法和雜湊式消息驗證（HMAC）類別（包括 `*Managed` 類別）都會延遲到 OS 程式庫。 雖然各種作業系統程式庫的效能各有不同，但它們應該是相容的。

## <a name="symmetric-encryption"></a>對稱式加密

基礎的加密和連結是由系統程式庫所完成，所有平臺都支援所有這些作業。

| Cipher + 模式 | Windows | Linux | macOS |
|---------------|---------|-------|-------|
| AES-CBC       | ✔️     | ✔️    | ✔️   |
| AES-ECB       | ✔️     | ✔️    | ✔️   |
| 3DES-CBC      | ✔️     | ✔️    | ✔️   |
| 3DES-ECB      | ✔️     | ✔️    | ✔️   |
| DES-CBC       | ✔️     | ✔️    | ✔️   |
| DES-ECB       | ✔️     | ✔️    | ✔️   |

## <a name="authenticated-encryption"></a>已驗證的加密

透過和類別提供 AES-CCM 和 AES GCM 的驗證加密（AE）支援 <xref:System.Security.Cryptography.AesCcm?displayProperty=fullName> <xref:System.Security.Cryptography.AesGcm?displayProperty=fullName> 。

在 Windows 和 Linux 上，AES-CCM 和 AES GCM 的執行是由作業系統程式庫所提供。

### <a name="aes-ccm-and-aes-gcm-on-macos"></a>MacOS 上的 AES-CCM 和 AES GCM

在 macOS 上，系統程式庫不支援以 AES-CCM 或 AES-GCM 進行協力廠商程式碼，因此 <xref:System.Security.Cryptography.AesCcm> 和 <xref:System.Security.Cryptography.AesGcm> 類別會使用 OpenSSL 來支援。 MacOS 上的使用者需要取得適當的 OpenSSL （libcrypto）複本，才能讓這些類型運作，而且它必須位於系統預設載入程式庫的路徑中。 我們建議您從套件管理員（例如 Homebrew）安裝 OpenSSL。

`libcrypto.0.9.7.dylib` `libcrypto.0.9.8.dylib` 包含在 macOS 中的和程式庫是來自舊版的 OpenSSL，且不會使用。 `libcrypto.35.dylib`、 `libcrypto.41.dylib` 和連結 `libcrypto.42.dylib` 庫來自 LibreSSL，而且不會使用。

### <a name="aes-ccm-keys-nonces-and-tags"></a>AES-CCM 金鑰、nonce 和標記

* 金鑰大小

  AES-CCM 可與128、192和256位金鑰搭配運作。

* Nonce 大小

  <xref:System.Security.Cryptography.AesCcm>類別支援56、64、72、80、88、96和104位（7、8、9、10、11、12和13個位元組） nonce。

* 標記大小

  <xref:System.Security.Cryptography.AesCcm>類別支援建立或處理32、48、64、80、96、112和128位（4、8、10、12、14和16位元組）標記。

### <a name="aes-gcm-keys-nonces-and-tags"></a>AES-GCM 金鑰、nonce 和標記

* 金鑰大小

  AES-GCM 可與128、192和256位金鑰搭配運作。

* Nonce 大小

  <xref:System.Security.Cryptography.AesGcm>類別僅支援96位（12位元組）的 nonce。

* 標記大小

  <xref:System.Security.Cryptography.AesGcm>類別支援建立或處理96、104、112、120和128位（12、13、14、15和16位元組）標記。

## <a name="asymmetric-cryptography"></a>非對稱式密碼編譯

本節包含下列小節：

* [RSA](#rsa)
* [ECDSA](#ecdsa)
* [ECDH](#ecdh)
* [DSA](#dsa)

### <a name="rsa"></a>RSA

RSA （Rivest – Shamir – Adleman）金鑰產生是由作業系統程式庫所執行，並受限於其大小限制和效能特性。

RSA 金鑰作業是由 OS 程式庫執行，而且可以載入的金鑰類型受限於 OS 需求。

.NET 不會公開「原始」（未填補之） RSA 作業。

OS 程式庫會用於加密和解密填補。 並非所有平臺都支援相同的填補選項：

| 填補模式                          | Windows （CNG） | Linux （OpenSSL） | macOS | Windows （CAPI） |
|---------------------------------------|---------------|-----------------|-------|----------------|
| PKCS1 加密                      | ✔️           | ✔️              | ✔️   | ✔️             |
| OAEP-SHA-1                          | ✔️           | ✔️              | ✔️   | ✔️             |
| OAEP-SHA-1 （SHA256、SHA384、SHA512） | ✔️           | ✔️              | ✔️   | ❌             |
| PKCS1 簽章（MD5、SHA-1）          | ✔️           | ✔️              | ✔️   | ✔️             |
| PKCS1 簽章（SHA-1）               | ✔️           | ✔️              | ✔️   | ⚠️\*           |
| PSS                                   | ✔️           | ✔️              | ✔️   | ❌             |

\*Windows CryptoAPI （CAPI）能夠 PKCS1 具有 SHA-1 演算法的簽章。 但是，個別的 RSA 物件可能會載入不支援的密碼編譯服務提供者（CSP）中。

#### <a name="rsa-on-windows"></a>Windows 上的 RSA

* 使用時，會使用 Windows CryptoAPI （CAPI） [`new RSACryptoServiceProvider()`](xref:System.Security.Cryptography.RSACryptoServiceProvider) 。
* 每次使用時，都會使用 Windows 密碼編譯 API 新一代（CNG） [`new RSACng()`](xref:System.Security.Cryptography.RSACng) 。
* 傳回的物件 <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> 是由 WINDOWS CNG 內部提供技術支援。 這種 Windows CNG 的使用方式是一個執行詳細資料，而且可能隨時變更。
* 的 <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey%2A> 擴充方法會傳回 <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> <xref:System.Security.Cryptography.RSACng> 實例。 這項使用 <xref:System.Security.Cryptography.RSACng> 是一個執行詳細資料，而且可能隨時變更。
* <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey%2A>目前偏好實例的擴充方法 <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> <xref:System.Security.Cryptography.RSACng> ，但如果 <xref:System.Security.Cryptography.RSACng> 無法開啟此索引鍵， <xref:System.Security.Cryptography.RSACryptoServiceProvider> 則會嘗試。 慣用的提供者是一個執行詳細資料，而且可能會變更。

#### <a name="rsa-native-interop"></a>RSA 原生 interop

.NET 會公開類型，以允許程式與 .NET 密碼編譯器代碼所使用的 OS 程式庫交互操作。 所涉及的類型不會在平臺之間轉譯，而且應該只在必要時才直接使用。

| 類型                                                         | Windows | Linux         | macOS         |
|--------------------------------------------------------------|---------|---------------|---------------|
| <xref:System.Security.Cryptography.RSACryptoServiceProvider> | ✔️     | ⚠️<sup>1</sup>| ⚠️<sup>1</sup> |
| <xref:System.Security.Cryptography.RSACng>                   | ✔️     | ❌            | ❌            |
| <xref:System.Security.Cryptography.RSAOpenSsl>               | ❌     | ✔️            | ⚠️<sup>2</sup> |

<sup>1</sup>在 MacOS 和 Linux 上， <xref:System.Security.Cryptography.RSACryptoServiceProvider> 可以用來與現有的程式相容。 在此情況下，任何需要 OS interop 的方法（例如開啟已命名的金鑰）都會擲回 <xref:System.PlatformNotSupportedException> 。

<sup>2</sup> On macOS， <xref:System.Security.Cryptography.RSAOpenSsl> 適用于 OpenSSL 已安裝，且可透過動態連結程式庫載入找到適當的 libcrypto dylib。 如果找不到適當的程式庫，則會擲回例外狀況。

### <a name="ecdsa"></a>ECDSA

ECDSA （橢圓曲線數位簽章演算法）金鑰產生是由作業系統程式庫所完成，並且受限於其大小限制和效能特性。

ECDSA 主要曲線是由作業系統程式庫所定義，並受限於其限制。

| 橢圓曲線                     | Windows 10    | Windows 7-8。1 | Linux         | macOS         |
|------------------------------------|---------------|-----------------|---------------|---------------|
| NIST P-256 （secp256r1）             | ✔️           | ✔️              | ✔️           | ✔️            |
| NIST P-384 （secp384r1）             | ✔️           | ✔️              | ✔️           | ✔️            |
| NIST P-521 （secp521r1）             | ✔️           | ✔️              | ✔️           | ✔️            |
| Brainpool 曲線（如命名曲線） | ✔️           | ❌              | ⚠️<sup>1</sup>| ❌           |
| 其他命名曲線                 | ⚠️<sup>2</sup>| ❌             | ⚠️<sup>1</sup>| ❌           |
| 明確曲線                    | ✔️           | ❌              | ✔️           | ❌            |
| 匯出或匯入為明確       | ✔️           | ❌<sup>第</sup>  | ✔️           | ❌<sup>第</sup>|

<sup>1</sup> Linux 散發套件不支援相同的命名曲線。

<sup>2</sup>對命名曲線的支援已新增至 windows 10 中的 windows CNG。 如需詳細資訊，請參閱[名為橢圓曲線的 CNG](https://msdn.microsoft.com/library/windows/desktop/mt632245(v=vs.85).aspx)。 在舊版 Windows 中無法使用命名曲線，但 Windows 7 中的三個曲線除外。

<sup>3</sup>使用明確的曲線參數匯出需要作業系統程式庫支援，這在 macOS 或舊版 Windows 中無法使用。

#### <a name="ecdsa-native-interop"></a>ECDSA 原生 Interop

.NET 會公開類型，以允許程式與 .NET 密碼編譯器代碼所使用的 OS 程式庫交互操作。 涉及的類型不會在平臺之間轉譯，而且應該只在必要時才直接使用。

| 類型                                             | Windows | Linux | macOS |
|--------------------------------------------------|---------|-------|-------|
| <xref:System.Security.Cryptography.ECDsaCng>     | ✔️     | ❌    | ❌    |
| <xref:System.Security.Cryptography.ECDsaOpenSsl> | ❌     | ✔️    | ⚠️\*  |

\*在 macOS 上， <xref:System.Security.Cryptography.ECDsaOpenSsl> 適用于 OpenSSL 是否安裝在系統中，而且可以透過動態連結程式庫載入找到適當的 libcrypto dylib。 如果找不到適當的程式庫，則會擲回例外狀況。

### <a name="ecdh"></a>ECDH

ECDH （橢圓曲線 Diffie-hellman）金鑰產生是由作業系統程式庫所完成，並且受限於其大小限制和效能特性。

<xref:System.Security.Cryptography.ECDiffieHellman>類別不會傳回 ECDH 計算的「原始」值。 所有傳回的資料都是索引鍵衍生函式：

* 雜湊（Z）
* 雜湊（前置 | |Z | |追加
* HMAC （索引鍵，Z）
* HMAC （索引鍵，前面加上 | |Z | |追加
* HMAC （Z，Z）
* HMAC （Z，前面加上 | |Z | |追加
* Tls11Prf （標籤、種子）

ECDH 主要曲線是由作業系統程式庫所定義，並受限於其限制。

| 橢圓曲線                     | Windows 10    | Windows 7-8。1 | Linux         | macOS         |
|------------------------------------|---------------|-----------------|---------------|---------------|
| NIST P-256 （secp256r1）             | ✔️           | ✔️              | ✔️           | ✔️            |
| NIST P-384 （secp384r1）             | ✔️           | ✔️              | ✔️           | ✔️            |
| NIST P-521 （secp521r1）             | ✔️           | ✔️              | ✔️           | ✔️            |
| brainpool 曲線（如命名曲線） | ✔️           | ❌              | ⚠️<sup>1</sup>| ❌           |
| 其他命名曲線                 | ⚠️<sup>2</sup>| ❌             | ⚠️<sup>1</sup>| ❌           |
| 明確曲線                    | ✔️           | ❌              | ✔️           | ❌            |
| 匯出或匯入為明確       | ✔️           | ❌<sup>第</sup>  | ✔️           | ❌<sup>第</sup>|

<sup>1</sup> Linux 散發套件不支援相同的命名曲線。

<sup>2</sup>對命名曲線的支援已新增至 windows 10 中的 windows CNG。 如需詳細資訊，請參閱[名為橢圓曲線的 CNG](https://msdn.microsoft.com/library/windows/desktop/mt632245(v=vs.85).aspx)。 在舊版 Windows 中無法使用命名曲線，但 Windows 7 中的三個曲線除外。

<sup>3</sup>使用明確的曲線參數匯出需要作業系統程式庫支援，這在 macOS 或舊版 Windows 中無法使用。

#### <a name="ecdh-native-interop"></a>ECDH 原生 interop

.NET 會公開類型，讓程式能夠與 .NET 所使用的 OS 程式庫相交互操作。 涉及的類型不會在平臺之間轉譯，而且應該只在必要時才直接使用。

| 類型                                                       | Windows | Linux | macOS |
|------------------------------------------------------------|---------|-------|-------|
| <xref:System.Security.Cryptography.ECDiffieHellmanCng>     | ✔️     | ❌    | ❌   |
| <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> | ❌     | ✔️    | ⚠️\* |

\*在 macOS 上， <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> 如果已安裝 OpenSSL，且可透過動態連結程式庫載入找到適當的 libcrypto dylib，則適用。 如果找不到適當的程式庫，則會擲回例外狀況。

### <a name="dsa"></a>DSA

DSA （數位簽章演算法）金鑰產生是由系統程式庫所執行，並受限於其大小限制和效能特性。

| 函式                      | Windows CNG | Linux | macOS         | Windows CAPI |
|-------------------------------|-------------|-------|---------------|--------------|
| 金鑰建立（<= 1024 位）   | ✔️         | ✔️    | ❌            | ✔️           |
| 金鑰建立（> 1024 位）    | ✔️         | ✔️    | ❌            | ❌            |
| 載入金鑰（<= 1024 位）   | ✔️         | ✔️    | ✔️            | ✔️           |
| 載入金鑰（> 1024 位）    | ✔️         | ✔️    | ⚠️\*          | ❌            |
| FIPS 186-2                    | ✔️         | ✔️    | ✔️            | ✔️           |
| FIPS 186-3 （SHA-2 簽章） | ✔️         | ✔️    | ❌            | ❌            |

\*macOS 會載入大於1024位的 DSA 金鑰，但不會定義這些金鑰的行為。 它們不會根據 FIPS 186-3 的行為。

#### <a name="dsa-on-windows"></a>Windows 上的 DSA

* 使用時，會使用 Windows CryptoAPI （CAPI） [`new DSACryptoServiceProvider()`](xref:System.Security.Cryptography.DSACryptoServiceProvider) 。
* 每次使用時，都會使用 Windows 密碼編譯 API 新一代（CNG） [`new DSACng()`](xref:System.Security.Cryptography.DSACng) 。
* 傳回的物件 <xref:System.Security.Cryptography.DSA.Create%2A?displayProperty=nameWithType> 是由 WINDOWS CNG 內部提供技術支援。 這種 Windows CNG 的使用方式是一個執行詳細資料，而且可能隨時變更。
* 的 <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPublicKey%2A> 擴充方法會傳回 <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> <xref:System.Security.Cryptography.DSACng> 實例。 這項使用 <xref:System.Security.Cryptography.DSACng> 是一個執行詳細資料，而且可能隨時變更。
* 偏好 <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPrivateKey%2A> 實例的擴充方法 <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> <xref:System.Security.Cryptography.DSACng> ，但如果 <xref:System.Security.Cryptography.DSACng> 無法開啟索引鍵， <xref:System.Security.Cryptography.DSACryptoServiceProvider> 則會嘗試。  慣用的提供者是一個執行詳細資料，而且可能會變更。

#### <a name="dsa-native-interop"></a>DSA 原生 interop

.NET 會公開類型，以允許程式與 .NET 密碼編譯器代碼所使用的 OS 程式庫交互操作。 涉及的類型不會在平臺之間轉譯，而且應該只在必要時才直接使用。

| 類型                                                         | Windows | Linux         | macOS         |
|--------------------------------------------------------------|---------|---------------|---------------|
| <xref:System.Security.Cryptography.DSACryptoServiceProvider> | ✔️     | ⚠️<sup>1</sup> | ⚠️<sup>1</sup> |
| <xref:System.Security.Cryptography.DSACng>                   | ✔️     | ❌             | ❌            |
| <xref:System.Security.Cryptography.DSAOpenSsl>               | ❌      | ✔️            | ⚠️<sup>2</sup> |

<sup>1</sup>在 MacOS 和 Linux 上， <xref:System.Security.Cryptography.DSACryptoServiceProvider> 可以用來與現有的程式相容。 在此情況下，任何需要系統 interop 的方法（例如開啟已命名的索引鍵）都會擲回 <xref:System.PlatformNotSupportedException> 。

<sup>2</sup> On macOS， <xref:System.Security.Cryptography.DSAOpenSsl> 適用于 OpenSSL 已安裝，且可透過動態連結程式庫載入找到適當的 libcrypto dylib。 如果找不到適當的程式庫，則會擲回例外狀況。

## <a name="x509-certificates"></a>X.509 憑證

.NET 中 x.509 憑證的大部分支援都來自作業系統程式庫。 若要將憑證載入至 <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> <xref:System.Security.Cryptography.X509Certificates.X509Certificate> .net 中的或實例，憑證必須由基礎 OS 程式庫載入。

### <a name="read-a-pkcs12pfx"></a>讀取 PKCS12/PFX

| 狀況                                     | Windows | Linux | macOS |
|----------------------------------------------|---------|-------|-------|
| 空白                                        | ✔️     | ✔️    | ✔️   |
| 一個憑證，沒有私密金鑰              | ✔️     | ✔️    | ✔️   |
| 一個憑證，具有私密金鑰            | ✔️     | ✔️    | ✔️   |
| 多個憑證，沒有私密金鑰       | ✔️     | ✔️    | ✔️   |
| 多個憑證，一個私密金鑰       | ✔️     | ✔️    | ✔️   |
| 多個憑證，多個私密金鑰 | ✔️     | ⚠️\*  | ✔️   |

\*適用于 .NET 5 preview 版本。

### <a name="write-a-pkcs12pfx"></a>撰寫 PKCS12/PFX

| 狀況                                     | Windows | Linux | macOS |
|----------------------------------------------|---------|-------|-------|
| 空白                                        | ✔️     | ✔️    | ⚠️\* |
| 一個憑證，沒有私密金鑰              | ✔️     | ✔️    | ⚠️\* |
| 一個憑證，具有私密金鑰            | ✔️     | ✔️    | ✔️   |
| 多個憑證，沒有私密金鑰       | ✔️     | ✔️    | ⚠️\* |
| 多個憑證，一個私密金鑰       | ✔️     | ✔️    | ✔️   |
| 多個憑證，多個私密金鑰 | ✔️     | ⚠️\*  | ✔️   |
| 暫時載入                            | ✔️     | ✔️    | ⚠️\* |

\*適用于 .NET 5 preview 版本。

macOS 無法在沒有 keychain 物件的情況下載入憑證私密金鑰，這需要寫入磁片。 系統會針對 PFX 載入自動建立金鑰鏈]，並在不再使用時將其刪除。 因為 <xref:System.Security.Cryptography.X509Certificates.X509KeyStorageFlags.EphemeralKeySet?displayProperty=nameWithType> 選項表示不應將私密金鑰寫入磁片，所以在 macOS 上判斷提示時，會產生中的旗標 <xref:System.PlatformNotSupportedException> 。

### <a name="write-a-pkcs7-certificate-collection"></a>寫入 PKCS7 憑證集合

Windows 和 Linux 都會發出 DER 編碼的 PKCS7 blob。 macOS 會發出不限長度的 CER 編碼 PKCS7 blob。

### <a name="x509store"></a>System.security.cryptography.x509certificates.x509store

在 Windows 上， <xref:System.Security.Cryptography.X509Certificates.X509Store> 類別是 Windows 憑證存放區 api 的標記法。 這些 Api 在 .NET Core 和 .NET 5 中的作用都相同，如同在 .NET Framework 中所做的一樣。

在 Linux 上， <xref:System.Security.Cryptography.X509Certificates.X509Store> 類別是系統信任決策（唯讀）、使用者信任決策（讀寫）和使用者金鑰儲存（讀寫）的投影。

在 macOS 上， <xref:System.Security.Cryptography.X509Certificates.X509Store> 類別是系統信任決策（唯讀）、使用者信任決策（唯讀）和使用者金鑰儲存（讀寫）的投影。

下表顯示每個平臺支援的案例。 針對不支援的案例（ ❌ 在資料表中），會擲回 <xref:System.Security.Cryptography.CryptographicException> 。

#### <a name="the-my-store"></a>我的存放區

| 狀況                                         | Windows | Linux | macOS |
|--------------------------------------------------|---------|-------|-------|
| Open CurrentUser\My （ReadOnly）                   | ✔️     | ✔️    | ✔️   |
| 開啟 CurrentUser\My （ReadWrite）                  | ✔️     | ✔️    | ✔️   |
| 開啟 CurrentUser\My （ExistingOnly）               | ✔️     | ⚠️    | ✔️   |
| 開啟 LocalMachine\My                             | ✔️     | ❌    | ✔️   |

在 Linux 上，存放區會在第一次寫入時建立，而且預設不會有任何使用者存放區，因此開啟 `CurrentUser\My` `ExistingOnly` 可能會失敗。

在 macOS 上， `CurrentUser\My` 存放區是使用者的預設 keychain，預設值是 `login.keychain` 。 `LocalMachine\My`存放區是 `System.keychain` 。

#### <a name="the-root-store"></a>根存放區

| 狀況                              | Windows | Linux | macOS           |
|---------------------------------------|---------|-------|-----------------|
| Open CurrentUser\Root （ReadOnly）      | ✔️     | ✔️    | ✔️             |
| 開啟 CurrentUser\Root （ReadWrite）     | ✔️     | ✔️    | ❌              |
| 開啟 CurrentUser\Root （ExistingOnly）  | ✔️     | ⚠️    | ✔️（若為 ReadOnly） |
| Open LocalMachine\Root （ReadOnly）     | ✔️     | ✔️    | ✔️             |
| 開啟 LocalMachine\Root （ReadWrite）    | ✔️     | ❌    | ❌              |
| 開啟 LocalMachine\Root （ExistingOnly） | ✔️     | ⚠️    | ✔️（若為 ReadOnly） |

在 Linux 上， `LocalMachine\Root` 存放區是 OpenSSL 預設路徑中 CA 配套的轉譯。

在 macOS 上， `CurrentUser\Root` 存放區是 `SecTrustSettings` 使用者信任網域的結果轉譯。 `LocalMachine\Root`存放區是 `SecTrustSettings` 系統管理員和系統信任網域的結果轉譯。

#### <a name="the-intermediate-store"></a>中繼存放區

| 狀況                                      | Windows | Linux | macOS           |
|-----------------------------------------------|---------|-------|-----------------|
| Open CurrentUser\Intermediate （ReadOnly）      | ✔️     | ✔️    | ✔️             |
| 開啟 CurrentUser\Intermediate （ReadWrite）     | ✔️     | ✔️    | ❌              |
| 開啟 CurrentUser\Intermediate （ExistingOnly）  | ✔️     | ⚠️    | ✔️（若為 ReadOnly） |
| Open LocalMachine\Intermediate （ReadOnly）     | ✔️     | ✔️    | ✔️             |
| 開啟 LocalMachine\Intermediate （ReadWrite）    | ✔️     | ❌    | ❌              |
| 開啟 LocalMachine\Intermediate （ExistingOnly） | ✔️     | ⚠️    | ✔️（若為 ReadOnly） |

在 Linux 上， `CurrentUser\Intermediate` 當 X509Chain 組建上的授權資訊存取記錄下載中繼 ca 時，會使用此存放區作為快取。 此 `LocalMachine\Intermediate` 存放區是 OpenSSL 預設路徑中的 CA 配套的轉譯。

#### <a name="the-disallowed-store"></a>不允許的存放區

| 狀況                                    | Windows | Linux | macOS           |
|---------------------------------------------|---------|-------|-----------------|
| Open CurrentUser\Disallowed （ReadOnly）      | ✔️     | ⚠️    | ✔️             |
| 開啟 CurrentUser\Disallowed （ReadWrite）     | ✔️     | ⚠️    | ❌              |
| 開啟 CurrentUser\Disallowed （ExistingOnly）  | ✔️     | ⚠️    | ✔️（若為 ReadOnly） |
| Open LocalMachine\Disallowed （ReadOnly）     | ✔️     | ❌    | ✔️             |
| 開啟 LocalMachine\Disallowed （ReadWrite）    | ✔️     | ❌    | ❌              |
| 開啟 LocalMachine\Disallowed （ExistingOnly） | ✔️     | ❌    | ✔️（若為 ReadOnly） |

在 Linux 上， `Disallowed` 存放區不會用於鏈建築物中，而嘗試在其中新增內容會導致 <xref:System.Security.Cryptography.CryptographicException> 。 <xref:System.Security.Cryptography.CryptographicException>如果已取得內容，則在開啟存放區時，會擲回 `Disallowed` 。

在 macOS 上，CurrentUser\Disallowed 和 LocalMachine\Disallowed 存放區是針對信任設定為之憑證的適當 SecTrustSettings 結果的解釋 `Always Deny` 。

#### <a name="nonexistent-store"></a>不存在的存放區

| 狀況                                         | Windows | Linux | macOS |
|--------------------------------------------------|---------|-------|-------|
| 開啟不存在的存放區（ExistingOnly）           | ❌     | ❌     | ❌    |
| 開啟 CurrentUser 不存在的存放區（ReadWrite）  | ✔️     | ✔️     | ⚠️   |
| 開啟 LocalMachine 不存在的存放區（ReadWrite） | ✔️     | ❌     | ❌    |

在 macOS 上，只有 location 才支援使用 System.security.cryptography.x509certificates.x509store API 建立自訂存放區 `CurrentUser` 。 它會在使用者的 keychain 目錄（*~/Library/Keychains*）中建立不含密碼的新 keychain。 若要建立具有密碼的 keychain，可以使用 P/Invoke `SecKeychainCreate` 。 同樣地， `SecKeychainOpen` 也可以用來開啟不同位置中的金鑰鏈]。 產生的 `IntPtr` 可以傳遞至， [`new X509Store(IntPtr)`](xref:System.Security.Cryptography.X509Certificates.X509Store.%23ctor(System.IntPtr)) 以取得具備讀取/寫入功能的存放區，受限於目前使用者的許可權。

### <a name="x509chain"></a>X509Chain

macOS 不支援離線 CRL 使用率，因此 `X509RevocationMode.Offline` 會被視為 `X509RevocationMode.Online` 。

macOS 不支援在 CRL （憑證撤銷清單）/OCSP （線上憑證狀態通訊協定）/AIA （授權資訊存取）下載時，使用者起始的超時時間，因此 `X509ChainPolicy.UrlRetrievalTimeout` 會予以忽略。

## <a name="additional-resources"></a>其他資源

* [.NET 密碼編譯模型](cryptography-model.md)
* [.NET 密碼編譯服務](cryptographic-services.md)

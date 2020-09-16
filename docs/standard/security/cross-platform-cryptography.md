---
title: .NET Core 和 .NET 5 的跨平臺密碼編譯
description: 瞭解 .NET 所支援平臺的密碼編譯功能。
ms.date: 06/19/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- cryptography, cross-platform
- encryption, cross-platform
ms.openlocfilehash: 7269b32e509039fdd767446bd6e10202b089c094
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550015"
---
# <a name="cross-platform-cryptography-in-net-core-and-net-5"></a>.NET Core 和 .NET 5 的跨平臺密碼編譯

.NET Core 和 .NET 5 中的密碼編譯作業是由作業系統 (OS) 程式庫所完成。 這項相依性有其優點：

* .NET 應用程式受益于作業系統可靠性。 讓密碼編譯程式庫免于受到弱點的安全，是 OS 廠商的高優先順序。 若要這樣做，他們會提供系統管理員應套用的更新。
* 如果作業系統程式庫經過 FIPS 驗證，則 .NET 應用程式可以存取 FIPS 驗證的演算法。

作業系統程式庫的相依性也表示 .NET 應用程式只能使用作業系統支援的密碼編譯功能。 雖然所有平臺都支援特定的核心功能，但某些 .NET 支援的功能無法在某些平臺上使用。 本文會識別每個平臺上支援的功能。

本文假設您已熟悉如何在 .NET 中使用加密。 如需詳細資訊，請參閱 [.Net 密碼編譯模型](cryptography-model.md) 和 .net 密碼編譯 [服務](cryptographic-services.md)。

## <a name="hash-algorithms"></a>雜湊演算法

所有雜湊演算法和雜湊式消息驗證 (HMAC) 類別（包括 `*Managed` 類別）會延後至 OS 程式庫。 雖然不同的作業系統程式庫的效能不同，但它們應該是相容的。

## <a name="symmetric-encryption"></a>對稱式加密

基礎的加密和連結是由系統程式庫所完成，所有平臺都支援所有的密碼和連結。

| Cipher + 模式 | Windows | Linux | macOS |
|---------------|---------|-------|-------|
| AES-CBC       | ✔️     | ✔️    | ✔️   |
| AES-ECB       | ✔️     | ✔️    | ✔️   |
| 3DES-CBC      | ✔️     | ✔️    | ✔️   |
| 3DES-ECB      | ✔️     | ✔️    | ✔️   |
| DES-CBC       | ✔️     | ✔️    | ✔️   |
| DES-ECB       | ✔️     | ✔️    | ✔️   |

## <a name="authenticated-encryption"></a>驗證的加密

通過驗證的加密 (AE) 支援是透過和類別提供給 AES-CCM 和 AES GCM <xref:System.Security.Cryptography.AesCcm?displayProperty=fullName> <xref:System.Security.Cryptography.AesGcm?displayProperty=fullName> 。

在 Windows 和 Linux 上，AES-CCM 和 AES-GCM 的執行是由 OS 程式庫所提供。

### <a name="aes-ccm-and-aes-gcm-on-macos"></a>AES-CCM 和 macOS 上的 AES-GCM

在 macOS 上，系統程式庫不支援協力廠商程式碼的 AES-CCM 或 AES-GCM，因此 <xref:System.Security.Cryptography.AesCcm> 和 <xref:System.Security.Cryptography.AesGcm> 類別會使用 OpenSSL 來提供支援。 MacOS 上的使用者必須取得適當的 OpenSSL 複本， (libcrypto) 這些類型才能運作，而且它必須在系統預設會載入程式庫的路徑中。 建議您從套件管理員（例如 Homebrew）安裝 OpenSSL。

`libcrypto.0.9.7.dylib` `libcrypto.0.9.8.dylib` MacOS 中包含的和程式庫來自舊版的 OpenSSL，將不會使用。 `libcrypto.35.dylib`、 `libcrypto.41.dylib` 和連結 `libcrypto.42.dylib` 庫來自 LibreSSL，將不會使用。

### <a name="aes-ccm-keys-nonces-and-tags"></a>AES-CCM 金鑰、nonce 和標記

* 金鑰大小

  AES-CCM 適用于128、192和256位金鑰。

* Nonce 大小

  此 <xref:System.Security.Cryptography.AesCcm> 類別支援56、64、72、80、88、96和104位 (7、8、9、10、11、12和13位元組) nonce。

* 標記大小

  <xref:System.Security.Cryptography.AesCcm>類別支援建立或處理32、48、64、80、96、112和128位 (4、8、10、12、14和16位元組) 標記。

### <a name="aes-gcm-keys-nonces-and-tags"></a>AES-GCM 金鑰、nonce 和標記

* 金鑰大小

  AES-GCM 適用于128、192和256位金鑰。

* Nonce 大小

  <xref:System.Security.Cryptography.AesGcm>類別僅支援96位 (12 個位元組) nonce。

* 標記大小

  <xref:System.Security.Cryptography.AesGcm>類別支援建立或處理96、104、112、120和128位 (12、13、14、15和16位元組) 標記。

## <a name="asymmetric-cryptography"></a>非對稱式密碼編譯

本節包含下列小節：

* [RSA](#rsa)
* [ECDSA](#ecdsa)
* [ECDH](#ecdh)
* [DSA](#dsa)

### <a name="rsa"></a>RSA

RSA (Rivest – Shamir – Adleman) 金鑰產生是由 OS 程式庫所執行，並且受限於其大小限制和效能特性。

RSA 金鑰作業是由 OS 程式庫所執行，而且可以載入的金鑰類型受限於作業系統需求。

.NET 不會公開「原始」 (未填補之) RSA 作業。

OS 程式庫用於加密和解密填補。 並非所有平臺都支援相同的填補選項：

| 填補模式                          | Windows (CNG)  | Linux (OpenSSL)  | macOS | Windows (CAPI)  |
|---------------------------------------|---------------|-----------------|-------|----------------|
| PKCS1 加密                      | ✔️           | ✔️              | ✔️   | ✔️             |
| OAEP-SHA-1                          | ✔️           | ✔️              | ✔️   | ✔️             |
| OAEP-SHA-2 (SHA256、SHA384、SHA512)  | ✔️           | ✔️              | ✔️   | ❌             |
| PKCS1 Signature (MD5，SHA-1)           | ✔️           | ✔️              | ✔️   | ✔️             |
| PKCS1 Signature (SHA-1)                | ✔️           | ✔️              | ✔️   | ⚠️\*           |
| PSS                                   | ✔️           | ✔️              | ✔️   | ❌             |

\* Windows CryptoAPI (CAPI) 能夠 PKCS1 具有 SHA-1 演算法的簽章。 但是個別的 RSA 物件可能會載入 (CSP) 不支援的加密服務提供者。

#### <a name="rsa-on-windows"></a>Windows 上的 RSA

* 每次使用時，都會使用 (CAPI) 的 Windows CryptoAPI [`new RSACryptoServiceProvider()`](xref:System.Security.Cryptography.RSACryptoServiceProvider) 。
* 每次使用時，會使用 Windows 密碼編譯 API 新一代 (CNG) [`new RSACng()`](xref:System.Security.Cryptography.RSACng) 。
* 所傳回的物件 <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> 是由 WINDOWS CNG 在內部提供技術支援。 這種 Windows CNG 的用途是執行的詳細資料，而且可能會變更。
* 的 <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey%2A> 擴充方法會傳回 <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> <xref:System.Security.Cryptography.RSACng> 實例。 這項使用 <xref:System.Security.Cryptography.RSACng> 是實作為的詳細資料，而且可能會變更。
* <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey%2A>目前偏好實例的擴充方法 <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> <xref:System.Security.Cryptography.RSACng> ，但如果 <xref:System.Security.Cryptography.RSACng> 無法開啟金鑰， <xref:System.Security.Cryptography.RSACryptoServiceProvider> 將會嘗試進行。 慣用的提供者是執行的詳細資料，而且可能會變更。

#### <a name="rsa-native-interop"></a>RSA 原生 interop

.NET 會公開類型，讓程式能夠與 .NET 密碼編譯器代碼所使用的 OS 程式庫交互操作。 相關的型別不會在平臺之間轉譯，而且應該只有在必要時才直接使用。

| 類型                                                         | Windows | Linux         | macOS         |
|--------------------------------------------------------------|---------|---------------|---------------|
| <xref:System.Security.Cryptography.RSACryptoServiceProvider> | ✔️     | ⚠️<sup>1</sup>| ⚠️<sup>1</sup> |
| <xref:System.Security.Cryptography.RSACng>                   | ✔️     | ❌            | ❌            |
| <xref:System.Security.Cryptography.RSAOpenSsl>               | ❌     | ✔️            | ⚠️<sup>二級</sup> |

<sup>1</sup> 在 MacOS 和 Linux 上， <xref:System.Security.Cryptography.RSACryptoServiceProvider> 可用於與現有的程式相容。 在此情況下，任何需要作業系統 interop 的方法（例如，開啟名為的金鑰）都會擲回 <xref:System.PlatformNotSupportedException> 。

<sup>2</sup> 在 macOS 上， <xref:System.Security.Cryptography.RSAOpenSsl> 如果已安裝 OpenSSL，且可透過動態連結程式庫載入找到適當的 libcrypto dylib，則適用。 如果找不到適當的程式庫，則會擲回例外狀況。

### <a name="ecdsa"></a>ECDSA

ECDSA (橢圓曲線數位簽章演算法) 金鑰產生是由 OS 程式庫完成，並受限於其大小限制和效能特性。

ECDSA 主要曲線是由 OS 程式庫所定義，且受限於其限制。

| 橢圓曲線                     | Windows 10    | Windows 7-8。1 | Linux         | macOS         |
|------------------------------------|---------------|-----------------|---------------|---------------|
| NIST P-256 (secp256r1)              | ✔️           | ✔️              | ✔️           | ✔️            |
| NIST P-384 (secp384r1)              | ✔️           | ✔️              | ✔️           | ✔️            |
| NIST P-521 (secp521r1)              | ✔️           | ✔️              | ✔️           | ✔️            |
| Brainpool 曲線 (為命名曲線)  | ✔️           | ❌              | ⚠️<sup>1</sup>| ❌           |
| 其他命名曲線                 | ⚠️<sup>二級</sup>| ❌             | ⚠️<sup>1</sup>| ❌           |
| 明確曲線                    | ✔️           | ❌              | ✔️           | ❌            |
| 匯出或匯入為明確       | ✔️           | ❌<sup>3</sup>  | ✔️           | ❌<sup>3</sup>|

<sup>1</sup> Linux 發行版本不支援相同的命名曲線。

在 Windows 10 中，已將命名曲線的<sup>2</sup>個支援新增至 Windows CNG。 如需詳細資訊，請參閱 [CNG 命名的橢圓曲線](/windows/win32/seccng/cng-named-elliptic-curves)。 在舊版 Windows 中無法使用命名曲線，但 Windows 7 中的三個曲線除外。

<sup>3</sup> 以明確曲線參數匯出需要 OS 程式庫支援，在 macOS 或舊版 Windows 上無法使用。

#### <a name="ecdsa-native-interop"></a>ECDSA 原生 Interop

.NET 會公開類型，讓程式能夠與 .NET 密碼編譯器代碼所使用的 OS 程式庫交互操作。 相關的型別不會在平臺之間轉譯，而且應該只有在必要時才直接使用。

| 類型                                             | Windows | Linux | macOS |
|--------------------------------------------------|---------|-------|-------|
| <xref:System.Security.Cryptography.ECDsaCng>     | ✔️     | ❌    | ❌    |
| <xref:System.Security.Cryptography.ECDsaOpenSsl> | ❌     | ✔️    | ⚠️\*  |

\* 在 macOS 上， <xref:System.Security.Cryptography.ECDsaOpenSsl> 適用于 OpenSSL 是否安裝在系統中，以及透過動態連結程式庫載入可以找到適當的 libcrypto dylib。 如果找不到適當的程式庫，則會擲回例外狀況。

### <a name="ecdh"></a>ECDH

ECDH (橢圓曲線 Diffie-hellman) 金鑰產生是由 OS 程式庫完成，並受限於其大小限制和效能特性。

<xref:System.Security.Cryptography.ECDiffieHellman>類別不會傳回 ECDH 計算的「原始」值。 所有傳回的資料都是以主要衍生函式為依據：

* 雜湊 (Z) 
* 預先 (雜湊Z | |附加) 
* HMAC (鍵，Z) 
* HMAC (機碼，在前面加上 | |Z | |附加) 
* HMAC (Z、Z) 
* HMAC (Z，在前面加上 | |Z | |附加) 
* Tls11Prf (標籤，種子) 

ECDH 主要曲線是由 OS 程式庫所定義，並且受限於其限制。

| 橢圓曲線                     | Windows 10    | Windows 7-8。1 | Linux         | macOS         |
|------------------------------------|---------------|-----------------|---------------|---------------|
| NIST P-256 (secp256r1)              | ✔️           | ✔️              | ✔️           | ✔️            |
| NIST P-384 (secp384r1)              | ✔️           | ✔️              | ✔️           | ✔️            |
| NIST P-521 (secp521r1)              | ✔️           | ✔️              | ✔️           | ✔️            |
| brainpool 曲線 (為命名曲線)  | ✔️           | ❌              | ⚠️<sup>1</sup>| ❌           |
| 其他命名曲線                 | ⚠️<sup>二級</sup>| ❌             | ⚠️<sup>1</sup>| ❌           |
| 明確曲線                    | ✔️           | ❌              | ✔️           | ❌            |
| 匯出或匯入為明確       | ✔️           | ❌<sup>3</sup>  | ✔️           | ❌<sup>3</sup>|

<sup>1</sup> Linux 發行版本不支援相同的命名曲線。

在 Windows 10 中，已將命名曲線的<sup>2</sup>個支援新增至 Windows CNG。 如需詳細資訊，請參閱 [CNG 命名的橢圓曲線](/windows/win32/seccng/cng-named-elliptic-curves)。 在舊版 Windows 中無法使用命名曲線，但 Windows 7 中的三個曲線除外。

<sup>3</sup> 以明確曲線參數匯出需要 OS 程式庫支援，在 macOS 或舊版 Windows 上無法使用。

#### <a name="ecdh-native-interop"></a>ECDH 原生 interop

.NET 會公開類型，讓程式能夠與 .NET 所使用的 OS 程式庫交互操作。 相關的型別不會在平臺之間轉譯，而且應該只有在必要時才直接使用。

| 類型                                                       | Windows | Linux | macOS |
|------------------------------------------------------------|---------|-------|-------|
| <xref:System.Security.Cryptography.ECDiffieHellmanCng>     | ✔️     | ❌    | ❌   |
| <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> | ❌     | ✔️    | ⚠️\* |

\* 在 macOS 上， <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> 如果已安裝 OpenSSL，且可透過動態連結程式庫載入找到適當的 libcrypto dylib，則適用。 如果找不到適當的程式庫，則會擲回例外狀況。

### <a name="dsa"></a>DSA

DSA (數位簽章演算法) 金鑰產生是由系統程式庫執行，並且受限於其大小限制和效能特性。

| 函式                      | Windows CNG | Linux | macOS         | Windows CAPI |
|-------------------------------|-------------|-------|---------------|--------------|
| 建立金鑰 ( # B0 = 1024 位)    | ✔️         | ✔️    | ❌            | ✔️           |
| 建立金鑰 ( # A0 1024 bits)     | ✔️         | ✔️    | ❌            | ❌            |
| 載入金鑰 ( # B0 = 1024 位)    | ✔️         | ✔️    | ✔️            | ✔️           |
|  ( # A0 1024 位載入金鑰)     | ✔️         | ✔️    | ⚠️\*          | ❌            |
| FIPS 186-2                    | ✔️         | ✔️    | ✔️            | ✔️           |
| FIPS 186-3 (SHA-1 簽名)  | ✔️         | ✔️    | ❌            | ❌            |

\* macOS 會載入大於1024位的 DSA 金鑰，但這些機碼的行為未定義。 它們不會根據 FIPS 186-3 的行為。

#### <a name="dsa-on-windows"></a>Windows 上的 DSA

* 每次使用時，都會使用 (CAPI) 的 Windows CryptoAPI [`new DSACryptoServiceProvider()`](xref:System.Security.Cryptography.DSACryptoServiceProvider) 。
* 每次使用時，會使用 Windows 密碼編譯 API 新一代 (CNG) [`new DSACng()`](xref:System.Security.Cryptography.DSACng) 。
* 所傳回的物件 <xref:System.Security.Cryptography.DSA.Create%2A?displayProperty=nameWithType> 是由 WINDOWS CNG 在內部提供技術支援。 這種 Windows CNG 的用途是執行的詳細資料，而且可能會變更。
* 的 <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPublicKey%2A> 擴充方法會傳回 <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> <xref:System.Security.Cryptography.DSACng> 實例。 這項使用 <xref:System.Security.Cryptography.DSACng> 是實作為的詳細資料，而且可能會變更。
* 的 <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPrivateKey%2A> 擴充方法 <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> 會優先于 <xref:System.Security.Cryptography.DSACng> 實例，但如果 <xref:System.Security.Cryptography.DSACng> 無法開啟索引鍵， <xref:System.Security.Cryptography.DSACryptoServiceProvider> 則會被嘗試。  慣用的提供者是執行的詳細資料，而且可能會變更。

#### <a name="dsa-native-interop"></a>DSA 原生 interop

.NET 會公開類型，讓程式能夠與 .NET 密碼編譯器代碼所使用的 OS 程式庫交互操作。 相關的型別不會在平臺之間轉譯，而且應該只有在必要時才直接使用。

| 類型                                                         | Windows | Linux         | macOS         |
|--------------------------------------------------------------|---------|---------------|---------------|
| <xref:System.Security.Cryptography.DSACryptoServiceProvider> | ✔️     | ⚠️<sup>1</sup> | ⚠️<sup>1</sup> |
| <xref:System.Security.Cryptography.DSACng>                   | ✔️     | ❌             | ❌            |
| <xref:System.Security.Cryptography.DSAOpenSsl>               | ❌      | ✔️            | ⚠️<sup>二級</sup> |

<sup>1</sup> 在 MacOS 和 Linux 上， <xref:System.Security.Cryptography.DSACryptoServiceProvider> 可用於與現有的程式相容。 在此情況下，任何需要系統 interop 的方法（例如，開啟名為的索引鍵）都會擲回 <xref:System.PlatformNotSupportedException> 。

<sup>2</sup> 在 macOS 上， <xref:System.Security.Cryptography.DSAOpenSsl> 如果已安裝 OpenSSL，且可透過動態連結程式庫載入找到適當的 libcrypto dylib，則適用。 如果找不到適當的程式庫，則會擲回例外狀況。

## <a name="x509-certificates"></a>X.509 憑證

在 .NET 中，x.509 憑證的大部分支援都是來自 OS 程式庫。 若要 <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> 在 .net 中將憑證載入或 <xref:System.Security.Cryptography.X509Certificates.X509Certificate> 實例，憑證必須由基礎 OS 程式庫載入。

### <a name="read-a-pkcs12pfx"></a>讀取 PKCS12/PFX

| 狀況                                     | Windows | Linux | macOS |
|----------------------------------------------|---------|-------|-------|
| 空白                                        | ✔️     | ✔️    | ✔️   |
| 一個憑證，無私密金鑰              | ✔️     | ✔️    | ✔️   |
| 一個具有私密金鑰的憑證            | ✔️     | ✔️    | ✔️   |
| 多個憑證，沒有私用金鑰       | ✔️     | ✔️    | ✔️   |
| 多個憑證，一個私密金鑰       | ✔️     | ✔️    | ✔️   |
| 多個憑證，多個私密金鑰 | ✔️     | ⚠️\*  | ✔️   |

\* 適用于 .NET 5 預覽版本。

### <a name="write-a-pkcs12pfx"></a>撰寫 PKCS12/PFX

| 狀況                                     | Windows | Linux | macOS |
|----------------------------------------------|---------|-------|-------|
| 空白                                        | ✔️     | ✔️    | ⚠️\* |
| 一個憑證，無私密金鑰              | ✔️     | ✔️    | ⚠️\* |
| 一個具有私密金鑰的憑證            | ✔️     | ✔️    | ✔️   |
| 多個憑證，沒有私用金鑰       | ✔️     | ✔️    | ⚠️\* |
| 多個憑證，一個私密金鑰       | ✔️     | ✔️    | ✔️   |
| 多個憑證，多個私密金鑰 | ✔️     | ⚠️\*  | ✔️   |
| 暫時載入                            | ✔️     | ✔️    | ⚠️\* |

\* 適用于 .NET 5 預覽版本。

macOS 無法在沒有 keychain 物件的情況下載入憑證私密金鑰，這需要寫入磁片。 系統會自動為 PFX 載入建立金鑰鏈，並在不再使用時將其刪除。 因為此 <xref:System.Security.Cryptography.X509Certificates.X509KeyStorageFlags.EphemeralKeySet?displayProperty=nameWithType> 選項表示不應將私密金鑰寫入磁片，所以判斷提示 macOS 上的旗標會產生 <xref:System.PlatformNotSupportedException> 。

### <a name="write-a-pkcs7-certificate-collection"></a>寫入 PKCS7 憑證集合

Windows 和 Linux 都會發出 DER 編碼的 PKCS7 blob。 macOS 會發出不定長度的 CER 編碼的 PKCS7 blob。

### <a name="x509store"></a>System.security.cryptography.x509certificates.x509store

在 Windows 中， <xref:System.Security.Cryptography.X509Certificates.X509Store> 類別是 Windows 憑證存放區 api 的標記法。 這些 Api 在 .NET Core 和 .NET 5 中的運作方式與 .NET Framework 中的相同。

在 Linux 上， <xref:System.Security.Cryptography.X509Certificates.X509Store> 類別是系統信任決策的投射 (唯讀) 、使用者信任決策 (讀寫) ，以及使用者金鑰儲存 (讀寫) 。

在 macOS 上， <xref:System.Security.Cryptography.X509Certificates.X509Store> 類別是系統信任決策的投射 (唯讀) 、使用者信任決策 (唯讀) ，以及使用者金鑰儲存 (讀寫) 。

下表顯示每個平臺支援的案例。 針對) 資料表中 (不支援的案例 ❌ ， <xref:System.Security.Cryptography.CryptographicException> 會擲回。

#### <a name="the-my-store"></a>我的存放區

| 狀況                                         | Windows | Linux | macOS |
|--------------------------------------------------|---------|-------|-------|
| 開啟 CurrentUser\My (ReadOnly)                    | ✔️     | ✔️    | ✔️   |
| 開啟 CurrentUser\My (ReadWrite)                   | ✔️     | ✔️    | ✔️   |
| 開啟 CurrentUser\My (ExistingOnly)                | ✔️     | ⚠️    | ✔️   |
| 開啟 LocalMachine\My                             | ✔️     | ❌    | ✔️   |

在 Linux 上，存放區是在第一次寫入時建立的，而且預設不存在任何使用者存放區，因此開啟 `CurrentUser\My` `ExistingOnly` 可能會失敗。

在 macOS 上， `CurrentUser\My` 存放區是使用者的預設 keychain，預設為 `login.keychain` 。 `LocalMachine\My`存放區為 `System.keychain` 。

#### <a name="the-root-store"></a>根存放區

| 狀況                              | Windows | Linux | macOS           |
|---------------------------------------|---------|-------|-----------------|
| 開啟 CurrentUser\Root (ReadOnly)       | ✔️     | ✔️    | ✔️             |
| 開啟 CurrentUser\Root (ReadWrite)      | ✔️     | ✔️    | ❌              |
| 開啟 CurrentUser\Root (ExistingOnly)   | ✔️     | ⚠️    | 如果 ReadOnly) ，則✔️ ( |
| 開啟 LocalMachine\Root (ReadOnly)      | ✔️     | ✔️    | ✔️             |
| 開啟 LocalMachine\Root (ReadWrite)     | ✔️     | ❌    | ❌              |
| 開啟 LocalMachine\Root (ExistingOnly)  | ✔️     | ⚠️    | 如果 ReadOnly) ，則✔️ ( |

在 Linux 上， `LocalMachine\Root` 存放區是 OpenSSL 預設路徑中 CA 組合的解釋。

在 macOS 上， `CurrentUser\Root` 存放區是 `SecTrustSettings` 使用者信任網域的結果轉譯。 `LocalMachine\Root`存放區是 `SecTrustSettings` 系統管理員和系統信任網域的結果解讀。

#### <a name="the-intermediate-store"></a>中繼存放區

| 狀況                                      | Windows | Linux | macOS           |
|-----------------------------------------------|---------|-------|-----------------|
| 開啟 CurrentUser\Intermediate (ReadOnly)       | ✔️     | ✔️    | ✔️             |
| 開啟 CurrentUser\Intermediate (ReadWrite)      | ✔️     | ✔️    | ❌              |
| 開啟 CurrentUser\Intermediate (ExistingOnly)   | ✔️     | ⚠️    | 如果 ReadOnly) ，則✔️ ( |
| 開啟 LocalMachine\Intermediate (ReadOnly)      | ✔️     | ✔️    | ✔️             |
| 開啟 LocalMachine\Intermediate (ReadWrite)     | ✔️     | ❌    | ❌              |
| 開啟 LocalMachine\Intermediate (ExistingOnly)  | ✔️     | ⚠️    | 如果 ReadOnly) ，則✔️ ( |

在 Linux 上，此 `CurrentUser\Intermediate` 存放區是用來作為快取，以在成功的 X509Chain 組建上下載中繼 ca 的授權資訊存取記錄。 `LocalMachine\Intermediate`存放區是 OpenSSL 預設路徑中 CA 組合的解釋。

#### <a name="the-disallowed-store"></a>不允許的存放區

| 狀況                                    | Windows | Linux | macOS           |
|---------------------------------------------|---------|-------|-----------------|
| 開啟 CurrentUser\Disallowed (ReadOnly)       | ✔️     | ⚠️    | ✔️             |
| 開啟 CurrentUser\Disallowed (ReadWrite)      | ✔️     | ⚠️    | ❌              |
| 開啟 CurrentUser\Disallowed (ExistingOnly)   | ✔️     | ⚠️    | 如果 ReadOnly) ，則✔️ ( |
| 開啟 LocalMachine\Disallowed (ReadOnly)      | ✔️     | ❌    | ✔️             |
| 開啟 LocalMachine\Disallowed (ReadWrite)     | ✔️     | ❌    | ❌              |
| 開啟 LocalMachine\Disallowed (ExistingOnly)  | ✔️     | ❌    | 如果 ReadOnly) ，則✔️ ( |

在 Linux 上， `Disallowed` 存放區不會用在鏈建築物中，因此嘗試將內容新增至該存放區會導致 <xref:System.Security.Cryptography.CryptographicException> 。 <xref:System.Security.Cryptography.CryptographicException>開啟 `Disallowed` 存放區時如果已取得內容，就會擲回。

在 macOS 上，CurrentUser\Disallowed 和 LocalMachine\Disallowed 存放區會針對信任設定為的憑證，解釋適當的 SecTrustSettings 結果 `Always Deny` 。

#### <a name="nonexistent-store"></a>不存在的存放區

| 狀況                                         | Windows | Linux | macOS |
|--------------------------------------------------|---------|-------|-------|
| 開啟不存在的存放區 (ExistingOnly)            | ❌     | ❌     | ❌    |
| 開啟 CurrentUser 不存在的存放區 (ReadWrite)   | ✔️     | ✔️     | ⚠️   |
| 開啟 LocalMachine 不存在的存放區 (ReadWrite)  | ✔️     | ❌     | ❌    |

在 macOS 上，只有位置才支援使用 System.security.cryptography.x509certificates.x509store API 建立自訂存放區 `CurrentUser` 。 它會在使用者的 keychain 目錄中建立沒有密碼的新 keychain， (*~/Library/Keychains*) 。 若要建立具有密碼的 keychain，可以使用 P/Invoke `SecKeychainCreate` 。 同樣地， `SecKeychainOpen` 也可以用來在不同的位置開啟金鑰鏈。 產生的結果 `IntPtr` 可以傳遞給，以 [`new X509Store(IntPtr)`](xref:System.Security.Cryptography.X509Certificates.X509Store.%23ctor(System.IntPtr)) 取得讀取/寫入支援的存放區，並受限於目前使用者的許可權。

### <a name="x509chain"></a>X509Chain

macOS 不支援離線 CRL 使用，因此 `X509RevocationMode.Offline` 會被視為 `X509RevocationMode.Online` 。

macOS 不支援以使用者起始的 CRL (憑證撤銷清單) /OCSP (線上憑證狀態通訊協定) /AIA (授權單位資訊存取) 下載，所以 `X509ChainPolicy.UrlRetrievalTimeout` 會忽略。

## <a name="additional-resources"></a>其他資源

* [.NET 密碼編譯模型](cryptography-model.md)
* [.NET 密碼編譯服務](cryptographic-services.md)
* [使用填補進行 CBC 模式對稱解密的時間弱點](vulnerabilities-cbc-mode.md)
* [ASP.NET Core 資料保護](/aspnet/core/security/data-protection/introduction)

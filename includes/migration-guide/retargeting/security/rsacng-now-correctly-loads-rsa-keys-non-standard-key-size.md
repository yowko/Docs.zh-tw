---
ms.openlocfilehash: c1e85941c8c6c31c7d937d0671ad955fa6490783
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614328"
---
### <a name="rsacng-now-correctly-loads-rsa-keys-of-non-standard-key-size"></a>RSACng 現在會正確地載入非標準金鑰大小的 RSA 金鑰

#### <a name="details"></a>詳細資料

在 .NET Framework 4.6.2 之前，使用非標準的 RSA 憑證金鑰大小客戶，無法透過 <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=fullName> 和 <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=fullName> 擴充方法存取這些金鑰。  會擲回 <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> 以及「不支援要求的金鑰大小」訊息。 在 .NET Framework 4.6.2 中，已修正此問題。 同樣地，<xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)> 和 <xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)> 現在可以使用非標準的金鑰大小，而不會擲回 <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName>。

#### <a name="suggestion"></a>建議

如果有任何例外狀況處理邏輯會依賴先前的行為，也就是使用非標準的金鑰大小時會擲回 <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName>，請考慮移除該邏輯。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Edge        |
| 版本 | 4.6.2       |
| 類型    | 正在重定目標 |

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=nameWithType>

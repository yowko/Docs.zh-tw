---
ms.openlocfilehash: c1e85941c8c6c31c7d937d0671ad955fa6490783
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614328"
---
### <a name="rsacng-now-correctly-loads-rsa-keys-of-non-standard-key-size"></a><span data-ttu-id="6ce1f-101">RSACng 現在會正確地載入非標準金鑰大小的 RSA 金鑰</span><span class="sxs-lookup"><span data-stu-id="6ce1f-101">RSACng now correctly loads RSA keys of non-standard key size</span></span>

#### <a name="details"></a><span data-ttu-id="6ce1f-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="6ce1f-102">Details</span></span>

<span data-ttu-id="6ce1f-103">在 .NET Framework 4.6.2 之前，使用非標準的 RSA 憑證金鑰大小客戶，無法透過 <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=fullName> 和 <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=fullName> 擴充方法存取這些金鑰。</span><span class="sxs-lookup"><span data-stu-id="6ce1f-103">In .NET Framework versions prior to 4.6.2, customers with non-standard key sizes for RSA certificates are unable to access those keys via the <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=fullName> and <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=fullName> extension methods.</span></span>  <span data-ttu-id="6ce1f-104">會擲回 <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> 以及「不支援要求的金鑰大小」訊息。</span><span class="sxs-lookup"><span data-stu-id="6ce1f-104">A <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> with the message &quot;The requested key size is not supported&quot; is thrown.</span></span> <span data-ttu-id="6ce1f-105">在 .NET Framework 4.6.2 中，已修正此問題。</span><span class="sxs-lookup"><span data-stu-id="6ce1f-105">In .NET Framework 4.6.2 this issue has been fixed.</span></span> <span data-ttu-id="6ce1f-106">同樣地，<xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)> 和 <xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)> 現在可以使用非標準的金鑰大小，而不會擲回 <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="6ce1f-106">Similarly, <xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)> and <xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)> now work with non-standard key sizes without throwing a <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="6ce1f-107">建議</span><span class="sxs-lookup"><span data-stu-id="6ce1f-107">Suggestion</span></span>

<span data-ttu-id="6ce1f-108">如果有任何例外狀況處理邏輯會依賴先前的行為，也就是使用非標準的金鑰大小時會擲回 <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName>，請考慮移除該邏輯。</span><span class="sxs-lookup"><span data-stu-id="6ce1f-108">If there is any exception handling logic that relies on the previous behavior where a <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> is thrown when non-standard key sizes are used, consider removing the logic.</span></span>

| <span data-ttu-id="6ce1f-109">名稱</span><span class="sxs-lookup"><span data-stu-id="6ce1f-109">Name</span></span>    | <span data-ttu-id="6ce1f-110">值</span><span class="sxs-lookup"><span data-stu-id="6ce1f-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="6ce1f-111">影響範圍</span><span class="sxs-lookup"><span data-stu-id="6ce1f-111">Scope</span></span>   | <span data-ttu-id="6ce1f-112">Edge</span><span class="sxs-lookup"><span data-stu-id="6ce1f-112">Edge</span></span>        |
| <span data-ttu-id="6ce1f-113">版本</span><span class="sxs-lookup"><span data-stu-id="6ce1f-113">Version</span></span> | <span data-ttu-id="6ce1f-114">4.6.2</span><span class="sxs-lookup"><span data-stu-id="6ce1f-114">4.6.2</span></span>       |
| <span data-ttu-id="6ce1f-115">類型</span><span class="sxs-lookup"><span data-stu-id="6ce1f-115">Type</span></span>    | <span data-ttu-id="6ce1f-116">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="6ce1f-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="6ce1f-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="6ce1f-117">Affected APIs</span></span>

- <xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=nameWithType>

---
ms.openlocfilehash: fa5cf2280cdd9535962568a6272d047d261eeba5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621083"
---
### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a><span data-ttu-id="a67f6-101">RSACng.VerifyHash 現在會針對任何驗證失敗傳回 False</span><span class="sxs-lookup"><span data-stu-id="a67f6-101">RSACng.VerifyHash now returns False for any verification failure</span></span>

#### <a name="details"></a><span data-ttu-id="a67f6-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a67f6-102">Details</span></span>

<span data-ttu-id="a67f6-103">從 .NET Framework 4.6.2 開始，如果簽章本身的格式不正確，此方法會傳回 **False**。</span><span class="sxs-lookup"><span data-stu-id="a67f6-103">Starting with the .NET Framework 4.6.2, this method returns **False** if the signature itself is badly formatted.</span></span> <span data-ttu-id="a67f6-104">現在任何驗證失敗都會傳回 False。在 .NET Framework 4.6 和 4.6.1 中，如果簽章本身的格式不正確，此方法會擲回 <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="a67f6-104">It now returns false for any verification failure.In the .NET Framework 4.6 and 4.6.1, the method throws a <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> if the signature itself is badly formatted.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="a67f6-105">建議</span><span class="sxs-lookup"><span data-stu-id="a67f6-105">Suggestion</span></span>

<span data-ttu-id="a67f6-106">如果驗證失敗且此方法傳回 **False**，應改為執行任何仰賴處理 <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> 來執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="a67f6-106">Any code whose execution depends on handling the <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> should instead execute if validation fails and the method returns **False**.</span></span>

| <span data-ttu-id="a67f6-107">名稱</span><span class="sxs-lookup"><span data-stu-id="a67f6-107">Name</span></span>    | <span data-ttu-id="a67f6-108">值</span><span class="sxs-lookup"><span data-stu-id="a67f6-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="a67f6-109">影響範圍</span><span class="sxs-lookup"><span data-stu-id="a67f6-109">Scope</span></span>   |<span data-ttu-id="a67f6-110">Minor</span><span class="sxs-lookup"><span data-stu-id="a67f6-110">Minor</span></span>|
|<span data-ttu-id="a67f6-111">版本</span><span class="sxs-lookup"><span data-stu-id="a67f6-111">Version</span></span>|<span data-ttu-id="a67f6-112">4.6.2</span><span class="sxs-lookup"><span data-stu-id="a67f6-112">4.6.2</span></span>|
|<span data-ttu-id="a67f6-113">類型</span><span class="sxs-lookup"><span data-stu-id="a67f6-113">Type</span></span>|<span data-ttu-id="a67f6-114">執行階段</span><span class="sxs-lookup"><span data-stu-id="a67f6-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a67f6-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="a67f6-115">Affected APIs</span></span>

-<xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|

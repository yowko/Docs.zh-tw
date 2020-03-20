---
ms.openlocfilehash: fc315faef750d93d914104dd568078aa3fc430d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "72887742"
---
### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a><span data-ttu-id="a0c66-101">RSACng.VerifyHash 現在會針對任何驗證失敗傳回 False</span><span class="sxs-lookup"><span data-stu-id="a0c66-101">RSACng.VerifyHash now returns False for any verification failure</span></span>

|   |   |
|---|---|
|<span data-ttu-id="a0c66-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a0c66-102">Details</span></span>|<span data-ttu-id="a0c66-103">從 .NET Framework 4.6.2 開始，如果簽章本身的格式不正確，此方法會傳回 **False**。</span><span class="sxs-lookup"><span data-stu-id="a0c66-103">Starting with the .NET Framework 4.6.2, this method returns **False** if the signature itself is badly formatted.</span></span> <span data-ttu-id="a0c66-104">現在任何驗證失敗都會傳回 False。在 .NET Framework 4.6 和 4.6.1 中，如果簽章本身的格式不正確，此方法會擲回 <xref:System.Security.Cryptography.CryptographicException?displayProperty=name>。</span><span class="sxs-lookup"><span data-stu-id="a0c66-104">It now returns false for any verification failure.In the .NET Framework 4.6 and 4.6.1, the method throws a <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> if the signature itself is badly formatted.</span></span>|
|<span data-ttu-id="a0c66-105">建議</span><span class="sxs-lookup"><span data-stu-id="a0c66-105">Suggestion</span></span>|<span data-ttu-id="a0c66-106">如果驗證失敗且此方法傳回 **False**，應改為執行任何仰賴處理 <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> 來執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="a0c66-106">Any code whose execution depends on handling the <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> should instead execute if validation fails and the method returns **False**.</span></span>|
|<span data-ttu-id="a0c66-107">影響範圍</span><span class="sxs-lookup"><span data-stu-id="a0c66-107">Scope</span></span>|<span data-ttu-id="a0c66-108">Minor</span><span class="sxs-lookup"><span data-stu-id="a0c66-108">Minor</span></span>|
|<span data-ttu-id="a0c66-109">版本</span><span class="sxs-lookup"><span data-stu-id="a0c66-109">Version</span></span>|<span data-ttu-id="a0c66-110">4.6.2</span><span class="sxs-lookup"><span data-stu-id="a0c66-110">4.6.2</span></span>|
|<span data-ttu-id="a0c66-111">類型</span><span class="sxs-lookup"><span data-stu-id="a0c66-111">Type</span></span>|<span data-ttu-id="a0c66-112">執行階段</span><span class="sxs-lookup"><span data-stu-id="a0c66-112">Runtime</span></span>|
|<span data-ttu-id="a0c66-113">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="a0c66-113">Affected APIs</span></span>|<ul><li><xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|

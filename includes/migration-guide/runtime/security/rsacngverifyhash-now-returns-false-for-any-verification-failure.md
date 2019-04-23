---
ms.openlocfilehash: acf4e8df2cef3d9ec5d123a14cc7bfcd6f1bfb8b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803470"
---
### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a><span data-ttu-id="8351f-101">RSACng.VerifyHash 現在會針對任何驗證失敗傳回 False</span><span class="sxs-lookup"><span data-stu-id="8351f-101">RSACng.VerifyHash now returns False for any verification failure</span></span>

|   |   |
|---|---|
|<span data-ttu-id="8351f-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8351f-102">Details</span></span>|<span data-ttu-id="8351f-103">從 .NET Framework 4.6.2 開始，如果簽章本身的格式不正確，此方法會傳回 <strong>False</strong>。</span><span class="sxs-lookup"><span data-stu-id="8351f-103">Starting with the .NET Framework 4.6.2, this method returns <strong>False</strong> if the signature itself is badly formatted.</span></span> <span data-ttu-id="8351f-104">現在任何驗證失敗都會傳回 False。在 .NET Framework 4.6 和 4.6.1 中，如果簽章本身的格式不正確，此方法會擲回 <xref:System.Security.Cryptography.CryptographicException?displayProperty=name>。</span><span class="sxs-lookup"><span data-stu-id="8351f-104">It now returns false for any verification failure.In the .NET Framework 4.6 and 4.6.1, the method throws a <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> if the signature itself is badly formatted.</span></span>|
|<span data-ttu-id="8351f-105">建議</span><span class="sxs-lookup"><span data-stu-id="8351f-105">Suggestion</span></span>|<span data-ttu-id="8351f-106">如果驗證失敗且此方法傳回 <strong>False</strong>，應改為執行任何仰賴處理 <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> 來執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="8351f-106">Any code whose execution depends on handling the <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> should instead execute if validation fails and the method returns <strong>False</strong>.</span></span>|
|<span data-ttu-id="8351f-107">範圍</span><span class="sxs-lookup"><span data-stu-id="8351f-107">Scope</span></span>|<span data-ttu-id="8351f-108">次要</span><span class="sxs-lookup"><span data-stu-id="8351f-108">Minor</span></span>|
|<span data-ttu-id="8351f-109">版本</span><span class="sxs-lookup"><span data-stu-id="8351f-109">Version</span></span>|<span data-ttu-id="8351f-110">4.6.2</span><span class="sxs-lookup"><span data-stu-id="8351f-110">4.6.2</span></span>|
|<span data-ttu-id="8351f-111">類型</span><span class="sxs-lookup"><span data-stu-id="8351f-111">Type</span></span>|<span data-ttu-id="8351f-112">執行階段</span><span class="sxs-lookup"><span data-stu-id="8351f-112">Runtime</span></span>|
|<span data-ttu-id="8351f-113">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="8351f-113">Affected APIs</span></span>|<ul><li><xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|

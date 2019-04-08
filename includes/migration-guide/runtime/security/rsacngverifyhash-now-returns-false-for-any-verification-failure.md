---
ms.openlocfilehash: 7d60578ac2913037e1cdeda329f06f9a4986574d
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760623"
---
### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a><span data-ttu-id="c40aa-101">RSACng.VerifyHash 現在會針對任何驗證失敗傳回 False</span><span class="sxs-lookup"><span data-stu-id="c40aa-101">RSACng.VerifyHash now returns False for any verification failure</span></span>

|   |   |
|---|---|
|<span data-ttu-id="c40aa-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c40aa-102">Details</span></span>|<span data-ttu-id="c40aa-103">從 .NET Framework 4.6.2 開始，如果簽章本身的格式不正確，此方法會傳回 <strong>False</strong>。</span><span class="sxs-lookup"><span data-stu-id="c40aa-103">Starting with the .NET Framework 4.6.2, this method returns <strong>False</strong> if the signature itself is badly formatted.</span></span> <span data-ttu-id="c40aa-104">現在任何驗證失敗都會傳回 False。在 .NET Framework 4.6 和 4.6.1 中，如果簽章本身的格式不正確，此方法會擲回 <xref:System.Security.Cryptography.CryptographicException?displayProperty=name>。</span><span class="sxs-lookup"><span data-stu-id="c40aa-104">It now returns false for any verification failure.In the .NET Framework 4.6 and 4.6.1, the method throws a <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> if the signature itself is badly formatted.</span></span>|
|<span data-ttu-id="c40aa-105">建議</span><span class="sxs-lookup"><span data-stu-id="c40aa-105">Suggestion</span></span>|<span data-ttu-id="c40aa-106">如果驗證失敗且此方法傳回 <strong>False</strong>，應改為執行任何仰賴處理 <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> 來執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="c40aa-106">Any code whose execution depends on handling the <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> should instead execute if validation fails and the method returns <strong>False</strong>.</span></span>|
|<span data-ttu-id="c40aa-107">範圍</span><span class="sxs-lookup"><span data-stu-id="c40aa-107">Scope</span></span>|<span data-ttu-id="c40aa-108">次要</span><span class="sxs-lookup"><span data-stu-id="c40aa-108">Minor</span></span>|
|<span data-ttu-id="c40aa-109">版本</span><span class="sxs-lookup"><span data-stu-id="c40aa-109">Version</span></span>|<span data-ttu-id="c40aa-110">4.6.2</span><span class="sxs-lookup"><span data-stu-id="c40aa-110">4.6.2</span></span>|
|<span data-ttu-id="c40aa-111">類型</span><span class="sxs-lookup"><span data-stu-id="c40aa-111">Type</span></span>|<span data-ttu-id="c40aa-112">執行階段</span><span class="sxs-lookup"><span data-stu-id="c40aa-112">Runtime</span></span>|
|<span data-ttu-id="c40aa-113">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="c40aa-113">Affected APIs</span></span>|<ul><li><xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|


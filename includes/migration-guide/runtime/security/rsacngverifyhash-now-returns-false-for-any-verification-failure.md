---
ms.openlocfilehash: 7d60578ac2913037e1cdeda329f06f9a4986574d
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67857589"
---
### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a><span data-ttu-id="a6580-101">RSACng.VerifyHash 現在會針對任何驗證失敗傳回 False</span><span class="sxs-lookup"><span data-stu-id="a6580-101">RSACng.VerifyHash now returns False for any verification failure</span></span>

|   |   |
|---|---|
|<span data-ttu-id="a6580-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a6580-102">Details</span></span>|<span data-ttu-id="a6580-103">從 .NET Framework 4.6.2 開始，如果簽章本身的格式不正確，此方法會傳回 <strong>False</strong>。</span><span class="sxs-lookup"><span data-stu-id="a6580-103">Starting with the .NET Framework 4.6.2, this method returns <strong>False</strong> if the signature itself is badly formatted.</span></span> <span data-ttu-id="a6580-104">現在任何驗證失敗都會傳回 False。在 .NET Framework 4.6 和 4.6.1 中，如果簽章本身的格式不正確，此方法會擲回 <xref:System.Security.Cryptography.CryptographicException?displayProperty=name>。</span><span class="sxs-lookup"><span data-stu-id="a6580-104">It now returns false for any verification failure.In the .NET Framework 4.6 and 4.6.1, the method throws a <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> if the signature itself is badly formatted.</span></span>|
|<span data-ttu-id="a6580-105">建議</span><span class="sxs-lookup"><span data-stu-id="a6580-105">Suggestion</span></span>|<span data-ttu-id="a6580-106">如果驗證失敗且此方法傳回 <strong>False</strong>，應改為執行任何仰賴處理 <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> 來執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="a6580-106">Any code whose execution depends on handling the <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> should instead execute if validation fails and the method returns <strong>False</strong>.</span></span>|
|<span data-ttu-id="a6580-107">範圍</span><span class="sxs-lookup"><span data-stu-id="a6580-107">Scope</span></span>|<span data-ttu-id="a6580-108">次要</span><span class="sxs-lookup"><span data-stu-id="a6580-108">Minor</span></span>|
|<span data-ttu-id="a6580-109">版本</span><span class="sxs-lookup"><span data-stu-id="a6580-109">Version</span></span>|<span data-ttu-id="a6580-110">4.6.2</span><span class="sxs-lookup"><span data-stu-id="a6580-110">4.6.2</span></span>|
|<span data-ttu-id="a6580-111">類型</span><span class="sxs-lookup"><span data-stu-id="a6580-111">Type</span></span>|<span data-ttu-id="a6580-112">執行階段</span><span class="sxs-lookup"><span data-stu-id="a6580-112">Runtime</span></span>|
|<span data-ttu-id="a6580-113">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="a6580-113">Affected APIs</span></span>|<ul><li><xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|


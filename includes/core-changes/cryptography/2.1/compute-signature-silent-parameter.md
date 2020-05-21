---
ms.openlocfilehash: b861dbaa02c97a03c015fdf4e63d25c40c90ea0a
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721255"
---
### <a name="boolean-parameter-of-signedcmscomputesignature-is-respected"></a><span data-ttu-id="39ebf-101">遵守 SignedCms 的布林值參數。 ComputeSignature</span><span class="sxs-lookup"><span data-stu-id="39ebf-101">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>

<span data-ttu-id="39ebf-102">在 .NET Core 中， `silent` 會遵守方法的布林值參數 <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="39ebf-102">In .NET Core, the Boolean `silent` parameter of the <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> method is respected.</span></span> <span data-ttu-id="39ebf-103">如果此參數設定為，則不會顯示 PIN 提示 `true` 。</span><span class="sxs-lookup"><span data-stu-id="39ebf-103">A PIN prompt is not shown if this parameter is set to `true`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="39ebf-104">變更描述</span><span class="sxs-lookup"><span data-stu-id="39ebf-104">Change description</span></span>

<span data-ttu-id="39ebf-105">在 .NET Framework 中， `silent` <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> 會忽略方法的參數，而且在提供者需要時，一律會顯示 PIN 提示。</span><span class="sxs-lookup"><span data-stu-id="39ebf-105">In .NET Framework, the `silent` parameter of the <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> method is ignored, and a PIN prompt is always shown if required by the provider.</span></span> <span data-ttu-id="39ebf-106">在 .NET Core 中， `silent` 會遵守參數，如果設定為，則永遠不會 `true` 顯示 PIN 提示（即使提供者需要）。</span><span class="sxs-lookup"><span data-stu-id="39ebf-106">In .NET Core, the `silent` parameter is respected, and if set to `true`, a PIN prompt is never shown, even if it's required by the provider.</span></span>

<span data-ttu-id="39ebf-107">2.1 版的 .NET Core 中引進了 CMS/PKCS #7 訊息的支援。</span><span class="sxs-lookup"><span data-stu-id="39ebf-107">Support for CMS/PKCS #7 messages was introduced into .NET Core in version 2.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="39ebf-108">引進的版本</span><span class="sxs-lookup"><span data-stu-id="39ebf-108">Version introduced</span></span>

<span data-ttu-id="39ebf-109">2.1</span><span class="sxs-lookup"><span data-stu-id="39ebf-109">2.1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="39ebf-110">建議的動作</span><span class="sxs-lookup"><span data-stu-id="39ebf-110">Recommended action</span></span>

<span data-ttu-id="39ebf-111">為確保在需要時顯示 PIN 提示，桌面應用程式應該呼叫， <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> 並將布林參數設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="39ebf-111">To ensure a PIN prompt appears if required, desktop applications should call <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> and set the Boolean parameter to `false`.</span></span> <span data-ttu-id="39ebf-112">產生的行為等同于 .NET Framework，不論是否在該處停用無訊息內容。</span><span class="sxs-lookup"><span data-stu-id="39ebf-112">The resulting behavior is the same as on .NET Framework regardless of whether the silent context is disabled there.</span></span>

#### <a name="category"></a><span data-ttu-id="39ebf-113">類別</span><span class="sxs-lookup"><span data-stu-id="39ebf-113">Category</span></span>

<span data-ttu-id="39ebf-114">密碼編譯</span><span class="sxs-lookup"><span data-stu-id="39ebf-114">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="39ebf-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="39ebf-115">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)`

-->

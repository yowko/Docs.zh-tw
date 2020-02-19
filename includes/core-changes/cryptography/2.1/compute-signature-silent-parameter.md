---
ms.openlocfilehash: 9583d868ee01117d7bd6e465e7d89a734489d1a8
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449208"
---
### <a name="boolean-parameter-of-signedcmscomputesignature-is-respected"></a><span data-ttu-id="9b793-101">遵守 SignedCms 的布林值參數。 ComputeSignature</span><span class="sxs-lookup"><span data-stu-id="9b793-101">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>

<span data-ttu-id="9b793-102">在 .NET Core 中，會遵守 <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> 方法的布林值 `silent` 參數。</span><span class="sxs-lookup"><span data-stu-id="9b793-102">In .NET Core, the Boolean `silent` parameter of the <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> method is respected.</span></span> <span data-ttu-id="9b793-103">如果此參數設定為 [`true`]，則不會顯示 PIN 提示。</span><span class="sxs-lookup"><span data-stu-id="9b793-103">A PIN prompt is not shown if this parameter is set to `true`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="9b793-104">變更描述</span><span class="sxs-lookup"><span data-stu-id="9b793-104">Change description</span></span>

<span data-ttu-id="9b793-105">在 .NET Framework 中，會忽略 <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> 方法的 `silent` 參數，並在提供者要求時一律顯示 PIN 提示。</span><span class="sxs-lookup"><span data-stu-id="9b793-105">In .NET Framework, the `silent` parameter of the <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> method is ignored, and a PIN prompt is always shown if required by the provider.</span></span> <span data-ttu-id="9b793-106">在 .NET Core 中，會遵守 `silent` 參數，如果設定為 `true`，則永遠不會顯示 PIN 提示（即使提供者需要）。</span><span class="sxs-lookup"><span data-stu-id="9b793-106">In .NET Core, the `silent` parameter is respected, and if set to `true`, a PIN prompt is never shown, even if it's required by the provider.</span></span>

<span data-ttu-id="9b793-107">2\.1 版的 .NET Core 中引進了 CMS/PKCS #7 訊息的支援。</span><span class="sxs-lookup"><span data-stu-id="9b793-107">Support for CMS/PKCS #7 messages was introduced into .NET Core in version 2.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9b793-108">引進的版本</span><span class="sxs-lookup"><span data-stu-id="9b793-108">Version introduced</span></span>

<span data-ttu-id="9b793-109">2.1</span><span class="sxs-lookup"><span data-stu-id="9b793-109">2.1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9b793-110">建議的動作</span><span class="sxs-lookup"><span data-stu-id="9b793-110">Recommended action</span></span>

<span data-ttu-id="9b793-111">為確保在需要時顯示 PIN 提示，桌面應用程式應該呼叫 <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> 並將布林參數設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="9b793-111">To ensure a PIN prompt appears if required, desktop applications should call <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> and set the Boolean parameter to `false`.</span></span> <span data-ttu-id="9b793-112">產生的行為等同于 .NET Framework，不論是否在該處停用無訊息內容。</span><span class="sxs-lookup"><span data-stu-id="9b793-112">The resulting behavior is the same as on .NET Framework regardless of whether the silent context is disabled there.</span></span>

### <a name="category"></a><span data-ttu-id="9b793-113">類別</span><span class="sxs-lookup"><span data-stu-id="9b793-113">Category</span></span>

<span data-ttu-id="9b793-114">Cryptography</span><span class="sxs-lookup"><span data-stu-id="9b793-114">Cryptography</span></span>

### <a name="affected-apis"></a><span data-ttu-id="9b793-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="9b793-115">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)`

-->

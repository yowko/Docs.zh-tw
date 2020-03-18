---
ms.openlocfilehash: 9583d868ee01117d7bd6e465e7d89a734489d1a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449208"
---
### <a name="boolean-parameter-of-signedcmscomputesignature-is-respected"></a><span data-ttu-id="e2512-101">簽名Cms的布林參數.計算簽名得到尊重</span><span class="sxs-lookup"><span data-stu-id="e2512-101">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>

<span data-ttu-id="e2512-102">在 .NET Core 中`silent`，<xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType>該方法的布林參數得到尊重。</span><span class="sxs-lookup"><span data-stu-id="e2512-102">In .NET Core, the Boolean `silent` parameter of the <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> method is respected.</span></span> <span data-ttu-id="e2512-103">如果此參數設置為`true`，則不顯示 PIN 提示。</span><span class="sxs-lookup"><span data-stu-id="e2512-103">A PIN prompt is not shown if this parameter is set to `true`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e2512-104">變更描述</span><span class="sxs-lookup"><span data-stu-id="e2512-104">Change description</span></span>

<span data-ttu-id="e2512-105">在 .NET 框架`silent`中，將<xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType>忽略該方法的參數，並且如果提供程式需要，則始終顯示 PIN 提示。</span><span class="sxs-lookup"><span data-stu-id="e2512-105">In .NET Framework, the `silent` parameter of the <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> method is ignored, and a PIN prompt is always shown if required by the provider.</span></span> <span data-ttu-id="e2512-106">在 .NET Core`silent`中，該參數受到尊重，如果`true`設置為 ，則永遠不會顯示 PIN 提示符，即使提供程式需要 PIN 提示符也是如此。</span><span class="sxs-lookup"><span data-stu-id="e2512-106">In .NET Core, the `silent` parameter is respected, and if set to `true`, a PIN prompt is never shown, even if it's required by the provider.</span></span>

<span data-ttu-id="e2512-107">對 CMS/PKCS 的支援#7消息在 2.1 版中引入到 .NET Core 中。</span><span class="sxs-lookup"><span data-stu-id="e2512-107">Support for CMS/PKCS #7 messages was introduced into .NET Core in version 2.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e2512-108">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="e2512-108">Version introduced</span></span>

<span data-ttu-id="e2512-109">2.1</span><span class="sxs-lookup"><span data-stu-id="e2512-109">2.1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e2512-110">建議的動作</span><span class="sxs-lookup"><span data-stu-id="e2512-110">Recommended action</span></span>

<span data-ttu-id="e2512-111">為確保在需要時出現 PIN 提示，桌面應用程式應調用<xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType>並將布林參數設置為`false`。</span><span class="sxs-lookup"><span data-stu-id="e2512-111">To ensure a PIN prompt appears if required, desktop applications should call <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> and set the Boolean parameter to `false`.</span></span> <span data-ttu-id="e2512-112">無論靜默上下文是否在那裡被禁用，生成的行為與 .NET 框架上的行為相同。</span><span class="sxs-lookup"><span data-stu-id="e2512-112">The resulting behavior is the same as on .NET Framework regardless of whether the silent context is disabled there.</span></span>

### <a name="category"></a><span data-ttu-id="e2512-113">類別</span><span class="sxs-lookup"><span data-stu-id="e2512-113">Category</span></span>

<span data-ttu-id="e2512-114">Cryptography</span><span class="sxs-lookup"><span data-stu-id="e2512-114">Cryptography</span></span>

### <a name="affected-apis"></a><span data-ttu-id="e2512-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="e2512-115">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)`

-->

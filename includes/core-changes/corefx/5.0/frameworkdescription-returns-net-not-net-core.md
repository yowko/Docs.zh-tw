---
ms.openlocfilehash: 80d13609f1b02ae0ac875b2028e745670bb8f503
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050558"
---
### <a name="frameworkdescriptions-value-is-net-instead-of-net-core"></a><span data-ttu-id="82a35-101">FrameworkDescription 的值是 .NET 而不是 .NET Core</span><span class="sxs-lookup"><span data-stu-id="82a35-101">FrameworkDescription's value is .NET instead of .NET Core</span></span>

<span data-ttu-id="82a35-102"><xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> 現在會傳回 ".NET" 而不是 ".NET Core"。</span><span class="sxs-lookup"><span data-stu-id="82a35-102"><xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> now returns ".NET" instead of ".NET Core".</span></span>

#### <a name="change-description"></a><span data-ttu-id="82a35-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="82a35-103">Change description</span></span>

<span data-ttu-id="82a35-104">在先前的 .NET 版本中，會傳回 <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> ".Net Core" 做為描述字串的一部分，例如， `.NET Core 3.1.1` 。</span><span class="sxs-lookup"><span data-stu-id="82a35-104">In previous .NET versions, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> returns ".NET Core" as part of the description string, for example, `.NET Core 3.1.1`.</span></span>

<span data-ttu-id="82a35-105">從 .NET 5.0 開始，會傳回 <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> ".net" 做為描述字串的一部分，例如， `.NET 5.0.0` 。</span><span class="sxs-lookup"><span data-stu-id="82a35-105">Starting in .NET 5.0, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> returns ".NET" as part of the description string, for example, `.NET 5.0.0`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="82a35-106">變更的原因</span><span class="sxs-lookup"><span data-stu-id="82a35-106">Reason for change</span></span>

<span data-ttu-id="82a35-107">使用 .NET 5 `netcoreapp` 時，會將取代 `net` 為簡短的目標架構名字。</span><span class="sxs-lookup"><span data-stu-id="82a35-107">With .NET 5, `netcoreapp` is replaced by `net` as the short target-framework moniker.</span></span> <span data-ttu-id="82a35-108">為了保持一致性，也更新了架構的描述。</span><span class="sxs-lookup"><span data-stu-id="82a35-108">For consistency, the framework's description has also been updated.</span></span> <span data-ttu-id="82a35-109">這項變更是表面，因為 `FrameworkName` 未編碼于屬性中的任何其他位置 <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="82a35-109">The change is cosmetic, as the `FrameworkName` isn't encoded anywhere else than in the <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> property.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="82a35-110">引進的版本</span><span class="sxs-lookup"><span data-stu-id="82a35-110">Version introduced</span></span>

<span data-ttu-id="82a35-111">5.0</span><span class="sxs-lookup"><span data-stu-id="82a35-111">5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="82a35-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="82a35-112">Recommended action</span></span>

<span data-ttu-id="82a35-113">更新在傳回的字串中搜尋 ".NET Core" 的任何程式碼 <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription> 。</span><span class="sxs-lookup"><span data-stu-id="82a35-113">Update any code that searches for ".NET Core" in the string returned by <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription>.</span></span>

#### <a name="category"></a><span data-ttu-id="82a35-114">類別</span><span class="sxs-lookup"><span data-stu-id="82a35-114">Category</span></span>

<span data-ttu-id="82a35-115">Core .NET 程式庫</span><span class="sxs-lookup"><span data-stu-id="82a35-115">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="82a35-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="82a35-116">Affected APIs</span></span>

- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->

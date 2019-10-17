---
ms.openlocfilehash: 1c9c899d77dd69e185281d98bfec18ce73d80815
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393932"
---
### <a name="kestrel-empty-https-assembly-removed"></a><span data-ttu-id="43d9a-101">Kestrel：已移除空的 HTTPS 元件</span><span class="sxs-lookup"><span data-stu-id="43d9a-101">Kestrel: Empty HTTPS assembly removed</span></span>

<span data-ttu-id="43d9a-102">元件 <xref:Microsoft.AspNetCore.Server.Kestrel.Https?displayProperty=fullName> 已移除。</span><span class="sxs-lookup"><span data-stu-id="43d9a-102">The assembly <xref:Microsoft.AspNetCore.Server.Kestrel.Https?displayProperty=fullName> has been removed.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="43d9a-103">引進的版本</span><span class="sxs-lookup"><span data-stu-id="43d9a-103">Version introduced</span></span>

<span data-ttu-id="43d9a-104">3.0</span><span class="sxs-lookup"><span data-stu-id="43d9a-104">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="43d9a-105">變更的原因</span><span class="sxs-lookup"><span data-stu-id="43d9a-105">Reason for change</span></span>

<span data-ttu-id="43d9a-106">在 ASP.NET Core 2.1 中，`Microsoft.AspNetCore.Server.Kestrel.Https` 的內容已移至 <xref:Microsoft.AspNetCore.Server.Kestrel.Core?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="43d9a-106">In ASP.NET Core 2.1, the contents of `Microsoft.AspNetCore.Server.Kestrel.Https` were moved to <xref:Microsoft.AspNetCore.Server.Kestrel.Core?displayProperty=fullName>.</span></span> <span data-ttu-id="43d9a-107">這項變更是使用 `[TypeForwardedTo]` 屬性，以不間斷的方式完成。</span><span class="sxs-lookup"><span data-stu-id="43d9a-107">This change was done in a non-breaking way using `[TypeForwardedTo]` attributes.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="43d9a-108">建議的動作</span><span class="sxs-lookup"><span data-stu-id="43d9a-108">Recommended action</span></span>

- <span data-ttu-id="43d9a-109">參考 `Microsoft.AspNetCore.Server.Kestrel.Https` 2.0 的程式庫應該將所有 ASP.NET Core 相依性更新為2.1 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="43d9a-109">Libraries referencing `Microsoft.AspNetCore.Server.Kestrel.Https` 2.0 should update all ASP.NET Core dependencies to 2.1 or later.</span></span> <span data-ttu-id="43d9a-110">否則，它們可能會在載入 ASP.NET Core 3.0 應用程式時中斷。</span><span class="sxs-lookup"><span data-stu-id="43d9a-110">Otherwise, they may break when loaded into an ASP.NET Core 3.0 app.</span></span>
- <span data-ttu-id="43d9a-111">以 ASP.NET Core 2.1 和更新版本為目標的應用程式和程式庫，應移除任何 `Microsoft.AspNetCore.Server.Kestrel.Https` NuGet 套件的直接參考。</span><span class="sxs-lookup"><span data-stu-id="43d9a-111">Apps and libraries targeting ASP.NET Core 2.1 and later should remove any direct references to the `Microsoft.AspNetCore.Server.Kestrel.Https` NuGet package.</span></span>

#### <a name="category"></a><span data-ttu-id="43d9a-112">分類</span><span class="sxs-lookup"><span data-stu-id="43d9a-112">Category</span></span>

<span data-ttu-id="43d9a-113">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="43d9a-113">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="43d9a-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="43d9a-114">Affected APIs</span></span>

<span data-ttu-id="43d9a-115">無</span><span class="sxs-lookup"><span data-stu-id="43d9a-115">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

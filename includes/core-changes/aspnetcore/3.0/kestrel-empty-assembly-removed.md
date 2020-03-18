---
ms.openlocfilehash: 1c9c899d77dd69e185281d98bfec18ce73d80815
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72393932"
---
### <a name="kestrel-empty-https-assembly-removed"></a><span data-ttu-id="0f62a-101">Kestrel： 空 HTTPS 程式集已刪除</span><span class="sxs-lookup"><span data-stu-id="0f62a-101">Kestrel: Empty HTTPS assembly removed</span></span>

<span data-ttu-id="0f62a-102">程式集<xref:Microsoft.AspNetCore.Server.Kestrel.Https?displayProperty=fullName>已被刪除。</span><span class="sxs-lookup"><span data-stu-id="0f62a-102">The assembly <xref:Microsoft.AspNetCore.Server.Kestrel.Https?displayProperty=fullName> has been removed.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0f62a-103">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="0f62a-103">Version introduced</span></span>

<span data-ttu-id="0f62a-104">3.0</span><span class="sxs-lookup"><span data-stu-id="0f62a-104">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="0f62a-105">更改原因</span><span class="sxs-lookup"><span data-stu-id="0f62a-105">Reason for change</span></span>

<span data-ttu-id="0f62a-106">在 ASP.NET 核心 2.1`Microsoft.AspNetCore.Server.Kestrel.Https`中，的內容<xref:Microsoft.AspNetCore.Server.Kestrel.Core?displayProperty=fullName>被移動到 。</span><span class="sxs-lookup"><span data-stu-id="0f62a-106">In ASP.NET Core 2.1, the contents of `Microsoft.AspNetCore.Server.Kestrel.Https` were moved to <xref:Microsoft.AspNetCore.Server.Kestrel.Core?displayProperty=fullName>.</span></span> <span data-ttu-id="0f62a-107">此更改使用`[TypeForwardedTo]`屬性以非中斷的方式完成。</span><span class="sxs-lookup"><span data-stu-id="0f62a-107">This change was done in a non-breaking way using `[TypeForwardedTo]` attributes.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0f62a-108">建議的動作</span><span class="sxs-lookup"><span data-stu-id="0f62a-108">Recommended action</span></span>

- <span data-ttu-id="0f62a-109">引用 2.0 的`Microsoft.AspNetCore.Server.Kestrel.Https`庫應將所有ASP.NET核心依賴項更新為 2.1 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="0f62a-109">Libraries referencing `Microsoft.AspNetCore.Server.Kestrel.Https` 2.0 should update all ASP.NET Core dependencies to 2.1 or later.</span></span> <span data-ttu-id="0f62a-110">否則，它們可能會在載入到 ASP.NET 酷睿 3.0 應用中時中斷。</span><span class="sxs-lookup"><span data-stu-id="0f62a-110">Otherwise, they may break when loaded into an ASP.NET Core 3.0 app.</span></span>
- <span data-ttu-id="0f62a-111">面向ASP.NET Core 2.1 和更高版本的應用和庫應刪除對`Microsoft.AspNetCore.Server.Kestrel.Https`NuGet 包的任何直接引用。</span><span class="sxs-lookup"><span data-stu-id="0f62a-111">Apps and libraries targeting ASP.NET Core 2.1 and later should remove any direct references to the `Microsoft.AspNetCore.Server.Kestrel.Https` NuGet package.</span></span>

#### <a name="category"></a><span data-ttu-id="0f62a-112">類別</span><span class="sxs-lookup"><span data-stu-id="0f62a-112">Category</span></span>

<span data-ttu-id="0f62a-113">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0f62a-113">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0f62a-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="0f62a-114">Affected APIs</span></span>

<span data-ttu-id="0f62a-115">None</span><span class="sxs-lookup"><span data-stu-id="0f62a-115">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

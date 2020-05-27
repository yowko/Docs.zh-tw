---
ms.openlocfilehash: c4e7864262a11aafa4b7f1f4bdf632fbf084c560
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507070"
---
### <a name="http-kestrel-and-iis-badhttprequestexception-types-marked-obsolete-and-replaced"></a><span data-ttu-id="84b7a-101">HTTP： Kestrel 和 IIS BadHttpRequestException 類型已標記為過時並被取代</span><span class="sxs-lookup"><span data-stu-id="84b7a-101">HTTP: Kestrel and IIS BadHttpRequestException types marked obsolete and replaced</span></span>

<span data-ttu-id="84b7a-102">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`和已 `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` 標示為過時，並已變更為衍生自 `Microsoft.AspNetCore.Http.BadHttpRequestException` 。</span><span class="sxs-lookup"><span data-stu-id="84b7a-102">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` and `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` have been marked obsolete and changed to derive from `Microsoft.AspNetCore.Http.BadHttpRequestException`.</span></span> <span data-ttu-id="84b7a-103">Kestrel 和 IIS 伺服器仍然會擲回舊的例外狀況類型，以提供回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="84b7a-103">The Kestrel and IIS servers still throw their old exception types for backwards compatibility.</span></span> <span data-ttu-id="84b7a-104">未來的版本將移除過時的類型。</span><span class="sxs-lookup"><span data-stu-id="84b7a-104">The obsolete types will be removed in a future release.</span></span>

<span data-ttu-id="84b7a-105">如需討論，請參閱[dotnet/aspnetcore # 20614](https://github.com/dotnet/aspnetcore/issues/20614)。</span><span class="sxs-lookup"><span data-stu-id="84b7a-105">For discussion, see [dotnet/aspnetcore#20614](https://github.com/dotnet/aspnetcore/issues/20614).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="84b7a-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="84b7a-106">Version introduced</span></span>

<span data-ttu-id="84b7a-107">5.0 Preview 4</span><span class="sxs-lookup"><span data-stu-id="84b7a-107">5.0 Preview 4</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="84b7a-108">舊的行為</span><span class="sxs-lookup"><span data-stu-id="84b7a-108">Old behavior</span></span>

<span data-ttu-id="84b7a-109">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`和 `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` 衍生自 <xref:System.IO.IOException?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="84b7a-109">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` and `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` derived from <xref:System.IO.IOException?displayProperty=nameWithType>.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="84b7a-110">新的行為</span><span class="sxs-lookup"><span data-stu-id="84b7a-110">New behavior</span></span>

<span data-ttu-id="84b7a-111">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`和 `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` 已經過時。</span><span class="sxs-lookup"><span data-stu-id="84b7a-111">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` and `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` are obsolete.</span></span> <span data-ttu-id="84b7a-112">類型也衍生自 `Microsoft.AspNetCore.Http.BadHttpRequestException` ，其衍生自 `System.IO.IOException` 。</span><span class="sxs-lookup"><span data-stu-id="84b7a-112">The types also derive from `Microsoft.AspNetCore.Http.BadHttpRequestException`, which derives from `System.IO.IOException`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="84b7a-113">變更的原因</span><span class="sxs-lookup"><span data-stu-id="84b7a-113">Reason for change</span></span>

<span data-ttu-id="84b7a-114">已進行變更：</span><span class="sxs-lookup"><span data-stu-id="84b7a-114">The change was made to:</span></span>

* <span data-ttu-id="84b7a-115">合併重複的類型。</span><span class="sxs-lookup"><span data-stu-id="84b7a-115">Consolidate duplicate types.</span></span>
* <span data-ttu-id="84b7a-116">跨伺服器的整合行為。</span><span class="sxs-lookup"><span data-stu-id="84b7a-116">Unify behavior across server implementations.</span></span>

<span data-ttu-id="84b7a-117">應用程式現在可以 `Microsoft.AspNetCore.Http.BadHttpRequestException` 在使用 Kestrel 或 IIS 時攔截基底例外狀況。</span><span class="sxs-lookup"><span data-stu-id="84b7a-117">An app can now catch the base exception `Microsoft.AspNetCore.Http.BadHttpRequestException` when using either Kestrel or IIS.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="84b7a-118">建議的動作</span><span class="sxs-lookup"><span data-stu-id="84b7a-118">Recommended action</span></span>

<span data-ttu-id="84b7a-119">以取代和的使用 `Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` 方式 `Microsoft.AspNetCore.Http.BadHttpRequestException` 。</span><span class="sxs-lookup"><span data-stu-id="84b7a-119">Replace usages of `Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` and `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` with `Microsoft.AspNetCore.Http.BadHttpRequestException`.</span></span>

#### <a name="category"></a><span data-ttu-id="84b7a-120">類別</span><span class="sxs-lookup"><span data-stu-id="84b7a-120">Category</span></span>

<span data-ttu-id="84b7a-121">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="84b7a-121">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="84b7a-122">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="84b7a-122">Affected APIs</span></span>

- [<span data-ttu-id="84b7a-123">AspNetCore. IIS. BadHttpRequestException</span><span class="sxs-lookup"><span data-stu-id="84b7a-123">Microsoft.AspNetCore.Server.IIS.BadHttpRequestException</span></span>](/dotnet/api/microsoft.aspnetcore.server.iis.badhttprequestexception?view=aspnetcore-3.1)
- [<span data-ttu-id="84b7a-124">AspNetCore. Kestrel. BadHttpRequestException</span><span class="sxs-lookup"><span data-stu-id="84b7a-124">Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.badhttprequestexception?view=aspnetcore-1.1)

<!--

#### Affected APIs

- `T:Microsoft.AspNetCore.Server.IIS.BadHttpRequestException`
- `T:Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`

-->

---
ms.openlocfilehash: 29908ed916690e67db3cc5d72ebe1b1c6aea45c6
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325231"
---
### <a name="iis-urlrewrite-middleware-query-strings-are-preserved"></a><span data-ttu-id="d657f-101">IIS： UrlRewrite 中介軟體查詢字串會保留</span><span class="sxs-lookup"><span data-stu-id="d657f-101">IIS: UrlRewrite middleware query strings are preserved</span></span>

<span data-ttu-id="d657f-102">IIS UrlRewrite 中介軟體瑕疵使查詢字串無法在重寫規則中保留。</span><span class="sxs-lookup"><span data-stu-id="d657f-102">An IIS UrlRewrite middleware defect prevented the query string from being preserved in rewrite rules.</span></span> <span data-ttu-id="d657f-103">已修正該瑕疵，以維持與 IIS UrlRewrite 模組行為的一致性。</span><span class="sxs-lookup"><span data-stu-id="d657f-103">That defect has been fixed to maintain consistency with the IIS UrlRewrite Module's behavior.</span></span>

<span data-ttu-id="d657f-104">如需討論，請參閱 issue [dotnet/aspnetcore # 22972](https://github.com/dotnet/aspnetcore/issues/22972)。</span><span class="sxs-lookup"><span data-stu-id="d657f-104">For discussion, see issue [dotnet/aspnetcore#22972](https://github.com/dotnet/aspnetcore/issues/22972).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d657f-105">引進的版本</span><span class="sxs-lookup"><span data-stu-id="d657f-105">Version introduced</span></span>

<span data-ttu-id="d657f-106">ASP.NET Core 5.0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="d657f-106">ASP.NET Core 5.0 Preview 7</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="d657f-107">舊的行為</span><span class="sxs-lookup"><span data-stu-id="d657f-107">Old behavior</span></span>

<span data-ttu-id="d657f-108">請考慮下列重寫規則：</span><span class="sxs-lookup"><span data-stu-id="d657f-108">Consider the following rewrite rule:</span></span>

```xml
<rule name="MyRule" stopProcessing="true">
  <match url="^about" />
  <action type="Redirect" url="/contact" redirectType="Temporary" appendQueryString="true" />
</rule>
```

<span data-ttu-id="d657f-109">上述規則不會附加查詢字串。</span><span class="sxs-lookup"><span data-stu-id="d657f-109">The preceding rule doesn't append the query string.</span></span> <span data-ttu-id="d657f-110">URI，例如重新 `/about?id=1` 導向至， `/contact` 而不是 `/contact?id=1` 。</span><span class="sxs-lookup"><span data-stu-id="d657f-110">A URI like `/about?id=1` redirects to `/contact` instead of `/contact?id=1`.</span></span> <span data-ttu-id="d657f-111">`appendQueryString`屬性的預設值 `true` 也是。</span><span class="sxs-lookup"><span data-stu-id="d657f-111">The `appendQueryString` attribute defaults to `true` as well.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="d657f-112">新的行為</span><span class="sxs-lookup"><span data-stu-id="d657f-112">New behavior</span></span>

<span data-ttu-id="d657f-113">查詢字串會保留下來。</span><span class="sxs-lookup"><span data-stu-id="d657f-113">The query string is preserved.</span></span> <span data-ttu-id="d657f-114">來自[舊行為](#old-behavior)之範例中的 URI 會是 `/contact?id=1` 。</span><span class="sxs-lookup"><span data-stu-id="d657f-114">The URI from the example in [Old behavior](#old-behavior) would be `/contact?id=1`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d657f-115">變更的原因</span><span class="sxs-lookup"><span data-stu-id="d657f-115">Reason for change</span></span>

<span data-ttu-id="d657f-116">舊的行為不符合 IIS UrlRewrite 模組的行為。</span><span class="sxs-lookup"><span data-stu-id="d657f-116">The old behavior didn't match the IIS UrlRewrite Module's behavior.</span></span> <span data-ttu-id="d657f-117">為了支援中介軟體和模組之間的移植，其目標是要維持一致的行為。</span><span class="sxs-lookup"><span data-stu-id="d657f-117">To support porting between the middleware and module, the goal is to maintain consistent behaviors.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d657f-118">建議的動作</span><span class="sxs-lookup"><span data-stu-id="d657f-118">Recommended action</span></span>

<span data-ttu-id="d657f-119">如果偏好移除查詢字串的行為，請將 `action` 元素設定為 `appendQueryString="false"` 。</span><span class="sxs-lookup"><span data-stu-id="d657f-119">If the behavior of removing the query string is preferred, set the `action` element to `appendQueryString="false"`.</span></span>

#### <a name="category"></a><span data-ttu-id="d657f-120">類別</span><span class="sxs-lookup"><span data-stu-id="d657f-120">Category</span></span>

<span data-ttu-id="d657f-121">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d657f-121">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d657f-122">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="d657f-122">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Rewrite.IISUrlRewriteOptionsExtensions.AddIISUrlRewrite%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Rewrite.IISUrlRewriteOptionsExtensions.AddIISUrlRewrite`

-->

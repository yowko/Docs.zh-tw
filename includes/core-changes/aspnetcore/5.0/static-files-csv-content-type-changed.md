---
ms.openlocfilehash: 8e077d5cde6e824af5aac3742308593f1d91dd92
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391178"
---
### <a name="static-files-csv-content-type-changed-to-standards-compliant"></a><span data-ttu-id="294e9-101">靜態檔：CSV 內容類型更改為符合標準</span><span class="sxs-lookup"><span data-stu-id="294e9-101">Static files: CSV content type changed to standards-compliant</span></span>

<span data-ttu-id="294e9-102">在 ASP.NET Core 5.0`Content-Type`中，[靜態檔中介軟體](/aspnet/core/fundamentals/static-files)用於 *.csv*檔的預設回應標頭值已更改為符合標準的值`text/csv`。</span><span class="sxs-lookup"><span data-stu-id="294e9-102">In ASP.NET Core 5.0, the default `Content-Type` response header value that the [Static File Middleware](/aspnet/core/fundamentals/static-files) uses for *.csv* files has changed to the standards-compliant value `text/csv`.</span></span>

<span data-ttu-id="294e9-103">有關此問題的討論，請參閱[dotnet/aspnetcore_17385](https://github.com/dotnet/AspNetCore/issues/17385)。</span><span class="sxs-lookup"><span data-stu-id="294e9-103">For discussion on this issue, see [dotnet/aspnetcore#17385](https://github.com/dotnet/AspNetCore/issues/17385).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="294e9-104">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="294e9-104">Version introduced</span></span>

<span data-ttu-id="294e9-105">5.0 預覽 1</span><span class="sxs-lookup"><span data-stu-id="294e9-105">5.0 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="294e9-106">舊的行為</span><span class="sxs-lookup"><span data-stu-id="294e9-106">Old behavior</span></span>

<span data-ttu-id="294e9-107">使用了`Content-Type`標頭值`application/octet-stream`。</span><span class="sxs-lookup"><span data-stu-id="294e9-107">The `Content-Type` header value `application/octet-stream` was used.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="294e9-108">新的行為</span><span class="sxs-lookup"><span data-stu-id="294e9-108">New behavior</span></span>

<span data-ttu-id="294e9-109">使用`Content-Type`標頭值`text/csv`。</span><span class="sxs-lookup"><span data-stu-id="294e9-109">The `Content-Type` header value `text/csv` is used.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="294e9-110">更改原因</span><span class="sxs-lookup"><span data-stu-id="294e9-110">Reason for change</span></span>

<span data-ttu-id="294e9-111">符合[RFC 7111](https://tools.ietf.org/html/rfc7111#section-5.1)標準。</span><span class="sxs-lookup"><span data-stu-id="294e9-111">Compliance with the [RFC 7111](https://tools.ietf.org/html/rfc7111#section-5.1) standard.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="294e9-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="294e9-112">Recommended action</span></span>

<span data-ttu-id="294e9-113">如果此更改影響你的應用，則可以自訂檔副檔名到 MIME 類型映射。</span><span class="sxs-lookup"><span data-stu-id="294e9-113">If this change impacts your app, you can customize the file extension-to-MIME type mapping.</span></span> <span data-ttu-id="294e9-114">要還原到`application/octet-stream`MIME 類型，<xref:Microsoft.AspNetCore.Builder.StaticFileExtensions.UseStaticFiles%2A>請修改 方法`Startup.Configure`調用。</span><span class="sxs-lookup"><span data-stu-id="294e9-114">To revert to the `application/octet-stream` MIME type, modify the <xref:Microsoft.AspNetCore.Builder.StaticFileExtensions.UseStaticFiles%2A> method call in `Startup.Configure`.</span></span> <span data-ttu-id="294e9-115">例如：</span><span class="sxs-lookup"><span data-stu-id="294e9-115">For example:</span></span>

```csharp
var provider = new FileExtensionContentTypeProvider();
provider.Mappings[".csv"] = MediaTypeNames.Application.Octet;

app.UseStaticFiles(new StaticFileOptions
{
    ContentTypeProvider = provider
});
```

<span data-ttu-id="294e9-116">有關自訂映射的詳細資訊，請參閱[檔擴展內容類型提供程式](/aspnet/core/fundamentals/static-files#fileextensioncontenttypeprovider)。</span><span class="sxs-lookup"><span data-stu-id="294e9-116">For more information on customizing the mapping, see [FileExtensionContentTypeProvider](/aspnet/core/fundamentals/static-files#fileextensioncontenttypeprovider).</span></span>

#### <a name="category"></a><span data-ttu-id="294e9-117">類別</span><span class="sxs-lookup"><span data-stu-id="294e9-117">Category</span></span>

<span data-ttu-id="294e9-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="294e9-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="294e9-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="294e9-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider`

-->

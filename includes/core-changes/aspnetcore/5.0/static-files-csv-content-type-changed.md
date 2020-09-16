---
ms.openlocfilehash: 8e077d5cde6e824af5aac3742308593f1d91dd92
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391178"
---
### <a name="static-files-csv-content-type-changed-to-standards-compliant"></a><span data-ttu-id="b1793-101">靜態檔案： CSV 內容類型已變更為符合標準</span><span class="sxs-lookup"><span data-stu-id="b1793-101">Static files: CSV content type changed to standards-compliant</span></span>

<span data-ttu-id="b1793-102">在 ASP.NET Core 5.0 中， `Content-Type` [靜態檔案中介軟體](/aspnet/core/fundamentals/static-files) 用於 *.csv* 檔案的預設回應標頭值已變更為符合標準規範的值 `text/csv` 。</span><span class="sxs-lookup"><span data-stu-id="b1793-102">In ASP.NET Core 5.0, the default `Content-Type` response header value that the [Static File Middleware](/aspnet/core/fundamentals/static-files) uses for *.csv* files has changed to the standards-compliant value `text/csv`.</span></span>

<span data-ttu-id="b1793-103">如需此問題的討論，請參閱 [dotnet/aspnetcore # 17385](https://github.com/dotnet/AspNetCore/issues/17385)。</span><span class="sxs-lookup"><span data-stu-id="b1793-103">For discussion on this issue, see [dotnet/aspnetcore#17385](https://github.com/dotnet/AspNetCore/issues/17385).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b1793-104">引進的版本</span><span class="sxs-lookup"><span data-stu-id="b1793-104">Version introduced</span></span>

<span data-ttu-id="b1793-105">5.0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="b1793-105">5.0 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="b1793-106">舊的行為</span><span class="sxs-lookup"><span data-stu-id="b1793-106">Old behavior</span></span>

<span data-ttu-id="b1793-107">`Content-Type`已使用標頭值 `application/octet-stream` 。</span><span class="sxs-lookup"><span data-stu-id="b1793-107">The `Content-Type` header value `application/octet-stream` was used.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="b1793-108">新的行為</span><span class="sxs-lookup"><span data-stu-id="b1793-108">New behavior</span></span>

<span data-ttu-id="b1793-109">`Content-Type`使用標頭值 `text/csv` 。</span><span class="sxs-lookup"><span data-stu-id="b1793-109">The `Content-Type` header value `text/csv` is used.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="b1793-110">變更的原因</span><span class="sxs-lookup"><span data-stu-id="b1793-110">Reason for change</span></span>

<span data-ttu-id="b1793-111">符合 [RFC 7111](https://tools.ietf.org/html/rfc7111#section-5.1) 標準。</span><span class="sxs-lookup"><span data-stu-id="b1793-111">Compliance with the [RFC 7111](https://tools.ietf.org/html/rfc7111#section-5.1) standard.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b1793-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="b1793-112">Recommended action</span></span>

<span data-ttu-id="b1793-113">如果此變更會影響您的應用程式，您可以自訂副檔名至 MIME 類型的對應。</span><span class="sxs-lookup"><span data-stu-id="b1793-113">If this change impacts your app, you can customize the file extension-to-MIME type mapping.</span></span> <span data-ttu-id="b1793-114">若要還原成 `application/octet-stream` MIME 型別，請修改 <xref:Microsoft.AspNetCore.Builder.StaticFileExtensions.UseStaticFiles%2A> 中的方法呼叫 `Startup.Configure` 。</span><span class="sxs-lookup"><span data-stu-id="b1793-114">To revert to the `application/octet-stream` MIME type, modify the <xref:Microsoft.AspNetCore.Builder.StaticFileExtensions.UseStaticFiles%2A> method call in `Startup.Configure`.</span></span> <span data-ttu-id="b1793-115">例如：</span><span class="sxs-lookup"><span data-stu-id="b1793-115">For example:</span></span>

```csharp
var provider = new FileExtensionContentTypeProvider();
provider.Mappings[".csv"] = MediaTypeNames.Application.Octet;

app.UseStaticFiles(new StaticFileOptions
{
    ContentTypeProvider = provider
});
```

<span data-ttu-id="b1793-116">如需自訂對應的詳細資訊，請參閱 [FileExtensionContentTypeProvider](/aspnet/core/fundamentals/static-files#fileextensioncontenttypeprovider)。</span><span class="sxs-lookup"><span data-stu-id="b1793-116">For more information on customizing the mapping, see [FileExtensionContentTypeProvider](/aspnet/core/fundamentals/static-files#fileextensioncontenttypeprovider).</span></span>

#### <a name="category"></a><span data-ttu-id="b1793-117">類別</span><span class="sxs-lookup"><span data-stu-id="b1793-117">Category</span></span>

<span data-ttu-id="b1793-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b1793-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b1793-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="b1793-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider`

-->

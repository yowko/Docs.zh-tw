---
title: 重大變更：靜態檔案： CSV 內容類型已變更為符合標準規範
description: 瞭解 ASP.NET Core 5.0 中標題為靜態檔案的重大變更： CSV 內容類型已變更為符合標準規範
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: c94a0cf213970d20559b7c061d8be220b43961e0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760796"
---
# <a name="static-files-csv-content-type-changed-to-standards-compliant"></a><span data-ttu-id="d0fde-103">靜態檔案： CSV 內容類型已變更為符合標準</span><span class="sxs-lookup"><span data-stu-id="d0fde-103">Static files: CSV content type changed to standards-compliant</span></span>

<span data-ttu-id="d0fde-104">在 ASP.NET Core 5.0 中， `Content-Type` [靜態檔案中介軟體](/aspnet/core/fundamentals/static-files) 用於 *.csv* 檔案的預設回應標頭值已變更為符合標準規範的值 `text/csv` 。</span><span class="sxs-lookup"><span data-stu-id="d0fde-104">In ASP.NET Core 5.0, the default `Content-Type` response header value that the [Static File Middleware](/aspnet/core/fundamentals/static-files) uses for *.csv* files has changed to the standards-compliant value `text/csv`.</span></span>

<span data-ttu-id="d0fde-105">如需此問題的討論，請參閱 [dotnet/aspnetcore # 17385](https://github.com/dotnet/AspNetCore/issues/17385)。</span><span class="sxs-lookup"><span data-stu-id="d0fde-105">For discussion on this issue, see [dotnet/aspnetcore#17385](https://github.com/dotnet/AspNetCore/issues/17385).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="d0fde-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="d0fde-106">Version introduced</span></span>

<span data-ttu-id="d0fde-107">5.0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="d0fde-107">5.0 Preview 1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="d0fde-108">舊的行為</span><span class="sxs-lookup"><span data-stu-id="d0fde-108">Old behavior</span></span>

<span data-ttu-id="d0fde-109">`Content-Type`已使用標頭值 `application/octet-stream` 。</span><span class="sxs-lookup"><span data-stu-id="d0fde-109">The `Content-Type` header value `application/octet-stream` was used.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="d0fde-110">新的行為</span><span class="sxs-lookup"><span data-stu-id="d0fde-110">New behavior</span></span>

<span data-ttu-id="d0fde-111">`Content-Type`使用標頭值 `text/csv` 。</span><span class="sxs-lookup"><span data-stu-id="d0fde-111">The `Content-Type` header value `text/csv` is used.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="d0fde-112">變更的原因</span><span class="sxs-lookup"><span data-stu-id="d0fde-112">Reason for change</span></span>

<span data-ttu-id="d0fde-113">符合 [RFC 7111](https://tools.ietf.org/html/rfc7111#section-5.1) 標準。</span><span class="sxs-lookup"><span data-stu-id="d0fde-113">Compliance with the [RFC 7111](https://tools.ietf.org/html/rfc7111#section-5.1) standard.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="d0fde-114">建議的動作</span><span class="sxs-lookup"><span data-stu-id="d0fde-114">Recommended action</span></span>

<span data-ttu-id="d0fde-115">如果此變更會影響您的應用程式，您可以自訂副檔名至 MIME 類型的對應。</span><span class="sxs-lookup"><span data-stu-id="d0fde-115">If this change impacts your app, you can customize the file extension-to-MIME type mapping.</span></span> <span data-ttu-id="d0fde-116">若要還原成 `application/octet-stream` MIME 型別，請修改 <xref:Microsoft.AspNetCore.Builder.StaticFileExtensions.UseStaticFiles%2A> 中的方法呼叫 `Startup.Configure` 。</span><span class="sxs-lookup"><span data-stu-id="d0fde-116">To revert to the `application/octet-stream` MIME type, modify the <xref:Microsoft.AspNetCore.Builder.StaticFileExtensions.UseStaticFiles%2A> method call in `Startup.Configure`.</span></span> <span data-ttu-id="d0fde-117">例如：</span><span class="sxs-lookup"><span data-stu-id="d0fde-117">For example:</span></span>

```csharp
var provider = new FileExtensionContentTypeProvider();
provider.Mappings[".csv"] = MediaTypeNames.Application.Octet;

app.UseStaticFiles(new StaticFileOptions
{
    ContentTypeProvider = provider
});
```

<span data-ttu-id="d0fde-118">如需自訂對應的詳細資訊，請參閱 [FileExtensionContentTypeProvider](/aspnet/core/fundamentals/static-files#fileextensioncontenttypeprovider)。</span><span class="sxs-lookup"><span data-stu-id="d0fde-118">For more information on customizing the mapping, see [FileExtensionContentTypeProvider](/aspnet/core/fundamentals/static-files#fileextensioncontenttypeprovider).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="d0fde-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="d0fde-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`T:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider`

-->

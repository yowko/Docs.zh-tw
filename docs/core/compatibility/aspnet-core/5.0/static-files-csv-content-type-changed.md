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
# <a name="static-files-csv-content-type-changed-to-standards-compliant"></a>靜態檔案： CSV 內容類型已變更為符合標準

在 ASP.NET Core 5.0 中， `Content-Type` [靜態檔案中介軟體](/aspnet/core/fundamentals/static-files) 用於 *.csv* 檔案的預設回應標頭值已變更為符合標準規範的值 `text/csv` 。

如需此問題的討論，請參閱 [dotnet/aspnetcore # 17385](https://github.com/dotnet/AspNetCore/issues/17385)。

## <a name="version-introduced"></a>引進的版本

5.0 Preview 1

## <a name="old-behavior"></a>舊的行為

`Content-Type`已使用標頭值 `application/octet-stream` 。

## <a name="new-behavior"></a>新的行為

`Content-Type`使用標頭值 `text/csv` 。

## <a name="reason-for-change"></a>變更的原因

符合 [RFC 7111](https://tools.ietf.org/html/rfc7111#section-5.1) 標準。

## <a name="recommended-action"></a>建議的動作

如果此變更會影響您的應用程式，您可以自訂副檔名至 MIME 類型的對應。 若要還原成 `application/octet-stream` MIME 型別，請修改 <xref:Microsoft.AspNetCore.Builder.StaticFileExtensions.UseStaticFiles%2A> 中的方法呼叫 `Startup.Configure` 。 例如：

```csharp
var provider = new FileExtensionContentTypeProvider();
provider.Mappings[".csv"] = MediaTypeNames.Application.Octet;

app.UseStaticFiles(new StaticFileOptions
{
    ContentTypeProvider = provider
});
```

如需自訂對應的詳細資訊，請參閱 [FileExtensionContentTypeProvider](/aspnet/core/fundamentals/static-files#fileextensioncontenttypeprovider)。

## <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`T:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider`

-->

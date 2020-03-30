---
ms.openlocfilehash: 8e077d5cde6e824af5aac3742308593f1d91dd92
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391178"
---
### <a name="static-files-csv-content-type-changed-to-standards-compliant"></a>靜態檔：CSV 內容類型更改為符合標準

在 ASP.NET Core 5.0`Content-Type`中，[靜態檔中介軟體](/aspnet/core/fundamentals/static-files)用於 *.csv*檔的預設回應標頭值已更改為符合標準的值`text/csv`。

有關此問題的討論，請參閱[dotnet/aspnetcore_17385](https://github.com/dotnet/AspNetCore/issues/17385)。

#### <a name="version-introduced"></a>介紹的版本

5.0 預覽 1

#### <a name="old-behavior"></a>舊的行為

使用了`Content-Type`標頭值`application/octet-stream`。

#### <a name="new-behavior"></a>新的行為

使用`Content-Type`標頭值`text/csv`。

#### <a name="reason-for-change"></a>更改原因

符合[RFC 7111](https://tools.ietf.org/html/rfc7111#section-5.1)標準。

#### <a name="recommended-action"></a>建議的動作

如果此更改影響你的應用，則可以自訂檔副檔名到 MIME 類型映射。 要還原到`application/octet-stream`MIME 類型，<xref:Microsoft.AspNetCore.Builder.StaticFileExtensions.UseStaticFiles%2A>請修改 方法`Startup.Configure`調用。 例如：

```csharp
var provider = new FileExtensionContentTypeProvider();
provider.Mappings[".csv"] = MediaTypeNames.Application.Octet;

app.UseStaticFiles(new StaticFileOptions
{
    ContentTypeProvider = provider
});
```

有關自訂映射的詳細資訊，請參閱[檔擴展內容類型提供程式](/aspnet/core/fundamentals/static-files#fileextensioncontenttypeprovider)。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider`

-->

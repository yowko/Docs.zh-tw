---
ms.openlocfilehash: 29908ed916690e67db3cc5d72ebe1b1c6aea45c6
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325231"
---
### <a name="iis-urlrewrite-middleware-query-strings-are-preserved"></a>IIS： UrlRewrite 中介軟體查詢字串會保留

IIS UrlRewrite 中介軟體瑕疵使查詢字串無法在重寫規則中保留。 已修正該瑕疵，以維持與 IIS UrlRewrite 模組行為的一致性。

如需討論，請參閱 issue [dotnet/aspnetcore # 22972](https://github.com/dotnet/aspnetcore/issues/22972)。

#### <a name="version-introduced"></a>引進的版本

ASP.NET Core 5.0 Preview 7

#### <a name="old-behavior"></a>舊的行為

請考慮下列重寫規則：

```xml
<rule name="MyRule" stopProcessing="true">
  <match url="^about" />
  <action type="Redirect" url="/contact" redirectType="Temporary" appendQueryString="true" />
</rule>
```

上述規則不會附加查詢字串。 URI，例如重新 `/about?id=1` 導向至， `/contact` 而不是 `/contact?id=1` 。 `appendQueryString`屬性的預設值 `true` 也是。

#### <a name="new-behavior"></a>新的行為

查詢字串會保留下來。 來自[舊行為](#old-behavior)之範例中的 URI 會是 `/contact?id=1` 。

#### <a name="reason-for-change"></a>變更的原因

舊的行為不符合 IIS UrlRewrite 模組的行為。 為了支援中介軟體和模組之間的移植，其目標是要維持一致的行為。

#### <a name="recommended-action"></a>建議的動作

如果偏好移除查詢字串的行為，請將 `action` 元素設定為 `appendQueryString="false"` 。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.AspNetCore.Rewrite.IISUrlRewriteOptionsExtensions.AddIISUrlRewrite%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Rewrite.IISUrlRewriteOptionsExtensions.AddIISUrlRewrite`

-->

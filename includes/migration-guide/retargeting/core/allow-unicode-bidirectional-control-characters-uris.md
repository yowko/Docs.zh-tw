---
ms.openlocfilehash: 53d74db1a77e62cc64250658281fd3e4706fe494
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614321"
---
### <a name="allow-unicode-bidirectional-control-characters-in-uris"></a>允許在 URI 中使用 Unicode 雙向控制字元

#### <a name="details"></a>詳細資料

Unicode 會指定數個特殊控制字元，用來指定文字的方向。 在舊版的 .NET Framework 中，這些字元會從所有 URI 中不正確地移除，即使它們存在於自己的百分比編碼中。 為進一步遵循 [RFC 3987](https://tools.ietf.org/html/rfc3987)，我們現在允許在 URI 中使用這些字元。 在 URI 找到未編碼的內容時，它們是百分比編碼的。 找到百分比編碼的內容時，它們會保持現況。

#### <a name="suggestion"></a>建議

以 .NET Framework 4.7.2 版開始為目標的應用程式，預設啟用對 Unicode 雙向字元的支援。 如果不需要這項變更，您可以在應用程式組態檔的 `<runtime>` 區段中新增下列 [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 參數來停用此變更：

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.Uri.DontKeepUnicodeBidiFormattingCharacters=true" />
</runtime>
```

對於以舊版 .NET Framework 為目標，但執行版本低於 .NET Framework 4.7.2 (含) 的應用程式，預設停用對 Unicode 雙向字元的支援。 您可以在應用程式組態檔的 `<runtime>` 區段中新增下列 [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 參數停用它：

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.Uri.DontKeepUnicodeBidiFormattingCharacters=false" />
</runtime>
```

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Minor       |
| 版本 | 4.7.2       |
| 類型    | 正在重定目標 |

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Uri?displayProperty=nameWithType>

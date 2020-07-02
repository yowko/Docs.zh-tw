---
ms.openlocfilehash: 21921156295d89aad04f3197fef9fa322f3c8c87
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614332"
---
### <a name="ensure-systemuri-uses-a-consistent-reserved-character-set"></a>確定 System.Uri 使用一致的保留字集

#### <a name="details"></a>詳細資料

在 <xref:System.Uri?displayProperty=fullName> 中，某些有時已解碼的百分比編碼字元，現在一致保持編碼。 這發生在存取 URI 的路徑、查詢、片段或使用者資訊元件的屬性和方法之間。 行為只有在下列兩項都符合時才會變更：

- URI 包含下列任一保留字元的編碼格式：`:`、`'`、`(`、`)`、`!` 或 `*`。
- URI 包含 Unicode 或編碼的非保留字元。 如果符合上述兩項，則編碼的保留字元會保持編碼。 在舊版的 .NET Framework 中，它們是解碼的。

#### <a name="suggestion"></a>建議

對於以 .NET Framework 4.7.2 版開始為目標的應用程式，預設會啟用新的解碼行為。 如果不需要這項變更，您可以在應用程式組態檔的 `<runtime>` 區段中新增下列 [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 參數來停用此變更：

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets=true" />
</runtime>
```

對於以舊版 .NET Framework 為目標，但執行版本低於 .NET Framework 4.7.2 (含) 的應用程式，預設會停用新的解碼行為。 您可以藉由在[AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) `<runtime>` 應用程式佈建檔的區段中新增下列 AppCoNtextSwitchOverrides 參數來啟用它：

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets=false" />
</runtime>
```

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Minor       |
| 版本 | 4.7.2       |
| 類型    | 正在重定目標 |

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Uri?displayProperty=nameWithType>

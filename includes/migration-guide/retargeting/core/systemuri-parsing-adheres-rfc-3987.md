---
ms.openlocfilehash: 9c3c0bf7fbd8d45eba84eaa8634fd2d834195702
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617140"
---
### <a name="systemuri-parsing-adheres-to-rfc-3987"></a>System.Uri 剖析遵守 RFC 3987

#### <a name="details"></a>詳細資料

URI 剖析在 .NET Framework 4.5 中已做了幾項變更。 不過請注意，這些變更只會影響以 .NET Framework 4.5 為目標的程式碼。 如果某個二進位檔是以 .NET Framework 4.0 為目標，則會遵守舊版行為。 .NET Framework 4.5 中的 URI 剖析變更包括：

- URI 剖析將會根據 RFC 3987 中最新的 IRI 規則來執行正規化和字元檢查。
- 只會在 URI 的主機部分執行 Unicode 正規化格式 C。
- 無效的 mailto: URI 現在會造成例外狀況。
- 現在會保留路徑線段結尾的後置點。
- `file://` URI 不會逸出 `?` 字元。
- 不支援 Unicode 控制字元 `U+0080` 至 `U+009F`。
- 逗號字元 `,` 或 `%2c` 不會自動設為未逸出。

#### <a name="suggestion"></a>建議

如果需要舊版 .NET Framework 4.0 URI 剖析語意 (通常不需要)，藉由設定 .NET Framework 4.0 目標即可使用。 您可以在組件上使用 <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName>，或透過 Visual Studio 專案系統 UI 的 [專案屬性] 頁面來完成此作業。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | 主要       |
| 版本 | 4.5         |
| 類型    | 正在重定目標 |

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Uri.%23ctor(System.String)>
- <xref:System.Uri.%23ctor(System.String,System.Boolean)>
- <xref:System.Uri.%23ctor(System.String,System.UriKind)>
- <xref:System.Uri.%23ctor(System.Uri,System.String)>
- <xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType>
- <xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType>
- <xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType>

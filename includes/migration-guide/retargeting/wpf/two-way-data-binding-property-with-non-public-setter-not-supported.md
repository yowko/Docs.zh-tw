---
ms.openlocfilehash: 5f1a8af37a305ab0904801002dd99e17e8eca62e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616039"
---
### <a name="two-way-data-binding-to-a-property-with-a-non-public-setter-is-not-supported"></a>不支援具有非公用 setter 之屬性的雙向資料繫結

#### <a name="details"></a>詳細資料

嘗試將資料繫結至不含公用 setter 的屬性，是之前從未支援過的情況。 從 .NET Framework 4.5.1 開始，這種情況將會擲回 <xref:System.InvalidOperationException?displayProperty=fullName>。 請注意，只有專門以 .NET Framework 4.5.1 為目標的應用程式才會擲回此新的例外狀況。 如果應用程式是以 .NET Framework 4.5 為目標，則會允許此呼叫。 如果應用程式未以特定 .NET Framework 版本為目標，則會將繫結視為單向。

#### <a name="suggestion"></a>建議

您應該更新應用程式以使用單向繫結，或以公用方式公開屬性的 setter。 此外，以 .NET Framework 4.5 為目標也會使應用程式展示舊版行為。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Minor       |
| 版本 | 4.5.1       |
| 類型    | 正在重定目標 |

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Windows.Data.BindingMode.TwoWay?displayProperty=nameWithType>

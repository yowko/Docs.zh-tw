---
ms.openlocfilehash: 3300a74b81fc9eeba670ee0ceb2c2615fd3925bd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617142"
---
### <a name="listlttgtforeach-can-throw-exception-when-modifying-list-item"></a>修改清單項目時，List&lt;T&gt;.ForEach 可能會擲回例外狀況

#### <a name="details"></a>詳細資料

從 .NET Framework 4.5 開始，如果呼叫集合中有任何項目遭到修改，<xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})> 列舉程式將會擲回 <xref:System.InvalidOperationException?displayProperty=fullName> 例外狀況。 之前，這不會擲回例外狀況，但可能會造成競爭情形。

#### <a name="suggestion"></a>建議

在理想情況下，您應該修正程式碼，不要在列舉其項目時修改清單，因為這絕不是安全的作業。 不過，若要還原成舊版行為，應用程式可以將目標設為 .NET Framework 4.0。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Edge        |
| 版本 | 4.5         |
| 類型    | 正在重定目標 |

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})?displayProperty=nameWithType>

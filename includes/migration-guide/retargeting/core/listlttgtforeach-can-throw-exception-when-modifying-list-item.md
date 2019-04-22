---
ms.openlocfilehash: 4e81087431091dfa4d5432d5ea5e2b665be2b130
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774314"
---
### <a name="listtforeach-can-throw-exception-when-modifying-list-item"></a>修改清單項目時，List\<T>.ForEach 可能會擲回例外狀況

|   |   |
|---|---|
|詳細資料|從 .NET Framework 4.5 開始，如果呼叫集合中有任何項目遭到修改，<xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})> 列舉程式將會擲回 <xref:System.InvalidOperationException?displayProperty=name> 例外狀況。 之前，這不會擲回例外狀況，但可能會造成競爭情形。|
|建議|在理想情況下，您應該修正程式碼，不要在列舉其項目時修改清單，因為這絕不是安全的作業。 不過，若要還原成舊版行為，應用程式可以將目標設為 .NET Framework 4.0。|
|範圍|Edge|
|版本|4.5|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})?displayProperty=nameWithType></li></ul>|

---
ms.openlocfilehash: 4394e69dafeb6cce2d7719a67bbce396d3bc1086
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497116"
---
### <a name="wpf-datatemplate-elements-are-now-visible-to-uia"></a>UIA 現在看得到 WPF DataTemplate 項目

#### <a name="details"></a>詳細資料

之前，UI 自動化看不到 <xref:System.Windows.DataTemplate?displayProperty=fullName> 項目。 從 4.5 開始，使用者介面自動化將會偵測這些項目。 這在許多情況下很有用，但可能會中斷相依於不含 <xref:System.Windows.DataTemplate?displayProperty=fullName> 項目之 UIA 樹狀目錄的測試。

#### <a name="suggestion"></a>建議

您可能需要更新此應用程式的 UI 自動化測試，UIA 樹狀目錄現在才能包含先前不可見的 <xref:System.Windows.DataTemplate?displayProperty=fullName> 項目。 例如，預期某些項目彼此相鄰的測試，現在可能需要預期這些項目之間會出現先前不可見的 UIA 項目。 或者，依賴幾個 UIA 項目或其索引的測試，可能需要以新值更新。

| 名稱    | 值       |
|:--------|:------------|
| 範圍   |Edge|
|版本|4.5|
|類型|執行階段|

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Windows.DataTemplate.%23ctor>
- <xref:System.Windows.DataTemplate.%23ctor(System.Object)>

<!--

#### Affected APIs

- `M:System.Windows.DataTemplate.#ctor`
- `M:System.Windows.DataTemplate.#ctor(System.Object)`

-->

---
ms.openlocfilehash: a61005e317020c47a283dae292236624ec6057ce
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496354"
---
### <a name="flowdocument-may-show-an-extra-line-of-text"></a>FlowDocument 可能會顯示額外的文字行

#### <a name="details"></a>詳細資料

在某些情況下，相較於 <xref:System.Windows.Documents.FlowDocument> 項目在 .NET Framework 4.0 上執行時的顯示方式，其在 .NET Framework 4.5 上執行時，會顯示額外的文字行。 沒有任何已知的變更情況會導致文字顯示不良或無法辨識，但它可能會導致顯示之前已從 <xref:System.Windows.Documents.FlowDocument> 檢視表中省略的文字。

#### <a name="suggestion"></a>建議

在某些情況下，將顯示項目的 PageHeight 屬性減 1 可以還原先前顯示的行數。

| 名稱    | 值       |
|:--------|:------------|
| 範圍   |Edge|
|版本|4.5|
|類型|執行階段|

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Windows.Documents.FlowDocument.%23ctor>
- <xref:System.Windows.Documents.FlowDocument.%23ctor(System.Windows.Documents.Block)>
- <xref:System.Windows.Controls.FlowDocumentReader.%23ctor>
- <xref:System.Windows.Controls.FlowDocumentPageViewer.%23ctor>
- <xref:System.Windows.Controls.Primitives.DocumentPageView.%23ctor>

<!--

#### Affected APIs

- `M:System.Windows.Documents.FlowDocument.#ctor`
- `M:System.Windows.Documents.FlowDocument.#ctor(System.Windows.Documents.Block)`
- `M:System.Windows.Controls.FlowDocumentReader.#ctor`
- `M:System.Windows.Controls.FlowDocumentPageViewer.#ctor`
- `M:System.Windows.Controls.Primitives.DocumentPageView.#ctor`

-->

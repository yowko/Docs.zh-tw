---
ms.openlocfilehash: e47a24239872e3fe86ff6902f66b38daaa106598
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497635"
---
### <a name="eventlistener-truncates-strings-with-embedded-nulls"></a>EventListener 會截斷內嵌 Null 的字串

#### <a name="details"></a>詳細資料

<xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> 會截斷內嵌 Null 的字串。 <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> 類別不支援 Null 字元。 這項變更只會影響使用 <xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> 讀取處理中 <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> 資料並使用 Ｎull 字元做為分隔符號的應用程式。

#### <a name="suggestion"></a>建議

如果可能的話，您應該更新 <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> 資料，不要使用內嵌 Null 字元。

| 名稱    | 值       |
|:--------|:------------|
| 範圍   |Edge|
|版本|4.5.1|
|類型|執行階段|

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Diagnostics.Tracing.EventListener.%23ctor>
- <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType>
- <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords)?displayProperty=nameWithType>
- <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords,System.Collections.Generic.IDictionary{System.String,System.String})?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Diagnostics.Tracing.EventListener.#ctor`
- `M:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)`
- `M:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords)`
- `M:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords,System.Collections.Generic.IDictionary{System.String,System.String})`

-->

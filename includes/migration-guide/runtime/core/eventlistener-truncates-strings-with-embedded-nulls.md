---
ms.openlocfilehash: 9084c135769f595491d645e49d24cf507f5f6070
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235310"
---
### <a name="eventlistener-truncates-strings-with-embedded-nulls"></a>EventListener 會截斷內嵌 Null 的字串

|   |   |
|---|---|
|詳細資料|<xref:System.Diagnostics.Tracing.EventListener?displayProperty=name> 會截斷內嵌 Null 的字串。 <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> 類別不支援 Null 字元。 這項變更只會影響使用 <xref:System.Diagnostics.Tracing.EventListener?displayProperty=name> 讀取處理中 <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> 資料並使用 Ｎull 字元做為分隔符號的應用程式。|
|建議|<xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> 資料應該更新 (可能的話)，不要使用內嵌 Null 字元。|
|範圍|Edge|
|版本|4.5.1|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Diagnostics.Tracing.EventListener.%23ctor?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords,System.Collections.Generic.IDictionary{System.String,System.String})?displayProperty=nameWithType></li></ul>|

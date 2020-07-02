---
ms.openlocfilehash: 7d50962b518c15875a5f1a82f5b89ab87a1db02e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619971"
---
### <a name="etw-eventlisteners-do-not-capture-events-from-providers-with-explicit-keywords-like-the-tpl-provider"></a>ETW EventListeners 無法使用 Explicit 關鍵字從提供者擷取事件 (例如 TPL 提供者)

#### <a name="details"></a>詳細資料

具有空白關鍵字遮罩的 ETW EventListeners 無法使用 Explicit 關鍵字從提供者正確地擷取事件。 在 .NET Framework 4.5 中，TPL 提供者已開始提供 Explicit 關鍵字並觸發此問題。 在 .NET Framework 4.6 中，已更新 EventListeners，因此不會再發生此問題。

#### <a name="suggestion"></a>建議

若要解決此問題，請將 <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)> 的呼叫取代為 EnableEvents 多載的呼叫，該呼叫明確指定「任何關鍵字」遮罩以使用︰<code>EnableEvents(eventSource, level, unchecked((EventKeywords)0xFFFFffffFFFFffff))</code>。此外，此問題在 .NET Framework 4.6 中已修正，因此可藉由升級至該版 .NET Framework 來解決。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |Edge|
|版本|4.5|
|類型|執行階段

#### <a name="affected-apis"></a>受影響的 API

-<xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType></li></ul>|

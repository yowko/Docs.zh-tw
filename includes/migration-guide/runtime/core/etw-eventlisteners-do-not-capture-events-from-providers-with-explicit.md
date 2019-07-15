---
ms.openlocfilehash: eab476a1d3f275e851e5af4198c30b60ad0c17b8
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858529"
---
### <a name="etw-eventlisteners-do-not-capture-events-from-providers-with-explicit-keywords-like-the-tpl-provider"></a>ETW EventListeners 無法使用 Explicit 關鍵字從提供者擷取事件 (例如 TPL 提供者)

|   |   |
|---|---|
|詳細資料|具有空白關鍵字遮罩的 ETW EventListeners 無法使用 Explicit 關鍵字從提供者正確地擷取事件。 在 .NET Framework 4.5 中，TPL 提供者已開始提供 Explicit 關鍵字並觸發此問題。 在 .NET Framework 4.6 中，已更新 EventListeners，因此不會再發生此問題。|
|建議|若要解決此問題，請將 <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)> 的呼叫取代為 EnableEvents 多載的呼叫，該呼叫明確指定「任何關鍵字」遮罩以使用︰<code>EnableEvents(eventSource, level, unchecked((EventKeywords)0xFFFFffffFFFFffff))</code>。此外，此問題在 .NET Framework 4.6 中已修正，因此可藉由升級至該版 .NET Framework 來解決。|
|範圍|Edge|
|版本|4.5|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType></li></ul>|


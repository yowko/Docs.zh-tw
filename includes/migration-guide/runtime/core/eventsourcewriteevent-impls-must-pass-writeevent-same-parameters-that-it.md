---
ms.openlocfilehash: 662c140f019add66ff6605d47ad1f32c3f50d711
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619976"
---
### <a name="eventsourcewriteevent-impls-must-pass-writeevent-the-same-parameters-that-it-received-plus-id"></a>EventSource.WriteEvent impl 必須將收到的相同參數傳遞給 WriteEvent (再加上識別碼)

#### <a name="details"></a>詳細資料

執行階段現在會強制執行指定下列作業的合約：定義 ETW 事件方法之衍生自 <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> 的類別在呼叫基底類別 <code>EventSource.WriteEvent</code> 方法時，必須在事件識別碼後面接著傳遞 ETW 事件方法的相同目的地引數。

#### <a name="suggestion"></a>建議

如果 <xref:System.IndexOutOfRangeException?displayProperty=fullName> 讀取來自於違反此合約之事件來源的處理中 <xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> 資料，則會擲回 <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> 例外狀況。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |Minor|
|版本|4.5.1|
|類型|執行階段|

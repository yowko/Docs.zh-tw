---
ms.openlocfilehash: fc6066fd0b23d299158114cb397934041b99ba47
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620096"
---
### <a name="wpf-dispatchersynchronizationcontextcreatecopy-now-returns-a-new-copy-instead-of-the-current-instance"></a>WPF DispatcherSynchronizationContext.CreateCopy 現在會傳回新的複本，而不是目前的執行個體

#### <a name="details"></a>詳細資料

在 .NET Framework 4 中，<xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> 會傳回目前執行個體的參考，主要是當作效能最佳化。 在 .NET Framework 4.5 中，則會傳回新的執行個體，這是第一次能夠認定同等參考，表示執行中執行緒是在正確的同步處理內容中。  程式碼不太可能檢查這些參考的識別是否會受到影響，但由於這項變更，您應該在移轉至 .NET Framework 4.5 或更新版本的過程中，測試呼叫 <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> 的程式碼。

#### <a name="suggestion"></a>建議

請注意，<xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> 現在會傳回新的 <xref:System.Threading.SynchronizationContext?displayProperty=fullName> 物件。 之前，使用以此方式產生之對等參考的程式碼不會實際檢查它是否在適當的內容中，但針對 .NET Framework 4.5 或更新版本建置時則會進行檢查。  雖然不太可能會造成問題，但執行受影響的程式碼路徑應該足以判斷是否會造成任何問題。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |Minor|
|版本|4.5|
|類型|執行階段

#### <a name="affected-apis"></a>受影響的 API

-<xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy?displayProperty=nameWithType></li></ul>|

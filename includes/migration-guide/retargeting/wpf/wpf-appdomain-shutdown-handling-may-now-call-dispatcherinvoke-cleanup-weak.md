---
ms.openlocfilehash: 8b804d23247b95381f3ff83bc12c32215a420fb6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614610"
---
### <a name="wpf-appdomain-shutdown-handling-may-now-call-dispatcherinvoke-in-cleanup-of-weak-events"></a>WPF AppDomain 關閉處理現在可能呼叫發送器。清除弱式事件時叫用

#### <a name="details"></a>詳細資料

在 .NET Framework 4.7.1 和較早的版本中，WPF 可能會在 <xref:System.Windows.Threading.Dispatcher?displayProperty=nameWithType> AppDomain 關閉期間，于 .net 完成項執行緒上建立。  這是在 .NET Framework 4.7.2 和更新版本中修正，方法是讓清除弱式事件的執行緒感知。  因此，WPF 可能會呼叫 <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=nameWithType> 來完成清除程式。在某些應用程式中，完成項時間的變更可能會在 AppDomain 或處理常式關閉期間造成例外狀況。  在進程或 AppDomain 關閉之前，未正確關閉工作者執行緒上執行之發送器的應用程式中，通常會出現這種情況。  這類應用程式應該負責妥善管理發送器的存留期。

#### <a name="suggestion"></a>建議

在 .NET Framework 4.7.2 和更新版本中，開發人員可以停用此修正程式，以協助減少（但不能消除）因清除變更而可能發生的時間問題。若要停用清除中的變更，請使用下列 AppCoNtext 旗標。<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotInvokeInWeakEventTableShutdownListener=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Edge        |
| 版本 | 4.7.2       |
| 類型    | 正在重定目標 |

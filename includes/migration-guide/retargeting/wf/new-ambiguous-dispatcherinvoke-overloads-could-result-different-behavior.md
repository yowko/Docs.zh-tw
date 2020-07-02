---
ms.openlocfilehash: 80e61d4dd5b8d4754a39e95e37475fefff57fcbd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617135"
---
### <a name="new-ambiguous-dispatcherinvoke-overloads-could-result-in-different-behavior"></a>新的 (模稜兩可的) Dispatcher.Invoke 多載可能會導致不同的行為

#### <a name="details"></a>詳細資料

.NET Framework 4.5 將包含 <xref:System.Action> 類型參數的多載新增至 <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=nameWithType>。 重新編譯現有的程式碼時，編譯器可能會將呼叫解析為具有 <xref:System.Delegate> 參數的 Dispatcher.Invoke 方法，就像呼叫具有 <xref:System.Action> 參數的 Dispatcher.Invoke 方法。 如果將具有 <xref:System.Delegate> 參數的 Dispatcher.Invoke 多載呼叫解析成具有 <xref:System.Action> 參數的 Dispatcher.Invoke 多載呼叫，則可能會出現下列行為上的差異：

- 如果發生例外狀況，則不會引發 <xref:System.Windows.Threading.Dispatcher.UnhandledExceptionFilter> 和 <xref:System.Windows.Threading.Dispatcher.UnhandledException> 事件。 而是由 <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=fullName> 事件處理例外狀況。
- 對某些成員 (例如 <xref:System.Windows.Threading.DispatcherOperation.Result>) 的呼叫會遭到封鎖，直到作業完成為止。

#### <a name="suggestion"></a>建議

若要避免模稜兩可的情況 (以及例外狀況處理或封鎖行為上的可能差異)，呼叫 Dispatcher.Invoke 的程式碼可以傳遞空的 object[] 作為 Invoke 呼叫的第二個參數，以確定解析為 .NET Framework 4.0 方法多載。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Minor       |
| 版本 | 4.5         |
| 類型    | 正在重定目標 |

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.Object[])?displayProperty=nameWithType>
- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.TimeSpan,System.Object[])?displayProperty=nameWithType>
- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.TimeSpan,System.Windows.Threading.DispatcherPriority,System.Object[])?displayProperty=nameWithType>
- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.Windows.Threading.DispatcherPriority,System.Object[])?displayProperty=nameWithType>

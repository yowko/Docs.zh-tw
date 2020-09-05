---
ms.openlocfilehash: 9d0791f00db7d830fc5d327af30218a0bbfcb25f
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497323"
---
### <a name="change-in-behavior-for-taskwaitall-methods-with-time-out-arguments"></a>含逾時引數之 Task.WaitAll 方法的行為變更

#### <a name="details"></a>詳細資料

在 .NET Framework 4.5 中，<xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType> 行為變得更一致。在 .NET Framework 4 中，這些方法的行為不一致。 逾時過期時，如果在方法呼叫之前已完成或取消一個或多個工作，則方法會擲回 <xref:System.AggregateException?displayProperty=fullName> 例外狀況。 當逾時過期時，如果在方法呼叫之前沒有任何已完成或取消的工作，但是有一個或多個工作在方法呼叫之後進入這兩種狀態，則方法會傳回 false。<br/><br/>在 .NET Framework 4.5 中，如果逾時間隔到期時仍有任何工作正在執行，這些方法多載現在會傳回 false，而只有在取消輸入工作 (不論是在方法呼叫之前或之後)，且沒有其他工作仍在執行時，才會擲回 <xref:System.AggregateException?displayProperty=fullName> 例外狀況。

#### <a name="suggestion"></a>建議

如果透過攔截 <xref:System.AggregateException?displayProperty=fullName> 來偵測某個工作在叫用 <xref:System.Threading.Tasks.Task.WaitAll%2A> 呼叫之前是否已取消，該程式碼應改為透過 <xref:System.Threading.Tasks.Task.IsCanceled%2A> 屬性 (例如：.Any(t =&gt; t.IsCanceled)) 執行相同的偵測，因為 .NET Framework 4.6 只會在所有等候的工作在逾時前都已完成時，才會擲回此例外狀況。

| 名稱    | 值       |
|:--------|:------------|
| 範圍   |Minor|
|版本|4.5|
|類型|執行階段

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32,System.Threading.CancellationToken)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.TimeSpan)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32)`
- `M:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32,System.Threading.CancellationToken)`
- `M:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.TimeSpan)`

-->

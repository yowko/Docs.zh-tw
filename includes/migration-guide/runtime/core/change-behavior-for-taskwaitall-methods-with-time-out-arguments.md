---
ms.openlocfilehash: 9d0791f00db7d830fc5d327af30218a0bbfcb25f
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497323"
---
### <a name="change-in-behavior-for-taskwaitall-methods-with-time-out-arguments"></a><span data-ttu-id="82df5-101">含逾時引數之 Task.WaitAll 方法的行為變更</span><span class="sxs-lookup"><span data-stu-id="82df5-101">Change in behavior for Task.WaitAll methods with time-out arguments</span></span>

#### <a name="details"></a><span data-ttu-id="82df5-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="82df5-102">Details</span></span>

<span data-ttu-id="82df5-103">在 .NET Framework 4.5 中，<xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType> 行為變得更一致。在 .NET Framework 4 中，這些方法的行為不一致。</span><span class="sxs-lookup"><span data-stu-id="82df5-103"><xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType> behavior was made more consistent in .NET Framework 4.5.In the .NET Framework 4, these methods behaved inconsistently.</span></span> <span data-ttu-id="82df5-104">逾時過期時，如果在方法呼叫之前已完成或取消一個或多個工作，則方法會擲回 <xref:System.AggregateException?displayProperty=fullName> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="82df5-104">When the time-out expired, if one or more tasks were completed or canceled before the method call, the method threw an <xref:System.AggregateException?displayProperty=fullName> exception.</span></span> <span data-ttu-id="82df5-105">當逾時過期時，如果在方法呼叫之前沒有任何已完成或取消的工作，但是有一個或多個工作在方法呼叫之後進入這兩種狀態，則方法會傳回 false。</span><span class="sxs-lookup"><span data-stu-id="82df5-105">When the time-out expired, if no tasks were completed or canceled before the method call, but one or more tasks entered these states after the method call, the method returned false.</span></span><br/><br/><span data-ttu-id="82df5-106">在 .NET Framework 4.5 中，如果逾時間隔到期時仍有任何工作正在執行，這些方法多載現在會傳回 false，而只有在取消輸入工作 (不論是在方法呼叫之前或之後)，且沒有其他工作仍在執行時，才會擲回 <xref:System.AggregateException?displayProperty=fullName> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="82df5-106">In the .NET Framework 4.5, these method overloads now return false if any tasks are still running when the time-out interval expired, and they throw an <xref:System.AggregateException?displayProperty=fullName> exception only if an input task was cancelled (regardless of whether it was before or after the method call) and no other tasks are still running.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="82df5-107">建議</span><span class="sxs-lookup"><span data-stu-id="82df5-107">Suggestion</span></span>

<span data-ttu-id="82df5-108">如果透過攔截 <xref:System.AggregateException?displayProperty=fullName> 來偵測某個工作在叫用 <xref:System.Threading.Tasks.Task.WaitAll%2A> 呼叫之前是否已取消，該程式碼應改為透過 <xref:System.Threading.Tasks.Task.IsCanceled%2A> 屬性 (例如：.Any(t =&gt; t.IsCanceled)) 執行相同的偵測，因為 .NET Framework 4.6 只會在所有等候的工作在逾時前都已完成時，才會擲回此例外狀況。</span><span class="sxs-lookup"><span data-stu-id="82df5-108">If an <xref:System.AggregateException?displayProperty=fullName> was being caught as a means of detecting a task that was cancelled prior to the <xref:System.Threading.Tasks.Task.WaitAll%2A> call being invoked, that code should instead do the same detection via the  <xref:System.Threading.Tasks.Task.IsCanceled%2A> property (for example: .Any(t =&gt; t.IsCanceled)) since .NET Framework 4.6 will only throw in that case if all awaited tasks are completed prior to the timeout.</span></span>

| <span data-ttu-id="82df5-109">名稱</span><span class="sxs-lookup"><span data-stu-id="82df5-109">Name</span></span>    | <span data-ttu-id="82df5-110">值</span><span class="sxs-lookup"><span data-stu-id="82df5-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="82df5-111">範圍</span><span class="sxs-lookup"><span data-stu-id="82df5-111">Scope</span></span>   |<span data-ttu-id="82df5-112">Minor</span><span class="sxs-lookup"><span data-stu-id="82df5-112">Minor</span></span>|
|<span data-ttu-id="82df5-113">版本</span><span class="sxs-lookup"><span data-stu-id="82df5-113">Version</span></span>|<span data-ttu-id="82df5-114">4.5</span><span class="sxs-lookup"><span data-stu-id="82df5-114">4.5</span></span>|
|<span data-ttu-id="82df5-115">類型</span><span class="sxs-lookup"><span data-stu-id="82df5-115">Type</span></span>|<span data-ttu-id="82df5-116">執行階段</span><span class="sxs-lookup"><span data-stu-id="82df5-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="82df5-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="82df5-117">Affected APIs</span></span>

- <xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32,System.Threading.CancellationToken)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.TimeSpan)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32)`
- `M:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32,System.Threading.CancellationToken)`
- `M:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.TimeSpan)`

-->

---
ms.openlocfilehash: bae211e5684dc1fbbb1d7e69c928e37c1c532096
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496696"
---
### <a name="exceptions-during-unobserved-processing-in-systemthreadingtaskstask-no-longer-propagate-on-finalizer-thread"></a><span data-ttu-id="727b1-101">在 System.Threading.Tasks.Task 中未觀察到的處理期間發生的例外狀況，將不再於完成項執行緒上傳播</span><span class="sxs-lookup"><span data-stu-id="727b1-101">Exceptions during unobserved processing in System.Threading.Tasks.Task no longer propagate on finalizer thread</span></span>

#### <a name="details"></a><span data-ttu-id="727b1-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="727b1-102">Details</span></span>

<span data-ttu-id="727b1-103">由於 <xref:System.Threading.Tasks.Task?displayProperty=fullName> 類別代表非同步作業，因此它會攔截非同步處理期間發生的所有非嚴重的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="727b1-103">Because the <xref:System.Threading.Tasks.Task?displayProperty=fullName> class represents an asynchronous operation, it catches all non-severe exceptions that occur during asynchronous processing.</span></span> <span data-ttu-id="727b1-104">在 .NET Framework 4.5 中，如果未觀察到某個例外狀況，而您的程式碼絕不會等候這項工作，則該例外狀況將不再於完成項執行緒上傳播，並且會在記憶體回收期間損毀處理序。</span><span class="sxs-lookup"><span data-stu-id="727b1-104">In the .NET Framework 4.5, if an exception is not observed and your code never waits on the task, the exception will no longer propagate on the finalizer thread and crash the process during garbage collection.</span></span> <span data-ttu-id="727b1-105">這項變更可以增強使用 Task 類別執行未觀察到的非同步處理之應用程式的可靠性。</span><span class="sxs-lookup"><span data-stu-id="727b1-105">This change enhances the reliability of applications that use the Task class to perform unobserved asynchronous processing.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="727b1-106">建議</span><span class="sxs-lookup"><span data-stu-id="727b1-106">Suggestion</span></span>

<span data-ttu-id="727b1-107">如果應用程式必須將未觀察到的非同步例外狀況傳播至完成項執行緒，可以藉由提供適當的處理常式給 <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> 事件，或藉由設定[執行階段組態項目](~/docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md)，來還原舊版行為。</span><span class="sxs-lookup"><span data-stu-id="727b1-107">If an app depends on unobserved asynchronous exceptions propagating to the finalizer thread, the previous behavior can be restored by providing an appropriate handler for the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> event, or by setting a [runtime configuration element](~/docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md).</span></span>

| <span data-ttu-id="727b1-108">名稱</span><span class="sxs-lookup"><span data-stu-id="727b1-108">Name</span></span>    | <span data-ttu-id="727b1-109">值</span><span class="sxs-lookup"><span data-stu-id="727b1-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="727b1-110">範圍</span><span class="sxs-lookup"><span data-stu-id="727b1-110">Scope</span></span>   |<span data-ttu-id="727b1-111">Edge</span><span class="sxs-lookup"><span data-stu-id="727b1-111">Edge</span></span>|
|<span data-ttu-id="727b1-112">版本</span><span class="sxs-lookup"><span data-stu-id="727b1-112">Version</span></span>|<span data-ttu-id="727b1-113">4.5</span><span class="sxs-lookup"><span data-stu-id="727b1-113">4.5</span></span>|
|<span data-ttu-id="727b1-114">類型</span><span class="sxs-lookup"><span data-stu-id="727b1-114">Type</span></span>|<span data-ttu-id="727b1-115">執行階段</span><span class="sxs-lookup"><span data-stu-id="727b1-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="727b1-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="727b1-116">Affected APIs</span></span>

- <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task.Run(System.Action,System.Threading.CancellationToken)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task.Run(System.Func{System.Threading.Tasks.Task})?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task.Run(System.Func{System.Threading.Tasks.Task},System.Threading.CancellationToken)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task.Run%60%601(System.Func{%60%600})?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task.Run%60%601(System.Func{%60%600},System.Threading.CancellationToken)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task.Run%60%601(System.Func{System.Threading.Tasks.Task{%60%600}})?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task.Run%60%601(System.Func{System.Threading.Tasks.Task{%60%600}},System.Threading.CancellationToken)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task.Start?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task.Start(System.Threading.Tasks.TaskScheduler)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Threading.Tasks.Task.Run(System.Action)`
- `M:System.Threading.Tasks.Task.Run(System.Action,System.Threading.CancellationToken)`
- `M:System.Threading.Tasks.Task.Run(System.Func{System.Threading.Tasks.Task})`
- `M:System.Threading.Tasks.Task.Run(System.Func{System.Threading.Tasks.Task},System.Threading.CancellationToken)`
- ``M:System.Threading.Tasks.Task.Run``1(System.Func{``0})``
- ``M:System.Threading.Tasks.Task.Run``1(System.Func{``0},System.Threading.CancellationToken)``
- ``M:System.Threading.Tasks.Task.Run``1(System.Func{System.Threading.Tasks.Task{``0}})``
- ``M:System.Threading.Tasks.Task.Run``1(System.Func{System.Threading.Tasks.Task{``0}},System.Threading.CancellationToken)``
- `M:System.Threading.Tasks.Task.Start`
- `M:System.Threading.Tasks.Task.Start(System.Threading.Tasks.TaskScheduler)`

-->

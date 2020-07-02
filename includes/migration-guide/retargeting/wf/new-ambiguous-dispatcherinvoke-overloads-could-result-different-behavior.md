---
ms.openlocfilehash: 80e61d4dd5b8d4754a39e95e37475fefff57fcbd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617135"
---
### <a name="new-ambiguous-dispatcherinvoke-overloads-could-result-in-different-behavior"></a><span data-ttu-id="51b1d-101">新的 (模稜兩可的) Dispatcher.Invoke 多載可能會導致不同的行為</span><span class="sxs-lookup"><span data-stu-id="51b1d-101">New (ambiguous) Dispatcher.Invoke overloads could result in different behavior</span></span>

#### <a name="details"></a><span data-ttu-id="51b1d-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="51b1d-102">Details</span></span>

<span data-ttu-id="51b1d-103">.NET Framework 4.5 將包含 <xref:System.Action> 類型參數的多載新增至 <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="51b1d-103">The .NET Framework 4.5 adds new overloads to <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=nameWithType> that include a parameter of type <xref:System.Action>.</span></span> <span data-ttu-id="51b1d-104">重新編譯現有的程式碼時，編譯器可能會將呼叫解析為具有 <xref:System.Delegate> 參數的 Dispatcher.Invoke 方法，就像呼叫具有 <xref:System.Action> 參數的 Dispatcher.Invoke 方法。</span><span class="sxs-lookup"><span data-stu-id="51b1d-104">When existing code is recompiled, compilers may resolve calls to Dispatcher.Invoke methods that have a <xref:System.Delegate> parameter as calls to Dispatcher.Invoke methods with an <xref:System.Action> parameter.</span></span> <span data-ttu-id="51b1d-105">如果將具有 <xref:System.Delegate> 參數的 Dispatcher.Invoke 多載呼叫解析成具有 <xref:System.Action> 參數的 Dispatcher.Invoke 多載呼叫，則可能會出現下列行為上的差異：</span><span class="sxs-lookup"><span data-stu-id="51b1d-105">If a call to a Dispatcher.Invoke overload with a  <xref:System.Delegate> parameter is resolved as a call to a Dispatcher.Invoke overload with an <xref:System.Action> parameter, the following differences in behavior may occur:</span></span>

- <span data-ttu-id="51b1d-106">如果發生例外狀況，則不會引發 <xref:System.Windows.Threading.Dispatcher.UnhandledExceptionFilter> 和 <xref:System.Windows.Threading.Dispatcher.UnhandledException> 事件。</span><span class="sxs-lookup"><span data-stu-id="51b1d-106">If an exception occurs, the <xref:System.Windows.Threading.Dispatcher.UnhandledExceptionFilter> and <xref:System.Windows.Threading.Dispatcher.UnhandledException> events are not raised.</span></span> <span data-ttu-id="51b1d-107">而是由 <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=fullName> 事件處理例外狀況。</span><span class="sxs-lookup"><span data-stu-id="51b1d-107">Instead, exceptions are handled by the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=fullName> event.</span></span>
- <span data-ttu-id="51b1d-108">對某些成員 (例如 <xref:System.Windows.Threading.DispatcherOperation.Result>) 的呼叫會遭到封鎖，直到作業完成為止。</span><span class="sxs-lookup"><span data-stu-id="51b1d-108">Calls to some members, such as <xref:System.Windows.Threading.DispatcherOperation.Result>, block until the operation has completed.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="51b1d-109">建議</span><span class="sxs-lookup"><span data-stu-id="51b1d-109">Suggestion</span></span>

<span data-ttu-id="51b1d-110">若要避免模稜兩可的情況 (以及例外狀況處理或封鎖行為上的可能差異)，呼叫 Dispatcher.Invoke 的程式碼可以傳遞空的 object[] 作為 Invoke 呼叫的第二個參數，以確定解析為 .NET Framework 4.0 方法多載。</span><span class="sxs-lookup"><span data-stu-id="51b1d-110">To avoid ambiguity (and potential differences in exception handling or blocking behaviors), code calling Dispatcher.Invoke can pass an empty object[] as a second parameter to the Invoke call to be sure of resolving to the .NET Framework 4.0 method overload.</span></span>

| <span data-ttu-id="51b1d-111">名稱</span><span class="sxs-lookup"><span data-stu-id="51b1d-111">Name</span></span>    | <span data-ttu-id="51b1d-112">值</span><span class="sxs-lookup"><span data-stu-id="51b1d-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="51b1d-113">影響範圍</span><span class="sxs-lookup"><span data-stu-id="51b1d-113">Scope</span></span>   | <span data-ttu-id="51b1d-114">Minor</span><span class="sxs-lookup"><span data-stu-id="51b1d-114">Minor</span></span>       |
| <span data-ttu-id="51b1d-115">版本</span><span class="sxs-lookup"><span data-stu-id="51b1d-115">Version</span></span> | <span data-ttu-id="51b1d-116">4.5</span><span class="sxs-lookup"><span data-stu-id="51b1d-116">4.5</span></span>         |
| <span data-ttu-id="51b1d-117">類型</span><span class="sxs-lookup"><span data-stu-id="51b1d-117">Type</span></span>    | <span data-ttu-id="51b1d-118">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="51b1d-118">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="51b1d-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="51b1d-119">Affected APIs</span></span>

- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.Object[])?displayProperty=nameWithType>
- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.TimeSpan,System.Object[])?displayProperty=nameWithType>
- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.TimeSpan,System.Windows.Threading.DispatcherPriority,System.Object[])?displayProperty=nameWithType>
- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.Windows.Threading.DispatcherPriority,System.Object[])?displayProperty=nameWithType>

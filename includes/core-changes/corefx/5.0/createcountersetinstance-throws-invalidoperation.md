---
ms.openlocfilehash: fabbc9a51f61a703ce97db50ab251e7a13ffe348
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144473"
---
### <a name="countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists"></a><span data-ttu-id="4f9dd-101">如果實例已經存在，CreateCounterSetInstance 現在會擲回 InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="4f9dd-101">CounterSet.CreateCounterSetInstance now throws InvalidOperationException if instance already exists</span></span>

<span data-ttu-id="4f9dd-102">從 .NET 5.0 開始， <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)?displayProperty=nameWithType> <xref:System.InvalidOperationException> <xref:System.ArgumentException> 如果計數器集合已經存在，則會擲回，而不是。</span><span class="sxs-lookup"><span data-stu-id="4f9dd-102">Starting in .NET 5.0, <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)?displayProperty=nameWithType> throws an <xref:System.InvalidOperationException> instead of an <xref:System.ArgumentException> if the counter set already exists.</span></span>

#### <a name="change-description"></a><span data-ttu-id="4f9dd-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="4f9dd-103">Change description</span></span>

<span data-ttu-id="4f9dd-104">在 .NET Framework 和 .NET Core 1.0 到3.1 中，您可以藉由呼叫來建立計數器集合的實例 <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> 。</span><span class="sxs-lookup"><span data-stu-id="4f9dd-104">In .NET Framework and .NET Core 1.0 to 3.1, you can create an instance of the counter set by calling <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A>.</span></span> <span data-ttu-id="4f9dd-105">不過，如果計數器集合已經存在，方法就會擲回 <xref:System.ArgumentException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4f9dd-105">However, if the counter set already exists, the method throws an <xref:System.ArgumentException> exception.</span></span>

<span data-ttu-id="4f9dd-106">在 .NET 5.0 和更新版本中，當您呼叫 <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> 且計數器集合存在時， <xref:System.InvalidOperationException> 就會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4f9dd-106">In .NET 5.0 and later versions, when you call <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> and the counter set exists, an <xref:System.InvalidOperationException> exception is thrown.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4f9dd-107">引進的版本</span><span class="sxs-lookup"><span data-stu-id="4f9dd-107">Version introduced</span></span>

<span data-ttu-id="4f9dd-108">5.0 Preview 5</span><span class="sxs-lookup"><span data-stu-id="4f9dd-108">5.0 Preview 5</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4f9dd-109">建議的動作</span><span class="sxs-lookup"><span data-stu-id="4f9dd-109">Recommended action</span></span>

<span data-ttu-id="4f9dd-110">如果您在 <xref:System.ArgumentException> 呼叫時攔截應用程式中的例外狀況 <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> ，請考慮同時捕捉 <xref:System.InvalidOperationException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4f9dd-110">If you catch <xref:System.ArgumentException> exceptions in your app when calling <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A>, consider also catching <xref:System.InvalidOperationException> exceptions.</span></span>

> [!NOTE]
> <span data-ttu-id="4f9dd-111"><xref:System.ArgumentException>不建議捕捉例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4f9dd-111">Catching <xref:System.ArgumentException> exceptions is not recommended.</span></span>

#### <a name="category"></a><span data-ttu-id="4f9dd-112">類別</span><span class="sxs-lookup"><span data-stu-id="4f9dd-112">Category</span></span>

<span data-ttu-id="4f9dd-113">Core .NET 程式庫</span><span class="sxs-lookup"><span data-stu-id="4f9dd-113">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4f9dd-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="4f9dd-114">Affected APIs</span></span>

- <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)`

-->

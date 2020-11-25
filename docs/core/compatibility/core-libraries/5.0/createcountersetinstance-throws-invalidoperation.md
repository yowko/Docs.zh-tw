---
title: 重大變更：如果實例已存在，則 CreateCounterSetInstance 會擲回 InvalidOperationException
description: 瞭解核心 .NET 程式庫中的 .NET 5.0 重大變更，其中 CreateCounterSetInstance 會擲回不同的例外狀況（如果計數器已經存在的話）。
ms.date: 11/01/2020
ms.openlocfilehash: 28042690b71f9b86e4e54748ec75467bbe232684
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760723"
---
# <a name="countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists"></a><span data-ttu-id="18aa5-103">如果實例已經存在，則 CreateCounterSetInstance 現在會擲回 InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="18aa5-103">CounterSet.CreateCounterSetInstance now throws InvalidOperationException if instance already exists</span></span>

<span data-ttu-id="18aa5-104">從 .NET 5.0 開始， <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)?displayProperty=nameWithType> <xref:System.InvalidOperationException> <xref:System.ArgumentException> 如果計數器集合已經存在，則會擲回，而不是。</span><span class="sxs-lookup"><span data-stu-id="18aa5-104">Starting in .NET 5.0, <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)?displayProperty=nameWithType> throws an <xref:System.InvalidOperationException> instead of an <xref:System.ArgumentException> if the counter set already exists.</span></span>

## <a name="change-description"></a><span data-ttu-id="18aa5-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="18aa5-105">Change description</span></span>

<span data-ttu-id="18aa5-106">在 .NET Framework 和 .NET Core 1.0 至3.1，您可以藉由呼叫來建立計數器集合的實例 <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> 。</span><span class="sxs-lookup"><span data-stu-id="18aa5-106">In .NET Framework and .NET Core 1.0 to 3.1, you can create an instance of the counter set by calling <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A>.</span></span> <span data-ttu-id="18aa5-107">但是，如果計數器集合已經存在，則方法會擲回 <xref:System.ArgumentException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="18aa5-107">However, if the counter set already exists, the method throws an <xref:System.ArgumentException> exception.</span></span>

<span data-ttu-id="18aa5-108">在 .NET 5.0 和更新版本中，當您呼叫， <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> 且計數器集合存在時， <xref:System.InvalidOperationException> 就會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="18aa5-108">In .NET 5.0 and later versions, when you call <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> and the counter set exists, an <xref:System.InvalidOperationException> exception is thrown.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="18aa5-109">引進的版本</span><span class="sxs-lookup"><span data-stu-id="18aa5-109">Version introduced</span></span>

<span data-ttu-id="18aa5-110">5.0</span><span class="sxs-lookup"><span data-stu-id="18aa5-110">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="18aa5-111">建議的動作</span><span class="sxs-lookup"><span data-stu-id="18aa5-111">Recommended action</span></span>

<span data-ttu-id="18aa5-112">如果您在 <xref:System.ArgumentException> 呼叫時捕捉到應用程式中的例外狀況 <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> ，請考慮同時攔截 <xref:System.InvalidOperationException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="18aa5-112">If you catch <xref:System.ArgumentException> exceptions in your app when calling <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A>, consider also catching <xref:System.InvalidOperationException> exceptions.</span></span>

> [!NOTE]
> <span data-ttu-id="18aa5-113"><xref:System.ArgumentException>不建議攔截例外狀況。</span><span class="sxs-lookup"><span data-stu-id="18aa5-113">Catching <xref:System.ArgumentException> exceptions is not recommended.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="18aa5-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="18aa5-114">Affected APIs</span></span>

- <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `M:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)`

-->

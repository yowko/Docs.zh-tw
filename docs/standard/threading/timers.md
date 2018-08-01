---
title: 計時器
description: 了解哪些 .NET 計時器可用於多執行緒環境。
ms.date: 07/03/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [.NET Framework], timers
- timers, about timers
ms.assetid: 7091500d-be18-499b-a942-95366ce185e5
author: pkulikov
ms.author: ronpet
ms.openlocfilehash: ae41c535d8bc1c0a05174b9051ba34f1a0a34638
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2018
ms.locfileid: "37875062"
---
# <a name="timers"></a><span data-ttu-id="be7fd-103">計時器</span><span class="sxs-lookup"><span data-stu-id="be7fd-103">Timers</span></span>

<span data-ttu-id="be7fd-104">.NET 提供兩種計時器，可用於多執行緒環境：</span><span class="sxs-lookup"><span data-stu-id="be7fd-104">.NET provides two timers to use in a multithreaded environment:</span></span>

- <span data-ttu-id="be7fd-105"><xref:System.Threading.Timer?displayProperty=nameWithType> 會定期在 <xref:System.Threading.ThreadPool> 執行緒上執行單一回呼方法。</span><span class="sxs-lookup"><span data-stu-id="be7fd-105"><xref:System.Threading.Timer?displayProperty=nameWithType>, which executes a single callback method on a <xref:System.Threading.ThreadPool> thread at regular intervals.</span></span>
- <span data-ttu-id="be7fd-106"><xref:System.Timers.Timer?displayProperty=nameWithType> 預設會定期在 <xref:System.Threading.ThreadPool> 執行緒上引發事件。</span><span class="sxs-lookup"><span data-stu-id="be7fd-106"><xref:System.Timers.Timer?displayProperty=nameWithType>, which by default raises an event on a <xref:System.Threading.ThreadPool> thread at regular intervals.</span></span>

> [!NOTE]
> <span data-ttu-id="be7fd-107">某些 .NET 實作可能會包含其他計時器：</span><span class="sxs-lookup"><span data-stu-id="be7fd-107">Some .NET implementations may include additional timers:</span></span>
>
> - <span data-ttu-id="be7fd-108"><xref:System.Windows.Forms.Timer?displayProperty=nameWithType>：定期引發事件的 Windows Forms 元件。</span><span class="sxs-lookup"><span data-stu-id="be7fd-108"><xref:System.Windows.Forms.Timer?displayProperty=nameWithType>: a Windows Forms component that fires an event at regular intervals.</span></span> <span data-ttu-id="be7fd-109">該元件沒有使用者介面，是專為用於單一執行緒環境所設計。</span><span class="sxs-lookup"><span data-stu-id="be7fd-109">The component has no user interface and is designed for use in a single-threaded environment.</span></span>  
> - <span data-ttu-id="be7fd-110"><xref:System.Web.UI.Timer?displayProperty=nameWithType>：定期執行非同步或同步網頁回傳的 ASP.NET 元件。</span><span class="sxs-lookup"><span data-stu-id="be7fd-110"><xref:System.Web.UI.Timer?displayProperty=nameWithType>: an ASP.NET component that performs asynchronous or synchronous web page postbacks at a regular interval.</span></span>
> - <span data-ttu-id="be7fd-111"><xref:System.Windows.Threading.DispatcherTimer?displayProperty=nameWithType>：整合到 <xref:System.Windows.Threading.Dispatcher> 佇列中的計時器，會依指定的時間間隔及指定的優先順序處理。</span><span class="sxs-lookup"><span data-stu-id="be7fd-111"><xref:System.Windows.Threading.DispatcherTimer?displayProperty=nameWithType>: a timer that is integrated into the <xref:System.Windows.Threading.Dispatcher> queue which is processed at a specified interval of time and at a specified priority.</span></span>

## <a name="the-systemthreadingtimer-class"></a><span data-ttu-id="be7fd-112">System.Threading.Timer 類別</span><span class="sxs-lookup"><span data-stu-id="be7fd-112">The System.Threading.Timer class</span></span>

<span data-ttu-id="be7fd-113"><xref:System.Threading.Timer?displayProperty=nameWithType> 類別可讓您依指定的時間間隔連續呼叫委派。</span><span class="sxs-lookup"><span data-stu-id="be7fd-113">The <xref:System.Threading.Timer?displayProperty=nameWithType> class enables you to continuously call a delegate at specified time intervals.</span></span> <span data-ttu-id="be7fd-114">您也可以使用此類別，排程單一委派呼叫依指定時間間隔執行。</span><span class="sxs-lookup"><span data-stu-id="be7fd-114">You also can use this class to schedule a single call to a delegate in a specified time interval.</span></span> <span data-ttu-id="be7fd-115">委派是在 <xref:System.Threading.ThreadPool> 執行緒上執行。</span><span class="sxs-lookup"><span data-stu-id="be7fd-115">The delegate is executed on a <xref:System.Threading.ThreadPool> thread.</span></span>

<span data-ttu-id="be7fd-116">當您建立 <xref:System.Threading.Timer?displayProperty=nameWithType> 物件時，您會指定定義回呼方法的 <xref:System.Threading.TimerCallback> 委派、傳遞至回呼的選擇性狀態物件、第一個回呼引動過程之前延遲的時間量，以及回呼引動過程之間的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="be7fd-116">When you create a <xref:System.Threading.Timer?displayProperty=nameWithType> object, you specify a <xref:System.Threading.TimerCallback> delegate that defines the callback method, an optional state object that is passed to the callback, the amount of time to delay before the first invocation of the callback, and the time interval between callback invocations.</span></span> <span data-ttu-id="be7fd-117">若要取消擱置中的計時器，請呼叫 <xref:System.Threading.Timer.Dispose%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="be7fd-117">To cancel a pending timer, call the <xref:System.Threading.Timer.Dispose%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="be7fd-118">下列範例會建立計時器，在一秒 (1000 毫秒) 後第一次呼叫提供的委派，然後每隔兩秒呼叫一次。</span><span class="sxs-lookup"><span data-stu-id="be7fd-118">The following example creates a timer that calls the provided delegate for the first time after one second (1000 milliseconds) and then calls it every two seconds.</span></span> <span data-ttu-id="be7fd-119">範例中的狀態物件可用來計算呼叫委派的次數。</span><span class="sxs-lookup"><span data-stu-id="be7fd-119">The state object in the example is used to count how many times the delegate is called.</span></span> <span data-ttu-id="be7fd-120">計時器會在委派至少呼叫 10 次時停止。</span><span class="sxs-lookup"><span data-stu-id="be7fd-120">The timer is stopped when the delegate has been called at least 10 times.</span></span>

[!code-cpp[System.Threading.Timer#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.Timer/CPP/source2.cpp#2)]
[!code-csharp[System.Threading.Timer#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.Timer/CS/source2.cs#2)]
[!code-vb[System.Threading.Timer#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.Timer/VB/source2.vb#2)]

<span data-ttu-id="be7fd-121">如需詳細資訊與範例，請參閱<xref:System.Threading.Timer?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="be7fd-121">For more information and examples, see <xref:System.Threading.Timer?displayProperty=nameWithType>.</span></span>

## <a name="the-systemtimerstimer-class"></a><span data-ttu-id="be7fd-122">System.Timers.Timer 類別</span><span class="sxs-lookup"><span data-stu-id="be7fd-122">The System.Timers.Timer class</span></span>

<span data-ttu-id="be7fd-123">可用於多執行緒環境的另一個計時器是 <xref:System.Timers.Timer?displayProperty=nameWithType>，預設會在 <xref:System.Threading.ThreadPool> 上引發事件。</span><span class="sxs-lookup"><span data-stu-id="be7fd-123">Another timer that can be used in a multithreaded environment is <xref:System.Timers.Timer?displayProperty=nameWithType> that by default raises an event on a <xref:System.Threading.ThreadPool> thread.</span></span>

<span data-ttu-id="be7fd-124">建立 <xref:System.Timers.Timer?displayProperty=nameWithType> 物件時，您可以指定要引發 <xref:System.Timers.Timer.Elapsed> 事件的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="be7fd-124">When you create a <xref:System.Timers.Timer?displayProperty=nameWithType> object, you may specify the time interval in which to raise an <xref:System.Timers.Timer.Elapsed> event.</span></span> <span data-ttu-id="be7fd-125">使用 <xref:System.Timers.Timer.Enabled%2A> 屬性指出計時器是否應該引發 <xref:System.Timers.Timer.Elapsed> 事件。</span><span class="sxs-lookup"><span data-stu-id="be7fd-125">Use the <xref:System.Timers.Timer.Enabled%2A> property to indicate if a timer should raise an <xref:System.Timers.Timer.Elapsed> event.</span></span> <span data-ttu-id="be7fd-126">如果您需要 <xref:System.Timers.Timer.Elapsed> 事件只在經過指定的間隔之後才引發，請將 <xref:System.Timers.Timer.AutoReset%2A> 設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="be7fd-126">If you need an <xref:System.Timers.Timer.Elapsed> event to be raised only once after the specified interval has elapsed, set the <xref:System.Timers.Timer.AutoReset%2A> to `false`.</span></span> <span data-ttu-id="be7fd-127"><xref:System.Timers.Timer.AutoReset%2A> 屬性的預設值為 `true`，表示 <xref:System.Timers.Timer.Elapsed> 事件會依 <xref:System.Timers.Timer.Interval%2A> 屬性定義的間隔定期引發。</span><span class="sxs-lookup"><span data-stu-id="be7fd-127">The default value of the <xref:System.Timers.Timer.AutoReset%2A> property is `true`, which means that an <xref:System.Timers.Timer.Elapsed> event is raised regularly at the interval defined by the <xref:System.Timers.Timer.Interval%2A> property.</span></span>

<span data-ttu-id="be7fd-128">如需詳細資訊與範例，請參閱<xref:System.Timers.Timer?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="be7fd-128">For more information and examples, see <xref:System.Timers.Timer?displayProperty=nameWithType>.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="be7fd-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be7fd-129">See also</span></span>

 <xref:System.Threading.Timer?displayProperty=nameWithType>  
 <xref:System.Timers.Timer?displayProperty=nameWithType>  
 [<span data-ttu-id="be7fd-130">執行緒物件和功能</span><span class="sxs-lookup"><span data-stu-id="be7fd-130">Threading Objects and Features</span></span>](threading-objects-and-features.md)

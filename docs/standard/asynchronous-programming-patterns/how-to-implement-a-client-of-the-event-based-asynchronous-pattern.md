---
title: 如何：實作事件架構非同步模式的用戶端
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- threading [Windows Forms], asynchronous features
- AsyncCompletedEventArgs class
ms.assetid: 21a858c1-3c99-4904-86ee-0d17b49804fa
ms.openlocfilehash: 4176d1a4cec91c5740b03c10d1a6d2cc263dba28
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "45998808"
---
# <a name="how-to-implement-a-client-of-the-event-based-asynchronous-pattern"></a><span data-ttu-id="c814e-102">如何：實作事件架構非同步模式的用戶端</span><span class="sxs-lookup"><span data-stu-id="c814e-102">How to: Implement a Client of the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="c814e-103">下列程式碼範例示範如何使用遵守[事件架構非同步模式概觀](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)的元件。</span><span class="sxs-lookup"><span data-stu-id="c814e-103">The following code example demonstrates how to use a component that adheres to the [Event-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span></span> <span data-ttu-id="c814e-104">此範例的表單使用 `PrimeNumberCalculator` 元件，請參閱[如何：實作支援事件架構非同步模式的元件](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)所述。</span><span class="sxs-lookup"><span data-stu-id="c814e-104">The form for this example uses the `PrimeNumberCalculator` component described in [How to: Implement a Component That Supports the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).</span></span>  
  
 <span data-ttu-id="c814e-105">當您執行使用此範例的專案時，就會看到含有資料格的「質數計算機」表單和兩個按鈕：[開始新工作] 和 [取消]。</span><span class="sxs-lookup"><span data-stu-id="c814e-105">When you run a project that uses this example, you will see a "Prime Number Calculator" form with a grid and two buttons: **Start New Task** and **Cancel**.</span></span> <span data-ttu-id="c814e-106">您可以連續按一下 [開始新工作] 按鈕數次，然後每按一下，非同步作業都會開始計算以決定隨機產生的測試數字是否為質數。</span><span class="sxs-lookup"><span data-stu-id="c814e-106">You can click the **Start New Task** button several times in succession, and for each click, an asynchronous operation will begin a computation to determine if a randomly generated test number is prime.</span></span> <span data-ttu-id="c814e-107">表單會定期顯示進度和累加結果。</span><span class="sxs-lookup"><span data-stu-id="c814e-107">The form will periodically display progress and incremental results.</span></span> <span data-ttu-id="c814e-108">每個作業都會指派一個工作識別碼。</span><span class="sxs-lookup"><span data-stu-id="c814e-108">Each operation is assigned a unique task ID.</span></span> <span data-ttu-id="c814e-109">計算結果會顯示在 [結果] 欄，如果測試號碼不是質數，就會標示為 [複合]，並顯示其第一個除數。</span><span class="sxs-lookup"><span data-stu-id="c814e-109">The result of the computation is displayed in the **Result** column; if the test number is not prime, it is labeled as **Composite,** and its first divisor is displayed.</span></span>  
  
 <span data-ttu-id="c814e-110">任何暫止的作業可以使用 [取消] 按鈕來取消。</span><span class="sxs-lookup"><span data-stu-id="c814e-110">Any pending operation can be canceled with the **Cancel** button.</span></span> <span data-ttu-id="c814e-111">您可以選取多個項目。</span><span class="sxs-lookup"><span data-stu-id="c814e-111">Multiple selections can be made.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c814e-112">大部分數字都不會是質數。</span><span class="sxs-lookup"><span data-stu-id="c814e-112">Most numbers will not be prime.</span></span> <span data-ttu-id="c814e-113">如果數次完成作業後都找不到質數，只要啟動更多工作，最終一定會找到一些質數。</span><span class="sxs-lookup"><span data-stu-id="c814e-113">If you have not found a prime number after several completed operations, simply start more tasks, and eventually you will find some prime numbers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c814e-114">範例</span><span class="sxs-lookup"><span data-stu-id="c814e-114">Example</span></span>  
 [!code-csharp[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#10)]
 [!code-vb[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="c814e-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c814e-115">See also</span></span>

- <xref:System.ComponentModel.AsyncOperation>  
- <xref:System.ComponentModel.AsyncOperationManager>  
- <xref:System.Windows.Forms.WindowsFormsSynchronizationContext>

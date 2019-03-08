---
title: 微調非同步應用程式 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 4c3e7997-a95f-4fbe-a6ac-60ba042d30b9
ms.openlocfilehash: bd03e0874cedd360f5b31984b4b49b3d5b647c7f
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2019
ms.locfileid: "57677041"
---
# <a name="fine-tuning-your-async-application-visual-basic"></a><span data-ttu-id="b1f95-102">微調非同步應用程式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b1f95-102">Fine-Tuning Your Async Application (Visual Basic)</span></span>
<span data-ttu-id="b1f95-103">您可以使用 <xref:System.Threading.Tasks.Task> 類型所提供的方法和屬性，來增加非同步應用程式的精確度和彈性。</span><span class="sxs-lookup"><span data-stu-id="b1f95-103">You can add precision and flexibility to your async applications by using the methods and properties that the <xref:System.Threading.Tasks.Task> type makes available.</span></span> <span data-ttu-id="b1f95-104">本節的主題會示範使用 <xref:System.Threading.CancellationToken> 以及 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> 和 <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> 等重要 `Task` 方法的範例。</span><span class="sxs-lookup"><span data-stu-id="b1f95-104">The topics in this section show examples that use <xref:System.Threading.CancellationToken> and important `Task` methods such as <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="b1f95-105">您可以使用 `WhenAny` 和 `WhenAll`，更輕鬆地啟動多個工作，並藉由監視單一工作等候其完成。</span><span class="sxs-lookup"><span data-stu-id="b1f95-105">By using `WhenAny` and `WhenAll`, you can more easily start multiple tasks and await their completion by monitoring a single task.</span></span>  
  
-   <span data-ttu-id="b1f95-106">`WhenAny` 會在集合中的任何工作完成時，傳回一個完成的工作。</span><span class="sxs-lookup"><span data-stu-id="b1f95-106">`WhenAny` returns a task that completes when any task in a collection is complete.</span></span>  
  
     <span data-ttu-id="b1f95-107">如需範例，使用`WhenAny`，請參閱 <<c2> [ 後一個 Is Complete (Visual Basic) 取消剩餘的非同步工作](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)並[啟動多項非同步工作和程序它們完成時進行 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)。</span><span class="sxs-lookup"><span data-stu-id="b1f95-107">For examples that use `WhenAny`, see  [Cancel Remaining Async Tasks after One Is Complete (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)and [Start Multiple Async Tasks and Process Them As They Complete (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).</span></span>  
  
-   <span data-ttu-id="b1f95-108">`WhenAll` 會在集合中的所有工作完成時，傳回一個完成的工作。</span><span class="sxs-lookup"><span data-stu-id="b1f95-108">`WhenAll` returns a task that completes when all tasks in a collection are complete.</span></span>  
  
     <span data-ttu-id="b1f95-109">如需使用 `WhenAll` 的詳細資訊和範例，請參閱[如何：使用 Task.WhenAll (Visual Basic) 來擴充非同步逐步解說](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)。</span><span class="sxs-lookup"><span data-stu-id="b1f95-109">For more information and an example that uses `WhenAll`, see [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
 <span data-ttu-id="b1f95-110">本節包含下列範例。</span><span class="sxs-lookup"><span data-stu-id="b1f95-110">This section includes the following examples.</span></span>  
  
-   <span data-ttu-id="b1f95-111">[取消一項非同步工作或一份工作 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)。</span><span class="sxs-lookup"><span data-stu-id="b1f95-111">[Cancel an Async Task or a List of Tasks (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).</span></span>  
  
-   [<span data-ttu-id="b1f95-112">一段時間 (Visual Basic) 後取消非同步工作</span><span class="sxs-lookup"><span data-stu-id="b1f95-112">Cancel Async Tasks after a Period of Time (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
-   [<span data-ttu-id="b1f95-113">當取消剩餘的非同步工作是完成 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b1f95-113">Cancel Remaining Async Tasks after One Is Complete (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
-   [<span data-ttu-id="b1f95-114">啟動多項非同步工作並處理完成 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b1f95-114">Start Multiple Async Tasks and Process Them As They Complete (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
>  <span data-ttu-id="b1f95-115">若要執行範例，您必須在電腦上安裝 Visual Studio 2012 或更新版本以及 .NET Framework 4.5 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="b1f95-115">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
 <span data-ttu-id="b1f95-116">這些專案會建立 UI，其中包含一個啟動處理序的按鈕和一個取消處理序的按鈕，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="b1f95-116">The projects create a UI that contains a button that starts the process and a button that cancels it, as the following image shows.</span></span> <span data-ttu-id="b1f95-117">這兩個按鈕的名稱分別是 `startButton` 和 `cancelButton`。</span><span class="sxs-lookup"><span data-stu-id="b1f95-117">The buttons are named `startButton` and `cancelButton`.</span></span>  
  
 <span data-ttu-id="b1f95-118">![具有 [取消] 按鈕的 WPF 視窗](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "具有啟動和停止按鈕的對話方塊")</span><span class="sxs-lookup"><span data-stu-id="b1f95-118">![WPF window with Cancel button](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Dialog box with a Start and Stop button")</span></span>  
  
 <span data-ttu-id="b1f95-119">您可以從 [Async Sample:Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) (非同步範例：微調應用程式) 下載完整 Windows Presentation Foundation (WPF) 專案。</span><span class="sxs-lookup"><span data-stu-id="b1f95-119">You can download the complete Windows Presentation Foundation (WPF) projects from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1f95-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1f95-120">See also</span></span>
- [<span data-ttu-id="b1f95-121">使用 Async 和 Await 進行非同步程式設計 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b1f95-121">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)

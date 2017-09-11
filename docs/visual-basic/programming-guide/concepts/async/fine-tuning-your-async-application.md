---
title: "微調非同步應用程式 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 4c3e7997-a95f-4fbe-a6ac-60ba042d30b9
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: e031c2e23430a62629424ee57a140a7d8da41777
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="fine-tuning-your-async-application-visual-basic"></a><span data-ttu-id="d06b4-102">微調非同步應用程式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d06b4-102">Fine-Tuning Your Async Application (Visual Basic)</span></span>
<span data-ttu-id="d06b4-103">您可以加入有效位數和彈性非同步應用程式所使用的方法和屬性，<xref:System.Threading.Tasks.Task>可產生型別。</xref:System.Threading.Tasks.Task></span><span class="sxs-lookup"><span data-stu-id="d06b4-103">You can add precision and flexibility to your async applications by using the methods and properties that the <xref:System.Threading.Tasks.Task> type makes available.</span></span> <span data-ttu-id="d06b4-104">本章節的主題說明使用範例<xref:System.Threading.CancellationToken>重要`Task`方法，例如<xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>和<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName>.</xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName> </xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> </xref:System.Threading.CancellationToken></span><span class="sxs-lookup"><span data-stu-id="d06b4-104">The topics in this section show examples that use <xref:System.Threading.CancellationToken> and important `Task` methods such as <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName>.</span></span>  
  
 <span data-ttu-id="d06b4-105">使用`WhenAny`和`WhenAll`，您可以更輕鬆地啟動多項工作，並藉由監視單一工作等候其完成。</span><span class="sxs-lookup"><span data-stu-id="d06b4-105">By using `WhenAny` and `WhenAll`, you can more easily start multiple tasks and await their completion by monitoring a single task.</span></span>  
  
-   <span data-ttu-id="d06b4-106">`WhenAny`傳回集合中的任何工作完成時完成的工作。</span><span class="sxs-lookup"><span data-stu-id="d06b4-106">`WhenAny` returns a task that completes when any task in a collection is complete.</span></span>  
  
     <span data-ttu-id="d06b4-107">如需使用範例`WhenAny`，請參閱[後一個完整 (Visual Basic) 取消剩餘的非同步工作](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)和[啟動多項非同步工作和程序它們做為它們完成 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)。</span><span class="sxs-lookup"><span data-stu-id="d06b4-107">For examples that use `WhenAny`, see  [Cancel Remaining Async Tasks after One Is Complete (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)and [Start Multiple Async Tasks and Process Them As They Complete (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).</span></span>  
  
-   <span data-ttu-id="d06b4-108">`WhenAll`傳回集合中的所有工作都都完成時完成的工作。</span><span class="sxs-lookup"><span data-stu-id="d06b4-108">`WhenAll` returns a task that completes when all tasks in a collection are complete.</span></span>  
  
     <span data-ttu-id="d06b4-109">如需詳細資訊和範例會使用`WhenAll`，請參閱[How to︰ 擴充非同步逐步解說使用 Task.WhenAll (Visual Basic) 的](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)。</span><span class="sxs-lookup"><span data-stu-id="d06b4-109">For more information and an example that uses `WhenAll`, see [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
 <span data-ttu-id="d06b4-110">本節包含下列的範例。</span><span class="sxs-lookup"><span data-stu-id="d06b4-110">This section includes the following examples.</span></span>  
  
-   <span data-ttu-id="d06b4-111">[取消一項非同步工作或一份工作 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)。</span><span class="sxs-lookup"><span data-stu-id="d06b4-111">[Cancel an Async Task or a List of Tasks (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).</span></span>  
  
-   [<span data-ttu-id="d06b4-112">取消非同步工作一段時間 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d06b4-112">Cancel Async Tasks after a Period of Time (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
-   [<span data-ttu-id="d06b4-113">當取消剩餘的非同步工作是完整 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d06b4-113">Cancel Remaining Async Tasks after One Is Complete (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
-   [<span data-ttu-id="d06b4-114">啟動多項非同步工作並處理它們完成 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d06b4-114">Start Multiple Async Tasks and Process Them As They Complete (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
>  <span data-ttu-id="d06b4-115">若要執行範例，您必須擁有 Visual Studio 2012 或較新和.NET Framework 4.5 或更新版本安裝在電腦上。</span><span class="sxs-lookup"><span data-stu-id="d06b4-115">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
 <span data-ttu-id="d06b4-116">專案會建立包含啟動處理序的按鈕和一個按鈕，取消它，如下列影像所示的 UI。</span><span class="sxs-lookup"><span data-stu-id="d06b4-116">The projects create a UI that contains a button that starts the process and a button that cancels it, as the following image shows.</span></span> <span data-ttu-id="d06b4-117">這些按鈕會命名為`startButton`和`cancelButton`。</span><span class="sxs-lookup"><span data-stu-id="d06b4-117">The buttons are named `startButton` and `cancelButton`.</span></span>  
  
 <span data-ttu-id="d06b4-118">![具有 [取消] 按鈕的 WPF 視窗](../../../../csharp/programming-guide/concepts/async/media/cancellation.png "取消")</span><span class="sxs-lookup"><span data-stu-id="d06b4-118">![WPF window with Cancel button](../../../../csharp/programming-guide/concepts/async/media/cancellation.png "Cancellation")</span></span>  
  
 <span data-ttu-id="d06b4-119">您可以下載完整的 Windows Presentation Foundation (WPF) 專案，從[非同步範例︰ 順利微調您的應用程式](http://go.microsoft.com/fwlink/?LinkId=255046)。</span><span class="sxs-lookup"><span data-stu-id="d06b4-119">You can download the complete Windows Presentation Foundation (WPF) projects from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d06b4-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d06b4-120">See Also</span></span>  
 [<span data-ttu-id="d06b4-121">非同步程式設計使用 Async 和 Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d06b4-121">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)

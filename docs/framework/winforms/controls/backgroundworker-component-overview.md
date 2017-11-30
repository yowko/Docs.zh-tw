---
title: "BackgroundWorker 元件概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
f1_keywords: BackgroundWorker
helpviewer_keywords:
- BackgroundWorker component
- background tasks
- Asynchronous Pattern
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- threading [Windows Forms], background operations
- background operations
ms.assetid: 64e9b3ab-7443-4a77-ab17-b8b8c0cb3f62
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f192081d9b7e30f10373342aef39443ff49e9931
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="backgroundworker-component-overview"></a><span data-ttu-id="66874-102">BackgroundWorker 元件概觀</span><span class="sxs-lookup"><span data-stu-id="66874-102">BackgroundWorker Component Overview</span></span>
<span data-ttu-id="66874-103">有許多經常執行的作業都需要長時間執行。</span><span class="sxs-lookup"><span data-stu-id="66874-103">There are many commonly performed operations that can take a long time to execute.</span></span> <span data-ttu-id="66874-104">例如：</span><span class="sxs-lookup"><span data-stu-id="66874-104">For example:</span></span>  
  
-   <span data-ttu-id="66874-105">映像下載</span><span class="sxs-lookup"><span data-stu-id="66874-105">Image downloads</span></span>  
  
-   <span data-ttu-id="66874-106">Web 服務叫用</span><span class="sxs-lookup"><span data-stu-id="66874-106">Web service invocations</span></span>  
  
-   <span data-ttu-id="66874-107">檔案下載及上傳 (包括對等應用程式)</span><span class="sxs-lookup"><span data-stu-id="66874-107">File downloads and uploads (including for peer-to-peer applications)</span></span>  
  
-   <span data-ttu-id="66874-108">複雜的本機運算</span><span class="sxs-lookup"><span data-stu-id="66874-108">Complex local computations</span></span>  
  
-   <span data-ttu-id="66874-109">資料庫交易</span><span class="sxs-lookup"><span data-stu-id="66874-109">Database transactions</span></span>  
  
-   <span data-ttu-id="66874-110">本機磁碟存取 (假設因為存取記憶體導致速度變慢)</span><span class="sxs-lookup"><span data-stu-id="66874-110">Local disk access, given its slow speed relative to memory access</span></span>  
  
 <span data-ttu-id="66874-111">當這類作業執行時，可能會導致您的使用者介面無回應。</span><span class="sxs-lookup"><span data-stu-id="66874-111">Operations like these can cause your user interface to hang while they are running.</span></span> <span data-ttu-id="66874-112">當您需要 UI 即時回應，但 UI 卻受到這些作業拖累，導致回應時間拉長時，<xref:System.ComponentModel.BackgroundWorker> 元件可以提供合宜的解決方法。</span><span class="sxs-lookup"><span data-stu-id="66874-112">When you want a responsive UI and you are faced with long delays associated with such operations, the <xref:System.ComponentModel.BackgroundWorker> component provides a convenient solution.</span></span>  
  
 <span data-ttu-id="66874-113"><xref:System.ComponentModel.BackgroundWorker> 元件可以非同步 (在背景中) 的方式，透過不同於應用程式之主要 UI 執行緒的執行緒來執行這些耗時的作業。</span><span class="sxs-lookup"><span data-stu-id="66874-113">The <xref:System.ComponentModel.BackgroundWorker> component gives you the ability to execute time-consuming operations asynchronously ("in the background"), on a thread different from your application's main UI thread.</span></span> <span data-ttu-id="66874-114">若要使用 <xref:System.ComponentModel.BackgroundWorker>，只須告知此函式要在背景中執行哪一個工作者方法，然後再呼叫 <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> 方法就可以了。</span><span class="sxs-lookup"><span data-stu-id="66874-114">To use a <xref:System.ComponentModel.BackgroundWorker>, you simply tell it what time-consuming worker method to execute in the background, and then you call the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method.</span></span> <span data-ttu-id="66874-115">您呼叫的執行緒會如常執行，而工作者方法也會以非同步的方式同時執行。</span><span class="sxs-lookup"><span data-stu-id="66874-115">Your calling thread continues to run normally while the worker method runs asynchronously.</span></span> <span data-ttu-id="66874-116">當方法結束時，<xref:System.ComponentModel.BackgroundWorker> 會引發 <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> 事件來提示您呼叫的執行緒，並視情況在事件中包含作業的結果。</span><span class="sxs-lookup"><span data-stu-id="66874-116">When the method is finished, the <xref:System.ComponentModel.BackgroundWorker> alerts the calling thread by firing the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event, which optionally contains the results of the operation.</span></span>  
  
 <span data-ttu-id="66874-117"><xref:System.ComponentModel.BackgroundWorker>元件可從**工具箱**，請在**元件** 索引標籤。若要將 <xref:System.ComponentModel.BackgroundWorker> 加入表單，可將 <xref:System.ComponentModel.BackgroundWorker> 元件拖曳至表單中。</span><span class="sxs-lookup"><span data-stu-id="66874-117">The <xref:System.ComponentModel.BackgroundWorker> component is available from the **Toolbox**, in the **Components** tab. To add a <xref:System.ComponentModel.BackgroundWorker> to your form, drag the <xref:System.ComponentModel.BackgroundWorker> component onto your form.</span></span> <span data-ttu-id="66874-118">它會出現在元件匣中，和其屬性會出現在**屬性**視窗。</span><span class="sxs-lookup"><span data-stu-id="66874-118">It appears in the component tray, and its properties appear in the **Properties** window.</span></span>  
  
 <span data-ttu-id="66874-119">若要啟動非同步作業，請使用 <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="66874-119">To start your asynchronous operation, use the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method.</span></span> <span data-ttu-id="66874-120"><xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> 可接受選用的 `object` 參數將引數傳遞給您的工作者方法。</span><span class="sxs-lookup"><span data-stu-id="66874-120"><xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> takes an optional `object` parameter, which can be used to pass arguments to your worker method.</span></span> <span data-ttu-id="66874-121"><xref:System.ComponentModel.BackgroundWorker> 類別會引發 <xref:System.ComponentModel.BackgroundWorker.DoWork> 事件，而您的工作者執行緒會經由 <xref:System.ComponentModel.BackgroundWorker.DoWork> 事件處理常式連結至此事件。</span><span class="sxs-lookup"><span data-stu-id="66874-121">The <xref:System.ComponentModel.BackgroundWorker> class exposes the <xref:System.ComponentModel.BackgroundWorker.DoWork> event, to which your worker thread is attached through a <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span>  
  
 <span data-ttu-id="66874-122"><xref:System.ComponentModel.BackgroundWorker.DoWork> 事件處理常式可接受具有 <xref:System.ComponentModel.DoWorkEventArgs> 屬性的 <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> 參數。</span><span class="sxs-lookup"><span data-stu-id="66874-122">The <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler takes a <xref:System.ComponentModel.DoWorkEventArgs> parameter, which has an <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> property.</span></span> <span data-ttu-id="66874-123">此屬性會從 <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> 接收參數，並可傳遞給 <xref:System.ComponentModel.BackgroundWorker.DoWork> 事件處理常式中所呼叫的工作者方法。</span><span class="sxs-lookup"><span data-stu-id="66874-123">This property receives the parameter from <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> and can be passed to your worker method, which will be called in the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span> <span data-ttu-id="66874-124">下列範例示範如何指派工作者方法 `ComputeFibonacci` 所產生的結果。</span><span class="sxs-lookup"><span data-stu-id="66874-124">The following example shows how to assign a result from a worker method called `ComputeFibonacci`.</span></span> <span data-ttu-id="66874-125">它是完整的範例，您可以在找到的一部分[How to： 實作使用背景作業的表單](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)。</span><span class="sxs-lookup"><span data-stu-id="66874-125">It is part of a larger example, which you can find at [How to: Implement a Form That Uses a Background Operation](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md).</span></span>  
  
 [!code-cpp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
 [!code-vb[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]  
  
 <span data-ttu-id="66874-126">如需有關如何使用事件處理常式的詳細資訊，請參閱[事件](../../../../docs/standard/events/index.md)。</span><span class="sxs-lookup"><span data-stu-id="66874-126">For more information on using event handlers, see [Events](../../../../docs/standard/events/index.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="66874-127">無論使用何種多執行緒作業，您都可能會面臨嚴重而複雜的錯誤。</span><span class="sxs-lookup"><span data-stu-id="66874-127">When using multithreading of any sort, you potentially expose yourself to very serious and complex bugs.</span></span> <span data-ttu-id="66874-128">請在實作使用多執行緒的任何解決方案之前參閱 [Managed 執行緒最佳做法](../../../../docs/standard/threading/managed-threading-best-practices.md)。</span><span class="sxs-lookup"><span data-stu-id="66874-128">Consult the [Managed Threading Best Practices](../../../../docs/standard/threading/managed-threading-best-practices.md) before implementing any solution that uses multithreading.</span></span>  
  
 <span data-ttu-id="66874-129">如需有關使用<xref:System.ComponentModel.BackgroundWorker>類別，請參閱[How to： 在背景執行作業](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)。</span><span class="sxs-lookup"><span data-stu-id="66874-129">For more information on using the <xref:System.ComponentModel.BackgroundWorker> class, see [How to: Run an Operation in the Background](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66874-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="66874-130">See Also</span></span>  
 [<span data-ttu-id="66874-131">不在組建中： Visual Basic 中的多執行緒</span><span class="sxs-lookup"><span data-stu-id="66874-131">NOT IN BUILD: Multithreading in Visual Basic</span></span>](http://msdn.microsoft.com/en-us/c731a50c-09c1-4468-9646-54c86b75d269)  
 [<span data-ttu-id="66874-132">操作說明：實作使用背景作業的表單</span><span class="sxs-lookup"><span data-stu-id="66874-132">How to: Implement a Form That Uses a Background Operation</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)

---
title: HOW TO：在背景下載檔案
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BackgroundWorker component
- background tasks
- Asynchronous Pattern
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- threading [Windows Forms], background operations
- background operations
ms.assetid: 9b7bc5ae-051c-4904-9720-18f6667388bd
ms.openlocfilehash: ed7d5593a29726412f5ea75812cf5a6d800ee77a
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591716"
---
# <a name="how-to-download-a-file-in-the-background"></a><span data-ttu-id="6c4fc-102">作法：在背景下載檔案</span><span class="sxs-lookup"><span data-stu-id="6c4fc-102">How to: Download a File in the Background</span></span>
<span data-ttu-id="6c4fc-103">下載檔案是常見的工作，在不同執行緒上執行這種可能很耗時的作業通常會相當實用。</span><span class="sxs-lookup"><span data-stu-id="6c4fc-103">Downloading a file is a common task, and it is often useful to run this potentially time-consuming operation on a separate thread.</span></span> <span data-ttu-id="6c4fc-104">使用 <xref:System.ComponentModel.BackgroundWorker> 元件，以非常少的程式碼來完成這項工作。</span><span class="sxs-lookup"><span data-stu-id="6c4fc-104">Use the <xref:System.ComponentModel.BackgroundWorker> component to accomplish this task with very little code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c4fc-105">範例</span><span class="sxs-lookup"><span data-stu-id="6c4fc-105">Example</span></span>  
 <span data-ttu-id="6c4fc-106">下列程式碼範例示範如何使用 <xref:System.ComponentModel.BackgroundWorker> 元件從 URL 載入 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="6c4fc-106">The following code example demonstrates how to use a <xref:System.ComponentModel.BackgroundWorker> component to load an XML file from a URL.</span></span> <span data-ttu-id="6c4fc-107">當使用者按一下**下載** 按鈕，<xref:System.Windows.Forms.Control.Click>事件處理常式呼叫<xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>方法<xref:System.ComponentModel.BackgroundWorker>元件來啟動下載作業。</span><span class="sxs-lookup"><span data-stu-id="6c4fc-107">When the user clicks the **Download** button, the <xref:System.Windows.Forms.Control.Click> event handler calls the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method of a <xref:System.ComponentModel.BackgroundWorker> component to start the download operation.</span></span> <span data-ttu-id="6c4fc-108">按鈕會在下載期間停用，然後當下載完成時再啟用。</span><span class="sxs-lookup"><span data-stu-id="6c4fc-108">The button is disabled for the duration of the download, and then enabled when the download is complete.</span></span> <span data-ttu-id="6c4fc-109"><xref:System.Windows.Forms.MessageBox> 會顯示檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="6c4fc-109">A <xref:System.Windows.Forms.MessageBox> displays the contents of the file.</span></span>  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#1)]  
  
 <span data-ttu-id="6c4fc-110">**下載檔案**</span><span class="sxs-lookup"><span data-stu-id="6c4fc-110">**Downloading the file**</span></span>  
  
 <span data-ttu-id="6c4fc-111">檔案會在 <xref:System.ComponentModel.BackgroundWorker> 元件的背景工作執行緒上下載，該執行緒會執行 <xref:System.ComponentModel.BackgroundWorker.DoWork> 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="6c4fc-111">The file is downloaded on the <xref:System.ComponentModel.BackgroundWorker> component's worker thread, which runs the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span> <span data-ttu-id="6c4fc-112">當您的程式碼呼叫 <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> 方法時，會啟動此執行緒。</span><span class="sxs-lookup"><span data-stu-id="6c4fc-112">This thread starts when your code calls the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method.</span></span>  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#3)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#3)]  
  
 <span data-ttu-id="6c4fc-113">**等候 BackgroundWorker 完成**</span><span class="sxs-lookup"><span data-stu-id="6c4fc-113">**Waiting for a BackgroundWorker to finish**</span></span>  
  
 <span data-ttu-id="6c4fc-114">`downloadButton_Click` 事件處理常式會示範如何等候 <xref:System.ComponentModel.BackgroundWorker> 元件完成其非同步工作。</span><span class="sxs-lookup"><span data-stu-id="6c4fc-114">The `downloadButton_Click` event handler demonstrates how to wait for a <xref:System.ComponentModel.BackgroundWorker> component to finish its asynchronous task.</span></span>  
  
 <span data-ttu-id="6c4fc-115">如果您只想要讓應用程式回應事件，並不想要在等候背景執行緒完成時，於主執行緒中執行任何工作，則直接結束這個處理常式即可。</span><span class="sxs-lookup"><span data-stu-id="6c4fc-115">If you only want the application to respond to events and do not want to do any work in the main thread while you wait for the background thread to complete, just exit the handler.</span></span>  
  
 <span data-ttu-id="6c4fc-116">如果您想要繼續進行主執行緒中的工作，請使用 <xref:System.ComponentModel.BackgroundWorker.IsBusy%2A> 屬性來判斷 <xref:System.ComponentModel.BackgroundWorker> 執行緒是否仍在執行中。</span><span class="sxs-lookup"><span data-stu-id="6c4fc-116">If you want to continue doing work in the main thread, use the <xref:System.ComponentModel.BackgroundWorker.IsBusy%2A> property to determine whether the <xref:System.ComponentModel.BackgroundWorker> thread is still running.</span></span> <span data-ttu-id="6c4fc-117">在本範例中，當正在處理下載時，會更新進度列。</span><span class="sxs-lookup"><span data-stu-id="6c4fc-117">In the example, a progress bar is updated while the download is processing.</span></span> <span data-ttu-id="6c4fc-118">請確定呼叫 <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> 方法，以保留 UI 回應性。</span><span class="sxs-lookup"><span data-stu-id="6c4fc-118">Be sure to call the <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> method to keep the UI responsive.</span></span>  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#2)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#2)]  
  
 <span data-ttu-id="6c4fc-119">**顯示結果**</span><span class="sxs-lookup"><span data-stu-id="6c4fc-119">**Displaying the result**</span></span>  
  
 <span data-ttu-id="6c4fc-120">`backgroundWorker1_RunWorkerCompleted` 方法會處理 <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> 事件，會在背景作業完成時被呼叫。</span><span class="sxs-lookup"><span data-stu-id="6c4fc-120">The `backgroundWorker1_RunWorkerCompleted` method handles the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event and is called when the background operation is completed.</span></span> <span data-ttu-id="6c4fc-121">這個方法會先檢查 <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="6c4fc-121">This method first checks the <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="6c4fc-122">如果 <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> 是 `null`，則這個方法會顯示檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="6c4fc-122">If <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> is `null`, then this method displays the contents of the file.</span></span> <span data-ttu-id="6c4fc-123">然後會啟用開始下載時被停用的下載按鈕，並重設其進度列。</span><span class="sxs-lookup"><span data-stu-id="6c4fc-123">It then enables the download button, which was disabled when the download began, and it resets the progress bar.</span></span>  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#4)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6c4fc-124">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="6c4fc-124">Compiling the Code</span></span>  
 <span data-ttu-id="6c4fc-125">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="6c4fc-125">This example requires:</span></span>  
  
- <span data-ttu-id="6c4fc-126">System.Drawing、System.Windows.Forms 和 System.Xml 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="6c4fc-126">References to the System.Drawing, System.Windows.Forms, and System.Xml assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="6c4fc-127">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="6c4fc-127">Robust Programming</span></span>  
 <span data-ttu-id="6c4fc-128">請務必檢查您 <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> 事件處理常式中的 <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> 屬性，再嘗試存取可能會受 <xref:System.ComponentModel.BackgroundWorker.DoWork> 事件處理常式影響的 <xref:System.ComponentModel.RunWorkerCompletedEventArgs.Result%2A?displayProperty=nameWithType> 屬性或任何其他物件。</span><span class="sxs-lookup"><span data-stu-id="6c4fc-128">Always check the <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> property in your <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler before attempting to access the <xref:System.ComponentModel.RunWorkerCompletedEventArgs.Result%2A?displayProperty=nameWithType> property or any other object that may have been affected by the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c4fc-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c4fc-129">See also</span></span>

- <xref:System.ComponentModel.BackgroundWorker>
- [<span data-ttu-id="6c4fc-130">如何：在背景執行作業</span><span class="sxs-lookup"><span data-stu-id="6c4fc-130">How to: Run an Operation in the Background</span></span>](how-to-run-an-operation-in-the-background.md)
- [<span data-ttu-id="6c4fc-131">如何：實作使用背景作業的表單</span><span class="sxs-lookup"><span data-stu-id="6c4fc-131">How to: Implement a Form That Uses a Background Operation</span></span>](how-to-implement-a-form-that-uses-a-background-operation.md)

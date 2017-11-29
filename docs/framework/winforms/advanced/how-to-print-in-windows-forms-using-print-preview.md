---
title: "如何：使用預覽列印在 Windows Form 中進行列印"
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
helpviewer_keywords:
- printing [Windows Forms], using print preview
- printing [Windows Forms], with print preview
- print preview
ms.assetid: 4a16f7e2-ae10-4485-b0ae-3d558334d0fe
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 08ed914ebd868390233cead97de5d326eb77e390
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-print-in-windows-forms-using-print-preview"></a><span data-ttu-id="75b6b-102">如何：使用預覽列印在 Windows Form 中進行列印</span><span class="sxs-lookup"><span data-stu-id="75b6b-102">How to: Print in Windows Forms Using Print Preview</span></span>
<span data-ttu-id="75b6b-103">這在 Windows Form 程式設計中很常見，除了列印服務，還提供預覽列印。</span><span class="sxs-lookup"><span data-stu-id="75b6b-103">It is very common in Windows Forms programming to offer print preview in addition to printing services.</span></span> <span data-ttu-id="75b6b-104">若要將預覽列印服務加入您的應用程式，有一個簡單的方法，那就是使用 <xref:System.Windows.Forms.PrintPreviewDialog> 控制項結合 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件處理邏輯來列印檔案。</span><span class="sxs-lookup"><span data-stu-id="75b6b-104">An easy way to add print preview services to your application is to use a <xref:System.Windows.Forms.PrintPreviewDialog> control in combination with the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event-handling logic for printing a file.</span></span>  
  
### <a name="to-preview-a-text-document-with-a-printpreviewdialog-control"></a><span data-ttu-id="75b6b-105">使用 PrintPreviewDialog 控制項來預覽文字文件</span><span class="sxs-lookup"><span data-stu-id="75b6b-105">To preview a text document with a PrintPreviewDialog control</span></span>  
  
1.  <span data-ttu-id="75b6b-106">將 <xref:System.Windows.Forms.PrintPreviewDialog>、 <xref:System.Drawing.Printing.PrintDocument>和兩個字串加入您的表單。</span><span class="sxs-lookup"><span data-stu-id="75b6b-106">Add a <xref:System.Windows.Forms.PrintPreviewDialog>, <xref:System.Drawing.Printing.PrintDocument>, and two strings to your form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#1)]  
  
2.  <span data-ttu-id="75b6b-107">將 <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> 屬性設定為您想要列印的文件，開啟文件，並將文件內容讀取至您之前加入的字串。</span><span class="sxs-lookup"><span data-stu-id="75b6b-107">Set the <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> property to the document you wish to print, and open and read the document's contents to the string you added previously.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#2)]  
  
3.  <span data-ttu-id="75b6b-108">就像平常在列印文件一樣，在 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件處理常式中，使用 <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> 類別的 <xref:System.Drawing.Printing.PrintPageEventArgs> 屬性以及檔案內容來計算每一頁的行數，並轉譯文件的內容。</span><span class="sxs-lookup"><span data-stu-id="75b6b-108">As you would for printing the document, in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler, use the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class and the file contents to calculate lines per page and render the document's contents.</span></span> <span data-ttu-id="75b6b-109">在繪製每一頁之後，請檢查該頁面是否為最後一頁，並且據此設定 <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> 的 <xref:System.Drawing.Printing.PrintPageEventArgs> 屬性。</span><span class="sxs-lookup"><span data-stu-id="75b6b-109">After each page is drawn, check to see if it is the last page, and set the <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> accordingly.</span></span> <span data-ttu-id="75b6b-110">在 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 成為 <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> 之前，會持續引發 `false`事件。</span><span class="sxs-lookup"><span data-stu-id="75b6b-110">The <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is raised until <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> is `false`.</span></span> <span data-ttu-id="75b6b-111">當文件已完成轉譯時，重設要轉譯的字串。</span><span class="sxs-lookup"><span data-stu-id="75b6b-111">When the document has finished rendering, reset the string to be rendered.</span></span> <span data-ttu-id="75b6b-112">此外，也請確定 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件與其事件處理方法相關聯。</span><span class="sxs-lookup"><span data-stu-id="75b6b-112">Also, make sure the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is associated with its event-handling method.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="75b6b-113">如果您已經在應用程式中實作列印，可能已經完成步驟 2 和 3。</span><span class="sxs-lookup"><span data-stu-id="75b6b-113">You may have already completed steps 2 and 3 if you have implemented printing in your application.</span></span>  
  
     <span data-ttu-id="75b6b-114">在下列程式碼範例中，會使用事件處理常式，以表單上使用的相同字型來列印 "testPage.txt" 檔案。</span><span class="sxs-lookup"><span data-stu-id="75b6b-114">In the following code example, the event handler is used to print the "testPage.txt" file in the same font used on the form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#3)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#3)]  
  
4.  <span data-ttu-id="75b6b-115">將 <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> 控制項的 <xref:System.Windows.Forms.PrintPreviewDialog> 屬性設為表單上的 <xref:System.Drawing.Printing.PrintDocument> 元件。</span><span class="sxs-lookup"><span data-stu-id="75b6b-115">Set the <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> property of the <xref:System.Windows.Forms.PrintPreviewDialog> control to the <xref:System.Drawing.Printing.PrintDocument> component on the form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#5)]  
  
5.  <span data-ttu-id="75b6b-116">在 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 控制項上呼叫 <xref:System.Windows.Forms.PrintPreviewDialog> 方法。</span><span class="sxs-lookup"><span data-stu-id="75b6b-116">Call the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method on the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span> <span data-ttu-id="75b6b-117">您通常會從按鈕的 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 事件處理方法來呼叫 <xref:System.Windows.Forms.Control.Click> 。</span><span class="sxs-lookup"><span data-stu-id="75b6b-117">You would typically call <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> from the <xref:System.Windows.Forms.Control.Click> event-handling method of a button.</span></span> <span data-ttu-id="75b6b-118">呼叫 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 會引發 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件，並將輸出轉譯至 <xref:System.Windows.Forms.PrintPreviewDialog> 控制項。</span><span class="sxs-lookup"><span data-stu-id="75b6b-118">Calling <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> raises the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event and renders the output to the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span> <span data-ttu-id="75b6b-119">當使用者按一下對話方塊中的列印圖示，就會再引發一次 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件，將輸出傳送至印表機，而不是預覽對話方塊。</span><span class="sxs-lookup"><span data-stu-id="75b6b-119">When the user clicks the print icon on the dialog, the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is raised again, sending the output to the printer instead of the preview dialog.</span></span> <span data-ttu-id="75b6b-120">這就是為什麼在步驟 3 中轉譯程序的最後會重設字串的原因。</span><span class="sxs-lookup"><span data-stu-id="75b6b-120">This is why the string is reset at the end of the rendering process in step 3.</span></span>  
  
     <span data-ttu-id="75b6b-121">下列程式碼範例顯示針對表單上的按鈕所使用的 <xref:System.Windows.Forms.Control.Click> 事件處理方法。</span><span class="sxs-lookup"><span data-stu-id="75b6b-121">The following code example shows the <xref:System.Windows.Forms.Control.Click> event-handling method for a button on the form.</span></span> <span data-ttu-id="75b6b-122">這個事件處理方法會呼叫方法來讀取文件，並顯示預覽列印對話方塊。</span><span class="sxs-lookup"><span data-stu-id="75b6b-122">This event-handling method calls the methods to read the document and show the print preview dialog.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#4)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="75b6b-123">範例</span><span class="sxs-lookup"><span data-stu-id="75b6b-123">Example</span></span>  
 [!code-csharp[System.Drawing.Printing.PrintPreviewExample#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintPreviewExample#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="75b6b-124">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="75b6b-124">Compiling the Code</span></span>  
 <span data-ttu-id="75b6b-125">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="75b6b-125">This example requires:</span></span>  
  
-   <span data-ttu-id="75b6b-126">System、System.Windows.Forms、System.Drawing 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="75b6b-126">References to the System, System.Windows.Forms, System.Drawing assemblies.</span></span>  
  
-   <span data-ttu-id="75b6b-127">如需從 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 的命令列建置這個範例的資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[使用 csc.exe 建置命令列](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="75b6b-127">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="75b6b-128">您也可以將程式碼貼在新的專案中，以在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。</span><span class="sxs-lookup"><span data-stu-id="75b6b-128">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="75b6b-129">另請參閱[如何：使用 Visual Studio 編譯及執行完整的 Windows Forms 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="75b6b-129">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75b6b-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75b6b-130">See Also</span></span>  
 [<span data-ttu-id="75b6b-131">如何：在 Windows Forms 中列印多頁文字檔</span><span class="sxs-lookup"><span data-stu-id="75b6b-131">How to: Print a Multi-Page Text File in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 [<span data-ttu-id="75b6b-132">Windows Forms 列印支援</span><span class="sxs-lookup"><span data-stu-id="75b6b-132">Windows Forms Print Support</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)  
 [<span data-ttu-id="75b6b-133">Windows Forms 中更安全的列印</span><span class="sxs-lookup"><span data-stu-id="75b6b-133">More Secure Printing in Windows Forms</span></span>](../../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)

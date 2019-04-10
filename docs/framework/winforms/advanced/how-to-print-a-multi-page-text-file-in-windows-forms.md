---
title: HOW TO：在 Windows Forms 中列印多頁文字檔
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing [Windows Forms], printing multiple pages
- text [Windows Forms], printing Windows Forms
- Windows Forms, printing text
- printing [Windows Forms], text
ms.assetid: 362427f8-03d4-4826-b49f-60ab066ad322
ms.openlocfilehash: b17ddcb22f3e1b7dc181e977a0227db5490b66fa
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59330196"
---
# <a name="how-to-print-a-multi-page-text-file-in-windows-forms"></a><span data-ttu-id="6b77b-102">HOW TO：在 Windows Forms 中列印多頁文字檔</span><span class="sxs-lookup"><span data-stu-id="6b77b-102">How to: Print a Multi-Page Text File in Windows Forms</span></span>
<span data-ttu-id="6b77b-103">Windows 應用程式列印文字的情況極為常見。</span><span class="sxs-lookup"><span data-stu-id="6b77b-103">It is very common for Windows-based applications to print text.</span></span> <span data-ttu-id="6b77b-104"><xref:System.Drawing.Graphics> 類別提供將物件 (圖形或文字) 繪製到螢幕或印表機等裝置的方法。</span><span class="sxs-lookup"><span data-stu-id="6b77b-104">The <xref:System.Drawing.Graphics> class provides methods for drawing objects (graphics or text) to a device, such as a screen or printer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6b77b-105"><xref:System.Windows.Forms.TextRenderer> 的 <xref:System.Windows.Forms.TextRenderer.DrawText%2A> 方法不支援列印。</span><span class="sxs-lookup"><span data-stu-id="6b77b-105">The <xref:System.Windows.Forms.TextRenderer.DrawText%2A> methods of <xref:System.Windows.Forms.TextRenderer> are not supported for printing.</span></span> <span data-ttu-id="6b77b-106">您應該一律使用 <xref:System.Drawing.Graphics> 的 <xref:System.Drawing.Graphics.DrawString%2A> 方法，來繪製要用於列印的文字，如下列程式碼範例所示：</span><span class="sxs-lookup"><span data-stu-id="6b77b-106">You should always use the <xref:System.Drawing.Graphics.DrawString%2A> methods of <xref:System.Drawing.Graphics>, as shown in the following code example, to draw text for printing purposes.</span></span>  
  
### <a name="to-print-text"></a><span data-ttu-id="6b77b-107">列印文字</span><span class="sxs-lookup"><span data-stu-id="6b77b-107">To print text</span></span>  
  
1. <span data-ttu-id="6b77b-108">將一個 <xref:System.Drawing.Printing.PrintDocument> 元件和一個字串加入您的表單。</span><span class="sxs-lookup"><span data-stu-id="6b77b-108">Add a <xref:System.Drawing.Printing.PrintDocument> component and a string to your form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#8)]
     [!code-vb[System.Drawing.Printing.PrintExamples#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#8)]  
  
2. <span data-ttu-id="6b77b-109">如果是在列印文件，請將 <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> 屬性設定為您想要列印的文件，並且開啟文件內容，讀取到您在之前所加入的字串。</span><span class="sxs-lookup"><span data-stu-id="6b77b-109">If printing a document, set the <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> property to the document you wish to print, and open and read the documents contents to the string you added previously.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintExamples#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#1)]  
  
3. <span data-ttu-id="6b77b-110">在 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件處理常式中，使用 <xref:System.Drawing.Printing.PrintPageEventArgs> 類別的 <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> 屬性和文件內容來計算行的長度和每頁的行數。</span><span class="sxs-lookup"><span data-stu-id="6b77b-110">In the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler, use the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class and the document contents to calculate line length and lines per page.</span></span> <span data-ttu-id="6b77b-111">在繪製每一頁之後，請檢查該頁面是否為最後一頁，並且據此設定 <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> 的 <xref:System.Drawing.Printing.PrintPageEventArgs> 屬性。</span><span class="sxs-lookup"><span data-stu-id="6b77b-111">After each page is drawn, check to see if it is the last page, and set the <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> accordingly.</span></span> <span data-ttu-id="6b77b-112">在 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 成為 <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> 之前，會持續引發 `false`事件。</span><span class="sxs-lookup"><span data-stu-id="6b77b-112">The <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is raised until <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> is `false`.</span></span> <span data-ttu-id="6b77b-113">此外，也請確定 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件與其事件處理方法相關聯。</span><span class="sxs-lookup"><span data-stu-id="6b77b-113">Also, make sure the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is associated with its event-handling method.</span></span>  
  
     <span data-ttu-id="6b77b-114">在下列程式碼範例中，會使用事件處理常式以表單上所使用的相同字型來列印 "testPage.txt" 檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="6b77b-114">In the following code example, the event handler is used to print the contents of the "testPage.txt" file in the same font as is used on the form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintExamples#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#2)]  
  
4. <span data-ttu-id="6b77b-115">呼叫 <xref:System.Drawing.Printing.PrintDocument.Print%2A> 方法以引發 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件。</span><span class="sxs-lookup"><span data-stu-id="6b77b-115">Call the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to raise the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintExamples#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="6b77b-116">範例</span><span class="sxs-lookup"><span data-stu-id="6b77b-116">Example</span></span>  
 [!code-csharp[System.Drawing.Printing.PrintExamples#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintExamples#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6b77b-117">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="6b77b-117">Compiling the Code</span></span>  
 <span data-ttu-id="6b77b-118">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="6b77b-118">This example requires:</span></span>  
  
-   <span data-ttu-id="6b77b-119">位於磁碟機 C:\\ 根目錄之名為 testPage.txt 的文字檔，其中包含要列印的文字。</span><span class="sxs-lookup"><span data-stu-id="6b77b-119">A text file named testPage.txt containing the text to print, located in the root of drive C:\\.</span></span> <span data-ttu-id="6b77b-120">編輯這個程式碼可列印不同的檔案。</span><span class="sxs-lookup"><span data-stu-id="6b77b-120">Edit the code to print a different file.</span></span>  
  
-   <span data-ttu-id="6b77b-121">System、System.Windows.Forms、System.Drawing 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="6b77b-121">References to the System, System.Windows.Forms, System.Drawing assemblies.</span></span>  
  
-   <span data-ttu-id="6b77b-122">Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="6b77b-122">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="6b77b-123">您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="6b77b-123">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b77b-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b77b-124">See also</span></span>

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Brush>
- [<span data-ttu-id="6b77b-125">Windows Form 列印支援</span><span class="sxs-lookup"><span data-stu-id="6b77b-125">Windows Forms Print Support</span></span>](windows-forms-print-support.md)

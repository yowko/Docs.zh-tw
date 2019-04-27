---
title: PrintDocument 元件概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- PrintDocument
helpviewer_keywords:
- PrintDocument component [Windows Forms], about PrintDocument component
- printing [Windows Forms], PrintDocument component
ms.assetid: b59b4b60-dce5-42ca-8421-3a54a2f7bab0
ms.openlocfilehash: a3f08aa4bd5b63769cef35dbea2209d5d83261be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012616"
---
# <a name="printdocument-component-overview-windows-forms"></a><span data-ttu-id="5d485-102">PrintDocument 元件概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="5d485-102">PrintDocument Component Overview (Windows Forms)</span></span>
<span data-ttu-id="5d485-103">Windows Forms [PrintDocument](printdocument-component-windows-forms.md) 元件可用來設定描述列印項目的屬性，以及在 Windows 應用程式中列印文件的能力。</span><span class="sxs-lookup"><span data-stu-id="5d485-103">The Windows Forms [PrintDocument](printdocument-component-windows-forms.md) component is used to set the properties that describe what to print and the ability to print the document within Windows-based applications.</span></span> <span data-ttu-id="5d485-104">它可以與 [PrintDialog](printdialog-component-windows-forms.md) 元件一起使用，以控制文件列印的各個方面。</span><span class="sxs-lookup"><span data-stu-id="5d485-104">It can be used in conjunction with the [PrintDialog](printdialog-component-windows-forms.md) component to be in control of all aspects of document printing.</span></span>  
  
## <a name="working-with-the-printdocument-component"></a><span data-ttu-id="5d485-105">使用 PrintDocument 元件</span><span class="sxs-lookup"><span data-stu-id="5d485-105">Working with the PrintDocument Component</span></span>  
 <span data-ttu-id="5d485-106">兩個主要案例牽涉到<xref:System.Drawing.Printing.PrintDocument>元件：</span><span class="sxs-lookup"><span data-stu-id="5d485-106">Two of the main scenarios that involve the <xref:System.Drawing.Printing.PrintDocument> component are:</span></span>  
  
-   <span data-ttu-id="5d485-107">簡單列印工作，例如列印個別的文字檔。</span><span class="sxs-lookup"><span data-stu-id="5d485-107">Simple print jobs, such as printing an individual text file.</span></span> <span data-ttu-id="5d485-108">在此情況下，您可以加入<xref:System.Drawing.Printing.PrintDocument>元件至 Windows 表單，然後新增會列印的檔案中的程式設計邏輯<xref:System.Drawing.Printing.PrintDocument.PrintPage>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="5d485-108">In such a case you would add the <xref:System.Drawing.Printing.PrintDocument> component to a Windows Form, then add programming logic that prints a file in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler.</span></span> <span data-ttu-id="5d485-109">程式設計邏輯應做為目標<xref:System.Drawing.Printing.PrintDocument.Print%2A>列印文件的方法。</span><span class="sxs-lookup"><span data-stu-id="5d485-109">The programming logic should culminate with the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to print the document.</span></span> <span data-ttu-id="5d485-110">這個方法會傳送<xref:System.Drawing.Graphics>中所含的物件<xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A>屬性<xref:System.Drawing.Printing.PrintPageEventArgs>到印表機的類別。</span><span class="sxs-lookup"><span data-stu-id="5d485-110">This method sends a <xref:System.Drawing.Graphics> object, contained in the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class, to the printer.</span></span> <span data-ttu-id="5d485-111">如需範例，示範如何使用文字文件列印<xref:System.Drawing.Printing.PrintDocument>元件，請參閱[How to:列印 Windows Form 中的多頁文字檔](../advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="5d485-111">For an example that shows how to print a text document using the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Print a Multi-Page Text File in Windows Forms](../advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md).</span></span>  
  
-   <span data-ttu-id="5d485-112">更複雜的列印工作，例如，您想要重複使用您所撰寫之列印邏輯的情況。</span><span class="sxs-lookup"><span data-stu-id="5d485-112">More complex print jobs, such as a situation where you will want to reuse printing logic you have written.</span></span> <span data-ttu-id="5d485-113">這種情況中，您會衍生新的元件，從<xref:System.Drawing.Printing.PrintDocument>元件，並覆寫 (請參閱 <<c2> [ 覆寫](~/docs/visual-basic/language-reference/modifiers/overrides.md)適用於 Visual Basic 或[覆寫](~/docs/csharp/language-reference/keywords/override.md)的C#)<xref:System.Drawing.Printing.PrintDocument.PrintPage>事件。</c2></span><span class="sxs-lookup"><span data-stu-id="5d485-113">In such a case you would derive a new component from the <xref:System.Drawing.Printing.PrintDocument> component and override (see [Overrides](~/docs/visual-basic/language-reference/modifiers/overrides.md) for Visual Basic or [override](~/docs/csharp/language-reference/keywords/override.md) for C#) the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>  
  
 <span data-ttu-id="5d485-114">當加入至表單，<xref:System.Drawing.Printing.PrintDocument>元件會出現在底部的 Windows Form 設計工具的紙匣。</span><span class="sxs-lookup"><span data-stu-id="5d485-114">When it is added to a form, the <xref:System.Drawing.Printing.PrintDocument> component appears in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d485-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d485-115">See also</span></span>

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="5d485-116">Windows Forms 列印支援</span><span class="sxs-lookup"><span data-stu-id="5d485-116">Windows Forms Print Support</span></span>](../advanced/windows-forms-print-support.md)
- [<span data-ttu-id="5d485-117">PrintDocument 元件</span><span class="sxs-lookup"><span data-stu-id="5d485-117">PrintDocument Component</span></span>](printdocument-component-windows-forms.md)

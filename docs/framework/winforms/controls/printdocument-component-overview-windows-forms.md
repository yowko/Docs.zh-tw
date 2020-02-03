---
title: PrintDocument 元件概觀
ms.date: 03/30/2017
f1_keywords:
- PrintDocument
helpviewer_keywords:
- PrintDocument component [Windows Forms], about PrintDocument component
- printing [Windows Forms], PrintDocument component
ms.assetid: b59b4b60-dce5-42ca-8421-3a54a2f7bab0
ms.openlocfilehash: a82cc0cdcb8cfae796c9c6bf60ab73873f85a291
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728536"
---
# <a name="printdocument-component-overview-windows-forms"></a><span data-ttu-id="311ae-102">PrintDocument 元件概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="311ae-102">PrintDocument Component Overview (Windows Forms)</span></span>

<span data-ttu-id="311ae-103">Windows Forms [PrintDocument](printdocument-component-windows-forms.md) 元件可用來設定描述列印項目的屬性，以及在 Windows 應用程式中列印文件的能力。</span><span class="sxs-lookup"><span data-stu-id="311ae-103">The Windows Forms [PrintDocument](printdocument-component-windows-forms.md) component is used to set the properties that describe what to print and the ability to print the document within Windows-based applications.</span></span> <span data-ttu-id="311ae-104">它可以與 [PrintDialog](printdialog-component-windows-forms.md) 元件一起使用，以控制文件列印的各個方面。</span><span class="sxs-lookup"><span data-stu-id="311ae-104">It can be used in conjunction with the [PrintDialog](printdialog-component-windows-forms.md) component to be in control of all aspects of document printing.</span></span>

## <a name="working-with-the-printdocument-component"></a><span data-ttu-id="311ae-105">使用 PrintDocument 元件</span><span class="sxs-lookup"><span data-stu-id="311ae-105">Working with the PrintDocument Component</span></span>

<span data-ttu-id="311ae-106">牽涉到 <xref:System.Drawing.Printing.PrintDocument> 元件的兩個主要案例如下：</span><span class="sxs-lookup"><span data-stu-id="311ae-106">Two of the main scenarios that involve the <xref:System.Drawing.Printing.PrintDocument> component are:</span></span>

- <span data-ttu-id="311ae-107">簡單列印工作，例如列印個別的文字檔。</span><span class="sxs-lookup"><span data-stu-id="311ae-107">Simple print jobs, such as printing an individual text file.</span></span> <span data-ttu-id="311ae-108">在這種情況下，您會將 <xref:System.Drawing.Printing.PrintDocument> 元件新增至 Windows Form，然後加入在 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件處理常式中列印檔案的程式設計邏輯。</span><span class="sxs-lookup"><span data-stu-id="311ae-108">In such a case you would add the <xref:System.Drawing.Printing.PrintDocument> component to a Windows Form, then add programming logic that prints a file in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler.</span></span> <span data-ttu-id="311ae-109">程式設計邏輯應該使用 <xref:System.Drawing.Printing.PrintDocument.Print%2A> 方法來終於獲得，以列印檔案。</span><span class="sxs-lookup"><span data-stu-id="311ae-109">The programming logic should culminate with the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to print the document.</span></span> <span data-ttu-id="311ae-110">這個方法會將 <xref:System.Drawing.Printing.PrintPageEventArgs> 類別的 <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> 屬性中包含的 <xref:System.Drawing.Graphics> 物件傳送至印表機。</span><span class="sxs-lookup"><span data-stu-id="311ae-110">This method sends a <xref:System.Drawing.Graphics> object, contained in the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class, to the printer.</span></span> <span data-ttu-id="311ae-111">如需顯示如何使用 <xref:System.Drawing.Printing.PrintDocument> 元件來列印文字檔的範例，請參閱[如何：在 Windows Forms 中列印多頁文字檔](../advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="311ae-111">For an example that shows how to print a text document using the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Print a Multi-Page Text File in Windows Forms](../advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md).</span></span>

- <span data-ttu-id="311ae-112">更複雜的列印工作，例如，您想要重複使用您所撰寫之列印邏輯的情況。</span><span class="sxs-lookup"><span data-stu-id="311ae-112">More complex print jobs, such as a situation where you will want to reuse printing logic you have written.</span></span> <span data-ttu-id="311ae-113">在這種情況下，您會從 <xref:System.Drawing.Printing.PrintDocument> 元件衍生新的元件，並覆寫（請參閱[Visual Basic](../../../csharp/language-reference/keywords/override.md)的C#[覆](../../../visual-basic/language-reference/modifiers/overrides.md)寫） <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件。</span><span class="sxs-lookup"><span data-stu-id="311ae-113">In such a case you would derive a new component from the <xref:System.Drawing.Printing.PrintDocument> component and override (see [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md) for Visual Basic or [override](../../../csharp/language-reference/keywords/override.md) for C#) the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>

<span data-ttu-id="311ae-114">當它新增至表單時，<xref:System.Drawing.Printing.PrintDocument> 元件會出現在 Visual Studio Windows Form 設計工具底部的紙匣中。</span><span class="sxs-lookup"><span data-stu-id="311ae-114">When it is added to a form, the <xref:System.Drawing.Printing.PrintDocument> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="311ae-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="311ae-115">See also</span></span>

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="311ae-116">Windows Forms 列印支援</span><span class="sxs-lookup"><span data-stu-id="311ae-116">Windows Forms Print Support</span></span>](../advanced/windows-forms-print-support.md)
- [<span data-ttu-id="311ae-117">PrintDocument 元件</span><span class="sxs-lookup"><span data-stu-id="311ae-117">PrintDocument Component</span></span>](printdocument-component-windows-forms.md)

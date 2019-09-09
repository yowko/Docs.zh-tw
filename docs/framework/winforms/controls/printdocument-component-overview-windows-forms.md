---
title: PrintDocument 元件概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- PrintDocument
helpviewer_keywords:
- PrintDocument component [Windows Forms], about PrintDocument component
- printing [Windows Forms], PrintDocument component
ms.assetid: b59b4b60-dce5-42ca-8421-3a54a2f7bab0
ms.openlocfilehash: 16a7f3a34ccb280f7bf91c52e29b20edc22130b9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928979"
---
# <a name="printdocument-component-overview-windows-forms"></a><span data-ttu-id="4f71e-102">PrintDocument 元件概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="4f71e-102">PrintDocument Component Overview (Windows Forms)</span></span>

<span data-ttu-id="4f71e-103">Windows Forms [PrintDocument](printdocument-component-windows-forms.md) 元件可用來設定描述列印項目的屬性，以及在 Windows 應用程式中列印文件的能力。</span><span class="sxs-lookup"><span data-stu-id="4f71e-103">The Windows Forms [PrintDocument](printdocument-component-windows-forms.md) component is used to set the properties that describe what to print and the ability to print the document within Windows-based applications.</span></span> <span data-ttu-id="4f71e-104">它可以與 [PrintDialog](printdialog-component-windows-forms.md) 元件一起使用，以控制文件列印的各個方面。</span><span class="sxs-lookup"><span data-stu-id="4f71e-104">It can be used in conjunction with the [PrintDialog](printdialog-component-windows-forms.md) component to be in control of all aspects of document printing.</span></span>

## <a name="working-with-the-printdocument-component"></a><span data-ttu-id="4f71e-105">使用 PrintDocument 元件</span><span class="sxs-lookup"><span data-stu-id="4f71e-105">Working with the PrintDocument Component</span></span>

<span data-ttu-id="4f71e-106">涉及此<xref:System.Drawing.Printing.PrintDocument>元件的兩個主要案例如下：</span><span class="sxs-lookup"><span data-stu-id="4f71e-106">Two of the main scenarios that involve the <xref:System.Drawing.Printing.PrintDocument> component are:</span></span>

- <span data-ttu-id="4f71e-107">簡單列印工作，例如列印個別的文字檔。</span><span class="sxs-lookup"><span data-stu-id="4f71e-107">Simple print jobs, such as printing an individual text file.</span></span> <span data-ttu-id="4f71e-108">在這種情況下，您會<xref:System.Drawing.Printing.PrintDocument>將元件加入至 Windows Form，然後加入在<xref:System.Drawing.Printing.PrintDocument.PrintPage>事件處理常式中列印檔案的程式設計邏輯。</span><span class="sxs-lookup"><span data-stu-id="4f71e-108">In such a case you would add the <xref:System.Drawing.Printing.PrintDocument> component to a Windows Form, then add programming logic that prints a file in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler.</span></span> <span data-ttu-id="4f71e-109">程式設計邏輯應該使用<xref:System.Drawing.Printing.PrintDocument.Print%2A>方法來終於獲得以列印檔案。</span><span class="sxs-lookup"><span data-stu-id="4f71e-109">The programming logic should culminate with the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to print the document.</span></span> <span data-ttu-id="4f71e-110">這個方法會將<xref:System.Drawing.Graphics>包含<xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A>在<xref:System.Drawing.Printing.PrintPageEventArgs>類別之屬性中的物件傳送至印表機。</span><span class="sxs-lookup"><span data-stu-id="4f71e-110">This method sends a <xref:System.Drawing.Graphics> object, contained in the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class, to the printer.</span></span> <span data-ttu-id="4f71e-111">如需說明如何使用<xref:System.Drawing.Printing.PrintDocument>元件來列印文字檔的範例，請參閱[如何：在 Windows Forms](../advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)中列印多頁文字檔。</span><span class="sxs-lookup"><span data-stu-id="4f71e-111">For an example that shows how to print a text document using the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Print a Multi-Page Text File in Windows Forms](../advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md).</span></span>

- <span data-ttu-id="4f71e-112">更複雜的列印工作，例如，您想要重複使用您所撰寫之列印邏輯的情況。</span><span class="sxs-lookup"><span data-stu-id="4f71e-112">More complex print jobs, such as a situation where you will want to reuse printing logic you have written.</span></span> <span data-ttu-id="4f71e-113"><xref:System.Drawing.Printing.PrintDocument>在這種情況下，您會從元件衍生新的元件，並覆寫（請參閱 Visual Basic 的C#[覆](../../../visual-basic/language-reference/modifiers/overrides.md)寫<xref:System.Drawing.Printing.PrintDocument.PrintPage> [）](../../../csharp/language-reference/keywords/override.md)事件。</span><span class="sxs-lookup"><span data-stu-id="4f71e-113">In such a case you would derive a new component from the <xref:System.Drawing.Printing.PrintDocument> component and override (see [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md) for Visual Basic or [override](../../../csharp/language-reference/keywords/override.md) for C#) the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>

<span data-ttu-id="4f71e-114">當它新增至表單時，該<xref:System.Drawing.Printing.PrintDocument>元件就會出現在 Visual Studio 的 Windows Form 設計工具底部的紙匣中。</span><span class="sxs-lookup"><span data-stu-id="4f71e-114">When it is added to a form, the <xref:System.Drawing.Printing.PrintDocument> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="4f71e-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f71e-115">See also</span></span>

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="4f71e-116">Windows Forms 列印支援</span><span class="sxs-lookup"><span data-stu-id="4f71e-116">Windows Forms Print Support</span></span>](../advanced/windows-forms-print-support.md)
- [<span data-ttu-id="4f71e-117">PrintDocument 元件</span><span class="sxs-lookup"><span data-stu-id="4f71e-117">PrintDocument Component</span></span>](printdocument-component-windows-forms.md)

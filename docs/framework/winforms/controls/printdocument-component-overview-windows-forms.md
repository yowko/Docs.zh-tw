---
title: "PrintDocument 元件概觀 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PrintDocument
helpviewer_keywords:
- PrintDocument component [Windows Forms], about PrintDocument component
- printing [Windows Forms], PrintDocument component
ms.assetid: b59b4b60-dce5-42ca-8421-3a54a2f7bab0
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 414a7972550558b40403b7f4cbfd9a49194666be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="printdocument-component-overview-windows-forms"></a><span data-ttu-id="5dd32-102">PrintDocument 元件概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="5dd32-102">PrintDocument Component Overview (Windows Forms)</span></span>
<span data-ttu-id="5dd32-103">Windows Forms [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) 元件可用來設定描述列印項目的屬性，以及在 Windows 應用程式中列印文件的能力。</span><span class="sxs-lookup"><span data-stu-id="5dd32-103">The Windows Forms [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) component is used to set the properties that describe what to print and the ability to print the document within Windows-based applications.</span></span> <span data-ttu-id="5dd32-104">它可以與 [PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) 元件一起使用，以控制文件列印的各個方面。</span><span class="sxs-lookup"><span data-stu-id="5dd32-104">It can be used in conjunction with the [PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) component to be in control of all aspects of document printing.</span></span>  
  
## <a name="working-with-the-printdocument-component"></a><span data-ttu-id="5dd32-105">使用 PrintDocument 元件</span><span class="sxs-lookup"><span data-stu-id="5dd32-105">Working with the PrintDocument Component</span></span>  
 <span data-ttu-id="5dd32-106">兩個有關的主要案例<xref:System.Drawing.Printing.PrintDocument>元件是：</span><span class="sxs-lookup"><span data-stu-id="5dd32-106">Two of the main scenarios that involve the <xref:System.Drawing.Printing.PrintDocument> component are:</span></span>  
  
-   <span data-ttu-id="5dd32-107">簡單列印工作，例如列印個別的文字檔。</span><span class="sxs-lookup"><span data-stu-id="5dd32-107">Simple print jobs, such as printing an individual text file.</span></span> <span data-ttu-id="5dd32-108">在此情況下您會將<xref:System.Drawing.Printing.PrintDocument>元件至 Windows 表單，然後新增列印的檔案中的程式設計邏輯<xref:System.Drawing.Printing.PrintDocument.PrintPage>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="5dd32-108">In such a case you would add the <xref:System.Drawing.Printing.PrintDocument> component to a Windows Form, then add programming logic that prints a file in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler.</span></span> <span data-ttu-id="5dd32-109">與應該做為目標的程式設計邏輯<xref:System.Drawing.Printing.PrintDocument.Print%2A>列印文件的方法。</span><span class="sxs-lookup"><span data-stu-id="5dd32-109">The programming logic should culminate with the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to print the document.</span></span> <span data-ttu-id="5dd32-110">這個方法會傳送<xref:System.Drawing.Graphics>中包含的物件<xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A>屬性<xref:System.Drawing.Printing.PrintPageEventArgs>類別，以印表機。</span><span class="sxs-lookup"><span data-stu-id="5dd32-110">This method sends a <xref:System.Drawing.Graphics> object, contained in the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class, to the printer.</span></span> <span data-ttu-id="5dd32-111">如需範例，示範如何使用文字文件列印<xref:System.Drawing.Printing.PrintDocument>元件，請參閱[如何： 列印 Windows Form 中的多頁文字檔](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="5dd32-111">For an example that shows how to print a text document using the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Print a Multi-Page Text File in Windows Forms](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md).</span></span>  
  
-   <span data-ttu-id="5dd32-112">更複雜的列印工作，例如，您想要重複使用您所撰寫之列印邏輯的情況。</span><span class="sxs-lookup"><span data-stu-id="5dd32-112">More complex print jobs, such as a situation where you will want to reuse printing logic you have written.</span></span> <span data-ttu-id="5dd32-113">在這種情況下，您會衍生新的元件，從<xref:System.Drawing.Printing.PrintDocument>元件，然後覆寫 (請參閱[會覆寫](~/docs/visual-basic/language-reference/modifiers/overrides.md)適用於 Visual Basic 或[覆寫](~/docs/csharp/language-reference/keywords/override.md)C#)<xref:System.Drawing.Printing.PrintDocument.PrintPage>事件。</span><span class="sxs-lookup"><span data-stu-id="5dd32-113">In such a case you would derive a new component from the <xref:System.Drawing.Printing.PrintDocument> component and override (see [Overrides](~/docs/visual-basic/language-reference/modifiers/overrides.md) for Visual Basic or [override](~/docs/csharp/language-reference/keywords/override.md) for C#) the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>  
  
 <span data-ttu-id="5dd32-114">當加入至表單，<xref:System.Drawing.Printing.PrintDocument>元件會出現在 Windows Form 設計工具底部的紙匣。</span><span class="sxs-lookup"><span data-stu-id="5dd32-114">When it is added to a form, the <xref:System.Drawing.Printing.PrintDocument> component appears in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dd32-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="5dd32-115">See Also</span></span>  
 <xref:System.Drawing.Graphics>  
 <xref:System.Drawing.Printing.PrintDocument>  
 [<span data-ttu-id="5dd32-116">Windows Forms 列印支援</span><span class="sxs-lookup"><span data-stu-id="5dd32-116">Windows Forms Print Support</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)  
 [<span data-ttu-id="5dd32-117">PrintDocument 元件</span><span class="sxs-lookup"><span data-stu-id="5dd32-117">PrintDocument Component</span></span>](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)

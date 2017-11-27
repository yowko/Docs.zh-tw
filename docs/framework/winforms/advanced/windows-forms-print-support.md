---
title: "Windows Form 列印支援"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- forms [Windows Forms], printing (using designer)
- printing [Windows Forms], Windows Forms, support
- printing [Windows Forms], print support
ms.assetid: a4a2960c-eb70-48e2-b641-cfb222704e46
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 029d5ed424061807cf04446cbb10424ae20afba2
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="windows-forms-print-support"></a><span data-ttu-id="706e5-102">Windows Form 列印支援</span><span class="sxs-lookup"><span data-stu-id="706e5-102">Windows Forms Print Support</span></span>
<span data-ttu-id="706e5-103">在 Windows Form 中的列印工作主要是使用[PrintDocument 元件](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)元件，讓使用者列印，而[PrintPreviewDialog 控制項](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)控制項， [PrintDialog元件](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)和[PageSetupDialog 元件](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md)習慣使用 Windows 作業系統的使用者提供熟悉的圖形化介面的元件。</span><span class="sxs-lookup"><span data-stu-id="706e5-103">Printing in Windows Forms consists primarily of using the [PrintDocument Component](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) component to enable the user to print, and the [PrintPreviewDialog Control](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md) control, [PrintDialog Component](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) and [PageSetupDialog Component](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) components to provide a familiar graphical interface to users accustomed to the Windows operating system.</span></span>  
  
 <span data-ttu-id="706e5-104">一般而言，您建立的新執行個體<xref:System.Drawing.Printing.PrintDocument>元件，請設定屬性，描述要使用列印<xref:System.Drawing.Printing.PrinterSettings>和<xref:System.Drawing.Printing.PageSettings>類別，以及呼叫<xref:System.Drawing.Printing.PrintDocument.Print%2A>實際列印文件的方法。</span><span class="sxs-lookup"><span data-stu-id="706e5-104">Typically, you create a new instance of the <xref:System.Drawing.Printing.PrintDocument> component, set the properties that describe what to print using the <xref:System.Drawing.Printing.PrinterSettings> and <xref:System.Drawing.Printing.PageSettings> classes, and call the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to actually print the document.</span></span>  
  
 <span data-ttu-id="706e5-105">從 windows 應用程式，列印過程<xref:System.Drawing.Printing.PrintDocument>元件將會顯示一個中止的列印對話方塊，警告使用者正在發生之列印的事實，並允許列印工作取消。</span><span class="sxs-lookup"><span data-stu-id="706e5-105">During the course of printing from a Windows-based application, the <xref:System.Drawing.Printing.PrintDocument> component will show an abort print dialog box to alert users to the fact that printing is occurring and to allow the print job to be canceled.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="706e5-106">本章節內容</span><span class="sxs-lookup"><span data-stu-id="706e5-106">In This Section</span></span>  
 [<span data-ttu-id="706e5-107">操作說明：建立標準的 Windows Forms 列印工作</span><span class="sxs-lookup"><span data-stu-id="706e5-107">How to: Create Standard Windows Forms Print Jobs</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)  
 <span data-ttu-id="706e5-108">說明如何使用<xref:System.Drawing.Printing.PrintDocument>列印 Windows Form 中的元件。</span><span class="sxs-lookup"><span data-stu-id="706e5-108">Explains how to use the <xref:System.Drawing.Printing.PrintDocument> component to print from a Windows Form.</span></span>  
  
 [<span data-ttu-id="706e5-109">操作說明：在執行階段從 PrintDialog 擷取使用者輸入</span><span class="sxs-lookup"><span data-stu-id="706e5-109">How to: Capture User Input from a PrintDialog at Run Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 <span data-ttu-id="706e5-110">說明如何修改選取的列印選項，以程式設計方式使用<xref:System.Windows.Forms.PrintDialog>元件。</span><span class="sxs-lookup"><span data-stu-id="706e5-110">Explains how to modify selected print options programmatically using the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
 [<span data-ttu-id="706e5-111">操作說明：在 Windows Forms 中選擇附加至使用者電腦的印表機</span><span class="sxs-lookup"><span data-stu-id="706e5-111">How to: Choose the Printers Attached to a User's Computer in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-choose-the-printers-attached-to-user-computer-in-windows-forms.md)  
 <span data-ttu-id="706e5-112">描述變更列印到使用印表機<xref:System.Windows.Forms.PrintDialog>在執行階段元件。</span><span class="sxs-lookup"><span data-stu-id="706e5-112">Describes changing the printer to print to using the <xref:System.Windows.Forms.PrintDialog> component at run time.</span></span>  
  
 [<span data-ttu-id="706e5-113">如何：列印 Windows Forms 中的圖形</span><span class="sxs-lookup"><span data-stu-id="706e5-113">How to: Print Graphics in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)  
 <span data-ttu-id="706e5-114">描述圖形傳送至印表機。</span><span class="sxs-lookup"><span data-stu-id="706e5-114">Describes sending graphics to the printer.</span></span>  
  
 [<span data-ttu-id="706e5-115">如何：在 Windows Forms 中列印多頁文字檔</span><span class="sxs-lookup"><span data-stu-id="706e5-115">How to: Print a Multi-Page Text File in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 <span data-ttu-id="706e5-116">描述將文字傳送至印表機。</span><span class="sxs-lookup"><span data-stu-id="706e5-116">Describes sending text to the printer.</span></span>  
  
 [<span data-ttu-id="706e5-117">操作說明：完成 Windows Forms 列印工作</span><span class="sxs-lookup"><span data-stu-id="706e5-117">How to: Complete Windows Forms Print Jobs</span></span>](../../../../docs/framework/winforms/advanced/how-to-complete-windows-forms-print-jobs.md)  
 <span data-ttu-id="706e5-118">說明如何完成列印工作的使用者發出警示。</span><span class="sxs-lookup"><span data-stu-id="706e5-118">Explains how to alert users to the completion of a print job.</span></span>  
  
 [<span data-ttu-id="706e5-119">操作說明：列印 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="706e5-119">How to: Print a Windows Form</span></span>](../../../../docs/framework/winforms/advanced/how-to-print-a-windows-form.md)  
 <span data-ttu-id="706e5-120">示範如何列印一份目前的表單。</span><span class="sxs-lookup"><span data-stu-id="706e5-120">Shows how to print a copy of the current form.</span></span>  
  
 [<span data-ttu-id="706e5-121">操作說明：使用預覽列印在 Windows Forms 中進行列印</span><span class="sxs-lookup"><span data-stu-id="706e5-121">How to: Print in Windows Forms Using Print Preview</span></span>](../../../../docs/framework/winforms/advanced/how-to-print-in-windows-forms-using-print-preview.md)  
 <span data-ttu-id="706e5-122">示範如何使用<xref:System.Windows.Forms.PrintPreviewDialog>列印文件。</span><span class="sxs-lookup"><span data-stu-id="706e5-122">Shows how to use a <xref:System.Windows.Forms.PrintPreviewDialog> for printing a document.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="706e5-123">相關章節</span><span class="sxs-lookup"><span data-stu-id="706e5-123">Related Sections</span></span>  
 [<span data-ttu-id="706e5-124">PrintDocument 元件</span><span class="sxs-lookup"><span data-stu-id="706e5-124">PrintDocument Component</span></span>](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)  
 <span data-ttu-id="706e5-125">說明使用<xref:System.Drawing.Printing.PrintDocument>元件。</span><span class="sxs-lookup"><span data-stu-id="706e5-125">Explains usage of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
 [<span data-ttu-id="706e5-126">PrintDialog 元件</span><span class="sxs-lookup"><span data-stu-id="706e5-126">PrintDialog Component</span></span>](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)  
 <span data-ttu-id="706e5-127">說明使用<xref:System.Windows.Forms.PrintDialog>元件。</span><span class="sxs-lookup"><span data-stu-id="706e5-127">Explains usage of the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
 [<span data-ttu-id="706e5-128">PrintPreviewDialog 控制項</span><span class="sxs-lookup"><span data-stu-id="706e5-128">PrintPreviewDialog Control</span></span>](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 <span data-ttu-id="706e5-129">說明使用<xref:System.Windows.Forms.PrintPreviewDialog>控制項。</span><span class="sxs-lookup"><span data-stu-id="706e5-129">Explains usage of the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span>  
  
 [<span data-ttu-id="706e5-130">PageSetupDialog 元件</span><span class="sxs-lookup"><span data-stu-id="706e5-130">PageSetupDialog Component</span></span>](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md)  
 <span data-ttu-id="706e5-131">說明使用<xref:System.Windows.Forms.PageSetupDialog>元件。</span><span class="sxs-lookup"><span data-stu-id="706e5-131">Explains usage of the <xref:System.Windows.Forms.PageSetupDialog> component.</span></span>  
  
 <xref:System.Drawing.Printing>  
 <span data-ttu-id="706e5-132">描述中的類別<xref:System.Drawing.Printing>命名空間。</span><span class="sxs-lookup"><span data-stu-id="706e5-132">Describes the classes in the <xref:System.Drawing.Printing> namespace.</span></span>

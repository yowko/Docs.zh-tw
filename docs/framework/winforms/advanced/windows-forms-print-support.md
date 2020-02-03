---
title: 列印支援
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- forms [Windows Forms], printing (using designer)
- printing [Windows Forms], Windows Forms, support
- printing [Windows Forms], print support
ms.assetid: a4a2960c-eb70-48e2-b641-cfb222704e46
ms.openlocfilehash: d6e8f60db7afe2f1b04eaae6fe71aa93e5c22cae
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732500"
---
# <a name="windows-forms-print-support"></a><span data-ttu-id="ce592-102">Windows Form 列印支援</span><span class="sxs-lookup"><span data-stu-id="ce592-102">Windows Forms Print Support</span></span>
<span data-ttu-id="ce592-103">在 Windows Forms 中列印主要是使用[PrintDocument 元件](../controls/printdocument-component-windows-forms.md)元件，讓使用者能夠列印，而[PrintPreviewDialog 控制項](../controls/printpreviewdialog-control-windows-forms.md)控制項[PrintDialog 元件](../controls/printdialog-component-windows-forms.md)和[PageSetupDialog 元件](../controls/pagesetupdialog-component-windows-forms.md)元件則提供熟悉的圖形化介面給習慣 Windows 作業系統的使用者。</span><span class="sxs-lookup"><span data-stu-id="ce592-103">Printing in Windows Forms consists primarily of using the [PrintDocument Component](../controls/printdocument-component-windows-forms.md) component to enable the user to print, and the [PrintPreviewDialog Control](../controls/printpreviewdialog-control-windows-forms.md) control, [PrintDialog Component](../controls/printdialog-component-windows-forms.md) and [PageSetupDialog Component](../controls/pagesetupdialog-component-windows-forms.md) components to provide a familiar graphical interface to users accustomed to the Windows operating system.</span></span>  
  
 <span data-ttu-id="ce592-104">一般來說，您會建立 <xref:System.Drawing.Printing.PrintDocument> 元件的新實例、使用 <xref:System.Drawing.Printing.PrinterSettings> 和 <xref:System.Drawing.Printing.PageSettings> 類別來設定描述要列印之內容的屬性，以及呼叫 <xref:System.Drawing.Printing.PrintDocument.Print%2A> 方法來實際列印檔案。</span><span class="sxs-lookup"><span data-stu-id="ce592-104">Typically, you create a new instance of the <xref:System.Drawing.Printing.PrintDocument> component, set the properties that describe what to print using the <xref:System.Drawing.Printing.PrinterSettings> and <xref:System.Drawing.Printing.PageSettings> classes, and call the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to actually print the document.</span></span>  
  
 <span data-ttu-id="ce592-105">在從 Windows 應用程式進行列印的過程中，<xref:System.Drawing.Printing.PrintDocument> 元件將會顯示 [中止列印] 對話方塊，以提醒使用者發生列印的情況，並允許取消列印工作。</span><span class="sxs-lookup"><span data-stu-id="ce592-105">During the course of printing from a Windows-based application, the <xref:System.Drawing.Printing.PrintDocument> component will show an abort print dialog box to alert users to the fact that printing is occurring and to allow the print job to be canceled.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ce592-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="ce592-106">In This Section</span></span>  
 [<span data-ttu-id="ce592-107">操作說明：建立標準的 Windows Forms 列印工作</span><span class="sxs-lookup"><span data-stu-id="ce592-107">How to: Create Standard Windows Forms Print Jobs</span></span>](how-to-create-standard-windows-forms-print-jobs.md)  
 <span data-ttu-id="ce592-108">說明如何使用 <xref:System.Drawing.Printing.PrintDocument> 元件從 Windows Form 進行列印。</span><span class="sxs-lookup"><span data-stu-id="ce592-108">Explains how to use the <xref:System.Drawing.Printing.PrintDocument> component to print from a Windows Form.</span></span>  
  
 [<span data-ttu-id="ce592-109">操作說明：在執行階段從 PrintDialog 擷取使用者輸入</span><span class="sxs-lookup"><span data-stu-id="ce592-109">How to: Capture User Input from a PrintDialog at Run Time</span></span>](how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 <span data-ttu-id="ce592-110">說明如何使用 <xref:System.Windows.Forms.PrintDialog> 元件，以程式設計方式修改選取的列印選項。</span><span class="sxs-lookup"><span data-stu-id="ce592-110">Explains how to modify selected print options programmatically using the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
 [<span data-ttu-id="ce592-111">操作說明：在 Windows Forms 中選擇附加至使用者電腦的印表機</span><span class="sxs-lookup"><span data-stu-id="ce592-111">How to: Choose the Printers Attached to a User's Computer in Windows Forms</span></span>](how-to-choose-the-printers-attached-to-user-computer-in-windows-forms.md)  
 <span data-ttu-id="ce592-112">描述如何在執行時間使用 <xref:System.Windows.Forms.PrintDialog> 元件，將印表機變更為列印。</span><span class="sxs-lookup"><span data-stu-id="ce592-112">Describes changing the printer to print to using the <xref:System.Windows.Forms.PrintDialog> component at run time.</span></span>  
  
 [<span data-ttu-id="ce592-113">操作說明：列印 Windows Forms 中的圖形</span><span class="sxs-lookup"><span data-stu-id="ce592-113">How to: Print Graphics in Windows Forms</span></span>](how-to-print-graphics-in-windows-forms.md)  
 <span data-ttu-id="ce592-114">說明如何將圖形傳送至印表機。</span><span class="sxs-lookup"><span data-stu-id="ce592-114">Describes sending graphics to the printer.</span></span>  
  
 [<span data-ttu-id="ce592-115">操作說明：在 Windows Forms 中列印多頁文字檔</span><span class="sxs-lookup"><span data-stu-id="ce592-115">How to: Print a Multi-Page Text File in Windows Forms</span></span>](how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 <span data-ttu-id="ce592-116">說明如何將文字傳送至印表機。</span><span class="sxs-lookup"><span data-stu-id="ce592-116">Describes sending text to the printer.</span></span>  
  
 [<span data-ttu-id="ce592-117">操作說明：完成 Windows Forms 列印工作</span><span class="sxs-lookup"><span data-stu-id="ce592-117">How to: Complete Windows Forms Print Jobs</span></span>](how-to-complete-windows-forms-print-jobs.md)  
 <span data-ttu-id="ce592-118">說明如何警示使用者完成列印工作。</span><span class="sxs-lookup"><span data-stu-id="ce592-118">Explains how to alert users to the completion of a print job.</span></span>  
  
 [<span data-ttu-id="ce592-119">操作說明：列印 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ce592-119">How to: Print a Windows Form</span></span>](how-to-print-a-windows-form.md)  
 <span data-ttu-id="ce592-120">顯示如何列印目前表單的複本。</span><span class="sxs-lookup"><span data-stu-id="ce592-120">Shows how to print a copy of the current form.</span></span>  
  
 [<span data-ttu-id="ce592-121">操作說明：使用預覽列印在 Windows Forms 中進行列印</span><span class="sxs-lookup"><span data-stu-id="ce592-121">How to: Print in Windows Forms Using Print Preview</span></span>](how-to-print-in-windows-forms-using-print-preview.md)  
 <span data-ttu-id="ce592-122">示範如何使用 <xref:System.Windows.Forms.PrintPreviewDialog> 來列印檔案。</span><span class="sxs-lookup"><span data-stu-id="ce592-122">Shows how to use a <xref:System.Windows.Forms.PrintPreviewDialog> for printing a document.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ce592-123">相關章節</span><span class="sxs-lookup"><span data-stu-id="ce592-123">Related Sections</span></span>  
 [<span data-ttu-id="ce592-124">PrintDocument 元件</span><span class="sxs-lookup"><span data-stu-id="ce592-124">PrintDocument Component</span></span>](../controls/printdocument-component-windows-forms.md)  
 <span data-ttu-id="ce592-125">說明 <xref:System.Drawing.Printing.PrintDocument> 元件的使用方式。</span><span class="sxs-lookup"><span data-stu-id="ce592-125">Explains usage of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
 [<span data-ttu-id="ce592-126">PrintDialog 元件</span><span class="sxs-lookup"><span data-stu-id="ce592-126">PrintDialog Component</span></span>](../controls/printdialog-component-windows-forms.md)  
 <span data-ttu-id="ce592-127">說明 <xref:System.Windows.Forms.PrintDialog> 元件的使用方式。</span><span class="sxs-lookup"><span data-stu-id="ce592-127">Explains usage of the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
 [<span data-ttu-id="ce592-128">PrintPreviewDialog 控制項</span><span class="sxs-lookup"><span data-stu-id="ce592-128">PrintPreviewDialog Control</span></span>](../controls/printpreviewdialog-control-windows-forms.md)  
 <span data-ttu-id="ce592-129">說明 <xref:System.Windows.Forms.PrintPreviewDialog> 控制項的使用方式。</span><span class="sxs-lookup"><span data-stu-id="ce592-129">Explains usage of the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span>  
  
 [<span data-ttu-id="ce592-130">PageSetupDialog 元件</span><span class="sxs-lookup"><span data-stu-id="ce592-130">PageSetupDialog Component</span></span>](../controls/pagesetupdialog-component-windows-forms.md)  
 <span data-ttu-id="ce592-131">說明 <xref:System.Windows.Forms.PageSetupDialog> 元件的使用方式。</span><span class="sxs-lookup"><span data-stu-id="ce592-131">Explains usage of the <xref:System.Windows.Forms.PageSetupDialog> component.</span></span>  
  
 <xref:System.Drawing.Printing>  
 <span data-ttu-id="ce592-132">描述 <xref:System.Drawing.Printing> 命名空間中的類別。</span><span class="sxs-lookup"><span data-stu-id="ce592-132">Describes the classes in the <xref:System.Drawing.Printing> namespace.</span></span>

---
title: "PrintPreviewDialog 控制項概觀 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PrintPreviewDialog
helpviewer_keywords: PrintPreviewDialog control (using designer), about PrintPreviewDialog
ms.assetid: efd4ee8d-6edd-47ec-88e4-4a4759bd2384
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ed071a4d38a0167ac9414ee7d383736dd38a62a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="printpreviewdialog-control-overview-windows-forms"></a><span data-ttu-id="2745f-102">PrintPreviewDialog 控制項概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="2745f-102">PrintPreviewDialog Control Overview (Windows Forms)</span></span>
<span data-ttu-id="2745f-103">Windows Form<xref:System.Windows.Forms.PrintPreviewDialog>控制項是預先設定的對話方塊，用來顯示如何[PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)列印時。</span><span class="sxs-lookup"><span data-stu-id="2745f-103">The Windows Forms <xref:System.Windows.Forms.PrintPreviewDialog> control is a pre-configured dialog box used to display how a [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) will appear when printed.</span></span> <span data-ttu-id="2745f-104">該應用程式中使用 windows 做為簡單的解決方案，而不是設定您自己的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="2745f-104">Use it within your Windows-based application as a simple solution instead of configuring your own dialog box.</span></span> <span data-ttu-id="2745f-105">這個控制項包含列印、放大、顯示一或多頁及關閉對話方塊等按鈕。</span><span class="sxs-lookup"><span data-stu-id="2745f-105">The control contains buttons for printing, zooming in, displaying one or multiple pages, and closing the dialog box.</span></span>  
  
## <a name="key-properties-and-methods"></a><span data-ttu-id="2745f-106">索引鍵屬性和方法</span><span class="sxs-lookup"><span data-stu-id="2745f-106">Key Properties and Methods</span></span>  
 <span data-ttu-id="2745f-107">控制項的索引鍵屬性是<xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>，它會設定要預覽的文件。</span><span class="sxs-lookup"><span data-stu-id="2745f-107">The control's key property is <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>, which sets the document to be previewed.</span></span> <span data-ttu-id="2745f-108">必須是文件<xref:System.Drawing.Printing.PrintDocument>物件。</span><span class="sxs-lookup"><span data-stu-id="2745f-108">The document must be a <xref:System.Drawing.Printing.PrintDocument> object.</span></span> <span data-ttu-id="2745f-109">為了顯示對話方塊，您必須呼叫其<xref:System.Windows.Forms.Form.ShowDialog%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="2745f-109">In order to display the dialog box, you must call its <xref:System.Windows.Forms.Form.ShowDialog%2A> method.</span></span> <span data-ttu-id="2745f-110">消除鋸齒可以讓文字出現較平滑，但是它可以讓較慢; 顯示若要使用它，<xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A>屬性`true`。</span><span class="sxs-lookup"><span data-stu-id="2745f-110">Anti-aliasing can make the text appear smoother, but it can also make the display slower; to use it, set the <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> property to `true`.</span></span>  
  
 <span data-ttu-id="2745f-111">某些屬性都是透過<xref:System.Windows.Forms.PrintPreviewControl>，<xref:System.Windows.Forms.PrintPreviewDialog>包含。</span><span class="sxs-lookup"><span data-stu-id="2745f-111">Certain properties are available through the <xref:System.Windows.Forms.PrintPreviewControl> that the <xref:System.Windows.Forms.PrintPreviewDialog> contains.</span></span> <span data-ttu-id="2745f-112">(您沒有加入此<xref:System.Windows.Forms.PrintPreviewControl>表單; 它會自動包含在<xref:System.Windows.Forms.PrintPreviewDialog>將對話方塊加入至表單。)可透過使用屬性的範例<xref:System.Windows.Forms.PrintPreviewControl>是<xref:System.Windows.Forms.PrintPreviewControl.Columns%2A>和<xref:System.Windows.Forms.PrintPreviewControl.Rows%2A>屬性，判斷在控制項上顯示水平及垂直的頁數。</span><span class="sxs-lookup"><span data-stu-id="2745f-112">(You do not have to add this <xref:System.Windows.Forms.PrintPreviewControl> to the form; it is automatically contained within the <xref:System.Windows.Forms.PrintPreviewDialog> when you add the dialog to your form.) Examples of properties available through the <xref:System.Windows.Forms.PrintPreviewControl> are the <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> and <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> properties, which determine the number of pages displayed horizontally and vertically on the control.</span></span> <span data-ttu-id="2745f-113">您可以存取<xref:System.Windows.Forms.PrintPreviewControl.Columns%2A>屬性做為`PrintPreviewDialog1.PrintPreviewControl.Columns`中[!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]，`printPreviewDialog1.PrintPreviewControl.Columns`中[!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]，或`printPreviewDialog1->PrintPreviewControl->Columns`中[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2745f-113">You can access the <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> property as `PrintPreviewDialog1.PrintPreviewControl.Columns` in [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], `printPreviewDialog1.PrintPreviewControl.Columns` in [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], or `printPreviewDialog1->PrintPreviewControl->Columns` in [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2745f-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="2745f-114">See Also</span></span>  
 <xref:System.Windows.Forms.PrintPreviewDialog>  
 [<span data-ttu-id="2745f-115">PrintPreviewControl 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="2745f-115">PrintPreviewControl Control Overview</span></span>](../../../../docs/framework/winforms/controls/printpreviewcontrol-control-overview-windows-forms.md)  
 [<span data-ttu-id="2745f-116">PrintPreviewDialog 控制項</span><span class="sxs-lookup"><span data-stu-id="2745f-116">PrintPreviewDialog Control</span></span>](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 [<span data-ttu-id="2745f-117">對話方塊控制項和元件</span><span class="sxs-lookup"><span data-stu-id="2745f-117">Dialog-Box Controls and Components</span></span>](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)

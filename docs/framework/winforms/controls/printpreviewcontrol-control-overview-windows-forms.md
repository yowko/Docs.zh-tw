---
title: "PrintPreviewControl 控制項概觀 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PrintPreviewControl
helpviewer_keywords:
- print preview
- PrintPreviewControl control
ms.assetid: 4513c6c7-5e9b-4f4c-82ca-00f993a26955
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 47bef441b01d8bdcf9a365c341005cff28c64f27
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="printpreviewcontrol-control-overview-windows-forms"></a><span data-ttu-id="14807-102">PrintPreviewControl 控制項概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="14807-102">PrintPreviewControl Control Overview (Windows Forms)</span></span>
<span data-ttu-id="14807-103">Windows Form<xref:System.Windows.Forms.PrintPreviewControl>用來顯示[PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)列印時出現。</span><span class="sxs-lookup"><span data-stu-id="14807-103">The Windows Forms <xref:System.Windows.Forms.PrintPreviewControl> is used to display a [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) as it will appear when printed.</span></span> <span data-ttu-id="14807-104">這個控制項沒有任何按鈕或其他使用者介面項目，因此，通常只有當您想要撰寫您自己的預覽列印使用者介面時，才會使用 <xref:System.Windows.Forms.PrintPreviewControl>。</span><span class="sxs-lookup"><span data-stu-id="14807-104">This control has no buttons or other user interface elements, so typically you use the <xref:System.Windows.Forms.PrintPreviewControl> only if you wish to write your own print-preview user interface.</span></span> <span data-ttu-id="14807-105">如果您想要標準使用者介面，使用<xref:System.Windows.Forms.PrintPreviewDialog>控制，請參閱 < [PrintPreviewDialog 控制項概觀](../../../../docs/framework/winforms/controls/printpreviewdialog-control-overview-windows-forms.md)的概觀。</span><span class="sxs-lookup"><span data-stu-id="14807-105">If you want the standard user interface, use a <xref:System.Windows.Forms.PrintPreviewDialog> control; see [PrintPreviewDialog Control Overview](../../../../docs/framework/winforms/controls/printpreviewdialog-control-overview-windows-forms.md) for an overview.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="14807-106">索引鍵內容</span><span class="sxs-lookup"><span data-stu-id="14807-106">Key Properties</span></span>  
 <span data-ttu-id="14807-107">控制項的索引鍵屬性是<xref:System.Windows.Forms.PrintPreviewControl.Document%2A>，它會設定要預覽的文件。</span><span class="sxs-lookup"><span data-stu-id="14807-107">The control's key property is <xref:System.Windows.Forms.PrintPreviewControl.Document%2A>, which sets the document to be previewed.</span></span> <span data-ttu-id="14807-108">必須是文件<xref:System.Drawing.Printing.PrintDocument>物件。</span><span class="sxs-lookup"><span data-stu-id="14807-108">The document must be a <xref:System.Drawing.Printing.PrintDocument> object.</span></span> <span data-ttu-id="14807-109">如需建立列印的文件的概觀，請參閱[PrintDocument 元件概觀](../../../../docs/framework/winforms/controls/printdocument-component-overview-windows-forms.md)和[Windows Form 列印支援](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)。</span><span class="sxs-lookup"><span data-stu-id="14807-109">For an overview of creating documents for printing, see [PrintDocument Component Overview](../../../../docs/framework/winforms/controls/printdocument-component-overview-windows-forms.md) and [Windows Forms Print Support](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md).</span></span> <span data-ttu-id="14807-110"><xref:System.Windows.Forms.PrintPreviewControl.Columns%2A>和<xref:System.Windows.Forms.PrintPreviewControl.Rows%2A>屬性決定控制項上顯示水平及垂直的頁數。</span><span class="sxs-lookup"><span data-stu-id="14807-110">The <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> and <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> properties determine the number of pages displayed horizontally and vertically on the control.</span></span> <span data-ttu-id="14807-111">反鋸齒功能可以讓文字出現較平滑，但它也可顯示更慢。若要使用它，<xref:System.Windows.Forms.PrintPreviewControl.UseAntiAlias%2A>屬性`true`。</span><span class="sxs-lookup"><span data-stu-id="14807-111">Antialiasing can make the text appear smoother, but it can also make the display slower; to use it, set the <xref:System.Windows.Forms.PrintPreviewControl.UseAntiAlias%2A> property to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14807-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="14807-112">See Also</span></span>  
 <xref:System.Windows.Forms.PrintPreviewControl>  
 [<span data-ttu-id="14807-113">PrintPreviewDialog 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="14807-113">PrintPreviewDialog Control Overview</span></span>](../../../../docs/framework/winforms/controls/printpreviewdialog-control-overview-windows-forms.md)  
 [<span data-ttu-id="14807-114">PrintPreviewControl 控制項</span><span class="sxs-lookup"><span data-stu-id="14807-114">PrintPreviewControl Control</span></span>](../../../../docs/framework/winforms/controls/printpreviewcontrol-control-windows-forms.md)  
 [<span data-ttu-id="14807-115">對話方塊控制項和元件</span><span class="sxs-lookup"><span data-stu-id="14807-115">Dialog-Box Controls and Components</span></span>](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)

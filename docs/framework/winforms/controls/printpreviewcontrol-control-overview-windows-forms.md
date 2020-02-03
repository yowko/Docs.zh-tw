---
title: PrintPreviewControl 控制項概觀
ms.date: 03/30/2017
f1_keywords:
- PrintPreviewControl
helpviewer_keywords:
- print preview
- PrintPreviewControl control
ms.assetid: 4513c6c7-5e9b-4f4c-82ca-00f993a26955
ms.openlocfilehash: 8dfe5802a24d5ec85ed908fd04c5550e1fbec012
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741432"
---
# <a name="printpreviewcontrol-control-overview-windows-forms"></a><span data-ttu-id="09848-102">PrintPreviewControl 控制項概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="09848-102">PrintPreviewControl Control Overview (Windows Forms)</span></span>
<span data-ttu-id="09848-103">Windows Forms <xref:System.Windows.Forms.PrintPreviewControl> 會用來顯示[PrintDocument](printdocument-component-windows-forms.md) ，因為它會在列印時顯示。</span><span class="sxs-lookup"><span data-stu-id="09848-103">The Windows Forms <xref:System.Windows.Forms.PrintPreviewControl> is used to display a [PrintDocument](printdocument-component-windows-forms.md) as it will appear when printed.</span></span> <span data-ttu-id="09848-104">這個控制項沒有任何按鈕或其他使用者介面項目，因此，通常只有當您想要撰寫您自己的預覽列印使用者介面時，才會使用 <xref:System.Windows.Forms.PrintPreviewControl>。</span><span class="sxs-lookup"><span data-stu-id="09848-104">This control has no buttons or other user interface elements, so typically you use the <xref:System.Windows.Forms.PrintPreviewControl> only if you wish to write your own print-preview user interface.</span></span> <span data-ttu-id="09848-105">如果您想要標準使用者介面，請使用 <xref:System.Windows.Forms.PrintPreviewDialog> 控制項;如需總覽，請參閱[PrintPreviewDialog 控制項總覽](printpreviewdialog-control-overview-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="09848-105">If you want the standard user interface, use a <xref:System.Windows.Forms.PrintPreviewDialog> control; see [PrintPreviewDialog Control Overview](printpreviewdialog-control-overview-windows-forms.md) for an overview.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="09848-106">索引鍵內容</span><span class="sxs-lookup"><span data-stu-id="09848-106">Key Properties</span></span>  
 <span data-ttu-id="09848-107">控制項的索引鍵屬性是 <xref:System.Windows.Forms.PrintPreviewControl.Document%2A>，它會設定要預覽的檔。</span><span class="sxs-lookup"><span data-stu-id="09848-107">The control's key property is <xref:System.Windows.Forms.PrintPreviewControl.Document%2A>, which sets the document to be previewed.</span></span> <span data-ttu-id="09848-108">檔必須是 <xref:System.Drawing.Printing.PrintDocument> 物件。</span><span class="sxs-lookup"><span data-stu-id="09848-108">The document must be a <xref:System.Drawing.Printing.PrintDocument> object.</span></span> <span data-ttu-id="09848-109">如需建立檔以進行列印的總覽，請參閱[PrintDocument 元件總覽](printdocument-component-overview-windows-forms.md)和[Windows Forms 列印支援](../advanced/windows-forms-print-support.md)。</span><span class="sxs-lookup"><span data-stu-id="09848-109">For an overview of creating documents for printing, see [PrintDocument Component Overview](printdocument-component-overview-windows-forms.md) and [Windows Forms Print Support](../advanced/windows-forms-print-support.md).</span></span> <span data-ttu-id="09848-110">[<xref:System.Windows.Forms.PrintPreviewControl.Columns%2A>] 和 [<xref:System.Windows.Forms.PrintPreviewControl.Rows%2A>] 屬性會決定在控制項上水準和垂直顯示的頁面數目。</span><span class="sxs-lookup"><span data-stu-id="09848-110">The <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> and <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> properties determine the number of pages displayed horizontally and vertically on the control.</span></span> <span data-ttu-id="09848-111">消除鋸齒可以讓文字看起來更平滑，但也可以讓顯示器變慢;若要使用它，請將 <xref:System.Windows.Forms.PrintPreviewControl.UseAntiAlias%2A> 屬性設定為 [`true`]。</span><span class="sxs-lookup"><span data-stu-id="09848-111">Antialiasing can make the text appear smoother, but it can also make the display slower; to use it, set the <xref:System.Windows.Forms.PrintPreviewControl.UseAntiAlias%2A> property to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09848-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09848-112">See also</span></span>

- <xref:System.Windows.Forms.PrintPreviewControl>
- [<span data-ttu-id="09848-113">PrintPreviewDialog 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="09848-113">PrintPreviewDialog Control Overview</span></span>](printpreviewdialog-control-overview-windows-forms.md)
- [<span data-ttu-id="09848-114">PrintPreviewControl 控制項</span><span class="sxs-lookup"><span data-stu-id="09848-114">PrintPreviewControl Control</span></span>](printpreviewcontrol-control-windows-forms.md)
- [<span data-ttu-id="09848-115">對話方塊控制項和元件</span><span class="sxs-lookup"><span data-stu-id="09848-115">Dialog-Box Controls and Components</span></span>](dialog-box-controls-and-components-windows-forms.md)

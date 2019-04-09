---
title: PrintPreviewControl 控制項概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- PrintPreviewControl
helpviewer_keywords:
- print preview
- PrintPreviewControl control
ms.assetid: 4513c6c7-5e9b-4f4c-82ca-00f993a26955
ms.openlocfilehash: e9f1c2ae912b6beeba70c318b94a3052e2f99acb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122495"
---
# <a name="printpreviewcontrol-control-overview-windows-forms"></a><span data-ttu-id="998ab-102">PrintPreviewControl 控制項概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="998ab-102">PrintPreviewControl Control Overview (Windows Forms)</span></span>
<span data-ttu-id="998ab-103">Windows Forms<xref:System.Windows.Forms.PrintPreviewControl>用來顯示[PrintDocument](printdocument-component-windows-forms.md)列印時出現。</span><span class="sxs-lookup"><span data-stu-id="998ab-103">The Windows Forms <xref:System.Windows.Forms.PrintPreviewControl> is used to display a [PrintDocument](printdocument-component-windows-forms.md) as it will appear when printed.</span></span> <span data-ttu-id="998ab-104">這個控制項沒有任何按鈕或其他使用者介面項目，因此，通常只有當您想要撰寫您自己的預覽列印使用者介面時，才會使用 <xref:System.Windows.Forms.PrintPreviewControl>。</span><span class="sxs-lookup"><span data-stu-id="998ab-104">This control has no buttons or other user interface elements, so typically you use the <xref:System.Windows.Forms.PrintPreviewControl> only if you wish to write your own print-preview user interface.</span></span> <span data-ttu-id="998ab-105">如果您想要的標準使用者介面，使用<xref:System.Windows.Forms.PrintPreviewDialog>控制，請參閱[PrintPreviewDialog 控制項概觀](printpreviewdialog-control-overview-windows-forms.md)的概觀。</span><span class="sxs-lookup"><span data-stu-id="998ab-105">If you want the standard user interface, use a <xref:System.Windows.Forms.PrintPreviewDialog> control; see [PrintPreviewDialog Control Overview](printpreviewdialog-control-overview-windows-forms.md) for an overview.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="998ab-106">索引鍵內容</span><span class="sxs-lookup"><span data-stu-id="998ab-106">Key Properties</span></span>  
 <span data-ttu-id="998ab-107">控制項的索引鍵屬性是<xref:System.Windows.Forms.PrintPreviewControl.Document%2A>，可設定要預覽的文件。</span><span class="sxs-lookup"><span data-stu-id="998ab-107">The control's key property is <xref:System.Windows.Forms.PrintPreviewControl.Document%2A>, which sets the document to be previewed.</span></span> <span data-ttu-id="998ab-108">必須是文件<xref:System.Drawing.Printing.PrintDocument>物件。</span><span class="sxs-lookup"><span data-stu-id="998ab-108">The document must be a <xref:System.Drawing.Printing.PrintDocument> object.</span></span> <span data-ttu-id="998ab-109">建立列印的文件的概觀，請參閱[PrintDocument 元件概觀](printdocument-component-overview-windows-forms.md)並[Windows Forms 列印支援](../advanced/windows-forms-print-support.md)。</span><span class="sxs-lookup"><span data-stu-id="998ab-109">For an overview of creating documents for printing, see [PrintDocument Component Overview](printdocument-component-overview-windows-forms.md) and [Windows Forms Print Support](../advanced/windows-forms-print-support.md).</span></span> <span data-ttu-id="998ab-110"><xref:System.Windows.Forms.PrintPreviewControl.Columns%2A>和<xref:System.Windows.Forms.PrintPreviewControl.Rows%2A>屬性會決定控制項上顯示水平和垂直的頁數。</span><span class="sxs-lookup"><span data-stu-id="998ab-110">The <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> and <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> properties determine the number of pages displayed horizontally and vertically on the control.</span></span> <span data-ttu-id="998ab-111">消除鋸齒功能可以讓文字出現更順暢，但可能也會使速度較慢; 顯示若要使用它，將<xref:System.Windows.Forms.PrintPreviewControl.UseAntiAlias%2A>屬性設`true`。</span><span class="sxs-lookup"><span data-stu-id="998ab-111">Antialiasing can make the text appear smoother, but it can also make the display slower; to use it, set the <xref:System.Windows.Forms.PrintPreviewControl.UseAntiAlias%2A> property to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="998ab-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="998ab-112">See also</span></span>

- <xref:System.Windows.Forms.PrintPreviewControl>
- [<span data-ttu-id="998ab-113">PrintPreviewDialog 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="998ab-113">PrintPreviewDialog Control Overview</span></span>](printpreviewdialog-control-overview-windows-forms.md)
- [<span data-ttu-id="998ab-114">PrintPreviewControl 控制項</span><span class="sxs-lookup"><span data-stu-id="998ab-114">PrintPreviewControl Control</span></span>](printpreviewcontrol-control-windows-forms.md)
- [<span data-ttu-id="998ab-115">對話方塊控制項和元件</span><span class="sxs-lookup"><span data-stu-id="998ab-115">Dialog-Box Controls and Components</span></span>](dialog-box-controls-and-components-windows-forms.md)

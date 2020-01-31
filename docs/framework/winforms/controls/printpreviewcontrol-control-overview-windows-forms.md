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
# <a name="printpreviewcontrol-control-overview-windows-forms"></a>PrintPreviewControl 控制項概觀 (Windows Form)
Windows Forms <xref:System.Windows.Forms.PrintPreviewControl> 會用來顯示[PrintDocument](printdocument-component-windows-forms.md) ，因為它會在列印時顯示。 這個控制項沒有任何按鈕或其他使用者介面項目，因此，通常只有當您想要撰寫您自己的預覽列印使用者介面時，才會使用 <xref:System.Windows.Forms.PrintPreviewControl>。 如果您想要標準使用者介面，請使用 <xref:System.Windows.Forms.PrintPreviewDialog> 控制項;如需總覽，請參閱[PrintPreviewDialog 控制項總覽](printpreviewdialog-control-overview-windows-forms.md)。  
  
## <a name="key-properties"></a>索引鍵內容  
 控制項的索引鍵屬性是 <xref:System.Windows.Forms.PrintPreviewControl.Document%2A>，它會設定要預覽的檔。 檔必須是 <xref:System.Drawing.Printing.PrintDocument> 物件。 如需建立檔以進行列印的總覽，請參閱[PrintDocument 元件總覽](printdocument-component-overview-windows-forms.md)和[Windows Forms 列印支援](../advanced/windows-forms-print-support.md)。 [<xref:System.Windows.Forms.PrintPreviewControl.Columns%2A>] 和 [<xref:System.Windows.Forms.PrintPreviewControl.Rows%2A>] 屬性會決定在控制項上水準和垂直顯示的頁面數目。 消除鋸齒可以讓文字看起來更平滑，但也可以讓顯示器變慢;若要使用它，請將 <xref:System.Windows.Forms.PrintPreviewControl.UseAntiAlias%2A> 屬性設定為 [`true`]。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.PrintPreviewControl>
- [PrintPreviewDialog 控制項概觀](printpreviewdialog-control-overview-windows-forms.md)
- [PrintPreviewControl 控制項](printpreviewcontrol-control-windows-forms.md)
- [對話方塊控制項和元件](dialog-box-controls-and-components-windows-forms.md)

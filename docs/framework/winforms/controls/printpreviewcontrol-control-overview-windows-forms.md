---
title: PrintPreviewControl 控制項概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- PrintPreviewControl
helpviewer_keywords:
- print preview
- PrintPreviewControl control
ms.assetid: 4513c6c7-5e9b-4f4c-82ca-00f993a26955
ms.openlocfilehash: 330172a2ccf285cb75432572a558363e71de7ab1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="printpreviewcontrol-control-overview-windows-forms"></a>PrintPreviewControl 控制項概觀 (Windows Form)
Windows Form<xref:System.Windows.Forms.PrintPreviewControl>用來顯示[PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)列印時出現。 這個控制項沒有任何按鈕或其他使用者介面項目，因此，通常只有當您想要撰寫您自己的預覽列印使用者介面時，才會使用 <xref:System.Windows.Forms.PrintPreviewControl>。 如果您想要標準使用者介面，使用<xref:System.Windows.Forms.PrintPreviewDialog>控制，請參閱 < [PrintPreviewDialog 控制項概觀](../../../../docs/framework/winforms/controls/printpreviewdialog-control-overview-windows-forms.md)的概觀。  
  
## <a name="key-properties"></a>索引鍵內容  
 控制項的索引鍵屬性是<xref:System.Windows.Forms.PrintPreviewControl.Document%2A>，它會設定要預覽的文件。 必須是文件<xref:System.Drawing.Printing.PrintDocument>物件。 如需建立列印的文件的概觀，請參閱[PrintDocument 元件概觀](../../../../docs/framework/winforms/controls/printdocument-component-overview-windows-forms.md)和[Windows Form 列印支援](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)。 <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A>和<xref:System.Windows.Forms.PrintPreviewControl.Rows%2A>屬性決定控制項上顯示水平及垂直的頁數。 反鋸齒功能可以讓文字出現較平滑，但它也可顯示更慢。若要使用它，<xref:System.Windows.Forms.PrintPreviewControl.UseAntiAlias%2A>屬性`true`。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.PrintPreviewControl>  
 [PrintPreviewDialog 控制項概觀](../../../../docs/framework/winforms/controls/printpreviewdialog-control-overview-windows-forms.md)  
 [PrintPreviewControl 控制項](../../../../docs/framework/winforms/controls/printpreviewcontrol-control-windows-forms.md)  
 [對話方塊控制項和元件](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)

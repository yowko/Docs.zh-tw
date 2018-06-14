---
title: Windows Form 列印支援
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- forms [Windows Forms], printing (using designer)
- printing [Windows Forms], Windows Forms, support
- printing [Windows Forms], print support
ms.assetid: a4a2960c-eb70-48e2-b641-cfb222704e46
ms.openlocfilehash: 4ea04d0b6bb8ffa7182d5166ebd66b809adeed34
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528550"
---
# <a name="windows-forms-print-support"></a>Windows Form 列印支援
在 Windows Form 中的列印工作主要是使用[PrintDocument 元件](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)元件，讓使用者列印，而[PrintPreviewDialog 控制項](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)控制項， [PrintDialog元件](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)和[PageSetupDialog 元件](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md)習慣使用 Windows 作業系統的使用者提供熟悉的圖形化介面的元件。  
  
 一般而言，您建立的新執行個體<xref:System.Drawing.Printing.PrintDocument>元件，請設定屬性，描述要使用列印<xref:System.Drawing.Printing.PrinterSettings>和<xref:System.Drawing.Printing.PageSettings>類別，以及呼叫<xref:System.Drawing.Printing.PrintDocument.Print%2A>實際列印文件的方法。  
  
 從 windows 應用程式，列印過程<xref:System.Drawing.Printing.PrintDocument>元件將會顯示一個中止的列印對話方塊，警告使用者正在發生之列印的事實，並允許列印工作取消。  
  
## <a name="in-this-section"></a>本節內容  
 [操作說明：建立標準的 Windows Forms 列印工作](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)  
 說明如何使用<xref:System.Drawing.Printing.PrintDocument>列印 Windows Form 中的元件。  
  
 [操作說明：在執行階段從 PrintDialog 擷取使用者輸入](../../../../docs/framework/winforms/advanced/how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 說明如何修改選取的列印選項，以程式設計方式使用<xref:System.Windows.Forms.PrintDialog>元件。  
  
 [操作說明：在 Windows Forms 中選擇附加至使用者電腦的印表機](../../../../docs/framework/winforms/advanced/how-to-choose-the-printers-attached-to-user-computer-in-windows-forms.md)  
 描述變更列印到使用印表機<xref:System.Windows.Forms.PrintDialog>在執行階段元件。  
  
 [如何：列印 Windows Forms 中的圖形](../../../../docs/framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)  
 描述圖形傳送至印表機。  
  
 [如何：在 Windows Forms 中列印多頁文字檔](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 描述將文字傳送至印表機。  
  
 [操作說明：完成 Windows Forms 列印工作](../../../../docs/framework/winforms/advanced/how-to-complete-windows-forms-print-jobs.md)  
 說明如何完成列印工作的使用者發出警示。  
  
 [操作說明：列印 Windows Forms](../../../../docs/framework/winforms/advanced/how-to-print-a-windows-form.md)  
 示範如何列印一份目前的表單。  
  
 [操作說明：使用預覽列印在 Windows Forms 中進行列印](../../../../docs/framework/winforms/advanced/how-to-print-in-windows-forms-using-print-preview.md)  
 示範如何使用<xref:System.Windows.Forms.PrintPreviewDialog>列印文件。  
  
## <a name="related-sections"></a>相關章節  
 [PrintDocument 元件](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)  
 說明使用<xref:System.Drawing.Printing.PrintDocument>元件。  
  
 [PrintDialog 元件](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)  
 說明使用<xref:System.Windows.Forms.PrintDialog>元件。  
  
 [PrintPreviewDialog 控制項](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 說明使用<xref:System.Windows.Forms.PrintPreviewDialog>控制項。  
  
 [PageSetupDialog 元件](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md)  
 說明使用<xref:System.Windows.Forms.PageSetupDialog>元件。  
  
 <xref:System.Drawing.Printing>  
 描述中的類別<xref:System.Drawing.Printing>命名空間。

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
ms.openlocfilehash: 8e008f2cb4b2f32cdba676e68d9fd790530e2b06
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011844"
---
# <a name="windows-forms-print-support"></a>Windows Form 列印支援
在 Windows Forms 中的列印工作主要是使用[PrintDocument 元件](../controls/printdocument-component-windows-forms.md)元件，讓使用者單次列印，而[PrintPreviewDialog 控制項](../controls/printpreviewdialog-control-windows-forms.md)控制項， [PrintDialog元件](../controls/printdialog-component-windows-forms.md)並[PageSetupDialog 元件](../controls/pagesetupdialog-component-windows-forms.md)習慣使用 Windows 作業系統的使用者提供熟悉的圖形化介面的元件。  
  
 一般而言，您建立的新執行個體<xref:System.Drawing.Printing.PrintDocument>元件，設定屬性，描述要使用列印<xref:System.Drawing.Printing.PrinterSettings>並<xref:System.Drawing.Printing.PageSettings>類別，以及呼叫<xref:System.Drawing.Printing.PrintDocument.Print%2A>實際列印文件的方法。  
  
 從以 Windows 為基礎的應用程式，列印過程<xref:System.Drawing.Printing.PrintDocument>元件會顯示 [中止] 列印的對話方塊中，警告使用者正在進行列印的事實，並允許列印工作取消。  
  
## <a name="in-this-section"></a>本節內容  
 [如何：建立標準的 Windows Forms 列印工作](how-to-create-standard-windows-forms-print-jobs.md)  
 說明如何使用<xref:System.Drawing.Printing.PrintDocument>列印 Windows Form 中的元件。  
  
 [如何：在執行階段擷取使用者輸入從 PrintDialog](how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 說明如何修改所選的列印選項，以程式設計方式使用<xref:System.Windows.Forms.PrintDialog>元件。  
  
 [如何：選擇 附加至 Windows Forms 中的使用者的電腦的印表機](how-to-choose-the-printers-attached-to-user-computer-in-windows-forms.md)  
 描述變更印表機來列印到使用<xref:System.Windows.Forms.PrintDialog>在執行階段元件。  
  
 [如何：列印 Windows Form 中的圖形](how-to-print-graphics-in-windows-forms.md)  
 描述圖形傳送至印表機。  
  
 [如何：列印 Windows Form 中的多頁文字檔](how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 描述將文字傳送至印表機。  
  
 [如何：完整的 Windows Forms 列印工作](how-to-complete-windows-forms-print-jobs.md)  
 說明如何以警示使用者的列印工作完成。  
  
 [如何：列印 Windows Form](how-to-print-a-windows-form.md)  
 示範如何列印一份目前的表單。  
  
 [如何：使用預覽列印 Windows Forms 中列印](how-to-print-in-windows-forms-using-print-preview.md)  
 示範如何使用<xref:System.Windows.Forms.PrintPreviewDialog>列印文件。  
  
## <a name="related-sections"></a>相關章節  
 [PrintDocument 元件](../controls/printdocument-component-windows-forms.md)  
 說明使用<xref:System.Drawing.Printing.PrintDocument>元件。  
  
 [PrintDialog 元件](../controls/printdialog-component-windows-forms.md)  
 說明使用<xref:System.Windows.Forms.PrintDialog>元件。  
  
 [PrintPreviewDialog 控制項](../controls/printpreviewdialog-control-windows-forms.md)  
 說明使用<xref:System.Windows.Forms.PrintPreviewDialog>控制項。  
  
 [PageSetupDialog 元件](../controls/pagesetupdialog-component-windows-forms.md)  
 說明使用<xref:System.Windows.Forms.PageSetupDialog>元件。  
  
 <xref:System.Drawing.Printing>  
 描述中的類別<xref:System.Drawing.Printing>命名空間。

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
# <a name="windows-forms-print-support"></a>Windows Form 列印支援
在 Windows Forms 中列印主要是使用[PrintDocument 元件](../controls/printdocument-component-windows-forms.md)元件，讓使用者能夠列印，而[PrintPreviewDialog 控制項](../controls/printpreviewdialog-control-windows-forms.md)控制項[PrintDialog 元件](../controls/printdialog-component-windows-forms.md)和[PageSetupDialog 元件](../controls/pagesetupdialog-component-windows-forms.md)元件則提供熟悉的圖形化介面給習慣 Windows 作業系統的使用者。  
  
 一般來說，您會建立 <xref:System.Drawing.Printing.PrintDocument> 元件的新實例、使用 <xref:System.Drawing.Printing.PrinterSettings> 和 <xref:System.Drawing.Printing.PageSettings> 類別來設定描述要列印之內容的屬性，以及呼叫 <xref:System.Drawing.Printing.PrintDocument.Print%2A> 方法來實際列印檔案。  
  
 在從 Windows 應用程式進行列印的過程中，<xref:System.Drawing.Printing.PrintDocument> 元件將會顯示 [中止列印] 對話方塊，以提醒使用者發生列印的情況，並允許取消列印工作。  
  
## <a name="in-this-section"></a>本章節內容  
 [操作說明：建立標準的 Windows Forms 列印工作](how-to-create-standard-windows-forms-print-jobs.md)  
 說明如何使用 <xref:System.Drawing.Printing.PrintDocument> 元件從 Windows Form 進行列印。  
  
 [操作說明：在執行階段從 PrintDialog 擷取使用者輸入](how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 說明如何使用 <xref:System.Windows.Forms.PrintDialog> 元件，以程式設計方式修改選取的列印選項。  
  
 [操作說明：在 Windows Forms 中選擇附加至使用者電腦的印表機](how-to-choose-the-printers-attached-to-user-computer-in-windows-forms.md)  
 描述如何在執行時間使用 <xref:System.Windows.Forms.PrintDialog> 元件，將印表機變更為列印。  
  
 [如何：列印 Windows Forms 中的圖形](how-to-print-graphics-in-windows-forms.md)  
 說明如何將圖形傳送至印表機。  
  
 [如何：在 Windows Forms 中列印多頁文字檔](how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 說明如何將文字傳送至印表機。  
  
 [操作說明：完成 Windows Forms 列印工作](how-to-complete-windows-forms-print-jobs.md)  
 說明如何警示使用者完成列印工作。  
  
 [操作說明：列印 Windows Forms](how-to-print-a-windows-form.md)  
 顯示如何列印目前表單的複本。  
  
 [操作說明：使用預覽列印在 Windows Forms 中進行列印](how-to-print-in-windows-forms-using-print-preview.md)  
 示範如何使用 <xref:System.Windows.Forms.PrintPreviewDialog> 來列印檔案。  
  
## <a name="related-sections"></a>相關章節  
 [PrintDocument 元件](../controls/printdocument-component-windows-forms.md)  
 說明 <xref:System.Drawing.Printing.PrintDocument> 元件的使用方式。  
  
 [PrintDialog 元件](../controls/printdialog-component-windows-forms.md)  
 說明 <xref:System.Windows.Forms.PrintDialog> 元件的使用方式。  
  
 [PrintPreviewDialog 控制項](../controls/printpreviewdialog-control-windows-forms.md)  
 說明 <xref:System.Windows.Forms.PrintPreviewDialog> 控制項的使用方式。  
  
 [PageSetupDialog Component](../controls/pagesetupdialog-component-windows-forms.md)  
 說明 <xref:System.Windows.Forms.PageSetupDialog> 元件的使用方式。  
  
 <xref:System.Drawing.Printing>  
 描述 <xref:System.Drawing.Printing> 命名空間中的類別。

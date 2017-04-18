---
title: "Windows Form 列印支援 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "表單, 列印 (使用設計工具)"
  - "列印 [Windows Form]"
  - "列印 [Windows Form], 列印支援"
  - "列印, Windows Form, 支援"
  - "Windows Form, 列印"
ms.assetid: a4a2960c-eb70-48e2-b641-cfb222704e46
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Windows Form 列印支援
Windows Form 中的列印主要包括使用 [PrintDocument 元件](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) 元件讓使用者進行輸入，以及使用 [PrintPreviewDialog 控制項](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md) 控制項、[PrintDialog 元件](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) 和 [PageSetupDialog 元件](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) 元件來提供使用者對 Windows 作業系統所熟悉的圖形介面。  
  
 通常，您會建立 <xref:System.Drawing.Printing.PrintDocument> 元件的新執行個體、使用 <xref:System.Drawing.Printing.PrinterSettings> 和 <xref:System.Drawing.Printing.PageSettings> 類別來設定描述列印項目的屬性，並呼叫 <xref:System.Drawing.Printing.PrintDocument.Print%2A> 方法以實際列印文件。  
  
 在從 Windows 架構應用程式進行列印期間，<xref:System.Drawing.Printing.PrintDocument> 元件會顯示中止列印對話方塊，以警示使用者列印正在進行並且允許取消列印的工作。  
  
## 在本節中  
 [如何：建立標準的 Windows Form 列印工作](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)  
 說明如何使用 <xref:System.Drawing.Printing.PrintDocument> 元件從 Windows Form 進行列印。  
  
 [如何：在執行階段從 PrintDialog 擷取使用者輸入](../../../../docs/framework/winforms/advanced/how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 說明如何使用 <xref:System.Windows.Forms.PrintDialog> 元件，以程式設計的方式修改選取的列印選項。  
  
 [如何：在 Windows Form 中選擇附加至使用者電腦的印表機](../../../../docs/framework/winforms/advanced/how-to-choose-the-printers-attached-to-user-computer-in-windows-forms.md)  
 描述在執行階段時使用 <xref:System.Windows.Forms.PrintDialog> 元件，變更要用來列印的印表機。  
  
 [如何：列印 Windows Form 中的圖形](../../../../docs/framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)  
 說明將圖形傳送至印表機。  
  
 [如何：在 Windows Form 中列印多頁文字檔](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 說明將文字傳送至印表機。  
  
 [如何：完成 Windows Form 列印工作](../../../../docs/framework/winforms/advanced/how-to-complete-windows-forms-print-jobs.md)  
 說明如何提醒使用者列印工作已完成。  
  
 [如何：列印 Windows Form](../../../../docs/framework/winforms/advanced/how-to-print-a-windows-form.md)  
 顯示如何列印一份目前的表單。  
  
 [如何：使用預覽列印在 Windows Form 中進行列印](../../../../docs/framework/winforms/advanced/how-to-print-in-windows-forms-using-print-preview.md)  
 示範如何使用 <xref:System.Windows.Forms.PrintPreviewDialog> 來列印文件。  
  
## 相關章節  
 [PrintDocument 元件](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)  
 解釋 <xref:System.Drawing.Printing.PrintDocument> 元件的使用方式。  
  
 [PrintDialog 元件](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)  
 解釋 <xref:System.Windows.Forms.PrintDialog> 元件的使用方式。  
  
 [PrintPreviewDialog 控制項](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 解釋 <xref:System.Windows.Forms.PrintPreviewDialog> 控制項的使用方式。  
  
 [PageSetupDialog 元件](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md)  
 解釋 <xref:System.Windows.Forms.PageSetupDialog> 元件的使用方式。  
  
 <xref:System.Drawing.Printing>  
 描述在 <xref:System.Drawing.Printing> 命名空間中的類別。
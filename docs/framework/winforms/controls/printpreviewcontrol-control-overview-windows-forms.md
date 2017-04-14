---
title: "PrintPreviewControl 控制項概觀 (Windows Form) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PrintPreviewControl"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "預覽列印"
  - "PrintPreviewControl 控制項"
ms.assetid: 4513c6c7-5e9b-4f4c-82ca-00f993a26955
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# PrintPreviewControl 控制項概觀 (Windows Form)
Windows Form <xref:System.Windows.Forms.PrintPreviewControl> 是用來顯示在列印 [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) 時會出現的外觀。  這個控制項並沒有按鈕或其他使用者介面項目，因此通常只有在您想要寫入自己的預覽列印使用者介面時，才會使用 <xref:System.Windows.Forms.PrintPreviewControl>。  若您希望使用標準的使用者介面，請使用 <xref:System.Windows.Forms.PrintPreviewDialog> 控制項。如需概觀，請參閱 [PrintPreviewDialog 控制項概觀](../../../../docs/framework/winforms/controls/printpreviewdialog-control-overview-windows-forms.md)。  
  
## 主要屬性  
 這個控制項的主要屬性 \(Property\) 是 <xref:System.Windows.Forms.PrintPreviewControl.Document%2A>，用來設定要預覽的文件。  文件必須是 <xref:System.Drawing.Printing.PrintDocument> 物件。  如需建立列印的文件的概觀，請參閱 [PrintDocument 元件概觀](../../../../docs/framework/winforms/controls/printdocument-component-overview-windows-forms.md) 和 [Windows Form 列印支援](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)。  <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> 和 <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> 屬性 \(Property\) 會決定在控制項上水平和垂直顯示的頁數。  反鋸齒 \(Antialiasing\) 可讓文字顯示更為平順，但也可能使顯示速度變慢，若要使用反鋸齒，請將 <xref:System.Windows.Forms.PrintPreviewControl.UseAntiAlias%2A> 屬性 \(Property\) 設定為 `true`。  
  
## 請參閱  
 <xref:System.Windows.Forms.PrintPreviewControl>   
 [PrintPreviewDialog 控制項概觀](../../../../docs/framework/winforms/controls/printpreviewdialog-control-overview-windows-forms.md)   
 [PrintPreviewControl 控制項](../../../../docs/framework/winforms/controls/printpreviewcontrol-control-windows-forms.md)   
 [對話方塊控制項和元件](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)
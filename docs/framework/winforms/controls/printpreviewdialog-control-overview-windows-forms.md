---
title: "PrintPreviewDialog 控制項概觀 (Windows Form) | Microsoft Docs"
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
  - "PrintPreviewDialog"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "PrintPreviewDialog 控制項 (使用設計工具), 關於 PrintPreviewDialog"
ms.assetid: efd4ee8d-6edd-47ec-88e4-4a4759bd2384
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# PrintPreviewDialog 控制項概觀 (Windows Form)
Windows Form <xref:System.Windows.Forms.PrintPreviewDialog> 控制項是預先設定的對話方塊，用來顯示 [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) 在列印時的顯示方式。  只要在 Windows 應用程式中使用它做為簡單的方案，您就不需設定自己的對話方塊。  這個控制項包含列印、放大、顯示一或多頁及關閉對話方塊等按鈕。  
  
## 主要屬性和方法  
 這個控制項的主要屬性 \(Property\) 是 <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>，用來設定要預覽的文件。  文件必須是 <xref:System.Drawing.Printing.PrintDocument> 物件。  若要顯示對話方塊，您必須呼叫它的 <xref:System.Windows.Forms.Form.ShowDialog%2A> 方法。  反鋸齒 \(Antialiasing\) 可讓文字顯示更為平順，但也可能使顯示速度變慢，若要使用反鋸齒，請將 <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> 屬性設定為 `true`。  
  
 某些屬性是透過 <xref:System.Windows.Forms.PrintPreviewDialog> 包含的 <xref:System.Windows.Forms.PrintPreviewControl> 所提供   \(您不需要將這個 <xref:System.Windows.Forms.PrintPreviewControl> 加入至表單，當您將對話方塊加入至表單時，它會自動包含在 <xref:System.Windows.Forms.PrintPreviewDialog> 中\)。 <xref:System.Windows.Forms.PrintPreviewControl> 所提供屬性的範例有 <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> 和 <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> 屬性，這些屬性會決定控制項上水平及垂直顯示的頁數。  存取 <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> 屬性的方式包括：在 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 中使用 `PrintPreviewDialog1.PrintPreviewControl.Columns`、在 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 中使用 `printPreviewDialog1.PrintPreviewControl.Columns` 或在 [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)] 中使用 `printPreviewDialog1->PrintPreviewControl->Columns`。  
  
## 請參閱  
 <xref:System.Windows.Forms.PrintPreviewDialog>   
 [PrintPreviewControl 控制項概觀](../../../../docs/framework/winforms/controls/printpreviewcontrol-control-overview-windows-forms.md)   
 [PrintPreviewDialog 控制項](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)   
 [對話方塊控制項和元件](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)
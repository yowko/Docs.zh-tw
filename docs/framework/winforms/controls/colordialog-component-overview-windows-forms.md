---
title: "ColorDialog 元件概觀 (Windows Form) | Microsoft Docs"
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
  - "ColorDialog"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "色彩對話方塊, 關於色彩對話方塊"
  - "ColorDialog 元件, 關於 ColorDialog"
ms.assetid: 6dbdd8f0-f697-4728-bb09-7ea156f6d800
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# ColorDialog 元件概觀 (Windows Form)
Windows Form <xref:System.Windows.Forms.ColorDialog> 元件是預先設定的對話方塊，能允許使用者從調色盤 \(Palette\) 選取色彩，並將自訂色彩加入至調色盤。  這和您在其他 Windows 架構應用程式中所見，用來選取色彩的對話方塊是一樣的。  在您的 Windows 架構應用程式中將它用來做為簡單方案，就不需設定您自己的對話方塊。  
  
 在對話方塊中選取的色彩會傳回至 <xref:System.Windows.Forms.ColorDialog.Color%2A> 屬性。  如果將 <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> 屬性設定為 `false`，則會停用 \[定義自訂色彩\] 按鈕，並限制使用者只能使用調色盤中預先定義的色彩。  如果將 <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> 屬性設定為 `true`，則使用者無法選取遞色 \(Dithered\) 色彩。  若要顯示對話方塊，您必須呼叫它的 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 方法。  
  
## 請參閱  
 <xref:System.Windows.Forms.ColorDialog>   
 [ColorDialog 元件](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)   
 [對話方塊控制項和元件](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)   
 [如何：變更 Windows Form ColorDialog 元件的外觀](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-colordialog-component.md)
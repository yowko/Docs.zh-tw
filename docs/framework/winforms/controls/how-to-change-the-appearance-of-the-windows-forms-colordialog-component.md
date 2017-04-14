---
title: "如何：變更 Windows Form ColorDialog 元件的外觀 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "色彩對話方塊, 設定外觀"
  - "ColorDialog 元件, 範例"
  - "ColorDialog 元件, 設定外觀格式"
ms.assetid: bba4e262-1cd7-4f63-89cf-330a36f7b539
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：變更 Windows Form ColorDialog 元件的外觀
您可以利用 <xref:System.Windows.Forms.ColorDialog> 元件的幾個屬性來設定其外觀。  這個對話方塊有兩個部分，一是用來顯示基本色彩，另一則允許使用者定義自訂色彩。  
  
 大部分的屬性都是用來限制使用者可從對話方塊選取哪些色彩。  如果將 <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> 屬性設定為 `true`，則使用者可以定義自訂色彩。  如果對話方塊是展開來定義自訂色彩的話，<xref:System.Windows.Forms.ColorDialog.FullOpen%2A> 屬性就為 `true`；否則使用者必須按一下 \[定義自訂色彩\] 按鈕。  當 <xref:System.Windows.Forms.ColorDialog.AnyColor%2A> 屬性設定為 `true` 時，對話方塊會顯示基本色彩集當中的所有的可用色彩。  如果將 <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> 屬性設定為 `true`，則使用者無法選取遞色色彩，而只能選取純色。  
  
 如果將 <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> 屬性設定為 `true`，則對話方塊上會出現 \[說明\] 按鈕。  當使用者按一下 \[說明\] 按鈕時，就會引發 <xref:System.Windows.Forms.ColorDialog> 元件的 <xref:System.Windows.Forms.CommonDialog.HelpRequest> 事件。  
  
### 若要設定色彩對話方塊的外觀  
  
1.  將 <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>、<xref:System.Windows.Forms.ColorDialog.AnyColor%2A>、<xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> 和 <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> 屬性設定為所需的值。  
  
    ```vb  
    ColorDialog1.AllowFullOpen = True  
    ColorDialog1.AnyColor = True  
    ColorDialog1.SolidColorOnly = False  
    ColorDialog1.ShowHelp = True  
  
    ```  
  
    ```csharp  
    colorDialog1.AllowFullOpen = true;  
    colorDialog1.AnyColor = true;  
    colorDialog1.SolidColorOnly = false;  
    colorDialog1.ShowHelp = true;  
  
    ```  
  
    ```cpp  
    colorDialog1->AllowFullOpen = true;  
    colorDialog1->AnyColor = true;  
    colorDialog1->SolidColorOnly = false;  
    colorDialog1->ShowHelp = true;  
    ```  
  
## 請參閱  
 <xref:System.Windows.Forms.ColorDialog>   
 [ColorDialog 元件](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)   
 [ColorDialog 元件概觀](../../../../docs/framework/winforms/controls/colordialog-component-overview-windows-forms.md)
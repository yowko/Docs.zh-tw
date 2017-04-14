---
title: "FontDialog 元件概觀 (Windows Form) | Microsoft Docs"
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
  - "FontDialog"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "字型對話方塊"
  - "字型對話方塊, Windows Form"
  - "FontDialog 元件 [Windows Form], 關於 FontDialog 元件"
ms.assetid: daf46e57-1b4b-4b7a-bad0-b50ca7ba75dc
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# FontDialog 元件概觀 (Windows Form)
Windows Form <xref:System.Windows.Forms.FontDialog> 元件是預先設定的對話方塊，這個標準的 Windows \[**字型**\] 對話方塊是用來公開 \(Expose\) 目前已安裝在系統上的字型。  在您的 Windows 架構應用程式中使用它做為字型選擇的簡單方案，您就不用設定自己的對話方塊。  
  
 對話方塊依預設會顯示字型、字型樣式和大小的清單方塊；刪除線和底線等效果的核取方塊；指令碼的下拉式清單；和字型如何顯示的範例   \(指令碼指的是特定字型可使用的不同字元指令碼，例如希伯來文或日文\)。 若要顯示字型對話方塊，請呼叫 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 方法。  
  
## 主要屬性  
 這個元件具有多個設定外觀的屬性。  設定對話方塊選取的屬性是 <xref:System.Windows.Forms.FontDialog.Font%2A> 和 <xref:System.Windows.Forms.FontDialog.Color%2A>。  <xref:System.Windows.Forms.FontDialog.Font%2A> 屬性會設定字型、樣式、大小、指令碼和效果；例如， `Arial, 10pt, style=Italic, Strikeout`。  
  
## 請參閱  
 <xref:System.Windows.Forms.FontDialog>   
 [FontDialog 元件](../../../../docs/framework/winforms/controls/fontdialog-component-windows-forms.md)
---
title: "PrintDialog 元件概觀 (Windows Form) | Microsoft Docs"
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
  - "PrintDialog"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "列印對話方塊, 顯示"
  - "PrintDialog 元件 [Windows Form], 關於 PrintDialog 元件"
ms.assetid: 8327b8ac-1017-4b5e-a88b-fea9dd56999c
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# PrintDialog 元件概觀 (Windows Form)
Windows Form [PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) 元件是預先設定的對話方塊，用來在 Windows 架構應用程式中選取印表機、選擇列印頁面，以及決定其他與列印相關的設定。  使用此元件做為印表機和列印相關設定選擇的簡單方案，您就不用設定自己的對話方塊。  您可以讓使用者列印文件的多個部分：列印全部、列印選擇的頁數範圍或列印選定的範圍。  利用標準的 Windows 對話方塊做為基礎，您可以建立使用者可立即熟悉基本功能的應用程式。  <xref:System.Windows.Forms.PrintDialog> 元件是繼承自 <xref:System.Windows.Forms.CommonDialog> 類別。  
  
## 使用元件  
 您可以使用 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 方法在執行階段顯示對話方塊，  這個元件具有與單一列印工作 \(<xref:System.Drawing.Printing.PrintDocument> 類別\) 或個別印表機設定 \(<xref:System.Drawing.Printing.PrinterSettings> 類別\) 相關的屬性。  其中任一屬性都可依序由多部印表機共用。  
  
 當 <xref:System.Windows.Forms.PrintDialog> 元件加入表單時，它會出現在 \[Windows Form 設計工具\] 下方的匣中。  
  
## 請參閱  
 <xref:System.Windows.Forms.PrintDialog>   
 [PrintDialog 元件](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)
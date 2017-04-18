---
title: "PrintDocument 元件概觀 (Windows Form) | Microsoft Docs"
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
  - "PrintDocument"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "PrintDocument 元件 [Windows Form], 關於 PrintDocument 元件"
  - "列印 [Windows Form], PrintDocument 元件"
ms.assetid: b59b4b60-dce5-42ca-8421-3a54a2f7bab0
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# PrintDocument 元件概觀 (Windows Form)
Windows Form [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) 元件可用來設定描述 Windows 架構應用程式中列印內容及列印文件能力的屬性。  它可以與 [PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) 元件一起用於控制與文件列印相關的所有事項。  
  
## 使用 PrintDocument 元件  
 涉及 <xref:System.Drawing.Printing.PrintDocument> 元件的兩個主要案例為：  
  
-   簡單列印工作，例如列印個別的文字檔。  在這種情況中，您會將 <xref:System.Drawing.Printing.PrintDocument> 元件加入至 Windows Form，接著在 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件處理常式中加入列印檔案的程式設計邏輯。  程式設計邏輯應該以 <xref:System.Drawing.Printing.PrintDocument.Print%2A> 方法列印文件做為目標。  這個方法會將包含在 <xref:System.Drawing.Printing.PrintPageEventArgs> 類別的 <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> 屬性中的 <xref:System.Drawing.Graphics> 物件傳送至印表機。  如需示範如何使用 <xref:System.Drawing.Printing.PrintDocument> 元件列印文字文件的範例，請參閱 [如何：在 Windows Form 中列印多頁文字檔](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)。  
  
-   較複雜的列印工作，例如您要重複使用已撰寫的列印邏輯。  在這種情況中，您會從 <xref:System.Drawing.Printing.PrintDocument> 元件衍生新元件，並覆寫 \(請參閱 Visual Basic 的 [Overrides](../Topic/Overrides%20\(Visual%20Basic\).md) 或 C\# 的 [override](../Topic/override%20\(C%23%20Reference\).md)\) <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件。  
  
 當 <xref:System.Drawing.Printing.PrintDocument> 元件加入表單時，它會出現在 \[Windows Form 設計工具\] 下方的匣中。  
  
## 請參閱  
 <xref:System.Drawing.Graphics>   
 <xref:System.Drawing.Printing.PrintDocument>   
 [Windows Form 列印支援](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)   
 [PrintDocument 元件](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)
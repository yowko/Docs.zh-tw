---
title: "LinkLabel 控制項概觀 (Windows Form) | Microsoft Docs"
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
  - "LinkLabel"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "Label 控制項 [Windows Form], 關於 Label 控制項"
  - "LinkLabel 控制項 [Windows Form], 關於 LinkLabel 控制項"
  - "連結, LinkLabel 控制項"
ms.assetid: 9e248549-10ca-43a3-bb5e-60f583d369f1
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# LinkLabel 控制項概觀 (Windows Form)
Windows Form <xref:System.Windows.Forms.LinkLabel> 控制項可讓您將 Web 樣式連結加入 Windows Form 應用程式。  您可以針對 <xref:System.Windows.Forms.Label> 控制項可作用的任何內容，使用 <xref:System.Windows.Forms.LinkLabel> 控制項；也可以設定部分文字做為檔案、資料夾或 Web 網頁的連結。  
  
## LinkLabel 控制項的功能  
 除了擁有 <xref:System.Windows.Forms.LinkLabel> 控制項的所有屬性、方法和事件外，<xref:System.Windows.Forms.Label> 控制項還有超連結 \(Hyperlink\) 和連結色彩的屬性。  <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> 屬性可設定啟動連結的文字區。  <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>、<xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> 和 <xref:System.Windows.Forms.LinkLabel.ActiveLinkColor%2A> 屬性會設定連結的色彩。  <xref:System.Windows.Forms.LinkLabel.LinkClicked> 事件可決定在選取連結文字時發生的結果。  
  
 <xref:System.Windows.Forms.LinkLabel> 控制項最簡單的用法就是使用 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> 屬性來顯示單一連結，但您也可以使用 <xref:System.Windows.Forms.LinkLabel.Links%2A> 屬性來顯示多個超連結。  <xref:System.Windows.Forms.LinkLabel.Links%2A> 屬性可讓您存取連結集合。  您也可以在每個 <xref:System.Windows.Forms.LinkLabel.Link> 物件的 <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> 屬性中指定資料。  <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> 屬性值可用來儲存要顯示檔案的位置或網站的位址。  
  
## 請參閱  
 <xref:System.Windows.Forms.LinkLabel>   
 [Label 控制項概觀](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)   
 [如何：使用 Windows Form LinkLabel 控制項連結至物件或 Web 網頁](../../../../docs/framework/winforms/controls/link-to-an-object-or-web-page-with-wf-linklabel-control.md)   
 [如何：變更 Windows Form LinkLabel 控制項的外觀](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
---
title: "如何：列印 Windows Form | Microsoft Docs"
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
  - "列印 [Windows Form], 列印表單"
  - "列印 [Windows Form]"
  - "列印表單"
  - "Windows Form, 列印"
ms.assetid: c8dff5f8-f56a-4c07-ae31-64643b31f8fc
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：列印 Windows Form
就像開發程序的一部分一樣，您通常會想列印一份 Windows Form。  下列程式碼範例會顯示如何使用 <xref:System.Drawing.Graphics.CopyFromScreen%2A> 方法列印一份目前的表單。  
  
## 範例  
 [!code-csharp[System.Drawing.Graphics.CopyFromScreen#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Graphics.CopyFromScreen#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/VB/Form1.vb#1)]  
  
## 編譯程式碼  
 這是包含 `Main` 方法的完整程式碼範例。  
  
## 穩固程式設計  
 下列情形可能會造成例外狀況 \(Exception\)：  
  
-   您沒有印表機的存取權限。  
  
-   未安裝任何印表機。  
  
## .NET Framework 安全性  
 為了執行此程式碼範例，您必須具備使用權限以存取電腦搭配使用的印表機。  
  
## 請參閱  
 <xref:System.Drawing.Printing.PrintDocument>   
 [如何：使用 GDI\+ 呈現影像](../../../../docs/framework/winforms/advanced/how-to-render-images-with-gdi.md)   
 [如何：列印 Windows Form 中的圖形](../../../../docs/framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)
---
title: "如何：繪製自訂短折線 | Microsoft Docs"
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
  - "線條, 自訂"
  - "線條, 虛線"
  - "線條, 繪製"
ms.assetid: cd0ed96a-cce4-47b9-b58a-3bae2e3d1bee
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 如何：繪製自訂短折線
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 提供數種列於 <xref:System.Drawing.Drawing2D.DashStyle> 列舉中的虛線樣式。  如果這些標準虛線樣式不符合您的需要，您可以建立自訂虛線圖樣。  
  
## 範例  
 若要繪製自訂短折線，請將虛線長度和空格長度放入在陣列中，再將陣列指派為 <xref:System.Drawing.Pen> 物件的 <xref:System.Drawing.Pen.DashPattern%2A> 屬性值。  下列範例根據 `{5, 2, 15, 4}` 陣列繪製出一條自訂短折線。  如果您將該陣列元素乘以畫筆寬度 5，可得 `{25, 10, 75, 20}`。  顯示的虛線長度會在 25 和 75 之間交替，空格長度會在 10 和 20 之間交替。  
  
 下圖顯示的是產生的短折線。  請注意，最後的虛線必須小於 25 個單位，線條才能結束在 \(405, 5\) 的位置。  
  
 ![畫筆](../../../../docs/framework/winforms/advanced/media/pens6.png "pens6")  
  
 [!code-csharp[System.Drawing.UsingAPen#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.UsingAPen#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#51)]  
  
## 編譯程式碼  
 建立 Windows Form 並處理該表單的 <xref:System.Windows.Forms.Control.Paint> 事件。  將上述程式碼貼至 <xref:System.Windows.Forms.Control.Paint> 事件處理常式中。  
  
## 請參閱  
 [使用畫筆繪製線條和形狀](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
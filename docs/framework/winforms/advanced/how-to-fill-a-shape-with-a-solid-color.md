---
title: "如何：使用純色填滿形狀 | Microsoft Docs"
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
  - "色彩, 加入到圖案"
  - "圖案, 填滿"
ms.assetid: 06088b31-bac9-4ef3-9ebe-06c2c764d6df
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：使用純色填滿形狀
若要使用純色填滿形狀，請建立 <xref:System.Drawing.SolidBrush> 物件，然後將這個 <xref:System.Drawing.SolidBrush> 物件當成引數傳遞至 <xref:System.Drawing.Graphics> 類別的其中一個填色方法。  下列範例顯示如何使用紅色填滿橢圓形。  
  
## 範例  
 在下列程式碼中，<xref:System.Drawing.SolidBrush.%23ctor%2A> 建構函式使用 <xref:System.Drawing.Color> 物件當做其唯一引數。  <xref:System.Drawing.Color.FromArgb%2A> 方法所使用的值代表色彩的 Alpha、紅色、綠色和藍色元素。  每一個值的範圍都必須介於 0 到 255 之間。  第一個 255 表示該色彩完全不透明，第二個 255 表示紅色元素的濃度達最高。  兩個零代表綠色和藍色兩個元素的濃度都是 0。  
  
 傳遞至 <xref:System.Drawing.Graphics.FillEllipse%2A> 方法的四個數字 \(0, 0, 100, 60\) 分別指定橢圓形的位置和其週框 \(Bounding Rectangle\) 大小。  矩形的左上角位於 \(0, 0\)，寬度為 100，高度為 60。  
  
 [!code-csharp[System.Drawing.UsingABrush#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingABrush#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#11)]  
  
## 編譯程式碼  
 上述範例是專為與 Windows Form 搭配使用而設計的，而且它需要 <xref:System.Windows.Forms.PaintEventArgs> `e` \(即 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數\)。  
  
## 請參閱  
 [使用筆刷填滿形狀](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
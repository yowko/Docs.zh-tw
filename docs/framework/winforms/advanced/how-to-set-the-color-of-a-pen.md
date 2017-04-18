---
title: "如何：設定畫筆顏色 | Microsoft Docs"
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
  - "色筆"
  - "畫筆, 設定色彩"
ms.assetid: a9df06f9-a6d5-4d9b-a2d1-583943540775
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：設定畫筆顏色
這個範例可變更已存在之 <xref:System.Drawing.Pen> 物件的色彩。  
  
## 範例  
 [!code-cpp[System.Drawing.ConceptualHowTos#9](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#9)]
 [!code-csharp[System.Drawing.ConceptualHowTos#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#9)]
 [!code-vb[System.Drawing.ConceptualHowTos#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#9)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   名為 `myPen` 的 <xref:System.Drawing.Pen> 物件。  
  
## 穩固程式設計  
 在結束使用消耗系統資源的物件後 \(例如 <xref:System.Drawing.Pen> 物件\)，您應一律呼叫物件的 <xref:System.Drawing.Pen.Dispose%2A>。  
  
## 請參閱  
 <xref:System.Drawing.Pen>   
 [圖形程式設計入門](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)   
 [如何：建立畫筆](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)   
 [使用畫筆繪製線條和形狀](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)   
 [GDI\+ 中的畫筆、線條和矩形](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)
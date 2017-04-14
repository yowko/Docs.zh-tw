---
title: "如何：建立具圖案的 Windows Form | Microsoft Docs"
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
  - "表單, 變更圖案"
  - "表單, 循環"
  - "表單, 自訂形狀"
  - "表單, 非矩形"
  - "表單, 圓角"
  - "具圖案的表單"
  - "Windows Form, 循環"
  - "Windows Form, 自訂形狀"
  - "Windows Form, 非矩形的圖案"
  - "Windows Form, 圓角"
  - "Windows Form, 具圖案"
ms.assetid: 6e6041e0-8e67-4487-b1e9-e410dbd1ef6c
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：建立具圖案的 Windows Form
這個範例使表單具有橢圓形狀，而該圖案會隨表單調整大小。  
  
## 範例  
 [!code-cpp[System.Drawing.ConceptualHowTos#10](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#10)]
 [!code-csharp[System.Drawing.ConceptualHowTos#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#10)]
 [!code-vb[System.Drawing.ConceptualHowTos#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#10)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   <xref:System.Windows.Forms> 和 <xref:System.Drawing> 命名空間的參考。  
  
 這個範例覆寫 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法來變更表單圖案。  若要使用這個程式碼，請複製方法宣告及方法內部的繪圖程式碼。  
  
## 請參閱  
 <xref:System.Windows.Forms.Control.OnPaint%2A>   
 <xref:System.Drawing.Region>   
 <xref:System.Drawing>   
 <xref:System.Drawing.Drawing2D.GraphicsPath.AddEllipse%2A>   
 <xref:System.Windows.Forms.Control.Region%2A>   
 [圖形程式設計入門](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)
---
title: "如何：建立實心筆刷 | Microsoft Docs"
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
  - "筆刷, 建立實心"
  - "筆刷, 範例"
  - "純色筆刷"
ms.assetid: 85c3fe7d-fb1d-4591-8a9f-d75b556b90af
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：建立實心筆刷
這個範例會建立 <xref:System.Drawing.SolidBrush> 物件，<xref:System.Drawing.Graphics> 物件可以使用這個物件來填滿圖案。  
  
## 範例  
 [!code-cpp[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#1)]
 [!code-csharp[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#1)]
 [!code-vb[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#1)]  
  
## 穩固程式設計  
 用完物件之後，您應該對任何使用系統資源的物件 \(如筆刷物件\) 呼叫 <xref:System.IDisposable.Dispose%2A>。  
  
## 請參閱  
 <xref:System.Drawing.SolidBrush>   
 <xref:System.Drawing.Brush>   
 [圖形程式設計入門](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)   
 [GDI\+ 中的筆刷和填滿的形狀](../../../../docs/framework/winforms/advanced/brushes-and-filled-shapes-in-gdi.md)   
 [使用筆刷填滿形狀](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
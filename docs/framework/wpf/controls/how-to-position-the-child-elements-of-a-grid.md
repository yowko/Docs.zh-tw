---
title: "如何：置放 Grid 的子項目 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Grid 控制項, 定位子項目"
ms.assetid: 27b3ba9b-ad32-44e2-bcab-a79d573a463c
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：置放 Grid 的子項目
本範例示範如何使用 <xref:System.Windows.Controls.Grid> 上定義的 Get 和 Set 方法，以置放子項目。  
  
## 範例  
 下列範例定義具有三個資料行和三個資料列的父 <xref:System.Windows.Controls.Grid> 項目 \(`grid1`\)。  將子 <xref:System.Windows.Shapes.Rectangle> 項目 \(`rect1`\) 加入至資料行位置零和資料列位置零中的 <xref:System.Windows.Controls.Grid>。  <xref:System.Windows.Controls.Button> 項目表示可呼叫的方法，以便在 <xref:System.Windows.Controls.Grid> 中重新置放 <xref:System.Windows.Shapes.Rectangle> 項目。  當使用者按一下按鈕時，就會啟動相關方法。  
  
 [!code-xml[gridGetSetMethods#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml#1)]  
  
 下列程式碼後置範例處理按鈕 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件所引發的方法。  此範例將這些方法呼叫寫入 <xref:System.Windows.Controls.TextBlock> 項目，此項目使用相關的 Get 方法將新的屬性值輸出為字串。  
  
 [!code-csharp[gridGetSetMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
  
## 請參閱  
 <xref:System.Windows.Controls.Grid>   
 [面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)
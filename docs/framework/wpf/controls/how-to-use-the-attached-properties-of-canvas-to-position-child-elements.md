---
title: "如何：使用 Canvas 的附加屬性置放子項目 | Microsoft Docs"
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
  - "附加屬性 [WPF 設計工具]"
  - "Canvas 控制項, 附加屬性"
ms.assetid: 48f1d25d-3820-4107-a4cc-d6c1e5664a44
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：使用 Canvas 的附加屬性置放子項目
本範例示範如何使用 <xref:System.Windows.Controls.Canvas> 的[附加屬性](GTMT)來置放子項目。  
  
## 範例  
 下列範例加入四個 <xref:System.Windows.Controls.Button> 項目，做為父代 <xref:System.Windows.Controls.Canvas> 的子項目。  每個子項目分別代表 <xref:System.Windows.Controls.Canvas>: <xref:System.Windows.Controls.Canvas.Bottom%2A>、<xref:System.Windows.Controls.Canvas.Left%2A>、<xref:System.Windows.Controls.Canvas.Right%2A> 和 <xref:System.Windows.Controls.Canvas.Top%2A> 的不同附加屬性。  每個 <xref:System.Windows.Controls.Button> 的放置位置都是對相於父代 <xref:System.Windows.Controls.Canvas> 的位置，而且是根據其指定的屬性值來放置。  
  
 [!code-cpp[CanvasAttachedProperties#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/CanvasAttachedProperties/CPP/CanvasAttachedProps.cpp#1)]
 [!code-csharp[CanvasAttachedProperties#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasAttachedProperties/CSharp/CanvasAttachedProps.cs#1)]
 [!code-vb[CanvasAttachedProperties#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasAttachedProperties/VisualBasic/CanvasAttachedProps.vb#1)]  
  
## 請參閱  
 <xref:System.Windows.Controls.Canvas>   
 <xref:System.Windows.Controls.Canvas.Bottom%2A>   
 <xref:System.Windows.Controls.Canvas.Left%2A>   
 <xref:System.Windows.Controls.Canvas.Right%2A>   
 <xref:System.Windows.Controls.Canvas.Top%2A>   
 <xref:System.Windows.Controls.Button>   
 [面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/controls/canvas-how-to-topics.md)   
 [附加屬性概觀](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)
---
title: "如何：取得唯讀 Freezable 的可寫入複本 | Microsoft Docs"
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
  - "複製 Freezable 物件"
  - "Freezable 物件, 可修改的複製品"
ms.assetid: d028de61-bbe9-4d62-b656-8fe3b1b2ca24
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 如何：取得唯讀 Freezable 的可寫入複本
本範例說明如何使用 <xref:System.Windows.Freezable.Clone%2A> 方法建立唯讀 <xref:System.Windows.Freezable> 的可寫入複本。  
  
 <xref:System.Windows.Freezable> 物件標示為唯讀 \(「凍結」\) 後就無法修改。  不過，您可以使用 <xref:System.Windows.Freezable.Clone%2A> 方法，建立凍結物件的可修改複本。  
  
## 範例  
 下列範例會建立凍結 <xref:System.Windows.Media.SolidColorBrush> 物件的可修改複本。  
  
 [!code-csharp[freezablesample_procedural#CloneExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
 [!code-vb[freezablesample_procedural#CloneExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]  
  
 如需 <xref:System.Windows.Freezable> 物件的詳細資訊，請參閱 [Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)。  
  
## 請參閱  
 <xref:System.Windows.Freezable>   
 <xref:System.Windows.Freezable.CloneCurrentValue%2A>   
 [Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
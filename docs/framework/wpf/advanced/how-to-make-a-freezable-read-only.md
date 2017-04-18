---
title: "如何：建立 Freezable 唯讀 | Microsoft Docs"
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
  - "Freezable 物件, 使成為唯讀"
ms.assetid: 6c544b7d-d3c9-4736-aa90-4b8728234ccb
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 如何：建立 Freezable 唯讀
本範例說明如何呼叫 <xref:System.Windows.Freezable> 的 <xref:System.Windows.Freezable.Freeze%2A> 方法，將它設為唯讀。  
  
 若 <xref:System.Windows.Freezable> 物件的下列任一條件為 `true`，就不能凍結該物件：  
  
-   具有顯示為動畫或資料繫結屬性。  
  
-   具有動態資源設定的屬性。  如需動態資源的詳細資訊，請參閱[XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)。  
  
-   包含無法凍結的 <xref:System.Windows.Freezable> 子物件。  
  
 如果 <xref:System.Windows.Freezable> 物件的上述條件都為 `false`，而您也不打算修改它，可以考慮予以凍結來提升效能。  
  
## 範例  
 下列範例會凍結屬於 <xref:System.Windows.Freezable> 物件類型的 <xref:System.Windows.Media.SolidColorBrush>。  
  
 [!code-csharp[freezablesample_procedural#FreezeExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#freezeexample1)]
 [!code-vb[freezablesample_procedural#FreezeExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#freezeexample1)]  
  
 如需 <xref:System.Windows.Freezable> 物件的詳細資訊，請參閱 [Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)。  
  
## 請參閱  
 <xref:System.Windows.Freezable>   
 <xref:System.Windows.Freezable.CanFreeze%2A>   
 <xref:System.Windows.Freezable.Freeze%2A>   
 [Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
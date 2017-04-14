---
title: "如何：對 Visual 中的幾何進行點擊測試 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Geometry 物件, 視覺物件構成"
  - "點擊測試, 對 Geometry 物件構成的視覺物件"
  - "視覺物件, 點擊測試"
ms.assetid: 8bf2643f-d7f9-4cb4-9ea6-5b893c23200d
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：對 Visual 中的幾何進行點擊測試
本範例示範如何在由一個或多個 <xref:System.Windows.Media.Geometry> 物件組成的視覺物件上執行[點擊測試](GTMT) \(Hit Test\)。  
  
## 範例  
 下列範例示範如何從使用 <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> 方法的視覺物件擷取 <xref:System.Windows.Media.DrawingGroup>。  接著在 <xref:System.Windows.Media.DrawingGroup> 中每個繪圖的呈現內容上執行點擊測試，以確定點擊的幾何圖案。  
  
> [!NOTE]
>  在大部分的情況下，您都可以使用 <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> 方法，判斷某個點是否與視覺項目的任何呈現內容交集。  
  
 [!code-csharp[VisualsOverview#VisualsOverviewSnippet4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#visualsoverviewsnippet4)]
 [!code-vb[VisualsOverview#VisualsOverviewSnippet4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#visualsoverviewsnippet4)]  
  
 <xref:System.Windows.Media.Geometry.FillContains%2A> 方法是一種多載方法，可以讓您使用指定的 <xref:System.Windows.Point> 或 <xref:System.Windows.Media.Geometry> 進行點擊測試。  如果為幾何圖案描邊，描邊部分可能會超出填色週框。  在這種情況下，除了 <xref:System.Windows.Media.Geometry.FillContains%2A> 之外，您可能還需要呼叫 <xref:System.Windows.Media.Geometry.StrokeContains%2A>。  
  
 您也可以提供 <xref:System.Windows.Media.ToleranceType>，以達到貝茲簡維化的目的。  
  
> [!NOTE]
>  這個範例並未考慮幾何圖案上可能套用的任何轉換或裁剪設定。  此外，此範例也不會使用樣式控制項，因為它沒有任何與其直接關聯的繪圖。  
  
## 請參閱  
 [視覺分層中的點擊測試](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)   
 [使用幾何當做參數進行點擊測試](../../../../docs/framework/wpf/graphics-multimedia/how-to-hit-test-using-geometry-as-a-parameter.md)
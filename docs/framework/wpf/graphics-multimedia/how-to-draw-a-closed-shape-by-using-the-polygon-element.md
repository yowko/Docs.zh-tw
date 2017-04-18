---
title: "如何：使用 Polygon 項目繪製封閉的形狀 | Microsoft Docs"
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
  - "封閉形狀, 使用 Polygon 項目繪製"
  - "繪製, 使用 Polygon 項目的封閉形狀"
  - "圖形, Polygon 項目"
  - "Polygon 項目"
ms.assetid: 4b0ca008-29ce-48dd-8bc3-f3a20ffca6a6
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 如何：使用 Polygon 項目繪製封閉的形狀
本範例說明如何使用 <xref:System.Windows.Shapes.Polygon> 項目繪製封閉的形狀。  若要繪製封閉的形狀，請建立 <xref:System.Windows.Shapes.Polygon> 項目，使用其 <xref:System.Windows.Shapes.Polygon.Points%2A> 屬性指定形狀的頂點。  起點和終點之間會自動繪製一條線連接兩點。  最後，指定 <xref:System.Windows.Shapes.Shape.Fill%2A>、<xref:System.Windows.Shapes.Shape.Stroke%2A> 或兩者都指定。  
  
## 範例  
 在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 中，有效的點語法是以空格分隔的 X 和 Y 座標配對 \(中間以逗號分隔\) 清單。  
  
 [!code-xml[drawingwithshapeelements#PolygonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polygonexample.xaml#polygonexample1)]  
  
 雖然本範例使用 <xref:System.Windows.Controls.Canvas> 包含多邊形，不過您可以將多邊形項目 \(以及所有其他圖案項目\) 與任何支援非文字內容的 <xref:System.Windows.Controls.Panel> 或 <xref:System.Windows.Controls.Control> 使用。  
  
 這個範例是完整範例的一部分。如需完整範例，請參閱[圖案項目範例](http://go.microsoft.com/fwlink/?LinkID=160037) \(英文\)。
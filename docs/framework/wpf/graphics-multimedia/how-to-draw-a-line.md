---
title: "如何：繪製線條 | Microsoft Docs"
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
  - "繪製, 線條"
  - "圖形 [WPF], 線條"
  - "線條, 繪製"
ms.assetid: 0513ee01-6b27-4bb3-85f3-3a3e6710d80e
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 如何：繪製線條
本範例說明如何使用 <xref:System.Windows.Shapes.Line> 項目來繪製線條。  
  
 若要繪製線條，請建立 <xref:System.Windows.Shapes.Line> 項目。  使用它的 <xref:System.Windows.Shapes.Line.X1%2A> 和 <xref:System.Windows.Shapes.Line.Y1%2A> 屬性來設定起始點，然後使用它的 <xref:System.Windows.Shapes.Line.X2%2A> 和 <xref:System.Windows.Shapes.Line.Y2%2A> 屬性來設定結束點。  最後，設定它的 <xref:System.Windows.Shapes.Shape.Stroke%2A> 和 <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>，因為如果線條沒有筆劃，就無法顯示出來。  
  
 設定線條的 <xref:System.Windows.Shapes.Shape.Fill%2A> 項目並沒有作用，因為線條沒有內部。  
  
 下列範例會在 <xref:System.Windows.Controls.Canvas> 項目中繪製三條線。  
  
## 範例  
 [!code-xml[drawingwithshapeelements#LineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 這個範例是完整範例的一部分。如需完整範例，請參閱[圖案項目範例](http://go.microsoft.com/fwlink/?LinkID=160037) \(英文\)。  
  
## 請參閱  
 <xref:System.Windows.Shapes.Line>   
 [圖案項目範例](http://go.microsoft.com/fwlink/?LinkID=160037)
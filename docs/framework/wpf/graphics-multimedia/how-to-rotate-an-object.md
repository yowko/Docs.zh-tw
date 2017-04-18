---
title: "如何：旋轉物件 | Microsoft Docs"
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
  - "圖形, 旋轉物件"
  - "旋轉物件"
ms.assetid: ee3466cd-e66f-4e8f-8a5a-71d77bc1e390
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：旋轉物件
本範例說明如何旋轉物件。  此範例會先建立 <xref:System.Windows.Media.RotateTransform>，然後設定其 <xref:System.Windows.Media.RotateTransform.Angle%2A> 的角度。  
  
 下列範例會以左上角為準，旋轉 <xref:System.Windows.Shapes.Polyline> 物件 45 度。  
  
## 範例  
 [!code-xml[Transforms_snip#RotatePolylineAboutTopLeft](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineabouttopleft)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineabouttopleft)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineabouttopleft)]  
  
 <xref:System.Windows.Media.RotateTransform> 的 <xref:System.Windows.Media.RotateTransform.CenterX%2A> 和 <xref:System.Windows.Media.RotateTransform.CenterY%2A> 屬性會指定旋轉物件所依據的中心點。  此中心點會以轉換項目的座標空間表示。  根據預設，旋轉會以 \(0,0\) 為準，也就是要轉換之物件的左上角。  
  
 下面的範例會以點 \(25,50\) 為準，順時針旋轉 <xref:System.Windows.Shapes.Polyline> 物件 45 度。  
  
 [!code-xml[Transforms_snip#RotatePolylineAboutCenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineaboutcenter)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutCenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineaboutcenter)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutCenter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineaboutcenter)]  
  
 下圖顯示將 <xref:System.Windows.Media.Transform> 套用到兩個物件的結果。  
  
 ![採用不同中心點的 45 度旋轉](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-rotatetransform45degrees.png "wcpsdk\_graphicsmm\_rotatetransform45degrees")  
從不同的旋轉中心旋轉 45 度的兩個物件  
  
 前述範例中的 <xref:System.Windows.Shapes.Polyline> 是一個 <xref:System.Windows.UIElement>。  當您將 <xref:System.Windows.Media.Transform> 套用到 <xref:System.Windows.UIElement> 的 <xref:System.Windows.UIElement.RenderTransform%2A> 屬性，可以使用 <xref:System.Windows.UIElement.RenderTransformOrigin%2A> 屬性指定要套用到項目的每個 <xref:System.Windows.Media.Transform> 的原點。  由於 <xref:System.Windows.UIElement.RenderTransformOrigin%2A> 屬性使用相對座標，即使不知道項目的大小，也能將轉換套用到項目的中心。  如需詳細資訊和範例，請參閱 [使用相對值指定轉換的原點](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-the-origin-of-a-transform-by-using-relative-values.md)。  
  
 如需完整範例，請參閱 [2D 轉換範例](http://go.microsoft.com/fwlink/?LinkID=158252) \(英文\)。  
  
## 請參閱  
 <xref:System.Windows.Media.Transform>   
 [轉換概觀](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
---
title: "如何：沿著路徑建立物件的動畫 (Double 動畫) | Microsoft Docs"
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
  - "沿著路徑 （雙動畫） 建立物件的動畫"
  - "雙動畫"
ms.assetid: 5a3c4a99-f303-42ad-a52a-e4794bb1798e
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：沿著路徑建立物件的動畫 (Double 動畫)
這個範例示範如何使用<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>移動物件沿著路徑所定義的類別<xref:System.Windows.Media.PathGeometry>。  
  
## <a name="example"></a>範例  
 下列範例會使用兩個<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>物件來移動矩形幾何的路徑︰  
  
-   第一個<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>動畫<xref:System.Windows.Media.TranslateTransform.X%2A>的<xref:System.Windows.Media.TranslateTransform>套用至矩形。 它會讓矩形沿著路徑水平移動。  
  
-   第二個<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>動畫<xref:System.Windows.Media.TranslateTransform.Y%2A>的<xref:System.Windows.Media.TranslateTransform>套用至矩形。 它會讓矩形沿著路徑垂直移動。  
  
 [!code-xml[PathAnimationGallery_snippet#DoubleAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/doubleanimationusingpathexample.xaml#doubleanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/DoubleAnimationUsingPathExample.cs#doubleanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/DoubleAnimationUsingPathExample.vb#doubleanimationusingpathwholepage)]  
  
 如需完整的範例，請參閱[路徑動畫範例](http://go.microsoft.com/fwlink/?LinkID=160028)。  
  
 使用幾何路徑移動物件的另一種方式是使用<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>物件。 如需範例，請參閱[製作動畫物件沿著路徑動畫 （矩陣動畫）](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md)。  
  
## <a name="see-also"></a>另請參閱  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [路徑動畫 how to 主題](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
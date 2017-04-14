---
title: "如何：沿著路徑建立物件的動畫 (點動畫) | Microsoft Docs"
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
  - "沿著路徑動畫 （點動畫） 建立物件的動畫"
  - "點動畫"
ms.assetid: 1fa3f817-35bc-41a1-b366-f5a20b70da0c
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 如何：沿著路徑建立物件的動畫 (點動畫)
這個範例示範如何使用<xref:System.Windows.Media.Animation.PointAnimationUsingPath>物件來建立動畫<xref:System.Windows.Point>沿著曲線的路徑。  
  
## <a name="example"></a>範例  
 下列範例會將<xref:System.Windows.Media.EllipseGeometry>沿著路徑所定義<xref:System.Windows.Media.PathGeometry>。 橢圓形幾何<xref:System.Windows.Media.EllipseGeometry.Center%2A>屬性，其中需要<xref:System.Windows.Point>值，指定其位置; 移動橢圓形幾何，您以動畫顯示其<xref:System.Windows.Media.EllipseGeometry.Center%2A>屬性。 此範例會使用<xref:System.Windows.Media.Animation.PointAnimationUsingPath>動畫<xref:System.Windows.Media.EllipseGeometry>物件的<xref:System.Windows.Media.EllipseGeometry.Center%2A>屬性。  
  
 [!code-xml[PathAnimationGallery_snippet#PointAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/pointanimationusingpathexample.xaml#pointanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/PointAnimationUsingPathExample.cs#pointanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/PointAnimationUsingPathExample.vb#pointanimationusingpathwholepage)]  
  
 如需完整的範例，請參閱[路徑動畫範例](http://go.microsoft.com/fwlink/?LinkID=160028)。  
  
 上述範例中使用的程式碼版本<xref:System.Windows.Media.Animation.Storyboard>動畫<xref:System.Windows.Media.EllipseGeometry>，即使只有一個動畫已套用。 A<xref:System.Windows.Media.Animation.Storyboard>通常是最簡單的方式套用多個動畫，因為這些動畫可以控制相同<xref:System.Windows.Media.Animation.Storyboard>。 不過，使用程式碼時，單一動畫套用至屬性的簡單方法是使用<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>方法。 如需範例，請參閱[屬性而不使用腳本建立動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)。  
  
## <a name="see-also"></a>另請參閱  
 [路徑動畫範例](http://go.microsoft.com/fwlink/?LinkID=160028)   
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [路徑動畫 how to 主題](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
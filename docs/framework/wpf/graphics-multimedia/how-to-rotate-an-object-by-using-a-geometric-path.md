---
title: "如何：使用幾何路徑旋轉物件 | Microsoft Docs"
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
  - "幾何路徑旋轉物件方式"
  - "使用幾何路徑旋轉物件"
ms.assetid: cb31ca4d-f05a-4c6b-9a18-4b6faaf38d45
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 如何：使用幾何路徑旋轉物件
這個範例示範如何旋轉物件所定義的幾何路徑沿著<xref:System.Windows.Media.PathGeometry>物件。  
  
## <a name="example"></a>範例  
 下列範例會使用三個<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>物件來移動矩形幾何的路徑。  
  
-   第一個<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>動畫<xref:System.Windows.Media.RotateTransform>套用至矩形。 動畫會產生角度值。 它會讓矩形旋轉沿著路徑的輪廓。  
  
-   建立兩個物件的動畫<xref:System.Windows.Media.TranslateTransform.X%2A>和<xref:System.Windows.Media.TranslateTransform.Y%2A>值<xref:System.Windows.Media.TranslateTransform>套用至矩形。 這會讓水平和垂直移動路徑上的矩形。  
  
 [!code-xml[PathAnimationGallery_snippet#RotateAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/rotateanimationusingpathexample.xaml#rotateanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/RotateAnimationUsingPathExample.cs#rotateanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/RotateAnimationUsingPathExample.vb#rotateanimationusingpathwholepage)]  
  
 使用幾何路徑旋轉物件的另一種方式是使用<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>物件，並設定其<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A>屬性`true`。 如需詳細資訊和範例，請參閱[旋轉物件使用幾何路徑動畫 （矩陣動畫）](../../../../docs/framework/wpf/graphics-multimedia/how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md)。  
  
 如需完整的範例，請參閱[路徑動畫範例](http://go.microsoft.com/fwlink/?LinkID=160028)。  
  
## <a name="see-also"></a>另請參閱  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [路徑動畫範例](http://go.microsoft.com/fwlink/?LinkID=160028)   
 [路徑動畫 how to 主題](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
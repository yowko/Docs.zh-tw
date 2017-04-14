---
title: "如何：沿著路徑建立物件的動畫 (矩陣動畫) | Microsoft Docs"
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
  - "沿著路徑動畫 （矩陣動畫） 建立物件的動畫"
  - "矩陣動畫"
ms.assetid: 7000e697-1414-468c-b915-cf66062fc49e
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 如何：沿著路徑建立物件的動畫 (矩陣動畫)
這個範例示範如何使用<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>類別來建立物件沿著路徑所定義的<xref:System.Windows.Media.PathGeometry>。  
  
## <a name="example"></a>範例  
 下列範例會沿著路徑的物件執行下列動作︰  
  
-   適用於<xref:System.Windows.Media.MatrixTransform>以移動物件。  
  
-   使用定義的路徑<xref:System.Windows.Media.PathGeometry>。  
  
-   建立<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>並用它來建立動畫<xref:System.Windows.Media.Matrix>屬性<xref:System.Windows.Media.MatrixTransform>。 <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>採用<xref:System.Windows.Media.PathGeometry> ，並用它來產生<xref:System.Windows.Media.Matrix>值。  
  
 [!code-xml[PathAnimationGallery_snippet#MatrixAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexample.xaml#matrixanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExample.cs#matrixanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExample.vb#matrixanimationusingpathwholepage)]  
  
 如需完整的範例，請參閱[路徑動畫範例](http://go.microsoft.com/fwlink/?LinkID=160028)。 如需幾何路徑的詳細資訊，請參閱[幾何概觀](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)。  
  
## <a name="see-also"></a>另請參閱  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [路徑動畫範例](http://go.microsoft.com/fwlink/?LinkID=160028)   
 [路徑動畫 how to 主題](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
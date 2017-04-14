---
title: "如何：使用幾何路徑旋轉物件 (矩陣動畫) | Microsoft Docs"
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
  - "矩陣動畫"
ms.assetid: 877dc9aa-6bdc-4beb-8772-3efaec32c0f0
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：使用幾何路徑旋轉物件 (矩陣動畫)
這個範例示範如何使用<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>和<xref:System.Windows.Media.MatrixTransform>來旋轉物件所定義的幾何路徑沿著<xref:System.Windows.Media.PathGeometry>物件。  
  
## <a name="example"></a>範例  
 下列範例會使用<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>物件來建立動畫<xref:System.Windows.Media.MatrixTransform.Matrix%2A>屬性<xref:System.Windows.Media.MatrixTransform>。 <xref:System.Windows.Media.MatrixTransform>套用至按鈕，因而會沿著曲線路徑移動。 因為<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A>屬性設定為`true`，矩形就會旋轉沿著路徑的正切函數。  
  
 [!code-xml[PathAnimationGallery_snippet#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathdoesrotatewithtangentexample.xaml#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathDoesRotateWithTangentExample.cs#matrixanimationusingpathdoesrotatewithtangentwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathDoesRotateWithTangentExample.vb#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 如需完整的範例，請參閱[路徑動畫範例](http://go.microsoft.com/fwlink/?LinkID=160028)。  
  
 上述範例中使用的程式碼版本<xref:System.Windows.Media.Animation.Storyboard>動畫<xref:System.Windows.Media.EllipseGeometry>，即使只有一個動畫已套用。 單一動畫套用於程式碼中屬性的簡單方法是使用<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>方法。 如需範例，請參閱[屬性而不使用腳本建立動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)。  
  
## <a name="see-also"></a>另請參閱  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [路徑動畫 how to 主題](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)   
 [路徑動畫範例](http://go.microsoft.com/fwlink/?LinkID=160028)
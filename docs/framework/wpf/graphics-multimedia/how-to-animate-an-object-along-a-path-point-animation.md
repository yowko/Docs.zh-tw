---
title: "操作說明：沿著路徑建立物件的動畫 (點動畫)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (point animation)
- point animation [WPF]
ms.assetid: 1fa3f817-35bc-41a1-b366-f5a20b70da0c
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 47cafab505bcbab7008385393bbacf093e264cd9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-an-object-along-a-path-point-animation"></a>操作說明：沿著路徑建立物件的動畫 (點動畫)
這個範例示範如何使用<xref:System.Windows.Media.Animation.PointAnimationUsingPath>要繪製動畫物件<xref:System.Windows.Point>沿著曲線的路徑。  
  
## <a name="example"></a>範例  
 下列範例會移動<xref:System.Windows.Media.EllipseGeometry>沿著路徑所定義<xref:System.Windows.Media.PathGeometry>。 橢圓形的幾何<xref:System.Windows.Media.EllipseGeometry.Center%2A>屬性，其中需要<xref:System.Windows.Point>值，指定其位置; 將橢圓形的幾何，您以動畫顯示其<xref:System.Windows.Media.EllipseGeometry.Center%2A>屬性。 此範例會使用<xref:System.Windows.Media.Animation.PointAnimationUsingPath>以動畫方式顯示<xref:System.Windows.Media.EllipseGeometry>物件的<xref:System.Windows.Media.EllipseGeometry.Center%2A>屬性。  
  
 [!code-xaml[PathAnimationGallery_snippet#PointAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/pointanimationusingpathexample.xaml#pointanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/PointAnimationUsingPathExample.cs#pointanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/PointAnimationUsingPathExample.vb#pointanimationusingpathwholepage)]  
  
 如需完整範例，請參閱[路徑動畫範例](http://go.microsoft.com/fwlink/?LinkID=160028)。  
  
 使用上述範例的程式碼版本<xref:System.Windows.Media.Animation.Storyboard>以動畫方式顯示<xref:System.Windows.Media.EllipseGeometry>，即使只有一個動畫已套用。 A<xref:System.Windows.Media.Animation.Storyboard>通常是最簡單的方式套用多個動畫，因為這些動畫可以控制相同<xref:System.Windows.Media.Animation.Storyboard>。 不過，使用程式碼時，單一的動畫套用至屬性的簡單方法是使用<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>方法。 如需範例，請參閱[不使用分鏡腳本而建立屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)。  
  
## <a name="see-also"></a>另請參閱  
 [路徑動畫範例](http://go.microsoft.com/fwlink/?LinkID=160028)  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [路徑動畫操作說明主題](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)

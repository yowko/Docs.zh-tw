---
title: "操作說明：使用幾何路徑旋轉物件"
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
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
ms.assetid: cb31ca4d-f05a-4c6b-9a18-4b6faaf38d45
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 078d1054f9b6a4c2f6172f00aa8c4ad9077e6db2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path"></a>操作說明：使用幾何路徑旋轉物件
這個範例示範如何旋轉物件所定義的幾何路徑沿著<xref:System.Windows.Media.PathGeometry>物件。  
  
## <a name="example"></a>範例  
 下列範例會使用三個<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>物件來移動矩形幾何的路徑。  
  
-   第一個<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>繪製<xref:System.Windows.Media.RotateTransform>套用至矩形。 動畫會產生角度值。 它會使矩形沿著路徑的輪廓旋轉 (繞樞軸轉動)。  
  
-   其他兩個物件以動畫顯示<xref:System.Windows.Media.TranslateTransform.X%2A>和<xref:System.Windows.Media.TranslateTransform.Y%2A>值<xref:System.Windows.Media.TranslateTransform>套用至矩形。 它們使矩形沿著路徑水平及垂直移動。  
  
 [!code-xaml[PathAnimationGallery_snippet#RotateAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/rotateanimationusingpathexample.xaml#rotateanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/RotateAnimationUsingPathExample.cs#rotateanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/RotateAnimationUsingPathExample.vb#rotateanimationusingpathwholepage)]  
  
 使用幾何路徑旋轉物件的另一種方式是使用<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>物件，並設定其<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A>屬性`true`。 如需詳細資訊和範例，請參閱[旋轉物件使用幾何的路徑 （矩陣動畫）](../../../../docs/framework/wpf/graphics-multimedia/how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md)。  
  
 如需完整範例，請參閱[路徑動畫範例](http://go.microsoft.com/fwlink/?LinkID=160028)。  
  
## <a name="see-also"></a>另請參閱  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [路徑動畫範例](http://go.microsoft.com/fwlink/?LinkID=160028)  
 [路徑動畫操作說明主題](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)

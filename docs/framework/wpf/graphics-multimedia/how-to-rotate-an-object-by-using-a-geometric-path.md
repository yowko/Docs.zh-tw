---
title: HOW TO：使用幾何路徑旋轉物件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
ms.assetid: cb31ca4d-f05a-4c6b-9a18-4b6faaf38d45
ms.openlocfilehash: 3e35169da7297ec62e0114ab21f4ba81c0a656ea
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59229208"
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path"></a>HOW TO：使用幾何路徑旋轉物件
此範例顯示如何旋轉 (powerpivot) 沿著幾何路徑所定義的物件<xref:System.Windows.Media.PathGeometry>物件。  
  
## <a name="example"></a>範例  
 下列範例使用三個<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>物件來沿著幾何路徑移動矩形。  
  
-   第一個<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>繪製<xref:System.Windows.Media.RotateTransform>套用至矩形。 動畫會產生角度值。 它會使矩形沿著路徑的輪廓旋轉 (繞樞軸轉動)。  
  
-   其他兩個物件建立動畫<xref:System.Windows.Media.TranslateTransform.X%2A>並<xref:System.Windows.Media.TranslateTransform.Y%2A>的值<xref:System.Windows.Media.TranslateTransform>套用至矩形。 它們使矩形沿著路徑水平及垂直移動。  
  
 [!code-xaml[PathAnimationGallery_snippet#RotateAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/rotateanimationusingpathexample.xaml#rotateanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/RotateAnimationUsingPathExample.cs#rotateanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/RotateAnimationUsingPathExample.vb#rotateanimationusingpathwholepage)]  
  
 使用幾何路徑旋轉物件的另一種方式是使用<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>物件，並設定其<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A>屬性設`true`。 如需詳細資訊和範例，請參閱 <<c0> [ 旋轉物件使用幾何路徑動畫 （矩陣動畫）](how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md)。  
  
 如需完整的範例，請參閱[路徑動畫範例](https://go.microsoft.com/fwlink/?LinkID=160028)。  
  
## <a name="see-also"></a>另請參閱

- [動畫概觀](animation-overview.md)
- [路徑動畫範例](https://go.microsoft.com/fwlink/?LinkID=160028)
- [路徑動畫操作說明主題](path-animation-how-to-topics.md)

---
title: 操作說明：使用幾何路徑旋轉物件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
ms.assetid: cb31ca4d-f05a-4c6b-9a18-4b6faaf38d45
ms.openlocfilehash: a351fdc936f634b7c57ba5a49e51501f7572a3c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186868"
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path"></a>操作說明：使用幾何路徑旋轉物件
此示例演示如何沿<xref:System.Windows.Media.PathGeometry>由物件定義的幾何路徑旋轉（透視）物件。  
  
## <a name="example"></a>範例  
 下面的示例使用三<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>個物件沿幾何路徑移動矩形。  
  
- 第一<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>個<xref:System.Windows.Media.RotateTransform>動畫為應用於矩形的 。 動畫會產生角度值。 它會使矩形沿著路徑的輪廓旋轉 (繞樞軸轉動)。  
  
- 其他兩個物件為<xref:System.Windows.Media.TranslateTransform.X%2A>應用於<xref:System.Windows.Media.TranslateTransform.Y%2A>矩形的<xref:System.Windows.Media.TranslateTransform>和 值設置動畫。 它們使矩形沿著路徑水平及垂直移動。  
  
 [!code-xaml[PathAnimationGallery_snippet#RotateAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/rotateanimationusingpathexample.xaml#rotateanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/RotateAnimationUsingPathExample.cs#rotateanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/RotateAnimationUsingPathExample.vb#rotateanimationusingpathwholepage)]  
  
 使用幾何路徑旋轉物件的另一種方法是使用<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>物件並將其<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A>屬性設置為`true`。 有關詳細資訊和示例，請參閱[使用幾何路徑旋轉物件（矩陣動畫）。](how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md)  
  
 有關完整示例，請參閱[路徑動畫示例](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)。  
  
## <a name="see-also"></a>另請參閱

- [動畫概觀](animation-overview.md)
- [路徑動畫範例](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
- [路徑動畫操作說明主題](path-animation-how-to-topics.md)

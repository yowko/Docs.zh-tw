---
title: 操作說明：沿著路徑建立物件的動畫 (矩陣動畫)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (matrix animation)
- matrix animation [WPF]
ms.assetid: 7000e697-1414-468c-b915-cf66062fc49e
ms.openlocfilehash: 7dfc233fe60e1cea293edc44a2bba79dc6962f7c
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452905"
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation"></a>操作說明：沿著路徑建立物件的動畫 (矩陣動畫)
這個範例示範如何使用 <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> 類別，沿著 <xref:System.Windows.Media.PathGeometry>所定義的路徑建立物件的動畫。  
  
## <a name="example"></a>範例  
 下列範例會執行下列動作，沿著路徑以動畫顯示的物件︰  
  
- 將 <xref:System.Windows.Media.MatrixTransform> 套用至物件，以便移動。  
  
- 使用 <xref:System.Windows.Media.PathGeometry>定義路徑。  
  
- 建立 <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>，並使用它以動畫顯示 <xref:System.Windows.Media.MatrixTransform>的 <xref:System.Windows.Media.Matrix> 屬性。 <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> 會採用 <xref:System.Windows.Media.PathGeometry>，並使用它來產生 <xref:System.Windows.Media.Matrix> 值。  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexample.xaml#matrixanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExample.cs#matrixanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExample.vb#matrixanimationusingpathwholepage)]  
  
 如需完整範例，請參閱[路徑動畫範例](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)。 如需幾何路徑的詳細資訊，請參閱[幾何總覽](geometry-overview.md)。  
  
## <a name="see-also"></a>另請參閱

- [動畫概觀](animation-overview.md)
- [路徑動畫範例](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
- [路徑動畫操作說明主題](path-animation-how-to-topics.md)

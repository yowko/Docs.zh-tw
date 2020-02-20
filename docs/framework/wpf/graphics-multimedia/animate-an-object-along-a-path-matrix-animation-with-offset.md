---
title: 操作說明：沿著路徑建立物件的動畫 (具有位移累加的矩陣動畫)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- offset accumulation [WPF]
- animation [WPF], objects along paths (matrix animation with offset accumulation)
- matrix animation with offset accumulation [WPF]
ms.assetid: 1bca90ef-9832-4128-8ed6-62908e7ec146
ms.openlocfilehash: 8b3975ef5031b50381dfa9baf7f34a58fc05ab4e
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453100"
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation-with-offset-accumulation"></a>操作說明：沿著路徑建立物件的動畫 (具有位移累加的矩陣動畫)
這個範例示範如何使用 <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> 類別，沿著路徑建立物件的動畫，並讓動畫在重複時累積其位移值。  
  
## <a name="example"></a>範例  
 下列範例會使用 <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> 物件，以動畫顯示套用至按鈕之 <xref:System.Windows.Media.MatrixTransform> 的 <xref:System.Windows.Media.MatrixTransform.Matrix%2A> 屬性。 如此一來，按鈕會沿著曲線路徑移動。  
  
 此外，此範例會將 <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> 屬性設定為 `true`，這會在動畫重複時，讓動畫矩陣的位移累加。 因為位移會一直累積，所以按鈕會在動畫重複時逐漸橫越螢幕移動，而不是重設為起始位置。  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathOffsetCumulativeWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexampleoffsetcumulative.xaml#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExampleOffsetCumulative.cs#matrixanimationusingpathoffsetcumulativewholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExampleOffsetCumulative.vb#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 請注意，雖然 <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> 屬性會導致位移值在重複時累積，但不會導致旋轉值累積。 若要累積旋轉值，請將動畫的 <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> 和 <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsAngleCumulative%2A> 屬性設定為 [`true`]。  
  
 如需完整範例，請參閱[路徑動畫範例](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)。 如需示範如何在沒有位移累加的情況下，以動畫顯示 <xref:System.Windows.Media.Matrix> 值的範例，請參閱[沿著路徑建立物件的動畫（矩陣動畫）](how-to-animate-an-object-along-a-path-matrix-animation.md)。  
  
## <a name="see-also"></a>另請參閱

- [動畫概觀](animation-overview.md)
- [路徑動畫操作說明主題](path-animation-how-to-topics.md)

---
title: "操作說明：沿著路徑建立物件的動畫 (具有位移累加的矩陣動畫)"
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
- offset accumulation [WPF]
- animation [WPF], objects along paths (matrix animation with offset accumulation)
- matrix animation with offset accumulation [WPF]
ms.assetid: 1bca90ef-9832-4128-8ed6-62908e7ec146
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8a9fd282d3ca4603eadd0ed10436944f7e9ab593
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation-with-offset-accumulation"></a>操作說明：沿著路徑建立物件的動畫 (具有位移累加的矩陣動畫)
這個範例示範如何使用<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>類別建立動畫物件沿著路徑，然後讓動畫累積它的位移值的重複。  
  
## <a name="example"></a>範例  
 下列範例會使用<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>要繪製動畫物件<xref:System.Windows.Media.MatrixTransform.Matrix%2A>屬性<xref:System.Windows.Media.MatrixTransform>套用至按鈕。 如此一來，按鈕會沿著曲線路徑移動。  
  
 此外，此範例設定<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A>屬性`true`，因而導致在動畫重複時累加動畫矩陣的位移。 因為位移會一直累積，所以按鈕會在動畫重複時逐漸橫越螢幕移動，而不是重設為起始位置。  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathOffsetCumulativeWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexampleoffsetcumulative.xaml#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExampleOffsetCumulative.cs#matrixanimationusingpathoffsetcumulativewholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExampleOffsetCumulative.vb#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 請注意，雖然<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A>屬性會隨著重複而累積的位移的值，但它不會造成旋轉累積的值。 若要讓旋轉累積的值，設定此動畫的<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A>和<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsAngleCumulative%2A>屬性`true`。  
  
 如需完整範例，請參閱[路徑動畫範例](http://go.microsoft.com/fwlink/?LinkID=160028)。 如需範例示範如何建立動畫<xref:System.Windows.Media.Matrix>沿著不含時差的累積的路徑值，請參閱[動畫物件沿著路徑 （矩陣動畫）](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md)。  
  
## <a name="see-also"></a>另請參閱  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [路徑動畫操作說明主題](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)

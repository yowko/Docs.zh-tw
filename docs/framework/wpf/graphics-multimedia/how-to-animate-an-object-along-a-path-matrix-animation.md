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
ms.openlocfilehash: 03e1e40f8ee6840558ad7b712d96e63d9e2bf15f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation"></a>操作說明：沿著路徑建立物件的動畫 (矩陣動畫)
這個範例示範如何使用<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>以動畫方式顯示物件沿著路徑所定義的類別<xref:System.Windows.Media.PathGeometry>。  
  
## <a name="example"></a>範例  
 下列範例會執行下列動作，沿著路徑以動畫顯示的物件︰  
  
-   適用於<xref:System.Windows.Media.MatrixTransform>以便移動該物件。  
  
-   使用定義的路徑<xref:System.Windows.Media.PathGeometry>。  
  
-   建立<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>並使用它來建立動畫<xref:System.Windows.Media.Matrix>屬性<xref:System.Windows.Media.MatrixTransform>。 <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>採用<xref:System.Windows.Media.PathGeometry>並用來產生<xref:System.Windows.Media.Matrix>值。  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexample.xaml#matrixanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExample.cs#matrixanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExample.vb#matrixanimationusingpathwholepage)]  
  
 如需完整範例，請參閱[路徑動畫範例](http://go.microsoft.com/fwlink/?LinkID=160028)。 如需幾何路徑的詳細資訊，請參閱[幾何概觀](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)。  
  
## <a name="see-also"></a>另請參閱  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [路徑動畫範例](http://go.microsoft.com/fwlink/?LinkID=160028)  
 [路徑動畫操作說明主題](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)

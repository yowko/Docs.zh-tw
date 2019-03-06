---
title: HOW TO：沿著路徑建立物件的動畫 (矩陣動畫)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (matrix animation)
- matrix animation [WPF]
ms.assetid: 7000e697-1414-468c-b915-cf66062fc49e
ms.openlocfilehash: c0c4f1fad5ab6b8d30e6809aa866b4629d08af23
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57363731"
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation"></a>HOW TO：沿著路徑建立物件的動畫 (矩陣動畫)
此範例示範如何使用<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>類別以動畫顯示物件沿著路徑所定義<xref:System.Windows.Media.PathGeometry>。  
  
## <a name="example"></a>範例  
 下列範例會執行下列動作，沿著路徑以動畫顯示的物件︰  
  
-   適用於<xref:System.Windows.Media.MatrixTransform>物件以便予以移動。  
  
-   使用定義的路徑<xref:System.Windows.Media.PathGeometry>。  
  
-   會建立<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>並使用它來建立動畫<xref:System.Windows.Media.Matrix>屬性<xref:System.Windows.Media.MatrixTransform>。 <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>會採用<xref:System.Windows.Media.PathGeometry>並用來產生<xref:System.Windows.Media.Matrix>值。  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexample.xaml#matrixanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExample.cs#matrixanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExample.vb#matrixanimationusingpathwholepage)]  
  
 如需完整的範例，請參閱[路徑動畫範例](https://go.microsoft.com/fwlink/?LinkID=160028)。 如需幾何路徑的詳細資訊，請參閱 <<c0> [ 幾何概觀](geometry-overview.md)。  
  
## <a name="see-also"></a>另請參閱
- [動畫概觀](animation-overview.md)
- [路徑動畫範例](https://go.microsoft.com/fwlink/?LinkID=160028)
- [路徑動畫操作說明主題](path-animation-how-to-topics.md)

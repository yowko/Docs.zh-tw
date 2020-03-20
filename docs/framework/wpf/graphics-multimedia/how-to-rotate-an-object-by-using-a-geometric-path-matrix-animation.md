---
title: 操作說明：使用幾何路徑旋轉物件 (矩陣動畫)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
- matrix animation [WPF]
ms.assetid: 877dc9aa-6bdc-4beb-8772-3efaec32c0f0
ms.openlocfilehash: 63dc873a2b840ea3f870a8c60c5691ab271c1c9f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187419"
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation"></a>操作說明：使用幾何路徑旋轉物件 (矩陣動畫)
此示例演示如何使用<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>和 a<xref:System.Windows.Media.MatrixTransform>沿<xref:System.Windows.Media.PathGeometry>物件定義的幾何路徑旋轉（透視）物件。  
  
## <a name="example"></a>範例  
 下面的示例使用 物件<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>為 屬性<xref:System.Windows.Media.MatrixTransform>設置<xref:System.Windows.Media.MatrixTransform.Matrix%2A>動畫。 <xref:System.Windows.Media.MatrixTransform>應用於按鈕，使其沿曲線路徑移動。 由於<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A>屬性設置為`true`，矩形沿路徑的切線旋轉。  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathdoesrotatewithtangentexample.xaml#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathDoesRotateWithTangentExample.cs#matrixanimationusingpathdoesrotatewithtangentwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathDoesRotateWithTangentExample.vb#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 有關完整示例，請參閱[路徑動畫示例](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)。  
  
 前面的示例的代碼版本使用<xref:System.Windows.Media.Animation.Storyboard>為<xref:System.Windows.Media.EllipseGeometry>（） 設置動畫，即使只應用了一個動畫。 將單個動畫應用於代碼中的屬性的一種更簡單的方法是使用 方法<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>。 例如，請參閱[在不使用分鏡腳本的情況下為屬性設置動畫](how-to-animate-a-property-without-using-a-storyboard.md)。  
  
## <a name="see-also"></a>另請參閱

- [動畫概觀](animation-overview.md)
- [路徑動畫操作說明主題](path-animation-how-to-topics.md)
- [路徑動畫範例](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)

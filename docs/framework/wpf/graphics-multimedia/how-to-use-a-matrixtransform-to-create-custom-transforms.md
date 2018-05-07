---
title: 操作說明：使用 MatrixTransform 建立自訂轉換
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], custom Transforms
ms.assetid: 919381ca-989f-47cf-86b4-1094060236e4
ms.openlocfilehash: 4ffbefea498e9a2bdc5546d112f6ff10e12fed67
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-a-matrixtransform-to-create-custom-transforms"></a>操作說明：使用 MatrixTransform 建立自訂轉換
這個範例示範如何使用<xref:System.Windows.Media.MatrixTransform>平移 （移動） 所在位置的而且扭曲的<xref:System.Windows.Controls.Button>。  
  
> [!NOTE]
>  使用<xref:System.Windows.Media.MatrixTransform>類別來建立自訂的轉換未提供的<xref:System.Windows.Media.RotateTransform>， <xref:System.Windows.Media.SkewTransform>， <xref:System.Windows.Media.ScaleTransform>，或<xref:System.Windows.Media.TranslateTransform>類別。  
  
## <a name="example"></a>範例  
 [!code-xaml[Transforms_snip#MatrixTransform](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MatrixTransformExample.xaml#matrixtransform)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Media.MatrixTransform>  
 <xref:System.Windows.Media.Transform>  
 [轉換概觀](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [HOW-TO 主題](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)  
 [WPF 中圖案和基本繪圖概觀](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)

---
title: HOW TO：使用 MatrixTransform 建立自訂轉換
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], custom Transforms
ms.assetid: 919381ca-989f-47cf-86b4-1094060236e4
ms.openlocfilehash: aeccb961db539d4cc6dea75fb487fba06e59d6de
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59182308"
---
# <a name="how-to-use-a-matrixtransform-to-create-custom-transforms"></a>HOW TO：使用 MatrixTransform 建立自訂轉換
此範例示範如何使用<xref:System.Windows.Media.MatrixTransform>平移 （移動） 所在位置的自動縮放，和扭曲的<xref:System.Windows.Controls.Button>。  
  
> [!NOTE]
>  使用<xref:System.Windows.Media.MatrixTransform>類別來建立自訂的轉換，不會提供<xref:System.Windows.Media.RotateTransform>， <xref:System.Windows.Media.SkewTransform>， <xref:System.Windows.Media.ScaleTransform>，或<xref:System.Windows.Media.TranslateTransform>類別。  
  
## <a name="example"></a>範例  
 [!code-xaml[Transforms_snip#MatrixTransform](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MatrixTransformExample.xaml#matrixtransform)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.MatrixTransform>
- <xref:System.Windows.Media.Transform>
- [轉換概觀](transforms-overview.md)
- [HOW-TO 主題](transformations-how-to-topics.md)
- [WPF 中圖案和基本繪圖概觀](shapes-and-basic-drawing-in-wpf-overview.md)

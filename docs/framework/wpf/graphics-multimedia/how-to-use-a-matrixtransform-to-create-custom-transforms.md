---
title: 作法：使用 MatrixTransform 建立自訂轉換
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], custom Transforms
ms.assetid: 919381ca-989f-47cf-86b4-1094060236e4
ms.openlocfilehash: 1971d5fe9422c5138f140517e6fd4c9f9b2cf48b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913923"
---
# <a name="how-to-use-a-matrixtransform-to-create-custom-transforms"></a>HOW TO：使用 MatrixTransform 建立自訂轉換
這個範例顯示如何使用<xref:System.Windows.Media.MatrixTransform>來轉譯 (移動) 的位置、延展和扭曲。 <xref:System.Windows.Controls.Button>  
  
> [!NOTE]
> <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.SkewTransform>使用類別來建立、 、<xref:System.Windows.Media.ScaleTransform>或<xref:System.Windows.Media.TranslateTransform>類別未提供的自訂轉換。 <xref:System.Windows.Media.MatrixTransform>  
  
## <a name="example"></a>範例  
 [!code-xaml[Transforms_snip#MatrixTransform](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MatrixTransformExample.xaml#matrixtransform)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.MatrixTransform>
- <xref:System.Windows.Media.Transform>
- [轉換概觀](transforms-overview.md)
- [HOW-TO 主題](transformations-how-to-topics.md)
- [WPF 中圖案和基本繪圖概觀](shapes-and-basic-drawing-in-wpf-overview.md)

---
title: HOW TO：使用 MatrixTransform 建立自訂轉換
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], custom Transforms
ms.assetid: 919381ca-989f-47cf-86b4-1094060236e4
ms.openlocfilehash: 3b5a6fbedd30c859dffadad00c8faab74fc0773b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628795"
---
# <a name="how-to-use-a-matrixtransform-to-create-custom-transforms"></a><span data-ttu-id="1fa8b-102">HOW TO：使用 MatrixTransform 建立自訂轉換</span><span class="sxs-lookup"><span data-stu-id="1fa8b-102">How to: Use a MatrixTransform to Create Custom Transforms</span></span>
<span data-ttu-id="1fa8b-103">此範例示範如何使用<xref:System.Windows.Media.MatrixTransform>平移 （移動） 所在位置的自動縮放，和扭曲的<xref:System.Windows.Controls.Button>。</span><span class="sxs-lookup"><span data-stu-id="1fa8b-103">This example shows how to use a <xref:System.Windows.Media.MatrixTransform> to translate (move) the position, stretch, and skew of a <xref:System.Windows.Controls.Button>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1fa8b-104">使用<xref:System.Windows.Media.MatrixTransform>類別來建立自訂的轉換，不會提供<xref:System.Windows.Media.RotateTransform>， <xref:System.Windows.Media.SkewTransform>， <xref:System.Windows.Media.ScaleTransform>，或<xref:System.Windows.Media.TranslateTransform>類別。</span><span class="sxs-lookup"><span data-stu-id="1fa8b-104">Use the <xref:System.Windows.Media.MatrixTransform> class to create custom transformations that are not provided by the <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.SkewTransform>, <xref:System.Windows.Media.ScaleTransform>, or <xref:System.Windows.Media.TranslateTransform> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1fa8b-105">範例</span><span class="sxs-lookup"><span data-stu-id="1fa8b-105">Example</span></span>  
 [!code-xaml[Transforms_snip#MatrixTransform](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MatrixTransformExample.xaml#matrixtransform)]  
  
## <a name="see-also"></a><span data-ttu-id="1fa8b-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1fa8b-106">See also</span></span>
- <xref:System.Windows.Media.MatrixTransform>
- <xref:System.Windows.Media.Transform>
- [<span data-ttu-id="1fa8b-107">轉換概觀</span><span class="sxs-lookup"><span data-stu-id="1fa8b-107">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
- [<span data-ttu-id="1fa8b-108">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="1fa8b-108">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
- [<span data-ttu-id="1fa8b-109">WPF 中圖案和基本繪圖概觀</span><span class="sxs-lookup"><span data-stu-id="1fa8b-109">Shapes and Basic Drawing in WPF Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)

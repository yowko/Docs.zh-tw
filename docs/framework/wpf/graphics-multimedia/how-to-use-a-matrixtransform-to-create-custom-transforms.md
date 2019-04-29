---
title: HOW TO：使用 MatrixTransform 建立自訂轉換
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], custom Transforms
ms.assetid: 919381ca-989f-47cf-86b4-1094060236e4
ms.openlocfilehash: aeccb961db539d4cc6dea75fb487fba06e59d6de
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769255"
---
# <a name="how-to-use-a-matrixtransform-to-create-custom-transforms"></a><span data-ttu-id="c90dd-102">HOW TO：使用 MatrixTransform 建立自訂轉換</span><span class="sxs-lookup"><span data-stu-id="c90dd-102">How to: Use a MatrixTransform to Create Custom Transforms</span></span>
<span data-ttu-id="c90dd-103">此範例示範如何使用<xref:System.Windows.Media.MatrixTransform>平移 （移動） 所在位置的自動縮放，和扭曲的<xref:System.Windows.Controls.Button>。</span><span class="sxs-lookup"><span data-stu-id="c90dd-103">This example shows how to use a <xref:System.Windows.Media.MatrixTransform> to translate (move) the position, stretch, and skew of a <xref:System.Windows.Controls.Button>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c90dd-104">使用<xref:System.Windows.Media.MatrixTransform>類別來建立自訂的轉換，不會提供<xref:System.Windows.Media.RotateTransform>， <xref:System.Windows.Media.SkewTransform>， <xref:System.Windows.Media.ScaleTransform>，或<xref:System.Windows.Media.TranslateTransform>類別。</span><span class="sxs-lookup"><span data-stu-id="c90dd-104">Use the <xref:System.Windows.Media.MatrixTransform> class to create custom transformations that are not provided by the <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.SkewTransform>, <xref:System.Windows.Media.ScaleTransform>, or <xref:System.Windows.Media.TranslateTransform> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c90dd-105">範例</span><span class="sxs-lookup"><span data-stu-id="c90dd-105">Example</span></span>  
 [!code-xaml[Transforms_snip#MatrixTransform](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MatrixTransformExample.xaml#matrixtransform)]  
  
## <a name="see-also"></a><span data-ttu-id="c90dd-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c90dd-106">See also</span></span>

- <xref:System.Windows.Media.MatrixTransform>
- <xref:System.Windows.Media.Transform>
- [<span data-ttu-id="c90dd-107">轉換概觀</span><span class="sxs-lookup"><span data-stu-id="c90dd-107">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="c90dd-108">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="c90dd-108">How-to Topics</span></span>](transformations-how-to-topics.md)
- [<span data-ttu-id="c90dd-109">WPF 中圖案和基本繪圖概觀</span><span class="sxs-lookup"><span data-stu-id="c90dd-109">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)

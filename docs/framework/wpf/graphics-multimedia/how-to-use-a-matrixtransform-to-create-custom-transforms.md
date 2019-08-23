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
# <a name="how-to-use-a-matrixtransform-to-create-custom-transforms"></a><span data-ttu-id="5eb0e-102">HOW TO：使用 MatrixTransform 建立自訂轉換</span><span class="sxs-lookup"><span data-stu-id="5eb0e-102">How to: Use a MatrixTransform to Create Custom Transforms</span></span>
<span data-ttu-id="5eb0e-103">這個範例顯示如何使用<xref:System.Windows.Media.MatrixTransform>來轉譯 (移動) 的位置、延展和扭曲。 <xref:System.Windows.Controls.Button></span><span class="sxs-lookup"><span data-stu-id="5eb0e-103">This example shows how to use a <xref:System.Windows.Media.MatrixTransform> to translate (move) the position, stretch, and skew of a <xref:System.Windows.Controls.Button>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5eb0e-104"><xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.SkewTransform>使用類別來建立、 、<xref:System.Windows.Media.ScaleTransform>或<xref:System.Windows.Media.TranslateTransform>類別未提供的自訂轉換。 <xref:System.Windows.Media.MatrixTransform></span><span class="sxs-lookup"><span data-stu-id="5eb0e-104">Use the <xref:System.Windows.Media.MatrixTransform> class to create custom transformations that are not provided by the <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.SkewTransform>, <xref:System.Windows.Media.ScaleTransform>, or <xref:System.Windows.Media.TranslateTransform> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5eb0e-105">範例</span><span class="sxs-lookup"><span data-stu-id="5eb0e-105">Example</span></span>  
 [!code-xaml[Transforms_snip#MatrixTransform](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MatrixTransformExample.xaml#matrixtransform)]  
  
## <a name="see-also"></a><span data-ttu-id="5eb0e-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5eb0e-106">See also</span></span>

- <xref:System.Windows.Media.MatrixTransform>
- <xref:System.Windows.Media.Transform>
- [<span data-ttu-id="5eb0e-107">轉換概觀</span><span class="sxs-lookup"><span data-stu-id="5eb0e-107">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="5eb0e-108">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="5eb0e-108">How-to Topics</span></span>](transformations-how-to-topics.md)
- [<span data-ttu-id="5eb0e-109">WPF 中圖案和基本繪圖概觀</span><span class="sxs-lookup"><span data-stu-id="5eb0e-109">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)

---
title: 操作說明：套用多重轉換至物件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- grouping Transform objects [WPF]
- Transform objects [WPF], grouping
- graphics [WPF], grouping Transform objects
- TransformGroup [WPF]
ms.assetid: 98cd1921-12bc-4bf5-8193-529228fb7402
ms.openlocfilehash: 3ef11104b2a4fc775d29d2a388c9a70a69a3f10f
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112111"
---
# <a name="how-to-apply-multiple-transforms-to-an-object"></a><span data-ttu-id="cd260-102">操作說明：套用多重轉換至物件</span><span class="sxs-lookup"><span data-stu-id="cd260-102">How to: Apply Multiple Transforms to an Object</span></span>
<span data-ttu-id="cd260-103">此示例演示如何使用<xref:System.Windows.Media.TransformGroup>將兩個或多個<xref:System.Windows.Media.Transform>物件分組到單個複合中。 <xref:System.Windows.Media.Transform></span><span class="sxs-lookup"><span data-stu-id="cd260-103">This example shows how to use a <xref:System.Windows.Media.TransformGroup> to group two or more <xref:System.Windows.Media.Transform> objects into a single composite <xref:System.Windows.Media.Transform>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd260-104">範例</span><span class="sxs-lookup"><span data-stu-id="cd260-104">Example</span></span>  
 <span data-ttu-id="cd260-105">下面的<xref:System.Windows.Media.TransformGroup>示例使用 將 和<xref:System.Windows.Media.ScaleTransform>a<xref:System.Windows.Media.RotateTransform>應用於<xref:System.Windows.Controls.Button>。</span><span class="sxs-lookup"><span data-stu-id="cd260-105">The following example uses a <xref:System.Windows.Media.TransformGroup> to apply a <xref:System.Windows.Media.ScaleTransform> and a <xref:System.Windows.Media.RotateTransform> to a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-xaml[Transforms_snip#MultipleTransformExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MultipleTransformExample.xaml#multipletransformexamplewholepage)]  
  
 [!code-csharp[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/MultipleTransformsExample.cs#multipletransformscodeexamplewholepage)]
 [!code-vb[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/MultipleTransformsExample.vb#multipletransformscodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="cd260-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd260-106">See also</span></span>

- <xref:System.Windows.UIElement.RenderTransform%2A>
- <xref:System.Windows.Media.TransformGroup>
- [<span data-ttu-id="cd260-107">轉換概觀</span><span class="sxs-lookup"><span data-stu-id="cd260-107">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="cd260-108">2D 變換示例</span><span class="sxs-lookup"><span data-stu-id="cd260-108">2D Transforms Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)

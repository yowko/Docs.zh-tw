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
ms.openlocfilehash: 0700a7ae3f18f745b0d479ace3acbf2d7fbd9722
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47082561"
---
# <a name="how-to-apply-multiple-transforms-to-an-object"></a><span data-ttu-id="8035e-102">操作說明：套用多重轉換至物件</span><span class="sxs-lookup"><span data-stu-id="8035e-102">How to: Apply Multiple Transforms to an Object</span></span>
<span data-ttu-id="8035e-103">此範例示範如何使用<xref:System.Windows.Media.TransformGroup>兩個或多個群組<xref:System.Windows.Media.Transform>組成為單一複合物件<xref:System.Windows.Media.Transform>。</span><span class="sxs-lookup"><span data-stu-id="8035e-103">This example shows how to use a <xref:System.Windows.Media.TransformGroup> to group two or more <xref:System.Windows.Media.Transform> objects into a single composite <xref:System.Windows.Media.Transform>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8035e-104">範例</span><span class="sxs-lookup"><span data-stu-id="8035e-104">Example</span></span>  
 <span data-ttu-id="8035e-105">下列範例會使用<xref:System.Windows.Media.TransformGroup>套用<xref:System.Windows.Media.ScaleTransform>並<xref:System.Windows.Media.RotateTransform>至<xref:System.Windows.Controls.Button>。</span><span class="sxs-lookup"><span data-stu-id="8035e-105">The following example uses a <xref:System.Windows.Media.TransformGroup> to apply a <xref:System.Windows.Media.ScaleTransform> and a <xref:System.Windows.Media.RotateTransform> to a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-xaml[Transforms_snip#MultipleTransformExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MultipleTransformExample.xaml#multipletransformexamplewholepage)]  
  
 [!code-csharp[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/MultipleTransformsExample.cs#multipletransformscodeexamplewholepage)]
 [!code-vb[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/MultipleTransformsExample.vb#multipletransformscodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="8035e-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8035e-106">See Also</span></span>  
 <xref:System.Windows.UIElement.RenderTransform%2A>  
 <xref:System.Windows.Media.TransformGroup>  
 [<span data-ttu-id="8035e-107">轉換概觀</span><span class="sxs-lookup"><span data-stu-id="8035e-107">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [<span data-ttu-id="8035e-108">2D 轉換範例</span><span class="sxs-lookup"><span data-stu-id="8035e-108">2-D Transforms Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=158252)

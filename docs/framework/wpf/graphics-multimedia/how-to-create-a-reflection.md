---
title: 如何：建立反映
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating reflections [WPF]
- brushes [WPF], creating reflections
- reflections [WPF], creating
ms.assetid: 4f017e16-ab80-43c7-98df-03b6bddbb203
ms.openlocfilehash: 716adff5c5c41e6601e384b6669516cb6ba1041d
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/21/2018
ms.locfileid: "46525093"
---
# <a name="how-to-create-a-reflection"></a><span data-ttu-id="86a88-102">如何：建立反映</span><span class="sxs-lookup"><span data-stu-id="86a88-102">How to: Create a Reflection</span></span>
<span data-ttu-id="86a88-103">此範例示範如何使用<xref:System.Windows.Media.VisualBrush>來建立反映。</span><span class="sxs-lookup"><span data-stu-id="86a88-103">This example shows how to use a <xref:System.Windows.Media.VisualBrush> to create a reflection.</span></span> <span data-ttu-id="86a88-104">因為<xref:System.Windows.Media.VisualBrush>可以顯示現有的視覺效果，您可以使用這項功能來產生有趣的視覺效果，例如反映與放大。</span><span class="sxs-lookup"><span data-stu-id="86a88-104">Because a <xref:System.Windows.Media.VisualBrush> can display an existing visual, you can use this capability to produce interesting visual effects, such as reflections and magnification.</span></span>  
  
## <a name="example"></a><span data-ttu-id="86a88-105">範例</span><span class="sxs-lookup"><span data-stu-id="86a88-105">Example</span></span>  
 <span data-ttu-id="86a88-106">下列範例會使用<xref:System.Windows.Media.VisualBrush>來建立的反映<xref:System.Windows.Controls.Border>，其中包含數個項目。</span><span class="sxs-lookup"><span data-stu-id="86a88-106">The following example uses a <xref:System.Windows.Media.VisualBrush> to create a reflection of a <xref:System.Windows.Controls.Border> that contains several elements.</span></span> <span data-ttu-id="86a88-107">下圖顯示的是這個範例產生的輸出。</span><span class="sxs-lookup"><span data-stu-id="86a88-107">The following illustration shows the output that this example produces.</span></span>  
  
 <span data-ttu-id="86a88-108">![A 反映視覺物件](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")</span><span class="sxs-lookup"><span data-stu-id="86a88-108">![A reflected Visual object](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")</span></span>  
<span data-ttu-id="86a88-109">反映後的 Visual 物件</span><span class="sxs-lookup"><span data-stu-id="86a88-109">A reflected Visual object</span></span>  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 <span data-ttu-id="86a88-110">完整的範例，其中包含說明如何放大螢幕的部分，以及如何建立反映的範例，請參閱 < [VisualBrush 範例](https://go.microsoft.com/fwlink/?LinkID=160049)。</span><span class="sxs-lookup"><span data-stu-id="86a88-110">For the complete sample, which includes examples that show how to magnify parts of the screen and how to create reflections, see [VisualBrush Sample](https://go.microsoft.com/fwlink/?LinkID=160049).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86a88-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86a88-111">See Also</span></span>  
 <xref:System.Windows.Media.VisualBrush>  
 [<span data-ttu-id="86a88-112">使用影像、繪圖和視覺效果繪製</span><span class="sxs-lookup"><span data-stu-id="86a88-112">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)

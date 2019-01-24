---
title: HOW TO：建立反映
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating reflections [WPF]
- brushes [WPF], creating reflections
- reflections [WPF], creating
ms.assetid: 4f017e16-ab80-43c7-98df-03b6bddbb203
ms.openlocfilehash: 0fae98966481003c7906f5cbb34afaea666d583d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559030"
---
# <a name="how-to-create-a-reflection"></a><span data-ttu-id="09d9f-102">HOW TO：建立反映</span><span class="sxs-lookup"><span data-stu-id="09d9f-102">How to: Create a Reflection</span></span>
<span data-ttu-id="09d9f-103">此範例示範如何使用<xref:System.Windows.Media.VisualBrush>來建立反映。</span><span class="sxs-lookup"><span data-stu-id="09d9f-103">This example shows how to use a <xref:System.Windows.Media.VisualBrush> to create a reflection.</span></span> <span data-ttu-id="09d9f-104">因為<xref:System.Windows.Media.VisualBrush>可以顯示現有的視覺效果，您可以使用這項功能來產生有趣的視覺效果，例如反映與放大。</span><span class="sxs-lookup"><span data-stu-id="09d9f-104">Because a <xref:System.Windows.Media.VisualBrush> can display an existing visual, you can use this capability to produce interesting visual effects, such as reflections and magnification.</span></span>  
  
## <a name="example"></a><span data-ttu-id="09d9f-105">範例</span><span class="sxs-lookup"><span data-stu-id="09d9f-105">Example</span></span>  
 <span data-ttu-id="09d9f-106">下列範例會使用<xref:System.Windows.Media.VisualBrush>來建立的反映<xref:System.Windows.Controls.Border>，其中包含數個項目。</span><span class="sxs-lookup"><span data-stu-id="09d9f-106">The following example uses a <xref:System.Windows.Media.VisualBrush> to create a reflection of a <xref:System.Windows.Controls.Border> that contains several elements.</span></span> <span data-ttu-id="09d9f-107">下圖顯示的是這個範例產生的輸出。</span><span class="sxs-lookup"><span data-stu-id="09d9f-107">The following illustration shows the output that this example produces.</span></span>  
  
 <span data-ttu-id="09d9f-108">![A 反映視覺物件](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")</span><span class="sxs-lookup"><span data-stu-id="09d9f-108">![A reflected Visual object](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")</span></span>  
<span data-ttu-id="09d9f-109">反映後的 Visual 物件</span><span class="sxs-lookup"><span data-stu-id="09d9f-109">A reflected Visual object</span></span>  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 <span data-ttu-id="09d9f-110">完整的範例，其中包含說明如何放大螢幕的部分，以及如何建立反映的範例，請參閱 < [VisualBrush 範例](https://go.microsoft.com/fwlink/?LinkID=160049)。</span><span class="sxs-lookup"><span data-stu-id="09d9f-110">For the complete sample, which includes examples that show how to magnify parts of the screen and how to create reflections, see [VisualBrush Sample](https://go.microsoft.com/fwlink/?LinkID=160049).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09d9f-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09d9f-111">See also</span></span>
- <xref:System.Windows.Media.VisualBrush>
- [<span data-ttu-id="09d9f-112">使用影像、繪圖和視覺效果繪製</span><span class="sxs-lookup"><span data-stu-id="09d9f-112">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)

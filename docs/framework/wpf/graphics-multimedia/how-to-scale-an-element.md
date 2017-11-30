---
title: "操作說明：縮放元素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- scaling [WPF], elements
- graphics [WPF], scaling elements
ms.assetid: 18158d94-bbe7-4f6a-814e-84d27fa748bf
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 23b3086452526e804bfdbe50bb0c134f33158f5d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-scale-an-element"></a><span data-ttu-id="73655-102">操作說明：縮放元素</span><span class="sxs-lookup"><span data-stu-id="73655-102">How to: Scale an Element</span></span>
<span data-ttu-id="73655-103">這個範例示範如何使用<xref:System.Windows.Media.ScaleTransform>調整項目。</span><span class="sxs-lookup"><span data-stu-id="73655-103">This example shows how to use a <xref:System.Windows.Media.ScaleTransform> to scale an element.</span></span>  
  
 <span data-ttu-id="73655-104">使用<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>和<xref:System.Windows.Media.ScaleTransform.ScaleY%2A>屬性，以調整元素大小依您指定的比例。</span><span class="sxs-lookup"><span data-stu-id="73655-104">Use the <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> and <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> properties to resize the element by the factor you specify.</span></span> <span data-ttu-id="73655-105">例如，<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>值為 1.5 延伸到 150%其原始寬度的項目。</span><span class="sxs-lookup"><span data-stu-id="73655-105">For example, a <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> value of 1.5 stretches the element to 150 percent of its original width.</span></span> <span data-ttu-id="73655-106">A<xref:System.Windows.Media.ScaleTransform.ScaleY%2A>值為 0.5 壓縮百分之 50 項目的高度。</span><span class="sxs-lookup"><span data-stu-id="73655-106">A <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> value of 0.5 shrinks the height of an element by 50 percent.</span></span>  
  
 <span data-ttu-id="73655-107">使用<xref:System.Windows.Media.ScaleTransform.CenterX%2A>和<xref:System.Windows.Media.ScaleTransform.CenterY%2A>屬性，以指定的調整規模作業的中心點。</span><span class="sxs-lookup"><span data-stu-id="73655-107">Use the <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A> properties to specify the point that is the center of the scale operation.</span></span> <span data-ttu-id="73655-108">根據預設，<xref:System.Windows.Media.ScaleTransform>會集中在時間點 (0，0)，對應至矩形左上角。</span><span class="sxs-lookup"><span data-stu-id="73655-108">By default, a <xref:System.Windows.Media.ScaleTransform> is centered at the point (0,0), which corresponds to the upper-left corner of the rectangle.</span></span> <span data-ttu-id="73655-109">這是移動項目，讓它看起來更大，因為當您將套用的效果<xref:System.Windows.Media.Transform>，變更座標空間存放物件。</span><span class="sxs-lookup"><span data-stu-id="73655-109">This has the effect of moving the element and also of making it appear larger, because when you apply a <xref:System.Windows.Media.Transform>, you change the coordinate space in which the object resides.</span></span>  
  
 <span data-ttu-id="73655-110">下列範例會使用<xref:System.Windows.Media.ScaleTransform>x 50 50 的大小增加兩倍<xref:System.Windows.Shapes.Rectangle>。</span><span class="sxs-lookup"><span data-stu-id="73655-110">The following example uses a <xref:System.Windows.Media.ScaleTransform> to double the size of a 50-by-50 <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="73655-111"><xref:System.Windows.Media.ScaleTransform>兩個具有值為 0 （預設值）<xref:System.Windows.Media.ScaleTransform.CenterX%2A>和<xref:System.Windows.Media.ScaleTransform.CenterY%2A>。</span><span class="sxs-lookup"><span data-stu-id="73655-111">The <xref:System.Windows.Media.ScaleTransform> has a value of 0 (the default) for both <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73655-112">範例</span><span class="sxs-lookup"><span data-stu-id="73655-112">Example</span></span>  
 [!code-xaml[transformsSample#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#21)]  
  
 <span data-ttu-id="73655-113">通常您設定<xref:System.Windows.Media.ScaleTransform.CenterX%2A>和<xref:System.Windows.Media.ScaleTransform.CenterY%2A>縮放物件的中央: (<xref:System.Windows.FrameworkElement.Width%2A>/2，  <xref:System.Windows.FrameworkElement.Height%2A> /2)。</span><span class="sxs-lookup"><span data-stu-id="73655-113">Typically, you set <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A> to the center of the object that is scaled: (<xref:System.Windows.FrameworkElement.Width%2A>/2, <xref:System.Windows.FrameworkElement.Height%2A>/2).</span></span>  
  
 <span data-ttu-id="73655-114">下列範例示範另一個<xref:System.Windows.Shapes.Rectangle>，就會加倍大小; 不過，這<xref:System.Windows.Media.ScaleTransform>兩者中的值為 25<xref:System.Windows.Media.ScaleTransform.CenterX%2A>和<xref:System.Windows.Media.ScaleTransform.CenterY%2A>，它會對應到中央的矩形。</span><span class="sxs-lookup"><span data-stu-id="73655-114">The following example shows another <xref:System.Windows.Shapes.Rectangle> that is doubled in size; however, this <xref:System.Windows.Media.ScaleTransform> has a value of 25 for both <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A>, which corresponds to the center of the rectangle.</span></span>  
  
 [!code-xaml[transformsSample#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#22)]  
  
 <span data-ttu-id="73655-115">下圖顯示兩者之間的差異<xref:System.Windows.Media.ScaleTransform>作業。</span><span class="sxs-lookup"><span data-stu-id="73655-115">The following illustration shows the difference between the two <xref:System.Windows.Media.ScaleTransform> operations.</span></span> <span data-ttu-id="73655-116">虛線顯示的是矩形在縮放之前的大小和位置。</span><span class="sxs-lookup"><span data-stu-id="73655-116">The dotted line shows the size and position of the rectangle before scaling.</span></span>  
  
 <span data-ttu-id="73655-117">![採用不同中心點的 2 倍縮放](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")</span><span class="sxs-lookup"><span data-stu-id="73655-117">![2x scales with different center points](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")</span></span>  
<span data-ttu-id="73655-118">兩個有相同 ScaleX 和 ScaleY 值，但不同中心的 ScaleTransform 作業</span><span class="sxs-lookup"><span data-stu-id="73655-118">Two ScaleTransform operations with identical ScaleX and ScaleY values but different centers</span></span>  
  
 <span data-ttu-id="73655-119">如需完整範例，請參閱 [2D 轉換範例](http://go.microsoft.com/fwlink/?LinkID=158252)。</span><span class="sxs-lookup"><span data-stu-id="73655-119">For the complete sample, see [2-D Transforms Sample](http://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73655-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73655-120">See Also</span></span>  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.ScaleTransform>  
 [<span data-ttu-id="73655-121">轉換概觀</span><span class="sxs-lookup"><span data-stu-id="73655-121">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [<span data-ttu-id="73655-122">操作說明主題</span><span class="sxs-lookup"><span data-stu-id="73655-122">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)

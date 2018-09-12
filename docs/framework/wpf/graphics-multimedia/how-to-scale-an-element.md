---
title: 操作說明：縮放元素
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], elements
- graphics [WPF], scaling elements
ms.assetid: 18158d94-bbe7-4f6a-814e-84d27fa748bf
ms.openlocfilehash: 44c638b58d828e5beb0b9de5c7bb0b67c8e82d87
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2018
ms.locfileid: "44698545"
---
# <a name="how-to-scale-an-element"></a><span data-ttu-id="98073-102">操作說明：縮放元素</span><span class="sxs-lookup"><span data-stu-id="98073-102">How to: Scale an Element</span></span>
<span data-ttu-id="98073-103">此範例示範如何使用<xref:System.Windows.Media.ScaleTransform>來縮放元素。</span><span class="sxs-lookup"><span data-stu-id="98073-103">This example shows how to use a <xref:System.Windows.Media.ScaleTransform> to scale an element.</span></span>  
  
 <span data-ttu-id="98073-104">使用<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>和<xref:System.Windows.Media.ScaleTransform.ScaleY%2A>屬性所指定的因數調整元素的大小。</span><span class="sxs-lookup"><span data-stu-id="98073-104">Use the <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> and <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> properties to resize the element by the factor you specify.</span></span> <span data-ttu-id="98073-105">比方說，<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>的 1.5 倍的值會自動縮放其原始寬度的 150%的項目。</span><span class="sxs-lookup"><span data-stu-id="98073-105">For example, a <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> value of 1.5 stretches the element to 150 percent of its original width.</span></span> <span data-ttu-id="98073-106">A <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> 50%的值為 0.5 會縮小的項目的高度。</span><span class="sxs-lookup"><span data-stu-id="98073-106">A <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> value of 0.5 shrinks the height of an element by 50 percent.</span></span>  
  
 <span data-ttu-id="98073-107">使用<xref:System.Windows.Media.ScaleTransform.CenterX%2A>和<xref:System.Windows.Media.ScaleTransform.CenterY%2A>屬性，以指定的縮放作業中心點。</span><span class="sxs-lookup"><span data-stu-id="98073-107">Use the <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A> properties to specify the point that is the center of the scale operation.</span></span> <span data-ttu-id="98073-108">根據預設，<xref:System.Windows.Media.ScaleTransform>中心點 (0，0)，其對應至矩形左上角。</span><span class="sxs-lookup"><span data-stu-id="98073-108">By default, a <xref:System.Windows.Media.ScaleTransform> is centered at the point (0,0), which corresponds to the upper-left corner of the rectangle.</span></span> <span data-ttu-id="98073-109">這具有移動元素同時也使它看起來更大的程式，因為當您將套用的效果<xref:System.Windows.Media.Transform>，變更物件所在的座標空間。</span><span class="sxs-lookup"><span data-stu-id="98073-109">This has the effect of moving the element and also of making it appear larger, because when you apply a <xref:System.Windows.Media.Transform>, you change the coordinate space in which the object resides.</span></span>  
  
 <span data-ttu-id="98073-110">下列範例會使用<xref:System.Windows.Media.ScaleTransform>x 50 50 大小的兩倍<xref:System.Windows.Shapes.Rectangle>。</span><span class="sxs-lookup"><span data-stu-id="98073-110">The following example uses a <xref:System.Windows.Media.ScaleTransform> to double the size of a 50-by-50 <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="98073-111"><xref:System.Windows.Media.ScaleTransform>具有值為 0 （預設值），同時<xref:System.Windows.Media.ScaleTransform.CenterX%2A>和<xref:System.Windows.Media.ScaleTransform.CenterY%2A>。</span><span class="sxs-lookup"><span data-stu-id="98073-111">The <xref:System.Windows.Media.ScaleTransform> has a value of 0 (the default) for both <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="98073-112">範例</span><span class="sxs-lookup"><span data-stu-id="98073-112">Example</span></span>  
 [!code-xaml[transformsSample#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#21)]  
  
 <span data-ttu-id="98073-113">一般而言，您設定<xref:System.Windows.Media.ScaleTransform.CenterX%2A>並<xref:System.Windows.Media.ScaleTransform.CenterY%2A>之物件的縮放中心: (<xref:System.Windows.FrameworkElement.Width%2A>/2，  <xref:System.Windows.FrameworkElement.Height%2A> /2)。</span><span class="sxs-lookup"><span data-stu-id="98073-113">Typically, you set <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A> to the center of the object that is scaled: (<xref:System.Windows.FrameworkElement.Width%2A>/2, <xref:System.Windows.FrameworkElement.Height%2A>/2).</span></span>  
  
 <span data-ttu-id="98073-114">下列範例示範另一個<xref:System.Windows.Shapes.Rectangle>，會增加一倍的大小; 不過，這<xref:System.Windows.Media.ScaleTransform>兩個具有的值為 25<xref:System.Windows.Media.ScaleTransform.CenterX%2A>和<xref:System.Windows.Media.ScaleTransform.CenterY%2A>，它會對應至矩形的中心。</span><span class="sxs-lookup"><span data-stu-id="98073-114">The following example shows another <xref:System.Windows.Shapes.Rectangle> that is doubled in size; however, this <xref:System.Windows.Media.ScaleTransform> has a value of 25 for both <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A>, which corresponds to the center of the rectangle.</span></span>  
  
 [!code-xaml[transformsSample#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#22)]  
  
 <span data-ttu-id="98073-115">下圖顯示兩者之間的差異<xref:System.Windows.Media.ScaleTransform>作業。</span><span class="sxs-lookup"><span data-stu-id="98073-115">The following illustration shows the difference between the two <xref:System.Windows.Media.ScaleTransform> operations.</span></span> <span data-ttu-id="98073-116">虛線顯示的是矩形在縮放之前的大小和位置。</span><span class="sxs-lookup"><span data-stu-id="98073-116">The dotted line shows the size and position of the rectangle before scaling.</span></span>  
  
 <span data-ttu-id="98073-117">![採用不同中心點的 2 倍縮放](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")</span><span class="sxs-lookup"><span data-stu-id="98073-117">![2x scales with different center points](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")</span></span>  
<span data-ttu-id="98073-118">兩個有相同 ScaleX 和 ScaleY 值，但不同中心的 ScaleTransform 作業</span><span class="sxs-lookup"><span data-stu-id="98073-118">Two ScaleTransform operations with identical ScaleX and ScaleY values but different centers</span></span>  
  
 <span data-ttu-id="98073-119">如需完整範例，請參閱 [2D 轉換範例](https://go.microsoft.com/fwlink/?LinkID=158252)。</span><span class="sxs-lookup"><span data-stu-id="98073-119">For the complete sample, see [2-D Transforms Sample](https://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98073-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98073-120">See Also</span></span>  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.ScaleTransform>  
 [<span data-ttu-id="98073-121">轉換概觀</span><span class="sxs-lookup"><span data-stu-id="98073-121">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [<span data-ttu-id="98073-122">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="98073-122">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)

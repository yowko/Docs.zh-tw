---
title: 操作說明：縮放元素
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], elements
- graphics [WPF], scaling elements
ms.assetid: 18158d94-bbe7-4f6a-814e-84d27fa748bf
ms.openlocfilehash: a383ad84f1db4d937469943092a03517f68777ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187442"
---
# <a name="how-to-scale-an-element"></a><span data-ttu-id="46d05-102">操作說明：縮放元素</span><span class="sxs-lookup"><span data-stu-id="46d05-102">How to: Scale an Element</span></span>
<span data-ttu-id="46d05-103">此示例演示如何使用<xref:System.Windows.Media.ScaleTransform>縮放元素。</span><span class="sxs-lookup"><span data-stu-id="46d05-103">This example shows how to use a <xref:System.Windows.Media.ScaleTransform> to scale an element.</span></span>  
  
 <span data-ttu-id="46d05-104">使用<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>和<xref:System.Windows.Media.ScaleTransform.ScaleY%2A>屬性按指定的因數調整元素的大小。</span><span class="sxs-lookup"><span data-stu-id="46d05-104">Use the <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> and <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> properties to resize the element by the factor you specify.</span></span> <span data-ttu-id="46d05-105">例如，<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>值 1.5 將元素拉伸到其原始寬度的 150%。</span><span class="sxs-lookup"><span data-stu-id="46d05-105">For example, a <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> value of 1.5 stretches the element to 150 percent of its original width.</span></span> <span data-ttu-id="46d05-106">值<xref:System.Windows.Media.ScaleTransform.ScaleY%2A>0.5 將元素的高度縮小 50%。</span><span class="sxs-lookup"><span data-stu-id="46d05-106">A <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> value of 0.5 shrinks the height of an element by 50 percent.</span></span>  
  
 <span data-ttu-id="46d05-107">使用<xref:System.Windows.Media.ScaleTransform.CenterX%2A>和<xref:System.Windows.Media.ScaleTransform.CenterY%2A>屬性指定是比例操作中心的點。</span><span class="sxs-lookup"><span data-stu-id="46d05-107">Use the <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A> properties to specify the point that is the center of the scale operation.</span></span> <span data-ttu-id="46d05-108">預設情況下，a<xref:System.Windows.Media.ScaleTransform>居中居於與矩形左上角相對應的點 （0，0）。</span><span class="sxs-lookup"><span data-stu-id="46d05-108">By default, a <xref:System.Windows.Media.ScaleTransform> is centered at the point (0,0), which corresponds to the upper-left corner of the rectangle.</span></span> <span data-ttu-id="46d05-109">這具有移動元素的效果，並且也使元素看起來更大，因為當您應用 時<xref:System.Windows.Media.Transform>，您將更改物件所在的座標空間。</span><span class="sxs-lookup"><span data-stu-id="46d05-109">This has the effect of moving the element and also of making it appear larger, because when you apply a <xref:System.Windows.Media.Transform>, you change the coordinate space in which the object resides.</span></span>  
  
 <span data-ttu-id="46d05-110">下面的示例使用 將<xref:System.Windows.Media.ScaleTransform>50 乘 50<xref:System.Windows.Shapes.Rectangle>的大小加倍。</span><span class="sxs-lookup"><span data-stu-id="46d05-110">The following example uses a <xref:System.Windows.Media.ScaleTransform> to double the size of a 50-by-50 <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="46d05-111">和<xref:System.Windows.Media.ScaleTransform>的值為 0（預設值）。 <xref:System.Windows.Media.ScaleTransform.CenterX%2A> <xref:System.Windows.Media.ScaleTransform.CenterY%2A></span><span class="sxs-lookup"><span data-stu-id="46d05-111">The <xref:System.Windows.Media.ScaleTransform> has a value of 0 (the default) for both <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46d05-112">範例</span><span class="sxs-lookup"><span data-stu-id="46d05-112">Example</span></span>  
 [!code-xaml[transformsSample#21](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#21)]  
  
 <span data-ttu-id="46d05-113">通常，您設置<xref:System.Windows.Media.ScaleTransform.CenterX%2A>並<xref:System.Windows.Media.ScaleTransform.CenterY%2A>設置為縮放的物件的中心：（/2，/2）。<xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A></span><span class="sxs-lookup"><span data-stu-id="46d05-113">Typically, you set <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A> to the center of the object that is scaled: (<xref:System.Windows.FrameworkElement.Width%2A>/2, <xref:System.Windows.FrameworkElement.Height%2A>/2).</span></span>  
  
 <span data-ttu-id="46d05-114">下面的示例顯示了另一<xref:System.Windows.Shapes.Rectangle>個大小加倍的，但是，這<xref:System.Windows.Media.ScaleTransform>兩個 值為<xref:System.Windows.Media.ScaleTransform.CenterX%2A>25，<xref:System.Windows.Media.ScaleTransform.CenterY%2A>對應于矩形的中心。</span><span class="sxs-lookup"><span data-stu-id="46d05-114">The following example shows another <xref:System.Windows.Shapes.Rectangle> that is doubled in size; however, this <xref:System.Windows.Media.ScaleTransform> has a value of 25 for both <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A>, which corresponds to the center of the rectangle.</span></span>  
  
 [!code-xaml[transformsSample#22](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#22)]  
  
 <span data-ttu-id="46d05-115">下圖顯示了兩<xref:System.Windows.Media.ScaleTransform>個操作之間的差異。</span><span class="sxs-lookup"><span data-stu-id="46d05-115">The following illustration shows the difference between the two <xref:System.Windows.Media.ScaleTransform> operations.</span></span> <span data-ttu-id="46d05-116">虛線顯示的是矩形在縮放之前的大小和位置。</span><span class="sxs-lookup"><span data-stu-id="46d05-116">The dotted line shows the size and position of the rectangle before scaling.</span></span>  
  
 <span data-ttu-id="46d05-117">![採用不同中心點的 2 倍縮放](./media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")</span><span class="sxs-lookup"><span data-stu-id="46d05-117">![2x scales with different center points](./media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")</span></span>  
<span data-ttu-id="46d05-118">兩個有相同 ScaleX 和 ScaleY 值，但不同中心的 ScaleTransform 作業</span><span class="sxs-lookup"><span data-stu-id="46d05-118">Two ScaleTransform operations with identical ScaleX and ScaleY values but different centers</span></span>  
  
 <span data-ttu-id="46d05-119">如需完整範例，請參閱 [2D 轉換範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)。</span><span class="sxs-lookup"><span data-stu-id="46d05-119">For the complete sample, see [2-D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46d05-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46d05-120">See also</span></span>

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.ScaleTransform>
- [<span data-ttu-id="46d05-121">轉換概觀</span><span class="sxs-lookup"><span data-stu-id="46d05-121">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="46d05-122">如何使用主題</span><span class="sxs-lookup"><span data-stu-id="46d05-122">How-to Topics</span></span>](transformations-how-to-topics.md)

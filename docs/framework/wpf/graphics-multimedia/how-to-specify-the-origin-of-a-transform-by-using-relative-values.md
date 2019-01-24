---
title: HOW TO：使用相對值指定轉換的原點
ms.date: 03/30/2017
helpviewer_keywords:
- origins of Transforms [WPF]
- Transforms [WPF], origins of
- graphics [WPF], origins of Transforms
ms.assetid: f4dbc29d-93c7-41cd-96d8-5cfd8624b470
ms.openlocfilehash: 55007575435ada809b8fba43d08abdd2ce9ddd73
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54570612"
---
# <a name="how-to-specify-the-origin-of-a-transform-by-using-relative-values"></a><span data-ttu-id="f02b8-102">HOW TO：使用相對值指定轉換的原點</span><span class="sxs-lookup"><span data-stu-id="f02b8-102">How to: Specify the Origin of a Transform by Using Relative Values</span></span>
<span data-ttu-id="f02b8-103">此範例示範如何使用相對值指定的原點<xref:System.Windows.UIElement.RenderTransform%2A>套用至<xref:System.Windows.FrameworkElement>。</span><span class="sxs-lookup"><span data-stu-id="f02b8-103">This example shows how to use relative values to specify the origin of a <xref:System.Windows.UIElement.RenderTransform%2A> that is applied to a <xref:System.Windows.FrameworkElement>.</span></span>  
  
 <span data-ttu-id="f02b8-104">當您可以在這裡旋轉、 縮放或扭曲<xref:System.Windows.FrameworkElement>使用<xref:System.Windows.UIElement.RenderTransform%2A>屬性，預設值將轉換套用至項目的左上角。</span><span class="sxs-lookup"><span data-stu-id="f02b8-104">When you rotate, scale, or skew a <xref:System.Windows.FrameworkElement> by using the <xref:System.Windows.UIElement.RenderTransform%2A> property, the default setting applies the transform to the upper-left corner of the element.</span></span> <span data-ttu-id="f02b8-105">如果您想要從元素的中心進行旋轉、縮放或扭曲，您可以將轉換的中心設為元素的中心。</span><span class="sxs-lookup"><span data-stu-id="f02b8-105">If you want to rotate, scale, or skew from the center of the element, you can compensate by setting the center of the transform to the center of the element.</span></span> <span data-ttu-id="f02b8-106">不過，使用此解決方案需要先知道元素的大小。</span><span class="sxs-lookup"><span data-stu-id="f02b8-106">However, that solution requires that you know the size of the element.</span></span> <span data-ttu-id="f02b8-107">將轉換套用至項目的中心更簡單的方法是設定其<xref:System.Windows.UIElement.RenderTransformOrigin%2A>屬性為 （0.5，0.5），而不是針對轉換本身設定中心值。</span><span class="sxs-lookup"><span data-stu-id="f02b8-107">An easier way of applying a transform to the center of an element is to set its <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property to (0.5, 0.5), instead of setting a center value on the transform itself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f02b8-108">範例</span><span class="sxs-lookup"><span data-stu-id="f02b8-108">Example</span></span>  
 <span data-ttu-id="f02b8-109">下列範例會使用<xref:System.Windows.Media.RotateTransform>旋轉<xref:System.Windows.Controls.Button>順時針旋轉 45 度。</span><span class="sxs-lookup"><span data-stu-id="f02b8-109">The following example uses a <xref:System.Windows.Media.RotateTransform> to rotate a <xref:System.Windows.Controls.Button> 45 degrees clockwise.</span></span> <span data-ttu-id="f02b8-110">由於範例沒有指定中心，因此按鈕會以點 (0, 0)，也就是左上角為中心旋轉。</span><span class="sxs-lookup"><span data-stu-id="f02b8-110">Because the example does not specify a center, the button rotates about the point (0, 0), which is its upper-left corner.</span></span> <span data-ttu-id="f02b8-111"><xref:System.Windows.Media.RotateTransform>套用至<xref:System.Windows.UIElement.RenderTransform%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="f02b8-111">The <xref:System.Windows.Media.RotateTransform> is applied to the <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span>  
  
 <span data-ttu-id="f02b8-112">下圖顯示後續範例的轉換結果。</span><span class="sxs-lookup"><span data-stu-id="f02b8-112">The following illustration shows the transformation result for the example that follows.</span></span>  
  
 <span data-ttu-id="f02b8-113">![使用 rendertransform 經過轉換的按鈕](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")</span><span class="sxs-lookup"><span data-stu-id="f02b8-113">![A button transformed using RenderTransform](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")</span></span>  
<span data-ttu-id="f02b8-114">使用 RenderTransform 屬性順時針旋轉 45 度</span><span class="sxs-lookup"><span data-stu-id="f02b8-114">A 45 degree clockwise rotation by using the RenderTransform property</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 <span data-ttu-id="f02b8-115">下列範例也會使用<xref:System.Windows.Media.RotateTransform>旋轉<xref:System.Windows.Controls.Button>45 度順時針旋轉; 不過，此範例會設定<xref:System.Windows.UIElement.RenderTransformOrigin%2A>的按鈕 （0.5，0.5）。</span><span class="sxs-lookup"><span data-stu-id="f02b8-115">The following example also uses a <xref:System.Windows.Media.RotateTransform> to rotate a <xref:System.Windows.Controls.Button> 45 degrees clockwise; however, this example sets the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> of the button to (0.5, 0.5).</span></span> <span data-ttu-id="f02b8-116">因此，旋轉會套用到按鈕的中心，而非左上角。</span><span class="sxs-lookup"><span data-stu-id="f02b8-116">As a result, the rotation is applied to the center of the button instead of to the upper-left corner.</span></span>  
  
 <span data-ttu-id="f02b8-117">下圖顯示後續範例的轉換結果。</span><span class="sxs-lookup"><span data-stu-id="f02b8-117">The following illustration shows the transformation result for the example that follows.</span></span>  
  
 <span data-ttu-id="f02b8-118">![繞著中心轉換的按鈕](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")</span><span class="sxs-lookup"><span data-stu-id="f02b8-118">![A button transformed about its center](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")</span></span>  
<span data-ttu-id="f02b8-119">使用 RenderTransform 屬性搭配 (0.5, 0.5) 的 RenderTransformOrigin 旋轉 45 度</span><span class="sxs-lookup"><span data-stu-id="f02b8-119">A 45 degree rotation by using the RenderTransform property with a RenderTransformOrigin of (0.5, 0.5)</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 <span data-ttu-id="f02b8-120">如需轉換的詳細資訊<xref:System.Windows.FrameworkElement>物件，請參閱[轉換概觀](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="f02b8-120">For more information about transforming <xref:System.Windows.FrameworkElement> objects, see the [Transforms Overview](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f02b8-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f02b8-121">See also</span></span>
- <xref:System.Windows.Media.Transform>
- [<span data-ttu-id="f02b8-122">轉換概觀</span><span class="sxs-lookup"><span data-stu-id="f02b8-122">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
- [<span data-ttu-id="f02b8-123">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="f02b8-123">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)

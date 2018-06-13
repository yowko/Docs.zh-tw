---
title: 操作說明：不使用分鏡腳本而建立屬性的動畫
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- non-Storyboard animation
- local animation [WPF]
- animation [WPF], non-Storyboard (local)
ms.assetid: d411db70-4df7-487d-82bc-95a7c1b2e7f8
ms.openlocfilehash: 18f8fb4edf5f71904335180e43dd65bd9910bdef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561010"
---
# <a name="how-to-animate-a-property-without-using-a-storyboard"></a><span data-ttu-id="d72a3-102">操作說明：不使用分鏡腳本而建立屬性的動畫</span><span class="sxs-lookup"><span data-stu-id="d72a3-102">How to: Animate a Property Without Using a Storyboard</span></span>
<span data-ttu-id="d72a3-103">這個範例示範一種方式套用至屬性的動畫，而不使用<xref:System.Windows.Media.Animation.Storyboard>。</span><span class="sxs-lookup"><span data-stu-id="d72a3-103">This example shows one way to apply an animation to a property without using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d72a3-104">[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 中無法使用此功能。</span><span class="sxs-lookup"><span data-stu-id="d72a3-104">This functionality is not available in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="d72a3-105">如需以動畫顯示 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中屬性的詳細資訊，請參閱[使用分鏡腳本建立屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)。</span><span class="sxs-lookup"><span data-stu-id="d72a3-105">For information about animating a property in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], see [Animate a Property by Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md).</span></span>  
  
 <span data-ttu-id="d72a3-106">若要將本機動畫套用至屬性，使用<xref:System.Windows.UIElement.BeginAnimation%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="d72a3-106">To apply a local animation to a property, use the <xref:System.Windows.UIElement.BeginAnimation%2A> method.</span></span> <span data-ttu-id="d72a3-107">這個方法會採用兩個參數：<xref:System.Windows.DependencyProperty>指定屬性，即可建立動畫的來源，以及要套用到該屬性的動畫。</span><span class="sxs-lookup"><span data-stu-id="d72a3-107">This method takes two parameters: a <xref:System.Windows.DependencyProperty> that specifies the property to animate, and the animation to apply to that property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d72a3-108">範例</span><span class="sxs-lookup"><span data-stu-id="d72a3-108">Example</span></span>  
 <span data-ttu-id="d72a3-109">下列範例示範如何建立動畫的寬度和背景色彩<xref:System.Windows.Controls.Button>。</span><span class="sxs-lookup"><span data-stu-id="d72a3-109">The following example shows how to animate the width and background color of a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-cpp[animateproperty#11](../../../../samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
 <span data-ttu-id="d72a3-110">動畫類別中的各種不同<xref:System.Windows.Media.Animation>命名空間存在適用於不同類型的屬性。</span><span class="sxs-lookup"><span data-stu-id="d72a3-110">A variety of animation classes in the <xref:System.Windows.Media.Animation> namespace exist for animating different types of properties.</span></span> <span data-ttu-id="d72a3-111">如需將屬性顯示為動畫的詳細資訊，請參閱[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="d72a3-111">For more information about animating properties, see [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span></span> <span data-ttu-id="d72a3-112">如需相依性屬性 (這些範例所示的內容類型) 和其功能的詳細資訊，請參閱[相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="d72a3-112">For more information about dependency properties (the type of properties that are shown in these examples) and their features, see [Dependency Properties Overview](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).</span></span>  
  
 <span data-ttu-id="d72a3-113">還有其他方式，以動畫方式顯示，而不使用<xref:System.Windows.Media.Animation.Storyboard>物件; 如需詳細資訊，請參閱[屬性動畫技術概觀](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="d72a3-113">There are other ways to animate without using <xref:System.Windows.Media.Animation.Storyboard> objects; for more information, see [Property Animation Techniques Overview](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d72a3-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d72a3-114">See Also</span></span>  
 <xref:System.Windows.Media.Animation.AnimationTimeline>  
 <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>  
 <xref:System.Windows.Media.Animation>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 [<span data-ttu-id="d72a3-115">屬性動畫技術概觀</span><span class="sxs-lookup"><span data-stu-id="d72a3-115">Property Animation Techniques Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)  
 [<span data-ttu-id="d72a3-116">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="d72a3-116">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)

---
title: HOW TO：不使用腳本而建立屬性的動畫
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
ms.openlocfilehash: b76afeb0187065ff07c832363d3a52896aa36822
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57371156"
---
# <a name="how-to-animate-a-property-without-using-a-storyboard"></a><span data-ttu-id="b4c3a-102">HOW TO：不使用腳本而建立屬性的動畫</span><span class="sxs-lookup"><span data-stu-id="b4c3a-102">How to: Animate a Property Without Using a Storyboard</span></span>
<span data-ttu-id="b4c3a-103">此範例示範套用至屬性的動畫，而不使用的一種方法<xref:System.Windows.Media.Animation.Storyboard>。</span><span class="sxs-lookup"><span data-stu-id="b4c3a-103">This example shows one way to apply an animation to a property without using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b4c3a-104">[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 中無法使用此功能。</span><span class="sxs-lookup"><span data-stu-id="b4c3a-104">This functionality is not available in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="b4c3a-105">如需以動畫顯示 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中屬性的詳細資訊，請參閱[使用分鏡腳本建立屬性的動畫](how-to-animate-a-property-by-using-a-storyboard.md)。</span><span class="sxs-lookup"><span data-stu-id="b4c3a-105">For information about animating a property in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], see [Animate a Property by Using a Storyboard](how-to-animate-a-property-by-using-a-storyboard.md).</span></span>  
  
 <span data-ttu-id="b4c3a-106">若要將本機動畫套用至屬性，使用<xref:System.Windows.UIElement.BeginAnimation%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="b4c3a-106">To apply a local animation to a property, use the <xref:System.Windows.UIElement.BeginAnimation%2A> method.</span></span> <span data-ttu-id="b4c3a-107">這個方法會採用兩個參數：<xref:System.Windows.DependencyProperty>可指定的屬性，以動畫顯示，以及要套用到該屬性的動畫。</span><span class="sxs-lookup"><span data-stu-id="b4c3a-107">This method takes two parameters: a <xref:System.Windows.DependencyProperty> that specifies the property to animate, and the animation to apply to that property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4c3a-108">範例</span><span class="sxs-lookup"><span data-stu-id="b4c3a-108">Example</span></span>  
 <span data-ttu-id="b4c3a-109">下列範例示範如何以動畫顯示的寬度和背景色彩<xref:System.Windows.Controls.Button>。</span><span class="sxs-lookup"><span data-stu-id="b4c3a-109">The following example shows how to animate the width and background color of a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-cpp[animateproperty#11](~/samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](~/samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
 <span data-ttu-id="b4c3a-110">中的動畫類別的各種<xref:System.Windows.Media.Animation>命名空間存在以動畫顯示不同類型的屬性。</span><span class="sxs-lookup"><span data-stu-id="b4c3a-110">A variety of animation classes in the <xref:System.Windows.Media.Animation> namespace exist for animating different types of properties.</span></span> <span data-ttu-id="b4c3a-111">如需將屬性顯示為動畫的詳細資訊，請參閱[動畫概觀](animation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="b4c3a-111">For more information about animating properties, see [Animation Overview](animation-overview.md).</span></span> <span data-ttu-id="b4c3a-112">如需相依性屬性 (這些範例所示的內容類型) 和其功能的詳細資訊，請參閱[相依性屬性概觀](../advanced/dependency-properties-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="b4c3a-112">For more information about dependency properties (the type of properties that are shown in these examples) and their features, see [Dependency Properties Overview](../advanced/dependency-properties-overview.md).</span></span>  
  
 <span data-ttu-id="b4c3a-113">還有其他方式，而不使用動畫<xref:System.Windows.Media.Animation.Storyboard>物件; 如需詳細資訊，請參閱[屬性動畫技術概觀](property-animation-techniques-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="b4c3a-113">There are other ways to animate without using <xref:System.Windows.Media.Animation.Storyboard> objects; for more information, see [Property Animation Techniques Overview](property-animation-techniques-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4c3a-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4c3a-114">See also</span></span>
- <xref:System.Windows.Media.Animation.AnimationTimeline>
- <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Animation.Storyboard>
- [<span data-ttu-id="b4c3a-115">屬性動畫技術概觀</span><span class="sxs-lookup"><span data-stu-id="b4c3a-115">Property Animation Techniques Overview</span></span>](property-animation-techniques-overview.md)
- [<span data-ttu-id="b4c3a-116">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="b4c3a-116">Animation Overview</span></span>](animation-overview.md)

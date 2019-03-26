---
title: HOW TO：對文字套用動畫
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], animations
- animation [WPF], text
ms.assetid: eec3d26c-0a21-420f-8012-671621c47089
ms.openlocfilehash: 4cc7932b43f8a3c35d750f9a9020e16257867f76
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/26/2019
ms.locfileid: "58463120"
---
# <a name="how-to-apply-animations-to-text"></a><span data-ttu-id="5ff37-102">HOW TO：對文字套用動畫</span><span class="sxs-lookup"><span data-stu-id="5ff37-102">How to: Apply Animations to Text</span></span>
<span data-ttu-id="5ff37-103">動畫可以變更應用程式中文字的顯示和外觀。</span><span class="sxs-lookup"><span data-stu-id="5ff37-103">Animations can alter the display and appearance of text in your application.</span></span> <span data-ttu-id="5ff37-104">下列範例會使用不同類型的動畫來影響中的文字顯示<xref:System.Windows.Controls.TextBlock>控制項。</span><span class="sxs-lookup"><span data-stu-id="5ff37-104">The following examples use different types of animations to affect the display of text in a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ff37-105">範例</span><span class="sxs-lookup"><span data-stu-id="5ff37-105">Example</span></span>  
 <span data-ttu-id="5ff37-106">下列範例會使用<xref:System.Windows.Media.Animation.DoubleAnimation>以動畫顯示文字區塊的寬度。</span><span class="sxs-lookup"><span data-stu-id="5ff37-106">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the width of the text block.</span></span> <span data-ttu-id="5ff37-107">寬度值會在 10 秒的期間內從文字區塊的寬度變更為 0，然後回復寬度值並繼續進行。</span><span class="sxs-lookup"><span data-stu-id="5ff37-107">The width value changes from the width of the text block to 0 over a duration of 10 seconds, and then reverses the width values and continues.</span></span> <span data-ttu-id="5ff37-108">這種動畫會建立擦去效果。</span><span class="sxs-lookup"><span data-stu-id="5ff37-108">This type of animation creates a wipe effect.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample1)]  
  
 <span data-ttu-id="5ff37-109">下列範例會使用<xref:System.Windows.Media.Animation.DoubleAnimation>以動畫顯示文字區塊的不透明度。</span><span class="sxs-lookup"><span data-stu-id="5ff37-109">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the opacity of the text block.</span></span> <span data-ttu-id="5ff37-110">不透明度值會在 5 秒的期間內從 1.0 變更為 0，然後回復不透明度值並繼續進行。</span><span class="sxs-lookup"><span data-stu-id="5ff37-110">The opacity value changes from 1.0 to 0 over a duration of 5 seconds, and then reverses the opacity values and continues.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample2)]  
  
 <span data-ttu-id="5ff37-111">下圖顯示的效果<xref:System.Windows.Controls.TextBlock>變更它的不透明度從控制項`1.00`要`0.00`期間所定義的 5 秒間隔<xref:System.Windows.Media.Animation.Timeline.Duration%2A>。</span><span class="sxs-lookup"><span data-stu-id="5ff37-111">The following diagram shows the effect of the <xref:System.Windows.Controls.TextBlock> control changing its opacity from `1.00` to `0.00` during the 5-second interval defined by the <xref:System.Windows.Media.Animation.Timeline.Duration%2A>.</span></span>  
  
 ![不是透明度從 1.00 變更為 0.00 的文字。](./media/how-to-apply-animations-to-text/faded-text-opacity-change.png)  
   
 <span data-ttu-id="5ff37-113">下列範例會使用<xref:System.Windows.Media.Animation.ColorAnimation>以動畫顯示文字區塊的前景色彩。</span><span class="sxs-lookup"><span data-stu-id="5ff37-113">The following example uses a <xref:System.Windows.Media.Animation.ColorAnimation> to animate the foreground color of the text block.</span></span> <span data-ttu-id="5ff37-114">前景色彩值會在 5 秒的期間內從某種色彩變更為第二種色彩，然後回復色彩值並繼續進行。</span><span class="sxs-lookup"><span data-stu-id="5ff37-114">The foreground color value changes from one color to a second color over a duration of 5 seconds, and then reverses the color values and continues.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample3)]  
  
 <span data-ttu-id="5ff37-115">下列範例會使用<xref:System.Windows.Media.Animation.DoubleAnimation>旋轉文字區塊。</span><span class="sxs-lookup"><span data-stu-id="5ff37-115">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to rotate the text block.</span></span> <span data-ttu-id="5ff37-116">文字區塊會在 20 秒的期間內執行完整旋轉，然後繼續重複進行旋轉。</span><span class="sxs-lookup"><span data-stu-id="5ff37-116">The text block performs a full rotation over a duration of 20 seconds, and then continues to repeat the rotation.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample4](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample4)]  
  
## <a name="see-also"></a><span data-ttu-id="5ff37-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5ff37-117">See also</span></span>
- [<span data-ttu-id="5ff37-118">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="5ff37-118">Animation Overview</span></span>](../graphics-multimedia/animation-overview.md)

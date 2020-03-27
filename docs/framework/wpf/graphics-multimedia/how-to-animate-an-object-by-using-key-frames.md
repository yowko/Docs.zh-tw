---
title: 如何：使用主要畫面格建立物件的動畫
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], objects with key frames
- key frames [WPF], animating objects with
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
ms.openlocfilehash: 0bc33b189fd856dbe8106c1db35bc18e27ea131e
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344710"
---
# <a name="how-to-animate-an-object-by-using-key-frames"></a><span data-ttu-id="80e12-102">如何：使用主要畫面格建立物件的動畫</span><span class="sxs-lookup"><span data-stu-id="80e12-102">How to: Animate an Object by Using Key Frames</span></span>
<span data-ttu-id="80e12-103">此示例演示如何使用關鍵幀為物件設置動畫，在此示例中，物件是<xref:System.Windows.Controls.Page.Background%2A><xref:System.Windows.Controls.Page>控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="80e12-103">This example shows how to animate an object, which in this example is the <xref:System.Windows.Controls.Page.Background%2A> property of a <xref:System.Windows.Controls.Page> control, by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="80e12-104">範例</span><span class="sxs-lookup"><span data-stu-id="80e12-104">Example</span></span>  
 <span data-ttu-id="80e12-105">下面的示例使用 類<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>為控制項<xref:System.Windows.Controls.Page.Background%2A>的屬性的顏色更改設置<xref:System.Windows.Controls.Page>動畫。</span><span class="sxs-lookup"><span data-stu-id="80e12-105">The following example uses the <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> class to animate color changes for the <xref:System.Windows.Controls.Page.Background%2A> property of a <xref:System.Windows.Controls.Page> control.</span></span> <span data-ttu-id="80e12-106">示例動畫會定期更改為不同的背景畫筆。</span><span class="sxs-lookup"><span data-stu-id="80e12-106">The example animation changes to a different background brush at regular intervals.</span></span> <span data-ttu-id="80e12-107">此動畫使用<xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>類創建三個不同的關鍵幀。</span><span class="sxs-lookup"><span data-stu-id="80e12-107">This animation uses the <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> class to create three different key frames.</span></span> <span data-ttu-id="80e12-108">動畫使用關鍵幀的方式如下：</span><span class="sxs-lookup"><span data-stu-id="80e12-108">The animation uses key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="80e12-109">在第一秒結束時，為<xref:System.Windows.Media.LinearGradientBrush>類的實例設置動畫。</span><span class="sxs-lookup"><span data-stu-id="80e12-109">At the end of the first second, animates an instance of the <xref:System.Windows.Media.LinearGradientBrush> class.</span></span> <span data-ttu-id="80e12-110">此示例的這一部分將線性漸層應用於背景顏色，以便顏色從黃色轉換為橙色轉換為紅色。</span><span class="sxs-lookup"><span data-stu-id="80e12-110">This section of the example applies a linear gradient to the background color so that the color transitions from yellow to orange to red.</span></span>  
  
2. <span data-ttu-id="80e12-111">在下一秒結束時，為<xref:System.Windows.Media.RadialGradientBrush>類的實例設置動畫。</span><span class="sxs-lookup"><span data-stu-id="80e12-111">At the end of the next second, animates an instance of the <xref:System.Windows.Media.RadialGradientBrush> class.</span></span> <span data-ttu-id="80e12-112">此示例的這一部分將徑向漸變應用於背景顏色，以便顏色從白色轉換為藍色轉換為黑色。</span><span class="sxs-lookup"><span data-stu-id="80e12-112">This section of the example applies a radial gradient to the background color so that the color transitions from white to blue to black.</span></span>  
  
3. <span data-ttu-id="80e12-113">在第三秒結束時，為<xref:System.Windows.Media.DrawingBrush>類的實例設置動畫。</span><span class="sxs-lookup"><span data-stu-id="80e12-113">At the end of the third second, animates an instance of the <xref:System.Windows.Media.DrawingBrush> class.</span></span> <span data-ttu-id="80e12-114">此示例的這一部分將棋盤圖案應用於背景。</span><span class="sxs-lookup"><span data-stu-id="80e12-114">This section of the example applies a checkerboard pattern to the background.</span></span>  
  
4. <span data-ttu-id="80e12-115">動畫再次開始並無限期重複。</span><span class="sxs-lookup"><span data-stu-id="80e12-115">The animation begins again and repeats indefinitely.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="80e12-116"><xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>是可用於<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>類的唯一類型的關鍵幀。</span><span class="sxs-lookup"><span data-stu-id="80e12-116"><xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> is the only type of key frame that you can use with the <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> class.</span></span> <span data-ttu-id="80e12-117">關鍵幀（<xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>如創建值的突然更改）即此示例中的顏色更改突然發生。</span><span class="sxs-lookup"><span data-stu-id="80e12-117">Key frames like <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> create sudden changes in values, that is, the color changes in this example occur suddenly.</span></span>  
  
 [!code-xaml[keyframes_snip#ObjectAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ObjectAnimationUsingKeyFramesExample.xaml#objectanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="80e12-118">如需完整的範例，請參閱[主要畫面格動畫範例](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)。</span><span class="sxs-lookup"><span data-stu-id="80e12-118">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80e12-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80e12-119">See also</span></span>

- <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>
- <xref:System.Windows.Controls.Page.Background%2A>
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>
- <xref:System.Windows.Media.LinearGradientBrush>
- <xref:System.Windows.Media.RadialGradientBrush>
- <xref:System.Windows.Media.DrawingBrush>
- [<span data-ttu-id="80e12-120">主要畫面格動畫概觀</span><span class="sxs-lookup"><span data-stu-id="80e12-120">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="80e12-121">關於主要畫面格操作說明的主題</span><span class="sxs-lookup"><span data-stu-id="80e12-121">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)

---
title: 作法：使用主要畫面格建立物件的動畫
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], objects with key frames
- key frames [WPF], animating objects with
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
ms.openlocfilehash: ffbe1845b634c8f94eb6a10dfa44fcf9903e0cd5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933913"
---
# <a name="how-to-animate-an-object-by-using-key-frames"></a><span data-ttu-id="1dd71-102">HOW TO：使用主要畫面格建立物件的動畫</span><span class="sxs-lookup"><span data-stu-id="1dd71-102">How to: Animate an Object by Using Key Frames</span></span>
<span data-ttu-id="1dd71-103">這個範例示範如何使用主要畫面格, 以動畫顯示物件 (在<xref:System.Windows.Controls.Page.Background%2A>此範例中<xref:System.Windows.Controls.Page>為控制項的屬性)。</span><span class="sxs-lookup"><span data-stu-id="1dd71-103">This example shows how to animate an object, which in this example is the <xref:System.Windows.Controls.Page.Background%2A> property of a <xref:System.Windows.Controls.Page> control, by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1dd71-104">範例</span><span class="sxs-lookup"><span data-stu-id="1dd71-104">Example</span></span>  
 <span data-ttu-id="1dd71-105">下列範例會使用<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>類別, 以動畫顯示<xref:System.Windows.Controls.Page>控制項<xref:System.Windows.Controls.Page.Background%2A>屬性的色彩變更。</span><span class="sxs-lookup"><span data-stu-id="1dd71-105">The following example uses the <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> class to animate color changes for the <xref:System.Windows.Controls.Page.Background%2A> property of a <xref:System.Windows.Controls.Page> control.</span></span> <span data-ttu-id="1dd71-106">範例動畫會以固定間隔變更為不同的背景筆刷。</span><span class="sxs-lookup"><span data-stu-id="1dd71-106">The example animation changes to a different background brush at regular intervals.</span></span> <span data-ttu-id="1dd71-107">這個動畫會使用<xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>類別來建立三個不同的主要畫面格。</span><span class="sxs-lookup"><span data-stu-id="1dd71-107">This animation uses the <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> class to create three different key frames.</span></span> <span data-ttu-id="1dd71-108">動畫會以下列方式使用主要畫面格:</span><span class="sxs-lookup"><span data-stu-id="1dd71-108">The animation uses key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="1dd71-109">在第一秒結束時, 會以動畫呈現<xref:System.Windows.Media.LinearGradientBrush>類別的實例。</span><span class="sxs-lookup"><span data-stu-id="1dd71-109">At the end of the first second, animates an instance of the <xref:System.Windows.Media.LinearGradientBrush> class.</span></span> <span data-ttu-id="1dd71-110">範例的這個部分會將線性漸層套用至背景色彩, 讓色彩從黃色轉換成紅色。</span><span class="sxs-lookup"><span data-stu-id="1dd71-110">This section of the example applies a linear gradient to the background color so that the color transitions from yellow to orange to red.</span></span>  
  
2. <span data-ttu-id="1dd71-111">在下一秒結束時, 會以動畫呈現<xref:System.Windows.Media.RadialGradientBrush>類別的實例。</span><span class="sxs-lookup"><span data-stu-id="1dd71-111">At the end of the next second, animates an instance of the <xref:System.Windows.Media.RadialGradientBrush> class.</span></span> <span data-ttu-id="1dd71-112">範例的這個部分會將放射漸層套用至背景色彩, 讓色彩從白色轉換成黑色。</span><span class="sxs-lookup"><span data-stu-id="1dd71-112">This section of the example applies a radial gradient to the background color so that the color transitions from white to blue to black.</span></span>  
  
3. <span data-ttu-id="1dd71-113">在第三秒結束時, 會以動畫呈現<xref:System.Windows.Media.DrawingBrush>類別的實例。</span><span class="sxs-lookup"><span data-stu-id="1dd71-113">At the end of the third second, animates an instance of the <xref:System.Windows.Media.DrawingBrush> class.</span></span> <span data-ttu-id="1dd71-114">範例的這個部分會將棋盤圖樣套用到背景。</span><span class="sxs-lookup"><span data-stu-id="1dd71-114">This section of the example applies a checkerboard pattern to the background.</span></span>  
  
4. <span data-ttu-id="1dd71-115">動畫會重新開始, 並無限期地重複。</span><span class="sxs-lookup"><span data-stu-id="1dd71-115">The animation begins again and repeats indefinitely.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1dd71-116"><xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>是唯一可與<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>類別搭配使用的主要畫面格類型。</span><span class="sxs-lookup"><span data-stu-id="1dd71-116"><xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> is the only type of key frame that you can use with the <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> class.</span></span> <span data-ttu-id="1dd71-117">像<xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>是在值中建立突然變更的主要畫面格 (也就是此範例中的色彩變更突然發生)。</span><span class="sxs-lookup"><span data-stu-id="1dd71-117">Key frames like <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> create sudden changes in values, that is, the color changes in this example occur suddenly.</span></span>  
  
 [!code-xaml[keyframes_snip#ObjectAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ObjectAnimationUsingKeyFramesExample.xaml#objectanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="1dd71-118">如需完整的範例，請參閱[主要畫面格動畫範例](https://go.microsoft.com/fwlink/?LinkID=160012)。</span><span class="sxs-lookup"><span data-stu-id="1dd71-118">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dd71-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1dd71-119">See also</span></span>

- <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>
- <xref:System.Windows.Controls.Page.Background%2A>
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>
- <xref:System.Windows.Media.LinearGradientBrush>
- <xref:System.Windows.Media.RadialGradientBrush>
- <xref:System.Windows.Media.DrawingBrush>
- [<span data-ttu-id="1dd71-120">主要畫面格動畫概觀</span><span class="sxs-lookup"><span data-stu-id="1dd71-120">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="1dd71-121">主要畫面格操作說明主題</span><span class="sxs-lookup"><span data-stu-id="1dd71-121">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)

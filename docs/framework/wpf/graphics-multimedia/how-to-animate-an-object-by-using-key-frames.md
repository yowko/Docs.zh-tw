---
title: HOW TO：使用主要畫面格建立物件的動畫
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], objects with key frames
- key frames [WPF], animating objects with
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
ms.openlocfilehash: eb9de4098c5fb9bde74fa93dda6dd5a878ed0339
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54697526"
---
# <a name="how-to-animate-an-object-by-using-key-frames"></a><span data-ttu-id="888dc-102">HOW TO：使用主要畫面格建立物件的動畫</span><span class="sxs-lookup"><span data-stu-id="888dc-102">How to: Animate an Object by Using Key Frames</span></span>
<span data-ttu-id="888dc-103">此範例示範如何以動畫顯示物件，這在此範例中是<xref:System.Windows.Controls.Page.Background%2A>屬性<xref:System.Windows.Controls.Page>控制項，使用主要畫面格。</span><span class="sxs-lookup"><span data-stu-id="888dc-103">This example shows how to animate an object, which in this example is the <xref:System.Windows.Controls.Page.Background%2A> property of a <xref:System.Windows.Controls.Page> control, by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="888dc-104">範例</span><span class="sxs-lookup"><span data-stu-id="888dc-104">Example</span></span>  
 <span data-ttu-id="888dc-105">下列範例會使用<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>類別以動畫顯示色彩變更為<xref:System.Windows.Controls.Page.Background%2A>屬性<xref:System.Windows.Controls.Page>控制項。</span><span class="sxs-lookup"><span data-stu-id="888dc-105">The following example uses the <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> class to animate color changes for the <xref:System.Windows.Controls.Page.Background%2A> property of a <xref:System.Windows.Controls.Page> control.</span></span> <span data-ttu-id="888dc-106">範例動畫會定期變成不同的背景筆刷。</span><span class="sxs-lookup"><span data-stu-id="888dc-106">The example animation changes to a different background brush at regular intervals.</span></span> <span data-ttu-id="888dc-107">這個動畫使用<xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>類別來建立三個不同的主要畫面格。</span><span class="sxs-lookup"><span data-stu-id="888dc-107">This animation uses the <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> class to create three different key frames.</span></span> <span data-ttu-id="888dc-108">動畫會使用主要畫面格，以下列方式：</span><span class="sxs-lookup"><span data-stu-id="888dc-108">The animation uses key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="888dc-109">在第一次的第二個結束時，以動畫顯示的執行個體<xref:System.Windows.Media.LinearGradientBrush>類別。</span><span class="sxs-lookup"><span data-stu-id="888dc-109">At the end of the first second, animates an instance of the <xref:System.Windows.Media.LinearGradientBrush> class.</span></span> <span data-ttu-id="888dc-110">本節的範例適用於線性漸層背景色彩，使色彩從黃色轉換為橙色為紅色。</span><span class="sxs-lookup"><span data-stu-id="888dc-110">This section of the example applies a linear gradient to the background color so that the color transitions from yellow to orange to red.</span></span>  
  
2.  <span data-ttu-id="888dc-111">在下一步 的第二個結束時，以動畫顯示的執行個體<xref:System.Windows.Media.RadialGradientBrush>類別。</span><span class="sxs-lookup"><span data-stu-id="888dc-111">At the end of the next second, animates an instance of the <xref:System.Windows.Media.RadialGradientBrush> class.</span></span> <span data-ttu-id="888dc-112">本節的範例適用於放射狀漸層背景色彩，以便從白色到黑色藍色的色彩轉換。</span><span class="sxs-lookup"><span data-stu-id="888dc-112">This section of the example applies a radial gradient to the background color so that the color transitions from white to blue to black.</span></span>  
  
3.  <span data-ttu-id="888dc-113">在第三個第二個結束時，以動畫顯示的執行個體<xref:System.Windows.Media.DrawingBrush>類別。</span><span class="sxs-lookup"><span data-stu-id="888dc-113">At the end of the third second, animates an instance of the <xref:System.Windows.Media.DrawingBrush> class.</span></span> <span data-ttu-id="888dc-114">本節的範例適用於在背景以棋盤式圖樣。</span><span class="sxs-lookup"><span data-stu-id="888dc-114">This section of the example applies a checkerboard pattern to the background.</span></span>  
  
4.  <span data-ttu-id="888dc-115">再次開始動畫，並且不斷重複。</span><span class="sxs-lookup"><span data-stu-id="888dc-115">The animation begins again and repeats indefinitely.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="888dc-116"><xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> 是唯一的類型，您可以搭配使用的主要畫面格<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>類別。</span><span class="sxs-lookup"><span data-stu-id="888dc-116"><xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> is the only type of key frame that you can use with the <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> class.</span></span> <span data-ttu-id="888dc-117">主要畫面格像<xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>也就是在值中，建立突然的變更，在此範例中的色彩變更會突然發生。</span><span class="sxs-lookup"><span data-stu-id="888dc-117">Key frames like <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> create sudden changes in values, that is, the color changes in this example occur suddenly.</span></span>  
  
 [!code-xaml[keyframes_snip#ObjectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ObjectAnimationUsingKeyFramesExample.xaml#objectanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="888dc-118">如需完整的範例，請參閱[主要畫面格動畫範例](https://go.microsoft.com/fwlink/?LinkID=160012)。</span><span class="sxs-lookup"><span data-stu-id="888dc-118">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="888dc-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="888dc-119">See also</span></span>
- <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>
- <xref:System.Windows.Controls.Page.Background%2A>
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>
- <xref:System.Windows.Media.LinearGradientBrush>
- <xref:System.Windows.Media.RadialGradientBrush>
- <xref:System.Windows.Media.DrawingBrush>
- [<span data-ttu-id="888dc-120">主要畫面格動畫概觀</span><span class="sxs-lookup"><span data-stu-id="888dc-120">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)
- [<span data-ttu-id="888dc-121">主要畫面格操作說明主題</span><span class="sxs-lookup"><span data-stu-id="888dc-121">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)

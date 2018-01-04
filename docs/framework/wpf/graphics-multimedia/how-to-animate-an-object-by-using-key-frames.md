---
title: "如何：使用主要畫面格建立物件的動畫"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], objects with key frames
- key frames [WPF], animating objects with
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5f513cda540b3337f1510ee0c46419a12023bcb6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-an-object-by-using-key-frames"></a><span data-ttu-id="eeca0-102">如何：使用主要畫面格建立物件的動畫</span><span class="sxs-lookup"><span data-stu-id="eeca0-102">How to: Animate an Object by Using Key Frames</span></span>
<span data-ttu-id="eeca0-103">這個範例示範如何建立物件，即在此範例中的<xref:System.Windows.Controls.Page.Background%2A>屬性<xref:System.Windows.Controls.Page>控制項，使用主要畫面格。</span><span class="sxs-lookup"><span data-stu-id="eeca0-103">This example shows how to animate an object, which in this example is the <xref:System.Windows.Controls.Page.Background%2A> property of a <xref:System.Windows.Controls.Page> control, by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eeca0-104">範例</span><span class="sxs-lookup"><span data-stu-id="eeca0-104">Example</span></span>  
 <span data-ttu-id="eeca0-105">下列範例會使用<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>類別以動畫方式顯示色彩變更為<xref:System.Windows.Controls.Page.Background%2A>屬性<xref:System.Windows.Controls.Page>控制項。</span><span class="sxs-lookup"><span data-stu-id="eeca0-105">The following example uses the <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> class to animate color changes for the <xref:System.Windows.Controls.Page.Background%2A> property of a <xref:System.Windows.Controls.Page> control.</span></span> <span data-ttu-id="eeca0-106">範例動畫會定期變成不同的背景筆刷。</span><span class="sxs-lookup"><span data-stu-id="eeca0-106">The example animation changes to a different background brush at regular intervals.</span></span> <span data-ttu-id="eeca0-107">這個動畫使用<xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>類別來建立三個不同的主要畫面格。</span><span class="sxs-lookup"><span data-stu-id="eeca0-107">This animation uses the <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> class to create three different key frames.</span></span> <span data-ttu-id="eeca0-108">動畫會以下列方式使用的主要畫面格：</span><span class="sxs-lookup"><span data-stu-id="eeca0-108">The animation uses key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="eeca0-109">在第一次的第二個結尾，以動畫顯示的執行個體<xref:System.Windows.Media.LinearGradientBrush>類別。</span><span class="sxs-lookup"><span data-stu-id="eeca0-109">At the end of the first second, animates an instance of the <xref:System.Windows.Media.LinearGradientBrush> class.</span></span> <span data-ttu-id="eeca0-110">本節的範例適用於線性漸層背景色彩，使色彩從黃色轉換為紅色的橙色。</span><span class="sxs-lookup"><span data-stu-id="eeca0-110">This section of the example applies a linear gradient to the background color so that the color transitions from yellow to orange to red.</span></span>  
  
2.  <span data-ttu-id="eeca0-111">在下一步的第二個結尾，以動畫顯示的執行個體<xref:System.Windows.Media.RadialGradientBrush>類別。</span><span class="sxs-lookup"><span data-stu-id="eeca0-111">At the end of the next second, animates an instance of the <xref:System.Windows.Media.RadialGradientBrush> class.</span></span> <span data-ttu-id="eeca0-112">本節的範例套用於放射狀漸層的背景色彩，以便從為藍色為黑色的白色轉換的色彩。</span><span class="sxs-lookup"><span data-stu-id="eeca0-112">This section of the example applies a radial gradient to the background color so that the color transitions from white to blue to black.</span></span>  
  
3.  <span data-ttu-id="eeca0-113">在第三個第二個結尾，以動畫顯示的執行個體<xref:System.Windows.Media.DrawingBrush>類別。</span><span class="sxs-lookup"><span data-stu-id="eeca0-113">At the end of the third second, animates an instance of the <xref:System.Windows.Media.DrawingBrush> class.</span></span> <span data-ttu-id="eeca0-114">本節的範例會套用至背景棋盤式圖樣。</span><span class="sxs-lookup"><span data-stu-id="eeca0-114">This section of the example applies a checkerboard pattern to the background.</span></span>  
  
4.  <span data-ttu-id="eeca0-115">動畫會重新開始計算，並且不斷重複。</span><span class="sxs-lookup"><span data-stu-id="eeca0-115">The animation begins again and repeats indefinitely.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eeca0-116"><xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>是您可以搭配使用的主要畫面格的唯一類型<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>類別。</span><span class="sxs-lookup"><span data-stu-id="eeca0-116"><xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> is the only type of key frame that you can use with the <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> class.</span></span> <span data-ttu-id="eeca0-117">主要畫面格像<xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>也就是建立值 中的突變、 突然出現在此範例中的色彩變更。</span><span class="sxs-lookup"><span data-stu-id="eeca0-117">Key frames like <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> create sudden changes in values, that is, the color changes in this example occur suddenly.</span></span>  
  
 [!code-xaml[keyframes_snip#ObjectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ObjectAnimationUsingKeyFramesExample.xaml#objectanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="eeca0-118">如需完整的範例，請參閱[主要畫面格動畫範例](http://go.microsoft.com/fwlink/?LinkID=160012)。</span><span class="sxs-lookup"><span data-stu-id="eeca0-118">For the complete sample, see [KeyFrame Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eeca0-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="eeca0-119">See Also</span></span>  
 <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>  
 <xref:System.Windows.Controls.Page.Background%2A>  
 <xref:System.Windows.Controls.Page>  
 <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>  
 <xref:System.Windows.Media.LinearGradientBrush>  
 <xref:System.Windows.Media.RadialGradientBrush>  
 <xref:System.Windows.Media.DrawingBrush>  
 [<span data-ttu-id="eeca0-120">主要畫面格動畫概觀</span><span class="sxs-lookup"><span data-stu-id="eeca0-120">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="eeca0-121">主要畫面格操作說明主題</span><span class="sxs-lookup"><span data-stu-id="eeca0-121">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)

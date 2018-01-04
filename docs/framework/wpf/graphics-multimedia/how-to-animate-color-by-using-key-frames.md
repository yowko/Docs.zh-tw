---
title: "操作說明：使用主要畫面格建立色彩的動畫"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [WPF], animating with key frames
- animation [WPF], colors with key frames
- key frames [WPF], animating colors with
ms.assetid: ab04ffa6-4de9-4d5b-a3b4-4e35d5b2ef35
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4c6b4dc6ee04b20f47599bad84dda4648da255ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-color-by-using-key-frames"></a><span data-ttu-id="d96f3-102">操作說明：使用主要畫面格建立色彩的動畫</span><span class="sxs-lookup"><span data-stu-id="d96f3-102">How to: Animate Color by Using Key Frames</span></span>
<span data-ttu-id="d96f3-103">此範例示範如何以動畫方式顯示<xref:System.Windows.Media.SolidColorBrush.Color%2A>的<xref:System.Windows.Media.SolidColorBrush>所使用的主要畫面格。</span><span class="sxs-lookup"><span data-stu-id="d96f3-103">This example shows how to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> of a <xref:System.Windows.Media.SolidColorBrush> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d96f3-104">範例</span><span class="sxs-lookup"><span data-stu-id="d96f3-104">Example</span></span>  
 <span data-ttu-id="d96f3-105">下列範例會使用<xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>類別以動畫方式顯示<xref:System.Windows.Media.SolidColorBrush.Color%2A>屬性<xref:System.Windows.Media.SolidColorBrush>。</span><span class="sxs-lookup"><span data-stu-id="d96f3-105">The following example uses the <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> property of a <xref:System.Windows.Media.SolidColorBrush>.</span></span> <span data-ttu-id="d96f3-106">這個動畫會以下列方式使用三個主要畫面格：</span><span class="sxs-lookup"><span data-stu-id="d96f3-106">This animation uses three key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="d96f3-107">在第一個兩秒中，會使用的執行個體<xref:System.Windows.Media.Animation.LinearColorKeyFrame>類別來逐漸從綠色將色彩變更為紅色。</span><span class="sxs-lookup"><span data-stu-id="d96f3-107">During the first two seconds, uses an instance of the <xref:System.Windows.Media.Animation.LinearColorKeyFrame> class to gradually change the color from green to red.</span></span> <span data-ttu-id="d96f3-108">線性的主要畫面格喜歡<xref:System.Windows.Media.Animation.LinearColorKeyFrame>建立值之間的平順地線性轉換。</span><span class="sxs-lookup"><span data-stu-id="d96f3-108">Linear key frames like <xref:System.Windows.Media.Animation.LinearColorKeyFrame> create a smooth linear transition between values.</span></span>  
  
2.  <span data-ttu-id="d96f3-109">在下個結束半秒，會使用的執行個體<xref:System.Windows.Media.Animation.DiscreteColorKeyFrame>類別，以快速地從紅色色彩變更為黃色。</span><span class="sxs-lookup"><span data-stu-id="d96f3-109">During the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> class to quickly change the color from red to yellow.</span></span> <span data-ttu-id="d96f3-110">獨立的主要畫面格喜歡<xref:System.Windows.Media.Animation.DiscreteColorKeyFrame>建立突變之間的值，也就是，動畫的這個部分中的色彩變更發生快速，並不是難以察覺。</span><span class="sxs-lookup"><span data-stu-id="d96f3-110">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> create sudden changes between values, that is, the color change in this part of the animation occurs quickly and is not subtle.</span></span>  
  
3.  <span data-ttu-id="d96f3-111">期間最後兩秒中，會使用的執行個體<xref:System.Windows.Media.Animation.SplineColorKeyFrame>再次變更色彩的類別，從黃色備份目前為綠色。</span><span class="sxs-lookup"><span data-stu-id="d96f3-111">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineColorKeyFrame> class to change the color again—this time from yellow back to green.</span></span> <span data-ttu-id="d96f3-112">曲線主要畫面格喜歡<xref:System.Windows.Media.Animation.SplineColorKeyFrame>建立變數的值根據值之間轉換<xref:System.Windows.Media.Animation.SplineColorKeyFrame.KeySpline%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="d96f3-112">Spline key frames like <xref:System.Windows.Media.Animation.SplineColorKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineColorKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="d96f3-113">在此範例中，色彩變更一開始速度緩慢，然後在接近時間區段結尾時會以指數方式加速。</span><span class="sxs-lookup"><span data-stu-id="d96f3-113">In this example, the change in color begins slowly and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/ColorAnimationUsingKeyFramesExample.cs#coloranimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/coloranimationusingkeyframesexample.vb#coloranimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ColorAnimationUsingKeyFramesExample.xaml#coloranimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="d96f3-114">如需完整的範例，請參閱[主要畫面格動畫範例](http://go.microsoft.com/fwlink/?LinkID=160012)。</span><span class="sxs-lookup"><span data-stu-id="d96f3-114">For the complete sample, see [KeyFrame Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d96f3-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="d96f3-115">See Also</span></span>  
 <xref:System.Windows.Media.SolidColorBrush.Color%2A>  
 <xref:System.Windows.Media.SolidColorBrush>  
 <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>  
 [<span data-ttu-id="d96f3-116">主要畫面格動畫概觀</span><span class="sxs-lookup"><span data-stu-id="d96f3-116">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="d96f3-117">主要畫面格操作說明主題</span><span class="sxs-lookup"><span data-stu-id="d96f3-117">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)

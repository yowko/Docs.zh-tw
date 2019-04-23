---
title: HOW TO：使用主要畫面格建立色彩的動畫
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [WPF], animating with key frames
- animation [WPF], colors with key frames
- key frames [WPF], animating colors with
ms.assetid: ab04ffa6-4de9-4d5b-a3b4-4e35d5b2ef35
ms.openlocfilehash: e579c4beb757ccf58eb1b9ca1f3852a5b96cac1a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59326082"
---
# <a name="how-to-animate-color-by-using-key-frames"></a><span data-ttu-id="a91f8-102">HOW TO：使用主要畫面格建立色彩的動畫</span><span class="sxs-lookup"><span data-stu-id="a91f8-102">How to: Animate Color by Using Key Frames</span></span>
<span data-ttu-id="a91f8-103">此範例示範如何建立動畫<xref:System.Windows.Media.SolidColorBrush.Color%2A>的<xref:System.Windows.Media.SolidColorBrush>使用主要畫面格。</span><span class="sxs-lookup"><span data-stu-id="a91f8-103">This example shows how to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> of a <xref:System.Windows.Media.SolidColorBrush> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a91f8-104">範例</span><span class="sxs-lookup"><span data-stu-id="a91f8-104">Example</span></span>  
 <span data-ttu-id="a91f8-105">下列範例會使用<xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>類別以動畫顯示<xref:System.Windows.Media.SolidColorBrush.Color%2A>屬性<xref:System.Windows.Media.SolidColorBrush>。</span><span class="sxs-lookup"><span data-stu-id="a91f8-105">The following example uses the <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> property of a <xref:System.Windows.Media.SolidColorBrush>.</span></span> <span data-ttu-id="a91f8-106">這個動畫會以下列方式使用三個主要畫面格：</span><span class="sxs-lookup"><span data-stu-id="a91f8-106">This animation uses three key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="a91f8-107">在前的兩秒期間使用的執行個體<xref:System.Windows.Media.Animation.LinearColorKeyFrame>逐漸變更色彩從綠色到紅色的類別。</span><span class="sxs-lookup"><span data-stu-id="a91f8-107">During the first two seconds, uses an instance of the <xref:System.Windows.Media.Animation.LinearColorKeyFrame> class to gradually change the color from green to red.</span></span> <span data-ttu-id="a91f8-108">線性主要畫面格喜歡<xref:System.Windows.Media.Animation.LinearColorKeyFrame>建立平滑的線性轉換值之間。</span><span class="sxs-lookup"><span data-stu-id="a91f8-108">Linear key frames like <xref:System.Windows.Media.Animation.LinearColorKeyFrame> create a smooth linear transition between values.</span></span>  
  
2. <span data-ttu-id="a91f8-109">下一步 結束期間半秒，使用的執行個體<xref:System.Windows.Media.Animation.DiscreteColorKeyFrame>類別，以快速地從紅色的色彩變更為黃色。</span><span class="sxs-lookup"><span data-stu-id="a91f8-109">During the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> class to quickly change the color from red to yellow.</span></span> <span data-ttu-id="a91f8-110">特定主要畫面格喜歡<xref:System.Windows.Media.Animation.DiscreteColorKeyFrame>突然之間建立變更的值，也就是，動畫的這個部分中的色彩變更很快就會完成，而不是微量。</span><span class="sxs-lookup"><span data-stu-id="a91f8-110">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> create sudden changes between values, that is, the color change in this part of the animation occurs quickly and is not subtle.</span></span>  
  
3. <span data-ttu-id="a91f8-111">在最後的兩秒期間使用的執行個體<xref:System.Windows.Media.Animation.SplineColorKeyFrame>再次變更色彩的類別，這次從黃色變回綠色。</span><span class="sxs-lookup"><span data-stu-id="a91f8-111">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineColorKeyFrame> class to change the color again—this time from yellow back to green.</span></span> <span data-ttu-id="a91f8-112">曲線主要畫面格喜歡<xref:System.Windows.Media.Animation.SplineColorKeyFrame>變數之間建立轉換的值根據<xref:System.Windows.Media.Animation.SplineColorKeyFrame.KeySpline%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="a91f8-112">Spline key frames like <xref:System.Windows.Media.Animation.SplineColorKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineColorKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="a91f8-113">在此範例中，色彩變更一開始速度緩慢，然後在接近時間區段結尾時會以指數方式加速。</span><span class="sxs-lookup"><span data-stu-id="a91f8-113">In this example, the change in color begins slowly and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/ColorAnimationUsingKeyFramesExample.cs#coloranimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/coloranimationusingkeyframesexample.vb#coloranimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ColorAnimationUsingKeyFramesExample.xaml#coloranimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="a91f8-114">如需完整的範例，請參閱[主要畫面格動畫範例](https://go.microsoft.com/fwlink/?LinkID=160012)。</span><span class="sxs-lookup"><span data-stu-id="a91f8-114">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a91f8-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a91f8-115">See also</span></span>

- <xref:System.Windows.Media.SolidColorBrush.Color%2A>
- <xref:System.Windows.Media.SolidColorBrush>
- <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>
- [<span data-ttu-id="a91f8-116">主要畫面格動畫概觀</span><span class="sxs-lookup"><span data-stu-id="a91f8-116">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="a91f8-117">主要畫面格操作說明主題</span><span class="sxs-lookup"><span data-stu-id="a91f8-117">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)

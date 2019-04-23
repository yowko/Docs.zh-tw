---
title: HOW TO：以動畫播放媒體
ms.date: 03/30/2017
helpviewer_keywords:
- multimedia [WPF], playback with animations
- playback of media [WPF], with animations
- animation [WPF], media playback with
- media [WPF], playback with animations
ms.assetid: 8982b7b7-1c6c-4b24-8801-b328862975f5
ms.openlocfilehash: 200f9d62c67a02088fe5a5789cdb41a04837d430
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59079899"
---
# <a name="how-to-play-media-with-animations"></a><span data-ttu-id="e2faf-102">HOW TO：以動畫播放媒體</span><span class="sxs-lookup"><span data-stu-id="e2faf-102">How to: Play Media with Animations</span></span>
<span data-ttu-id="e2faf-103">此範例示範如何同時播放媒體和動畫，使用<xref:System.Windows.Media.MediaTimeline>並<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>類別，在同一個<xref:System.Windows.Media.Animation.Storyboard>。</span><span class="sxs-lookup"><span data-stu-id="e2faf-103">This example shows how to play media and animations at the same time by using the <xref:System.Windows.Media.MediaTimeline> and <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> classes in the same <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2faf-104">範例</span><span class="sxs-lookup"><span data-stu-id="e2faf-104">Example</span></span>  
 <span data-ttu-id="e2faf-105">您可以使用一或多個<xref:System.Windows.Media.MediaTimeline>中的物件<xref:System.Windows.Media.Animation.Storyboard>與其它<xref:System.Windows.Media.Animation.Timeline>物件，例如動畫。</span><span class="sxs-lookup"><span data-stu-id="e2faf-105">You can use one or more <xref:System.Windows.Media.MediaTimeline> objects in a <xref:System.Windows.Media.Animation.Storyboard> together with other <xref:System.Windows.Media.Animation.Timeline> objects, such as animations.</span></span>  
  
 <span data-ttu-id="e2faf-106">下列範例會設定<xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A>的屬性<xref:System.Windows.Media.Animation.Storyboard>的值`Slip`，以指定動畫不會進行直到媒體 （在此範例影片） 進行。</span><span class="sxs-lookup"><span data-stu-id="e2faf-106">The following example sets the <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A> property of the <xref:System.Windows.Media.Animation.Storyboard> to a value of `Slip`, which specifies that the animation does not progress until the media (video in this example) progresses.</span></span> <span data-ttu-id="e2faf-107">如果因為載入時間而延遲媒體撥放，則可能需要此功能。</span><span class="sxs-lookup"><span data-stu-id="e2faf-107">This functionality might be needed if media playback is delayed because of loading time.</span></span>  
  
 [!code-xaml[MediaGallery_snippet#MediaTimelinePlusAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snippet/CSharp/MediaTimelinePlusAnimationExample.xaml#mediatimelineplusanimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="e2faf-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2faf-108">See also</span></span>

- <xref:System.Windows.Media.MediaTimeline>
- <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>
- <xref:System.Windows.Media.Animation.Storyboard>
- <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A>
- [<span data-ttu-id="e2faf-109">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="e2faf-109">How-to Topics</span></span>](audio-and-video-how-to-topics.md)
- [<span data-ttu-id="e2faf-110">分鏡腳本概觀</span><span class="sxs-lookup"><span data-stu-id="e2faf-110">Storyboards Overview</span></span>](storyboards-overview.md)
- [<span data-ttu-id="e2faf-111">主要畫面格動畫概觀</span><span class="sxs-lookup"><span data-stu-id="e2faf-111">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="e2faf-112">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="e2faf-112">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="e2faf-113">圖形和多媒體</span><span class="sxs-lookup"><span data-stu-id="e2faf-113">Graphics and Multimedia</span></span>](index.md)

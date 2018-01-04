---
title: "操作說明：以動畫播放媒體"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multimedia [WPF], playback with animations
- playback of media [WPF], with animations
- animation [WPF], media playback with
- media [WPF], playback with animations
ms.assetid: 8982b7b7-1c6c-4b24-8801-b328862975f5
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 44ebb89c25fc37292f82533c929aae44854db5c9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-play-media-with-animations"></a><span data-ttu-id="4972b-102">操作說明：以動畫播放媒體</span><span class="sxs-lookup"><span data-stu-id="4972b-102">How to: Play Media with Animations</span></span>
<span data-ttu-id="4972b-103">這個範例示範如何同時播放媒體和動畫，使用<xref:System.Windows.Media.MediaTimeline>和<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>中相同的類別<xref:System.Windows.Media.Animation.Storyboard>。</span><span class="sxs-lookup"><span data-stu-id="4972b-103">This example shows how to play media and animations at the same time by using the <xref:System.Windows.Media.MediaTimeline> and <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> classes in the same <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4972b-104">範例</span><span class="sxs-lookup"><span data-stu-id="4972b-104">Example</span></span>  
 <span data-ttu-id="4972b-105">您可以使用一或多個<xref:System.Windows.Media.MediaTimeline>中的物件<xref:System.Windows.Media.Animation.Storyboard>連同其他<xref:System.Windows.Media.Animation.Timeline>物件，例如動畫。</span><span class="sxs-lookup"><span data-stu-id="4972b-105">You can use one or more <xref:System.Windows.Media.MediaTimeline> objects in a <xref:System.Windows.Media.Animation.Storyboard> together with other <xref:System.Windows.Media.Animation.Timeline> objects, such as animations.</span></span>  
  
 <span data-ttu-id="4972b-106">下列範例會設定<xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A>屬性<xref:System.Windows.Media.Animation.Storyboard>為`Slip`，指定動畫不進度直到媒體 （在此範例中視訊） 進行。</span><span class="sxs-lookup"><span data-stu-id="4972b-106">The following example sets the <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A> property of the <xref:System.Windows.Media.Animation.Storyboard> to a value of `Slip`, which specifies that the animation does not progress until the media (video in this example) progresses.</span></span> <span data-ttu-id="4972b-107">如果因為載入時間而延遲媒體撥放，則可能需要此功能。</span><span class="sxs-lookup"><span data-stu-id="4972b-107">This functionality might be needed if media playback is delayed because of loading time.</span></span>  
  
 [!code-xaml[MediaGallery_snippet#MediaTimelinePlusAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snippet/CSharp/MediaTimelinePlusAnimationExample.xaml#mediatimelineplusanimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="4972b-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="4972b-108">See Also</span></span>  
 <xref:System.Windows.Media.MediaTimeline>  
 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A>  
 [<span data-ttu-id="4972b-109">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="4972b-109">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)  
 [<span data-ttu-id="4972b-110">分鏡腳本概觀</span><span class="sxs-lookup"><span data-stu-id="4972b-110">Storyboards Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [<span data-ttu-id="4972b-111">主要畫面格動畫概觀</span><span class="sxs-lookup"><span data-stu-id="4972b-111">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="4972b-112">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="4972b-112">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="4972b-113">圖形和多媒體</span><span class="sxs-lookup"><span data-stu-id="4972b-113">Graphics and Multimedia</span></span>](../../../../docs/framework/wpf/graphics-multimedia/index.md)

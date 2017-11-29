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
ms.openlocfilehash: fb5fd3575a0caa692e4a4013452e3069210c9a4c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-play-media-with-animations"></a><span data-ttu-id="772fb-102">操作說明：以動畫播放媒體</span><span class="sxs-lookup"><span data-stu-id="772fb-102">How to: Play Media with Animations</span></span>
<span data-ttu-id="772fb-103">這個範例示範如何同時播放媒體和動畫，使用<xref:System.Windows.Media.MediaTimeline>和<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>中相同的類別<xref:System.Windows.Media.Animation.Storyboard>。</span><span class="sxs-lookup"><span data-stu-id="772fb-103">This example shows how to play media and animations at the same time by using the <xref:System.Windows.Media.MediaTimeline> and <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> classes in the same <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="772fb-104">範例</span><span class="sxs-lookup"><span data-stu-id="772fb-104">Example</span></span>  
 <span data-ttu-id="772fb-105">您可以使用一或多個<xref:System.Windows.Media.MediaTimeline>中的物件<xref:System.Windows.Media.Animation.Storyboard>連同其他<xref:System.Windows.Media.Animation.Timeline>物件，例如動畫。</span><span class="sxs-lookup"><span data-stu-id="772fb-105">You can use one or more <xref:System.Windows.Media.MediaTimeline> objects in a <xref:System.Windows.Media.Animation.Storyboard> together with other <xref:System.Windows.Media.Animation.Timeline> objects, such as animations.</span></span>  
  
 <span data-ttu-id="772fb-106">下列範例會設定<xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A>屬性<xref:System.Windows.Media.Animation.Storyboard>為`Slip`，指定動畫不進度直到媒體 （在此範例中視訊） 進行。</span><span class="sxs-lookup"><span data-stu-id="772fb-106">The following example sets the <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A> property of the <xref:System.Windows.Media.Animation.Storyboard> to a value of `Slip`, which specifies that the animation does not progress until the media (video in this example) progresses.</span></span> <span data-ttu-id="772fb-107">如果因為載入時間而延遲媒體撥放，則可能需要此功能。</span><span class="sxs-lookup"><span data-stu-id="772fb-107">This functionality might be needed if media playback is delayed because of loading time.</span></span>  
  
 [!code-xaml[MediaGallery_snippet#MediaTimelinePlusAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snippet/CSharp/MediaTimelinePlusAnimationExample.xaml#mediatimelineplusanimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="772fb-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="772fb-108">See Also</span></span>  
 <xref:System.Windows.Media.MediaTimeline>  
 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A>  
 [<span data-ttu-id="772fb-109">操作說明主題</span><span class="sxs-lookup"><span data-stu-id="772fb-109">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)  
 [<span data-ttu-id="772fb-110">分鏡腳本概觀</span><span class="sxs-lookup"><span data-stu-id="772fb-110">Storyboards Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [<span data-ttu-id="772fb-111">主要畫面格動畫概觀</span><span class="sxs-lookup"><span data-stu-id="772fb-111">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="772fb-112">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="772fb-112">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="772fb-113">圖形和多媒體</span><span class="sxs-lookup"><span data-stu-id="772fb-113">Graphics and Multimedia</span></span>](../../../../docs/framework/wpf/graphics-multimedia/index.md)

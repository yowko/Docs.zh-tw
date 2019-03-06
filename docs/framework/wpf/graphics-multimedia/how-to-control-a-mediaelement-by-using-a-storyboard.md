---
title: HOW TO：使用腳本控制 MediaElement
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- multimedia [WPF], controlling playback of media with Storyboards
- controlling playback of media [WPF], with Storyboards
- Storyboards [WPF], controlling playback of media with
- media [WPF], controlling playback with Storyboards
- playback of media [WPF], controlling with Storyboards
ms.assetid: 6128ca77-b826-4e36-b968-6f237157c543
ms.openlocfilehash: 51d567101ee49095e27e9d440016a81cd49fa876
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369106"
---
# <a name="how-to-control-a-mediaelement-by-using-a-storyboard"></a><span data-ttu-id="73c56-102">HOW TO：使用腳本控制 MediaElement</span><span class="sxs-lookup"><span data-stu-id="73c56-102">How to: Control a MediaElement by Using a Storyboard</span></span>
<span data-ttu-id="73c56-103">此範例示範如何控制<xref:System.Windows.Controls.MediaElement>利用<xref:System.Windows.Media.MediaTimeline>在<xref:System.Windows.Media.Animation.Storyboard>。</span><span class="sxs-lookup"><span data-stu-id="73c56-103">This example shows how to control a <xref:System.Windows.Controls.MediaElement> by using a <xref:System.Windows.Media.MediaTimeline> in a <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73c56-104">範例</span><span class="sxs-lookup"><span data-stu-id="73c56-104">Example</span></span>  
 <span data-ttu-id="73c56-105">當您使用<xref:System.Windows.Media.MediaTimeline>中<xref:System.Windows.Media.Animation.Storyboard>若要控制的時機<xref:System.Windows.Controls.MediaElement>，功能相當於其他功能<xref:System.Windows.Media.Animation.Timeline>物件，例如動畫。</span><span class="sxs-lookup"><span data-stu-id="73c56-105">When you use a <xref:System.Windows.Media.MediaTimeline> in a <xref:System.Windows.Media.Animation.Storyboard> to control the timing of a <xref:System.Windows.Controls.MediaElement>, the functionality is identical to the functionality of other <xref:System.Windows.Media.Animation.Timeline> objects, such as animations.</span></span> <span data-ttu-id="73c56-106">例如，<xref:System.Windows.Media.MediaTimeline>會使用<xref:System.Windows.Media.Animation.Timeline>屬性，例如<xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>屬性，以指定何時開始<xref:System.Windows.Controls.MediaElement>（開始播放媒體）。</span><span class="sxs-lookup"><span data-stu-id="73c56-106">For example, a <xref:System.Windows.Media.MediaTimeline> uses <xref:System.Windows.Media.Animation.Timeline> properties like the <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> property to specify when to start a <xref:System.Windows.Controls.MediaElement> (start media playback).</span></span> <span data-ttu-id="73c56-107">它也會使用<xref:System.Windows.Media.Animation.Timeline.Duration%2A>屬性來指定時間長度<xref:System.Windows.Controls.MediaElement>作用中 （持續時間的播放媒體）。</span><span class="sxs-lookup"><span data-stu-id="73c56-107">It also uses the <xref:System.Windows.Media.Animation.Timeline.Duration%2A> property to specify how long the <xref:System.Windows.Controls.MediaElement> is active (duration of media playback).</span></span> <span data-ttu-id="73c56-108">如需使用詳細資訊<xref:System.Windows.Media.Animation.Timeline>具有物件<xref:System.Windows.Media.Animation.Storyboard>，請參閱[分鏡腳本概觀](storyboards-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="73c56-108">For more information about using <xref:System.Windows.Media.Animation.Timeline> objects with a <xref:System.Windows.Media.Animation.Storyboard>, see [Storyboards Overview](storyboards-overview.md).</span></span>  
  
 <span data-ttu-id="73c56-109">此範例示範如何建立會使用簡單的媒體播放程式<xref:System.Windows.Media.MediaTimeline>控制播放。</span><span class="sxs-lookup"><span data-stu-id="73c56-109">This example shows how to create a simple media player that uses a <xref:System.Windows.Media.MediaTimeline> to control playback.</span></span> <span data-ttu-id="73c56-110">Media player 還包括播放、 暫停、 繼續和停止按鈕。</span><span class="sxs-lookup"><span data-stu-id="73c56-110">The media player includes play, pause, resume, and stop buttons.</span></span> <span data-ttu-id="73c56-111">播放程式也有<xref:System.Windows.Controls.Slider>做為一個進度列控制項。</span><span class="sxs-lookup"><span data-stu-id="73c56-111">The player also has a <xref:System.Windows.Controls.Slider> control that acts as a progress bar.</span></span>  
  
 <span data-ttu-id="73c56-112">下列範例會建立[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]media player。</span><span class="sxs-lookup"><span data-stu-id="73c56-112">The following example creates the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] for the media player.</span></span>  
  
 [!code-xaml[MediaGallery_snip#MediaTimelineExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml#mediatimelineexamplewholepage)]  
  
 <span data-ttu-id="73c56-113">下列範例會建立進度列的功能。</span><span class="sxs-lookup"><span data-stu-id="73c56-113">The following example creates the functionality for the progress bar.</span></span>  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaTimelineExample.xaml.cs#codebehindmediatimelineexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml.vb#codebehindmediatimelineexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="73c56-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73c56-114">See also</span></span>
- <xref:System.Windows.Controls.MediaElement>
- <xref:System.Windows.Media.MediaTimeline>
- <xref:System.Windows.Media.Animation.Storyboard>
- [<span data-ttu-id="73c56-115">控制 MediaElement (播放、暫停、停止、音量和速度)</span><span class="sxs-lookup"><span data-stu-id="73c56-115">Control a MediaElement (Play, Pause, Stop, Volume, and Speed)</span></span>](how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md)
- [<span data-ttu-id="73c56-116">分鏡腳本概觀</span><span class="sxs-lookup"><span data-stu-id="73c56-116">Storyboards Overview</span></span>](storyboards-overview.md)
- [<span data-ttu-id="73c56-117">主要畫面格動畫概觀</span><span class="sxs-lookup"><span data-stu-id="73c56-117">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="73c56-118">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="73c56-118">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="73c56-119">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="73c56-119">How-to Topics</span></span>](audio-and-video-how-to-topics.md)
- [<span data-ttu-id="73c56-120">圖形和多媒體</span><span class="sxs-lookup"><span data-stu-id="73c56-120">Graphics and Multimedia</span></span>](index.md)

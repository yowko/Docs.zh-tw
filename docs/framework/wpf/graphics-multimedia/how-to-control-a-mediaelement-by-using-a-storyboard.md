---
title: 如何：使用腳本控制 MediaElement
description: 使用 Windows Presentation foundation （WPF）中的分鏡腳本來控制媒體播放。 請考慮使用此範例來建立簡單的媒體播放機。
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
ms.openlocfilehash: 5a5e41b9a28211495fd3374c1a51a655dd867bca
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853727"
---
# <a name="how-to-control-a-mediaelement-by-using-a-storyboard"></a><span data-ttu-id="3c896-104">如何：使用腳本控制 MediaElement</span><span class="sxs-lookup"><span data-stu-id="3c896-104">How to: Control a MediaElement by Using a Storyboard</span></span>
<span data-ttu-id="3c896-105">這個範例示範如何使用中的來控制 <xref:System.Windows.Controls.MediaElement> <xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Media.Animation.Storyboard> 。</span><span class="sxs-lookup"><span data-stu-id="3c896-105">This example shows how to control a <xref:System.Windows.Controls.MediaElement> by using a <xref:System.Windows.Media.MediaTimeline> in a <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c896-106">範例</span><span class="sxs-lookup"><span data-stu-id="3c896-106">Example</span></span>  
 <span data-ttu-id="3c896-107">當您使用 <xref:System.Windows.Media.MediaTimeline> 中的 <xref:System.Windows.Media.Animation.Storyboard> 來控制的時間時 <xref:System.Windows.Controls.MediaElement> ，此功能與其他 <xref:System.Windows.Media.Animation.Timeline> 物件（例如動畫）的功能完全相同。</span><span class="sxs-lookup"><span data-stu-id="3c896-107">When you use a <xref:System.Windows.Media.MediaTimeline> in a <xref:System.Windows.Media.Animation.Storyboard> to control the timing of a <xref:System.Windows.Controls.MediaElement>, the functionality is identical to the functionality of other <xref:System.Windows.Media.Animation.Timeline> objects, such as animations.</span></span> <span data-ttu-id="3c896-108">例如，會 <xref:System.Windows.Media.MediaTimeline> 使用屬性 <xref:System.Windows.Media.Animation.Timeline> （例如 <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> 屬性）來指定何時啟動 <xref:System.Windows.Controls.MediaElement> （啟動媒體播放）。</span><span class="sxs-lookup"><span data-stu-id="3c896-108">For example, a <xref:System.Windows.Media.MediaTimeline> uses <xref:System.Windows.Media.Animation.Timeline> properties like the <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> property to specify when to start a <xref:System.Windows.Controls.MediaElement> (start media playback).</span></span> <span data-ttu-id="3c896-109">它也會使用 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 屬性來指定作用中的時間長度 <xref:System.Windows.Controls.MediaElement> （媒體播放的持續時間）。</span><span class="sxs-lookup"><span data-stu-id="3c896-109">It also uses the <xref:System.Windows.Media.Animation.Timeline.Duration%2A> property to specify how long the <xref:System.Windows.Controls.MediaElement> is active (duration of media playback).</span></span> <span data-ttu-id="3c896-110">如需搭配使用物件的詳細資訊 <xref:System.Windows.Media.Animation.Timeline> <xref:System.Windows.Media.Animation.Storyboard> ，請參閱分鏡腳本[總覽](storyboards-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="3c896-110">For more information about using <xref:System.Windows.Media.Animation.Timeline> objects with a <xref:System.Windows.Media.Animation.Storyboard>, see [Storyboards Overview](storyboards-overview.md).</span></span>  
  
 <span data-ttu-id="3c896-111">這個範例示範如何建立使用來控制播放的簡單媒體播放機 <xref:System.Windows.Media.MediaTimeline> 。</span><span class="sxs-lookup"><span data-stu-id="3c896-111">This example shows how to create a simple media player that uses a <xref:System.Windows.Media.MediaTimeline> to control playback.</span></span> <span data-ttu-id="3c896-112">Media player 包含 [播放]、[暫停]、[繼續] 和 [停止] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="3c896-112">The media player includes play, pause, resume, and stop buttons.</span></span> <span data-ttu-id="3c896-113">播放程式也有 <xref:System.Windows.Controls.Slider> 做為進度列的控制項。</span><span class="sxs-lookup"><span data-stu-id="3c896-113">The player also has a <xref:System.Windows.Controls.Slider> control that acts as a progress bar.</span></span>  
  
 <span data-ttu-id="3c896-114">下列範例會建立 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] media player 的。</span><span class="sxs-lookup"><span data-stu-id="3c896-114">The following example creates the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] for the media player.</span></span>  
  
 [!code-xaml[MediaGallery_snip#MediaTimelineExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml#mediatimelineexamplewholepage)]  
  
 <span data-ttu-id="3c896-115">下列範例會建立進度列的功能。</span><span class="sxs-lookup"><span data-stu-id="3c896-115">The following example creates the functionality for the progress bar.</span></span>  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaTimelineExample.xaml.cs#codebehindmediatimelineexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml.vb#codebehindmediatimelineexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="3c896-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c896-116">See also</span></span>

- <xref:System.Windows.Controls.MediaElement>
- <xref:System.Windows.Media.MediaTimeline>
- <xref:System.Windows.Media.Animation.Storyboard>
- [<span data-ttu-id="3c896-117">控制 MediaElement (播放、暫停、停止、音量和速度)</span><span class="sxs-lookup"><span data-stu-id="3c896-117">Control a MediaElement (Play, Pause, Stop, Volume, and Speed)</span></span>](how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md)
- [<span data-ttu-id="3c896-118">分鏡腳本概觀</span><span class="sxs-lookup"><span data-stu-id="3c896-118">Storyboards Overview</span></span>](storyboards-overview.md)
- [<span data-ttu-id="3c896-119">主要畫面格動畫概觀</span><span class="sxs-lookup"><span data-stu-id="3c896-119">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="3c896-120">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="3c896-120">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="3c896-121">操作說明主題</span><span class="sxs-lookup"><span data-stu-id="3c896-121">How-to Topics</span></span>](audio-and-video-how-to-topics.md)
- [<span data-ttu-id="3c896-122">圖形和多媒體</span><span class="sxs-lookup"><span data-stu-id="3c896-122">Graphics and Multimedia</span></span>](index.md)

---
title: "如何：使用 VideoDrawing 播放媒體"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- playback of media [WPF]
- classes [WPF], MediaPlayer
ms.assetid: 165d47ed-22ce-4ded-aa6a-aa9b7467de87
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 773a0a1e2252b3f7154ef218f887be6f56e9995f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-play-media-using-a-videodrawing"></a><span data-ttu-id="87832-102">如何：使用 VideoDrawing 播放媒體</span><span class="sxs-lookup"><span data-stu-id="87832-102">How to: Play Media using a VideoDrawing</span></span>
<span data-ttu-id="87832-103">若要播放的音訊或視訊檔案，您使用<xref:System.Windows.Media.VideoDrawing>和<xref:System.Windows.Media.MediaPlayer>。</span><span class="sxs-lookup"><span data-stu-id="87832-103">To play an audio or video file, you use a <xref:System.Windows.Media.VideoDrawing> and a <xref:System.Windows.Media.MediaPlayer>.</span></span> <span data-ttu-id="87832-104">有兩種方法可以載入及播放媒體。</span><span class="sxs-lookup"><span data-stu-id="87832-104">There are two ways to load and play media.</span></span> <span data-ttu-id="87832-105">第一個方法是使用<xref:System.Windows.Media.MediaPlayer>和<xref:System.Windows.Media.VideoDrawing>本身，和第二個方法是建立您自己<xref:System.Windows.Media.MediaTimeline>搭配<xref:System.Windows.Media.MediaPlayer>和<xref:System.Windows.Media.VideoDrawing>。</span><span class="sxs-lookup"><span data-stu-id="87832-105">The first is to use a <xref:System.Windows.Media.MediaPlayer> and a <xref:System.Windows.Media.VideoDrawing> by themselves, and the second way is to create your own <xref:System.Windows.Media.MediaTimeline> to use with the <xref:System.Windows.Media.MediaPlayer> and <xref:System.Windows.Media.VideoDrawing>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="87832-106">利用您的應用程式散發媒體時，您無法跟散發影像一樣，使用媒體檔案當作專案資源。</span><span class="sxs-lookup"><span data-stu-id="87832-106">When distributing media with your application, you cannot use a media file as a project resource, like you would an image.</span></span> <span data-ttu-id="87832-107">在您的專案檔中，您必須改為將媒體類型設定為 `Content`，並將 `CopyToOutputDirectory` 設定為 `PreserveNewest` 或 `Always`。</span><span class="sxs-lookup"><span data-stu-id="87832-107">In your project file, you must instead set the media type to `Content` and set `CopyToOutputDirectory` to `PreserveNewest` or `Always`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87832-108">範例</span><span class="sxs-lookup"><span data-stu-id="87832-108">Example</span></span>  
 <span data-ttu-id="87832-109">下列範例會使用<xref:System.Windows.Media.VideoDrawing>和<xref:System.Windows.Media.MediaPlayer>播放視訊檔案一次。</span><span class="sxs-lookup"><span data-stu-id="87832-109">The following example uses a <xref:System.Windows.Media.VideoDrawing> and a <xref:System.Windows.Media.MediaPlayer> to play a video file once.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 <span data-ttu-id="87832-110">若要取得媒體的詳細計時控制權，請使用<xref:System.Windows.Media.MediaTimeline>與<xref:System.Windows.Media.MediaPlayer>和<xref:System.Windows.Media.VideoDrawing>物件。</span><span class="sxs-lookup"><span data-stu-id="87832-110">To gain additional timing control over the media, use a <xref:System.Windows.Media.MediaTimeline> with the <xref:System.Windows.Media.MediaPlayer> and <xref:System.Windows.Media.VideoDrawing> objects.</span></span> <span data-ttu-id="87832-111"><xref:System.Windows.Media.MediaTimeline>可讓您指定是否應該重複視訊。</span><span class="sxs-lookup"><span data-stu-id="87832-111">The <xref:System.Windows.Media.MediaTimeline> enables you to specify whether the video should repeat.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87832-112">範例</span><span class="sxs-lookup"><span data-stu-id="87832-112">Example</span></span>  
 <span data-ttu-id="87832-113">下列範例會使用<xref:System.Windows.Media.MediaTimeline>與<xref:System.Windows.Media.MediaPlayer>和<xref:System.Windows.Media.VideoDrawing>重複播放視訊的物件。</span><span class="sxs-lookup"><span data-stu-id="87832-113">The following example uses a <xref:System.Windows.Media.MediaTimeline> with the <xref:System.Windows.Media.MediaPlayer> and <xref:System.Windows.Media.VideoDrawing> objects to play a video repeatedly.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 <span data-ttu-id="87832-114">請注意，當您使用<xref:System.Windows.Media.MediaTimeline>，您會使用互動式<xref:System.Windows.Media.Animation.ClockController>從傳回<xref:System.Windows.Media.Animation.Clock.Controller%2A>屬性<xref:System.Windows.Media.MediaClock>控制媒體播放，而不是互動式方法<xref:System.Windows.Media.MediaPlayer>。</span><span class="sxs-lookup"><span data-stu-id="87832-114">Note that, when you use a <xref:System.Windows.Media.MediaTimeline>, you use the interactive <xref:System.Windows.Media.Animation.ClockController> returned from the <xref:System.Windows.Media.Animation.Clock.Controller%2A> property of the <xref:System.Windows.Media.MediaClock> to control media playback instead of the interactive methods of <xref:System.Windows.Media.MediaPlayer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87832-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="87832-115">See Also</span></span>  
 <xref:System.Windows.Media.VideoDrawing>  
 [<span data-ttu-id="87832-116">繪圖物件概觀</span><span class="sxs-lookup"><span data-stu-id="87832-116">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)

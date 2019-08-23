---
title: 作法：使用 VideoDrawing 播放媒體
ms.date: 03/30/2017
helpviewer_keywords:
- playback of media [WPF]
- classes [WPF], MediaPlayer
ms.assetid: 165d47ed-22ce-4ded-aa6a-aa9b7467de87
ms.openlocfilehash: 2e2007525be770186a17cf9d2d42a7c52ba93fba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956959"
---
# <a name="how-to-play-media-using-a-videodrawing"></a><span data-ttu-id="64d28-102">作法：使用 VideoDrawing 播放媒體</span><span class="sxs-lookup"><span data-stu-id="64d28-102">How to: Play Media using a VideoDrawing</span></span>
<span data-ttu-id="64d28-103">若要播放音訊或影片檔案, 請使用<xref:System.Windows.Media.VideoDrawing> <xref:System.Windows.Media.MediaPlayer>和。</span><span class="sxs-lookup"><span data-stu-id="64d28-103">To play an audio or video file, you use a <xref:System.Windows.Media.VideoDrawing> and a <xref:System.Windows.Media.MediaPlayer>.</span></span> <span data-ttu-id="64d28-104">有兩種方法可以載入及播放媒體。</span><span class="sxs-lookup"><span data-stu-id="64d28-104">There are two ways to load and play media.</span></span> <span data-ttu-id="64d28-105">第一種<xref:System.Windows.Media.MediaPlayer>是使用<xref:System.Windows.Media.VideoDrawing>和本身, 第二種方式是建立您自己<xref:System.Windows.Media.MediaTimeline>的<xref:System.Windows.Media.MediaPlayer> , 以搭配和<xref:System.Windows.Media.VideoDrawing>使用。</span><span class="sxs-lookup"><span data-stu-id="64d28-105">The first is to use a <xref:System.Windows.Media.MediaPlayer> and a <xref:System.Windows.Media.VideoDrawing> by themselves, and the second way is to create your own <xref:System.Windows.Media.MediaTimeline> to use with the <xref:System.Windows.Media.MediaPlayer> and <xref:System.Windows.Media.VideoDrawing>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="64d28-106">利用您的應用程式散發媒體時，您無法跟散發影像一樣，使用媒體檔案當作專案資源。</span><span class="sxs-lookup"><span data-stu-id="64d28-106">When distributing media with your application, you cannot use a media file as a project resource, like you would an image.</span></span> <span data-ttu-id="64d28-107">在您的專案檔中，您必須改為將媒體類型設定為 `Content`，並將 `CopyToOutputDirectory` 設定為 `PreserveNewest` 或 `Always`。</span><span class="sxs-lookup"><span data-stu-id="64d28-107">In your project file, you must instead set the media type to `Content` and set `CopyToOutputDirectory` to `PreserveNewest` or `Always`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64d28-108">範例</span><span class="sxs-lookup"><span data-stu-id="64d28-108">Example</span></span>  
 <span data-ttu-id="64d28-109">下列範例會使用<xref:System.Windows.Media.VideoDrawing> <xref:System.Windows.Media.MediaPlayer>和來播放影片檔案一次。</span><span class="sxs-lookup"><span data-stu-id="64d28-109">The following example uses a <xref:System.Windows.Media.VideoDrawing> and a <xref:System.Windows.Media.MediaPlayer> to play a video file once.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 <span data-ttu-id="64d28-110">若要對媒體取得額外的時間控制, 請<xref:System.Windows.Media.MediaTimeline>使用<xref:System.Windows.Media.MediaPlayer>搭配和<xref:System.Windows.Media.VideoDrawing>物件的。</span><span class="sxs-lookup"><span data-stu-id="64d28-110">To gain additional timing control over the media, use a <xref:System.Windows.Media.MediaTimeline> with the <xref:System.Windows.Media.MediaPlayer> and <xref:System.Windows.Media.VideoDrawing> objects.</span></span> <span data-ttu-id="64d28-111">可<xref:System.Windows.Media.MediaTimeline>讓您指定是否應該重複影片。</span><span class="sxs-lookup"><span data-stu-id="64d28-111">The <xref:System.Windows.Media.MediaTimeline> enables you to specify whether the video should repeat.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64d28-112">範例</span><span class="sxs-lookup"><span data-stu-id="64d28-112">Example</span></span>  
 <span data-ttu-id="64d28-113">下列範例會搭配<xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Media.MediaPlayer>和<xref:System.Windows.Media.VideoDrawing>物件使用, 以重複播放影片。</span><span class="sxs-lookup"><span data-stu-id="64d28-113">The following example uses a <xref:System.Windows.Media.MediaTimeline> with the <xref:System.Windows.Media.MediaPlayer> and <xref:System.Windows.Media.VideoDrawing> objects to play a video repeatedly.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 <span data-ttu-id="64d28-114">請注意, 當您<xref:System.Windows.Media.MediaTimeline>使用時, 您會使用<xref:System.Windows.Media.MediaClock>從<xref:System.Windows.Media.Animation.ClockController> <xref:System.Windows.Media.Animation.Clock.Controller%2A>的屬性傳回的互動式來控制媒體播放, 而不是的互動式方法<xref:System.Windows.Media.MediaPlayer>。</span><span class="sxs-lookup"><span data-stu-id="64d28-114">Note that, when you use a <xref:System.Windows.Media.MediaTimeline>, you use the interactive <xref:System.Windows.Media.Animation.ClockController> returned from the <xref:System.Windows.Media.Animation.Clock.Controller%2A> property of the <xref:System.Windows.Media.MediaClock> to control media playback instead of the interactive methods of <xref:System.Windows.Media.MediaPlayer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64d28-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64d28-115">See also</span></span>

- <xref:System.Windows.Media.VideoDrawing>
- [<span data-ttu-id="64d28-116">繪圖物件概觀</span><span class="sxs-lookup"><span data-stu-id="64d28-116">Drawing Objects Overview</span></span>](drawing-objects-overview.md)

---
title: 如何：控制 MediaElement (播放、暫停、停止、音量和速度)
description: 控制 Windows Presentation foundation （WPF）中媒體的播放。 啟動、停止、暫停、跳過來回，以及調整音量和速度。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- playback of media [WPF], controlling
- controlling playback of media [WPF]
- multimedia [WPF], controlling playback of media
- media [WPF], controlling playback of
ms.assetid: 6885a730-e054-4c16-8c1e-ffe17b1f7c32
ms.openlocfilehash: da846299eaa1e36b6e5caab08bc1f861e9f9c46d
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853609"
---
# <a name="how-to-control-a-mediaelement-play-pause-stop-volume-and-speed"></a><span data-ttu-id="92b94-104">如何：控制 MediaElement (播放、暫停、停止、音量和速度)</span><span class="sxs-lookup"><span data-stu-id="92b94-104">How to: Control a MediaElement (Play, Pause, Stop, Volume, and Speed)</span></span>
<span data-ttu-id="92b94-105">下列範例顯示如何使用控制媒體播放 <xref:System.Windows.Controls.MediaElement> 。</span><span class="sxs-lookup"><span data-stu-id="92b94-105">The following example shows how to control playback of media using a <xref:System.Windows.Controls.MediaElement>.</span></span> <span data-ttu-id="92b94-106">這個範例會建立簡單的媒體播放機，讓您在媒體中播放、暫停、停止和略過，以及調整音量和速度比例。</span><span class="sxs-lookup"><span data-stu-id="92b94-106">The example creates a simple media player that allows you to play, pause, stop, and skip back and forth in the media as well as adjust the volume and speed ratio.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92b94-107">範例</span><span class="sxs-lookup"><span data-stu-id="92b94-107">Example</span></span>  
 <span data-ttu-id="92b94-108">下列程式碼會建立 UI。</span><span class="sxs-lookup"><span data-stu-id="92b94-108">The code below creates the UI.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="92b94-109">的 <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> 屬性 <xref:System.Windows.Controls.MediaElement> 必須設定為，才能夠以 `Manual` 互動方式停止、暫停和播放媒體。</span><span class="sxs-lookup"><span data-stu-id="92b94-109">The <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> property of <xref:System.Windows.Controls.MediaElement> must be set to `Manual` in order to be able to interactively stop, pause, and play the media.</span></span>  
  
 [!code-xaml[MediaGallery_snip#MediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="92b94-110">範例</span><span class="sxs-lookup"><span data-stu-id="92b94-110">Example</span></span>  
 <span data-ttu-id="92b94-111">下列程式碼會執行範例 UI 控制項的功能。</span><span class="sxs-lookup"><span data-stu-id="92b94-111">The code below implements the functionality of the sample UI controls.</span></span> <span data-ttu-id="92b94-112"><xref:System.Windows.Controls.MediaElement.Play%2A>、 <xref:System.Windows.Controls.MediaElement.Pause%2A> 和 <xref:System.Windows.Controls.MediaElement.Stop%2A> 方法是用來分別播放、暫停和停止媒體。</span><span class="sxs-lookup"><span data-stu-id="92b94-112">The <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, and <xref:System.Windows.Controls.MediaElement.Stop%2A> methods are used to respectively play, pause and stop the media.</span></span> <span data-ttu-id="92b94-113">變更的 <xref:System.Windows.Controls.MediaElement.Position%2A> 屬性，可 <xref:System.Windows.Controls.MediaElement> 讓您略過媒體中的跳躍。</span><span class="sxs-lookup"><span data-stu-id="92b94-113">Changing the <xref:System.Windows.Controls.MediaElement.Position%2A> property of the <xref:System.Windows.Controls.MediaElement> allows you to skip around in the media.</span></span> <span data-ttu-id="92b94-114">最後， <xref:System.Windows.Controls.MediaElement.Volume%2A> 和 <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> 屬性是用來調整媒體的音量和播放速度。</span><span class="sxs-lookup"><span data-stu-id="92b94-114">Finally, the <xref:System.Windows.Controls.MediaElement.Volume%2A> and <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> properties are used to adjust the volume and playback speed of the media.</span></span>  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="92b94-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92b94-115">See also</span></span>

- [<span data-ttu-id="92b94-116">使用分鏡腳本控制 MediaElement</span><span class="sxs-lookup"><span data-stu-id="92b94-116">Control a MediaElement by Using a Storyboard</span></span>](how-to-control-a-mediaelement-by-using-a-storyboard.md)

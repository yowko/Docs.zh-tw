---
title: "如何：控制 MediaElement (播放、暫停、停止、音量和速度)"
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
- playback of media [WPF], controlling
- controlling playback of media [WPF]
- multimedia [WPF], controlling playback of media
- media [WPF], controlling playback of
ms.assetid: 6885a730-e054-4c16-8c1e-ffe17b1f7c32
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 57b140391526c5b2a0e73a8bab2355ae445b395b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-control-a-mediaelement-play-pause-stop-volume-and-speed"></a><span data-ttu-id="c018f-102">如何：控制 MediaElement (播放、暫停、停止、音量和速度)</span><span class="sxs-lookup"><span data-stu-id="c018f-102">How to: Control a MediaElement (Play, Pause, Stop, Volume, and Speed)</span></span>
<span data-ttu-id="c018f-103">下列範例示範如何控制播放的媒體使用<xref:System.Windows.Controls.MediaElement>。</span><span class="sxs-lookup"><span data-stu-id="c018f-103">The following example shows how to control playback of media using a <xref:System.Windows.Controls.MediaElement>.</span></span> <span data-ttu-id="c018f-104">此範例會建立簡單的媒體播放程式，可讓您播放、 暫停、 停止，並略過來回媒體中，以及調整磁碟區和速度比。</span><span class="sxs-lookup"><span data-stu-id="c018f-104">The example creates a simple media player that allows you to play, pause, stop, and skip back and forth in the media as well as adjust the volume and speed ratio.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c018f-105">範例</span><span class="sxs-lookup"><span data-stu-id="c018f-105">Example</span></span>  
 <span data-ttu-id="c018f-106">下列程式碼會建立 UI。</span><span class="sxs-lookup"><span data-stu-id="c018f-106">The code below creates the UI.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c018f-107"><xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>屬性<xref:System.Windows.Controls.MediaElement>必須設為`Manual`為了能夠以互動方式停止、 暫停和播放媒體。</span><span class="sxs-lookup"><span data-stu-id="c018f-107">The <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> property of <xref:System.Windows.Controls.MediaElement> must be set to `Manual` in order to be able to interactively stop, pause, and play the media.</span></span>  
  
 [!code-xaml[MediaGallery_snip#MediaElementExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="c018f-108">範例</span><span class="sxs-lookup"><span data-stu-id="c018f-108">Example</span></span>  
 <span data-ttu-id="c018f-109">下列程式碼會實作範例 UI 控制項的功能。</span><span class="sxs-lookup"><span data-stu-id="c018f-109">The code below implements the functionality of the sample UI controls.</span></span> <span data-ttu-id="c018f-110"><xref:System.Windows.Controls.MediaElement.Play%2A>， <xref:System.Windows.Controls.MediaElement.Pause%2A>，和<xref:System.Windows.Controls.MediaElement.Stop%2A>方法會用於分別播放、 暫停和停止媒體。</span><span class="sxs-lookup"><span data-stu-id="c018f-110">The <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, and <xref:System.Windows.Controls.MediaElement.Stop%2A> methods are used to respectively play, pause and stop the media.</span></span> <span data-ttu-id="c018f-111">變更<xref:System.Windows.Controls.MediaElement.Position%2A>屬性<xref:System.Windows.Controls.MediaElement>可讓您略過媒體中。</span><span class="sxs-lookup"><span data-stu-id="c018f-111">Changing the <xref:System.Windows.Controls.MediaElement.Position%2A> property of the <xref:System.Windows.Controls.MediaElement> allows you to skip around in the media.</span></span> <span data-ttu-id="c018f-112">最後，<xref:System.Windows.Controls.MediaElement.Volume%2A>和<xref:System.Windows.Controls.MediaElement.SpeedRatio%2A>屬性用來調整磁碟區和播放媒體的速度。</span><span class="sxs-lookup"><span data-stu-id="c018f-112">Finally, the <xref:System.Windows.Controls.MediaElement.Volume%2A> and <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> properties are used to adjust the volume and playback speed of the media.</span></span>  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="c018f-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="c018f-113">See Also</span></span>  
 [<span data-ttu-id="c018f-114">使用分鏡腳本控制 MediaElement</span><span class="sxs-lookup"><span data-stu-id="c018f-114">Control a MediaElement by Using a Storyboard</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-by-using-a-storyboard.md)

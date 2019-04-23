---
title: HOW TO：控制 MediaElement (播放、暫停、停止、音量和速度)
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
ms.openlocfilehash: bb7319fc7ccec0220cbd79a32d5d015f9f2422d0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59182854"
---
# <a name="how-to-control-a-mediaelement-play-pause-stop-volume-and-speed"></a><span data-ttu-id="14cc0-102">HOW TO：控制 MediaElement (播放、暫停、停止、音量和速度)</span><span class="sxs-lookup"><span data-stu-id="14cc0-102">How to: Control a MediaElement (Play, Pause, Stop, Volume, and Speed)</span></span>
<span data-ttu-id="14cc0-103">下列範例示範如何控制播放的媒體使用<xref:System.Windows.Controls.MediaElement>。</span><span class="sxs-lookup"><span data-stu-id="14cc0-103">The following example shows how to control playback of media using a <xref:System.Windows.Controls.MediaElement>.</span></span> <span data-ttu-id="14cc0-104">此範例會建立簡單的媒體播放程式，可讓您播放、 暫停、 停止和略過來回媒體中，以及調整音量和速度的比例。</span><span class="sxs-lookup"><span data-stu-id="14cc0-104">The example creates a simple media player that allows you to play, pause, stop, and skip back and forth in the media as well as adjust the volume and speed ratio.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14cc0-105">範例</span><span class="sxs-lookup"><span data-stu-id="14cc0-105">Example</span></span>  
 <span data-ttu-id="14cc0-106">下列程式碼會建立 UI。</span><span class="sxs-lookup"><span data-stu-id="14cc0-106">The code below creates the UI.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="14cc0-107"><xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>的屬性<xref:System.Windows.Controls.MediaElement>必須設為`Manual`為了能夠以互動方式停止，請暫停和播放媒體。</span><span class="sxs-lookup"><span data-stu-id="14cc0-107">The <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> property of <xref:System.Windows.Controls.MediaElement> must be set to `Manual` in order to be able to interactively stop, pause, and play the media.</span></span>  
  
 [!code-xaml[MediaGallery_snip#MediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="14cc0-108">範例</span><span class="sxs-lookup"><span data-stu-id="14cc0-108">Example</span></span>  
 <span data-ttu-id="14cc0-109">下列程式碼實作的範例 UI 控制項的功能。</span><span class="sxs-lookup"><span data-stu-id="14cc0-109">The code below implements the functionality of the sample UI controls.</span></span> <span data-ttu-id="14cc0-110"><xref:System.Windows.Controls.MediaElement.Play%2A>， <xref:System.Windows.Controls.MediaElement.Pause%2A>，和<xref:System.Windows.Controls.MediaElement.Stop%2A>方法來分別播放、 暫停和停止媒體播放。</span><span class="sxs-lookup"><span data-stu-id="14cc0-110">The <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, and <xref:System.Windows.Controls.MediaElement.Stop%2A> methods are used to respectively play, pause and stop the media.</span></span> <span data-ttu-id="14cc0-111">變更<xref:System.Windows.Controls.MediaElement.Position%2A>屬性<xref:System.Windows.Controls.MediaElement>可讓您在媒體中跳來跳去。</span><span class="sxs-lookup"><span data-stu-id="14cc0-111">Changing the <xref:System.Windows.Controls.MediaElement.Position%2A> property of the <xref:System.Windows.Controls.MediaElement> allows you to skip around in the media.</span></span> <span data-ttu-id="14cc0-112">最後，<xref:System.Windows.Controls.MediaElement.Volume%2A>和<xref:System.Windows.Controls.MediaElement.SpeedRatio%2A>屬性用來調整磁碟區和播放媒體的速度。</span><span class="sxs-lookup"><span data-stu-id="14cc0-112">Finally, the <xref:System.Windows.Controls.MediaElement.Volume%2A> and <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> properties are used to adjust the volume and playback speed of the media.</span></span>  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="14cc0-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="14cc0-113">See also</span></span>

- [<span data-ttu-id="14cc0-114">使用分鏡腳本控制 MediaElement</span><span class="sxs-lookup"><span data-stu-id="14cc0-114">Control a MediaElement by Using a Storyboard</span></span>](how-to-control-a-mediaelement-by-using-a-storyboard.md)

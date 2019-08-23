---
title: 作法：控制 MediaElement (播放、暫停、停止、音量和速度)
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
ms.openlocfilehash: cde7c32b48dff3d6d054e700b2f95771ba3b3773
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930154"
---
# <a name="how-to-control-a-mediaelement-play-pause-stop-volume-and-speed"></a><span data-ttu-id="fbf8e-102">HOW TO：控制 MediaElement (播放、暫停、停止、音量和速度)</span><span class="sxs-lookup"><span data-stu-id="fbf8e-102">How to: Control a MediaElement (Play, Pause, Stop, Volume, and Speed)</span></span>
<span data-ttu-id="fbf8e-103">下列範例顯示如何使用<xref:System.Windows.Controls.MediaElement>控制媒體播放。</span><span class="sxs-lookup"><span data-stu-id="fbf8e-103">The following example shows how to control playback of media using a <xref:System.Windows.Controls.MediaElement>.</span></span> <span data-ttu-id="fbf8e-104">這個範例會建立簡單的媒體播放機, 讓您在媒體中播放、暫停、停止和略過, 以及調整音量和速度比例。</span><span class="sxs-lookup"><span data-stu-id="fbf8e-104">The example creates a simple media player that allows you to play, pause, stop, and skip back and forth in the media as well as adjust the volume and speed ratio.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fbf8e-105">範例</span><span class="sxs-lookup"><span data-stu-id="fbf8e-105">Example</span></span>  
 <span data-ttu-id="fbf8e-106">下列程式碼會建立 UI。</span><span class="sxs-lookup"><span data-stu-id="fbf8e-106">The code below creates the UI.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fbf8e-107">的<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> `Manual`屬性必須設定為, 才能夠以互動方式停止、暫停和播放媒體。 <xref:System.Windows.Controls.MediaElement></span><span class="sxs-lookup"><span data-stu-id="fbf8e-107">The <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> property of <xref:System.Windows.Controls.MediaElement> must be set to `Manual` in order to be able to interactively stop, pause, and play the media.</span></span>  
  
 [!code-xaml[MediaGallery_snip#MediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="fbf8e-108">範例</span><span class="sxs-lookup"><span data-stu-id="fbf8e-108">Example</span></span>  
 <span data-ttu-id="fbf8e-109">下列程式碼會執行範例 UI 控制項的功能。</span><span class="sxs-lookup"><span data-stu-id="fbf8e-109">The code below implements the functionality of the sample UI controls.</span></span> <span data-ttu-id="fbf8e-110"><xref:System.Windows.Controls.MediaElement.Play%2A>、和方法<xref:System.Windows.Controls.MediaElement.Stop%2A>是用來分別播放、暫停和停止媒體。 <xref:System.Windows.Controls.MediaElement.Pause%2A></span><span class="sxs-lookup"><span data-stu-id="fbf8e-110">The <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, and <xref:System.Windows.Controls.MediaElement.Stop%2A> methods are used to respectively play, pause and stop the media.</span></span> <span data-ttu-id="fbf8e-111">變更的<xref:System.Windows.Controls.MediaElement>屬性, 可讓您略過媒體中的跳躍。 <xref:System.Windows.Controls.MediaElement.Position%2A></span><span class="sxs-lookup"><span data-stu-id="fbf8e-111">Changing the <xref:System.Windows.Controls.MediaElement.Position%2A> property of the <xref:System.Windows.Controls.MediaElement> allows you to skip around in the media.</span></span> <span data-ttu-id="fbf8e-112">最後, <xref:System.Windows.Controls.MediaElement.Volume%2A>和<xref:System.Windows.Controls.MediaElement.SpeedRatio%2A>屬性是用來調整媒體的音量和播放速度。</span><span class="sxs-lookup"><span data-stu-id="fbf8e-112">Finally, the <xref:System.Windows.Controls.MediaElement.Volume%2A> and <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> properties are used to adjust the volume and playback speed of the media.</span></span>  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="fbf8e-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fbf8e-113">See also</span></span>

- [<span data-ttu-id="fbf8e-114">使用分鏡腳本控制 MediaElement</span><span class="sxs-lookup"><span data-stu-id="fbf8e-114">Control a MediaElement by Using a Storyboard</span></span>](how-to-control-a-mediaelement-by-using-a-storyboard.md)

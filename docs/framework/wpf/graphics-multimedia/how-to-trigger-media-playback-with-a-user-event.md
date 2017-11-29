---
title: "操作說明：以使用者事件觸發媒體播放"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- synchronizing media playback with events [WPF]
- playback of media [WPF], synchronizing with events
- media [WPF], synchronizing playback with events
- multimedia [WPF], synchronizing media playback with events
ms.assetid: c4dbe632-6e7f-4d7f-9df5-98737a758bc3
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 39d50fc23be4a5cdf4df90cd6fa96466acc738aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-trigger-media-playback-with-a-user-event"></a><span data-ttu-id="205e6-102">操作說明：以使用者事件觸發媒體播放</span><span class="sxs-lookup"><span data-stu-id="205e6-102">How to: Trigger Media Playback with a User Event</span></span>
<span data-ttu-id="205e6-103">這個範例示範如何將媒體播放與某個事件同步。</span><span class="sxs-lookup"><span data-stu-id="205e6-103">This example shows how to synchronize media playback with an event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="205e6-104">範例</span><span class="sxs-lookup"><span data-stu-id="205e6-104">Example</span></span>  
 <span data-ttu-id="205e6-105">下列範例會使用<xref:System.Windows.Controls.MediaElement>控制項和<xref:System.Windows.Media.MediaTimeline>類別來播放發生於使用者按一下時的音效<xref:System.Windows.Controls.Button>。</span><span class="sxs-lookup"><span data-stu-id="205e6-105">The following example uses the <xref:System.Windows.Controls.MediaElement> control and the <xref:System.Windows.Media.MediaTimeline> class to play a sound that occurs when the user clicks a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-xaml[MediaGallery_snippet#SoundFromUserEventExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snippet/CSharp/SoundFromUserEventExample.xaml#soundfromusereventexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="205e6-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="205e6-106">See Also</span></span>  
 <xref:System.Windows.Controls.MediaElement>  
 <xref:System.Windows.Media.MediaTimeline>  
 <xref:System.Windows.EventTrigger.RoutedEvent%2A>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 [<span data-ttu-id="205e6-107">操作說明主題</span><span class="sxs-lookup"><span data-stu-id="205e6-107">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)  
 [<span data-ttu-id="205e6-108">圖形和多媒體</span><span class="sxs-lookup"><span data-stu-id="205e6-108">Graphics and Multimedia</span></span>](../../../../docs/framework/wpf/graphics-multimedia/index.md)

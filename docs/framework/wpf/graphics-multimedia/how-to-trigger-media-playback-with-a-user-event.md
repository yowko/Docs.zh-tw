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
# <a name="how-to-trigger-media-playback-with-a-user-event"></a>操作說明：以使用者事件觸發媒體播放
這個範例示範如何將媒體播放與某個事件同步。  
  
## <a name="example"></a>範例  
 下列範例會使用<xref:System.Windows.Controls.MediaElement>控制項和<xref:System.Windows.Media.MediaTimeline>類別來播放發生於使用者按一下時的音效<xref:System.Windows.Controls.Button>。  
  
 [!code-xaml[MediaGallery_snippet#SoundFromUserEventExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snippet/CSharp/SoundFromUserEventExample.xaml#soundfromusereventexamplewholepage)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Controls.MediaElement>  
 <xref:System.Windows.Media.MediaTimeline>  
 <xref:System.Windows.EventTrigger.RoutedEvent%2A>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 [操作說明主題](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)  
 [圖形和多媒體](../../../../docs/framework/wpf/graphics-multimedia/index.md)

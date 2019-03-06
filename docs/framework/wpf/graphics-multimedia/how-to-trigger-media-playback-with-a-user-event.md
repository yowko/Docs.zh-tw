---
title: HOW TO：以使用者事件觸發媒體播放
ms.date: 03/30/2017
helpviewer_keywords:
- synchronizing media playback with events [WPF]
- playback of media [WPF], synchronizing with events
- media [WPF], synchronizing playback with events
- multimedia [WPF], synchronizing media playback with events
ms.assetid: c4dbe632-6e7f-4d7f-9df5-98737a758bc3
ms.openlocfilehash: 1d71e69bcd0332ba7119977dcf67356a3d79a368
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377972"
---
# <a name="how-to-trigger-media-playback-with-a-user-event"></a>HOW TO：以使用者事件觸發媒體播放
這個範例示範如何將媒體播放與某個事件同步。  
  
## <a name="example"></a>範例  
 下列範例會使用<xref:System.Windows.Controls.MediaElement>控制項和<xref:System.Windows.Media.MediaTimeline>類別來播放音效，發生於使用者按一下<xref:System.Windows.Controls.Button>。  
  
 [!code-xaml[MediaGallery_snippet#SoundFromUserEventExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snippet/CSharp/SoundFromUserEventExample.xaml#soundfromusereventexamplewholepage)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Controls.MediaElement>
- <xref:System.Windows.Media.MediaTimeline>
- <xref:System.Windows.EventTrigger.RoutedEvent%2A>
- <xref:System.Windows.Media.Animation.Storyboard>
- [HOW-TO 主題](audio-and-video-how-to-topics.md)
- [圖形和多媒體](index.md)

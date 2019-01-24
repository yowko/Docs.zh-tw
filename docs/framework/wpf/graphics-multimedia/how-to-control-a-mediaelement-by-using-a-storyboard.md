---
title: HOW TO：使用腳本控制 MediaElement
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
ms.openlocfilehash: e4c4ed8131095f0183649c36b4cdb75be0d72ca9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54501996"
---
# <a name="how-to-control-a-mediaelement-by-using-a-storyboard"></a>HOW TO：使用腳本控制 MediaElement
此範例示範如何控制<xref:System.Windows.Controls.MediaElement>利用<xref:System.Windows.Media.MediaTimeline>在<xref:System.Windows.Media.Animation.Storyboard>。  
  
## <a name="example"></a>範例  
 當您使用<xref:System.Windows.Media.MediaTimeline>中<xref:System.Windows.Media.Animation.Storyboard>若要控制的時機<xref:System.Windows.Controls.MediaElement>，功能相當於其他功能<xref:System.Windows.Media.Animation.Timeline>物件，例如動畫。 例如，<xref:System.Windows.Media.MediaTimeline>會使用<xref:System.Windows.Media.Animation.Timeline>屬性，例如<xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>屬性，以指定何時開始<xref:System.Windows.Controls.MediaElement>（開始播放媒體）。 它也會使用<xref:System.Windows.Media.Animation.Timeline.Duration%2A>屬性來指定時間長度<xref:System.Windows.Controls.MediaElement>作用中 （持續時間的播放媒體）。 如需使用詳細資訊<xref:System.Windows.Media.Animation.Timeline>具有物件<xref:System.Windows.Media.Animation.Storyboard>，請參閱[分鏡腳本概觀](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)。  
  
 此範例示範如何建立會使用簡單的媒體播放程式<xref:System.Windows.Media.MediaTimeline>控制播放。 Media player 還包括播放、 暫停、 繼續和停止按鈕。 播放程式也有<xref:System.Windows.Controls.Slider>做為一個進度列控制項。  
  
 下列範例會建立[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]media player。  
  
 [!code-xaml[MediaGallery_snip#MediaTimelineExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml#mediatimelineexamplewholepage)]  
  
 下列範例會建立進度列的功能。  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaTimelineExample.xaml.cs#codebehindmediatimelineexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml.vb#codebehindmediatimelineexamplewholepage)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Controls.MediaElement>
- <xref:System.Windows.Media.MediaTimeline>
- <xref:System.Windows.Media.Animation.Storyboard>
- [控制 MediaElement (播放、暫停、停止、音量和速度)](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md)
- [分鏡腳本概觀](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
- [主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)
- [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [HOW-TO 主題](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)
- [圖形和多媒體](../../../../docs/framework/wpf/graphics-multimedia/index.md)

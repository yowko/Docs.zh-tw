---
title: "如何：使用腳本控制 MediaElement"
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
- multimedia [WPF], controlling playback of media with Storyboards
- controlling playback of media [WPF], with Storyboards
- Storyboards [WPF], controlling playback of media with
- media [WPF], controlling playback with Storyboards
- playback of media [WPF], controlling with Storyboards
ms.assetid: 6128ca77-b826-4e36-b968-6f237157c543
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2341d2814e5bd42c652865c76d115defcc5b15b2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-control-a-mediaelement-by-using-a-storyboard"></a>如何：使用腳本控制 MediaElement
這個範例示範如何控制<xref:System.Windows.Controls.MediaElement>使用<xref:System.Windows.Media.MediaTimeline>中<xref:System.Windows.Media.Animation.Storyboard>。  
  
## <a name="example"></a>範例  
 當您使用<xref:System.Windows.Media.MediaTimeline>中<xref:System.Windows.Media.Animation.Storyboard>控制的時機<xref:System.Windows.Controls.MediaElement>，功能相當於其他功能<xref:System.Windows.Media.Animation.Timeline>物件，例如動畫。 例如，<xref:System.Windows.Media.MediaTimeline>使用<xref:System.Windows.Media.Animation.Timeline>屬性，例如<xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>屬性可指定何時開始<xref:System.Windows.Controls.MediaElement>（開始播放媒體）。 它也會使用<xref:System.Windows.Media.Animation.Timeline.Duration%2A>屬性來指定時間長度<xref:System.Windows.Controls.MediaElement>為作用中 （播放媒體的持續時間）。 如需有關使用<xref:System.Windows.Media.Animation.Timeline>物件與<xref:System.Windows.Media.Animation.Storyboard>，請參閱[概觀腳本](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)。  
  
 這個範例示範如何建立簡單的媒體播放程式會使用<xref:System.Windows.Media.MediaTimeline>控制播放。 Media player 還包括播放、 暫停、 繼續和停止按鈕。 播放程式也有<xref:System.Windows.Controls.Slider>做為進度列控制項。  
  
 下列範例會建立[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]media player。  
  
 [!code-xaml[MediaGallery_snip#MediaTimelineExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml#mediatimelineexamplewholepage)]  
  
 下列範例會建立進度列的功能。  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaTimelineExample.xaml.cs#codebehindmediatimelineexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml.vb#codebehindmediatimelineexamplewholepage)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Controls.MediaElement>  
 <xref:System.Windows.Media.MediaTimeline>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 [控制 MediaElement (播放、暫停、停止、音量和速度)](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md)  
 [分鏡腳本概觀](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [操作說明主題](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)  
 [圖形和多媒體](../../../../docs/framework/wpf/graphics-multimedia/index.md)

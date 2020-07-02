---
title: 如何：使用腳本控制 MediaElement
description: 使用 Windows Presentation foundation （WPF）中的分鏡腳本來控制媒體播放。 請考慮使用此範例來建立簡單的媒體播放機。
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
ms.openlocfilehash: 5a5e41b9a28211495fd3374c1a51a655dd867bca
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853727"
---
# <a name="how-to-control-a-mediaelement-by-using-a-storyboard"></a>如何：使用腳本控制 MediaElement
這個範例示範如何使用中的來控制 <xref:System.Windows.Controls.MediaElement> <xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Media.Animation.Storyboard> 。  
  
## <a name="example"></a>範例  
 當您使用 <xref:System.Windows.Media.MediaTimeline> 中的 <xref:System.Windows.Media.Animation.Storyboard> 來控制的時間時 <xref:System.Windows.Controls.MediaElement> ，此功能與其他 <xref:System.Windows.Media.Animation.Timeline> 物件（例如動畫）的功能完全相同。 例如，會 <xref:System.Windows.Media.MediaTimeline> 使用屬性 <xref:System.Windows.Media.Animation.Timeline> （例如 <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> 屬性）來指定何時啟動 <xref:System.Windows.Controls.MediaElement> （啟動媒體播放）。 它也會使用 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 屬性來指定作用中的時間長度 <xref:System.Windows.Controls.MediaElement> （媒體播放的持續時間）。 如需搭配使用物件的詳細資訊 <xref:System.Windows.Media.Animation.Timeline> <xref:System.Windows.Media.Animation.Storyboard> ，請參閱分鏡腳本[總覽](storyboards-overview.md)。  
  
 這個範例示範如何建立使用來控制播放的簡單媒體播放機 <xref:System.Windows.Media.MediaTimeline> 。 Media player 包含 [播放]、[暫停]、[繼續] 和 [停止] 按鈕。 播放程式也有 <xref:System.Windows.Controls.Slider> 做為進度列的控制項。  
  
 下列範例會建立 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] media player 的。  
  
 [!code-xaml[MediaGallery_snip#MediaTimelineExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml#mediatimelineexamplewholepage)]  
  
 下列範例會建立進度列的功能。  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaTimelineExample.xaml.cs#codebehindmediatimelineexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml.vb#codebehindmediatimelineexamplewholepage)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.MediaElement>
- <xref:System.Windows.Media.MediaTimeline>
- <xref:System.Windows.Media.Animation.Storyboard>
- [控制 MediaElement (播放、暫停、停止、音量和速度)](how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md)
- [分鏡腳本概觀](storyboards-overview.md)
- [主要畫面格動畫概觀](key-frame-animations-overview.md)
- [動畫概觀](animation-overview.md)
- [操作說明主題](audio-and-video-how-to-topics.md)
- [圖形和多媒體](index.md)

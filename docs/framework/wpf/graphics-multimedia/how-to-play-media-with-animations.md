---
title: 操作說明：以動畫播放媒體
ms.date: 03/30/2017
helpviewer_keywords:
- multimedia [WPF], playback with animations
- playback of media [WPF], with animations
- animation [WPF], media playback with
- media [WPF], playback with animations
ms.assetid: 8982b7b7-1c6c-4b24-8801-b328862975f5
ms.openlocfilehash: 21c9b35828dca03c05def11cff22f1f1e33d45cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-play-media-with-animations"></a>操作說明：以動畫播放媒體
這個範例示範如何同時播放媒體和動畫，使用<xref:System.Windows.Media.MediaTimeline>和<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>中相同的類別<xref:System.Windows.Media.Animation.Storyboard>。  
  
## <a name="example"></a>範例  
 您可以使用一或多個<xref:System.Windows.Media.MediaTimeline>中的物件<xref:System.Windows.Media.Animation.Storyboard>連同其他<xref:System.Windows.Media.Animation.Timeline>物件，例如動畫。  
  
 下列範例會設定<xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A>屬性<xref:System.Windows.Media.Animation.Storyboard>為`Slip`，指定動畫不進度直到媒體 （在此範例中視訊） 進行。 如果因為載入時間而延遲媒體撥放，則可能需要此功能。  
  
 [!code-xaml[MediaGallery_snippet#MediaTimelinePlusAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snippet/CSharp/MediaTimelinePlusAnimationExample.xaml#mediatimelineplusanimationexamplewholepage)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Media.MediaTimeline>  
 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A>  
 [HOW-TO 主題](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)  
 [分鏡腳本概觀](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [圖形和多媒體](../../../../docs/framework/wpf/graphics-multimedia/index.md)

---
title: HOW TO：以動畫播放媒體
ms.date: 03/30/2017
helpviewer_keywords:
- multimedia [WPF], playback with animations
- playback of media [WPF], with animations
- animation [WPF], media playback with
- media [WPF], playback with animations
ms.assetid: 8982b7b7-1c6c-4b24-8801-b328862975f5
ms.openlocfilehash: 0dc39d08ef17a628675018c17602623f2efd0173
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372898"
---
# <a name="how-to-play-media-with-animations"></a>HOW TO：以動畫播放媒體
此範例示範如何同時播放媒體和動畫，使用<xref:System.Windows.Media.MediaTimeline>並<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>類別，在同一個<xref:System.Windows.Media.Animation.Storyboard>。  
  
## <a name="example"></a>範例  
 您可以使用一或多個<xref:System.Windows.Media.MediaTimeline>中的物件<xref:System.Windows.Media.Animation.Storyboard>與其它<xref:System.Windows.Media.Animation.Timeline>物件，例如動畫。  
  
 下列範例會設定<xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A>的屬性<xref:System.Windows.Media.Animation.Storyboard>的值`Slip`，以指定動畫不會進行直到媒體 （在此範例影片） 進行。 如果因為載入時間而延遲媒體撥放，則可能需要此功能。  
  
 [!code-xaml[MediaGallery_snippet#MediaTimelinePlusAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snippet/CSharp/MediaTimelinePlusAnimationExample.xaml#mediatimelineplusanimationexamplewholepage)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Media.MediaTimeline>
- <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>
- <xref:System.Windows.Media.Animation.Storyboard>
- <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A>
- [HOW-TO 主題](audio-and-video-how-to-topics.md)
- [分鏡腳本概觀](storyboards-overview.md)
- [主要畫面格動畫概觀](key-frame-animations-overview.md)
- [動畫概觀](animation-overview.md)
- [圖形和多媒體](index.md)

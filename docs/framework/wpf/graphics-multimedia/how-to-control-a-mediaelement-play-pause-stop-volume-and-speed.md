---
title: 如何：控制 MediaElement (播放、暫停、停止、音量和速度)
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
ms.openlocfilehash: beeddc658f16d8b52142a8a79f9c61e4f7070b01
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-control-a-mediaelement-play-pause-stop-volume-and-speed"></a>如何：控制 MediaElement (播放、暫停、停止、音量和速度)
下列範例示範如何控制播放的媒體使用<xref:System.Windows.Controls.MediaElement>。 此範例會建立簡單的媒體播放程式，可讓您播放、 暫停、 停止，並略過來回媒體中，以及調整磁碟區和速度比。  
  
## <a name="example"></a>範例  
 下列程式碼會建立 UI。  
  
> [!NOTE]
>  <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>屬性<xref:System.Windows.Controls.MediaElement>必須設為`Manual`為了能夠以互動方式停止、 暫停和播放媒體。  
  
 [!code-xaml[MediaGallery_snip#MediaElementExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## <a name="example"></a>範例  
 下列程式碼會實作範例 UI 控制項的功能。 <xref:System.Windows.Controls.MediaElement.Play%2A>， <xref:System.Windows.Controls.MediaElement.Pause%2A>，和<xref:System.Windows.Controls.MediaElement.Stop%2A>方法會用於分別播放、 暫停和停止媒體。 變更<xref:System.Windows.Controls.MediaElement.Position%2A>屬性<xref:System.Windows.Controls.MediaElement>可讓您略過媒體中。 最後，<xref:System.Windows.Controls.MediaElement.Volume%2A>和<xref:System.Windows.Controls.MediaElement.SpeedRatio%2A>屬性用來調整磁碟區和播放媒體的速度。  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## <a name="see-also"></a>另請參閱  
 [使用分鏡腳本控制 MediaElement](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-by-using-a-storyboard.md)

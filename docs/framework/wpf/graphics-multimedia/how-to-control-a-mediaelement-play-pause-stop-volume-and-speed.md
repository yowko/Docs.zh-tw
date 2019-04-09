---
title: HOW TO：控制 MediaElement (播放、暫停、停止、音量和速度)
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
ms.openlocfilehash: bb7319fc7ccec0220cbd79a32d5d015f9f2422d0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59182854"
---
# <a name="how-to-control-a-mediaelement-play-pause-stop-volume-and-speed"></a>HOW TO：控制 MediaElement (播放、暫停、停止、音量和速度)
下列範例示範如何控制播放的媒體使用<xref:System.Windows.Controls.MediaElement>。 此範例會建立簡單的媒體播放程式，可讓您播放、 暫停、 停止和略過來回媒體中，以及調整音量和速度的比例。  
  
## <a name="example"></a>範例  
 下列程式碼會建立 UI。  
  
> [!NOTE]
>  <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>的屬性<xref:System.Windows.Controls.MediaElement>必須設為`Manual`為了能夠以互動方式停止，請暫停和播放媒體。  
  
 [!code-xaml[MediaGallery_snip#MediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## <a name="example"></a>範例  
 下列程式碼實作的範例 UI 控制項的功能。 <xref:System.Windows.Controls.MediaElement.Play%2A>， <xref:System.Windows.Controls.MediaElement.Pause%2A>，和<xref:System.Windows.Controls.MediaElement.Stop%2A>方法來分別播放、 暫停和停止媒體播放。 變更<xref:System.Windows.Controls.MediaElement.Position%2A>屬性<xref:System.Windows.Controls.MediaElement>可讓您在媒體中跳來跳去。 最後，<xref:System.Windows.Controls.MediaElement.Volume%2A>和<xref:System.Windows.Controls.MediaElement.SpeedRatio%2A>屬性用來調整磁碟區和播放媒體的速度。  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## <a name="see-also"></a>另請參閱

- [使用分鏡腳本控制 MediaElement](how-to-control-a-mediaelement-by-using-a-storyboard.md)

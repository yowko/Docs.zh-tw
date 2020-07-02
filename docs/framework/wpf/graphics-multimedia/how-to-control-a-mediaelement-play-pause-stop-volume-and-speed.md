---
title: 如何：控制 MediaElement (播放、暫停、停止、音量和速度)
description: 控制 Windows Presentation foundation （WPF）中媒體的播放。 啟動、停止、暫停、跳過來回，以及調整音量和速度。
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
ms.openlocfilehash: da846299eaa1e36b6e5caab08bc1f861e9f9c46d
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853609"
---
# <a name="how-to-control-a-mediaelement-play-pause-stop-volume-and-speed"></a>如何：控制 MediaElement (播放、暫停、停止、音量和速度)
下列範例顯示如何使用控制媒體播放 <xref:System.Windows.Controls.MediaElement> 。 這個範例會建立簡單的媒體播放機，讓您在媒體中播放、暫停、停止和略過，以及調整音量和速度比例。  
  
## <a name="example"></a>範例  
 下列程式碼會建立 UI。  
  
> [!NOTE]
> 的 <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> 屬性 <xref:System.Windows.Controls.MediaElement> 必須設定為，才能夠以 `Manual` 互動方式停止、暫停和播放媒體。  
  
 [!code-xaml[MediaGallery_snip#MediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## <a name="example"></a>範例  
 下列程式碼會執行範例 UI 控制項的功能。 <xref:System.Windows.Controls.MediaElement.Play%2A>、 <xref:System.Windows.Controls.MediaElement.Pause%2A> 和 <xref:System.Windows.Controls.MediaElement.Stop%2A> 方法是用來分別播放、暫停和停止媒體。 變更的 <xref:System.Windows.Controls.MediaElement.Position%2A> 屬性，可 <xref:System.Windows.Controls.MediaElement> 讓您略過媒體中的跳躍。 最後， <xref:System.Windows.Controls.MediaElement.Volume%2A> 和 <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> 屬性是用來調整媒體的音量和播放速度。  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## <a name="see-also"></a>另請參閱

- [使用分鏡腳本控制 MediaElement](how-to-control-a-mediaelement-by-using-a-storyboard.md)

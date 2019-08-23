---
title: 作法：使用 VideoDrawing 播放媒體
ms.date: 03/30/2017
helpviewer_keywords:
- playback of media [WPF]
- classes [WPF], MediaPlayer
ms.assetid: 165d47ed-22ce-4ded-aa6a-aa9b7467de87
ms.openlocfilehash: 2e2007525be770186a17cf9d2d42a7c52ba93fba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956959"
---
# <a name="how-to-play-media-using-a-videodrawing"></a>作法：使用 VideoDrawing 播放媒體
若要播放音訊或影片檔案, 請使用<xref:System.Windows.Media.VideoDrawing> <xref:System.Windows.Media.MediaPlayer>和。 有兩種方法可以載入及播放媒體。 第一種<xref:System.Windows.Media.MediaPlayer>是使用<xref:System.Windows.Media.VideoDrawing>和本身, 第二種方式是建立您自己<xref:System.Windows.Media.MediaTimeline>的<xref:System.Windows.Media.MediaPlayer> , 以搭配和<xref:System.Windows.Media.VideoDrawing>使用。  
  
> [!NOTE]
> 利用您的應用程式散發媒體時，您無法跟散發影像一樣，使用媒體檔案當作專案資源。 在您的專案檔中，您必須改為將媒體類型設定為 `Content`，並將 `CopyToOutputDirectory` 設定為 `PreserveNewest` 或 `Always`。  
  
## <a name="example"></a>範例  
 下列範例會使用<xref:System.Windows.Media.VideoDrawing> <xref:System.Windows.Media.MediaPlayer>和來播放影片檔案一次。  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 若要對媒體取得額外的時間控制, 請<xref:System.Windows.Media.MediaTimeline>使用<xref:System.Windows.Media.MediaPlayer>搭配和<xref:System.Windows.Media.VideoDrawing>物件的。 可<xref:System.Windows.Media.MediaTimeline>讓您指定是否應該重複影片。  
  
## <a name="example"></a>範例  
 下列範例會搭配<xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Media.MediaPlayer>和<xref:System.Windows.Media.VideoDrawing>物件使用, 以重複播放影片。  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 請注意, 當您<xref:System.Windows.Media.MediaTimeline>使用時, 您會使用<xref:System.Windows.Media.MediaClock>從<xref:System.Windows.Media.Animation.ClockController> <xref:System.Windows.Media.Animation.Clock.Controller%2A>的屬性傳回的互動式來控制媒體播放, 而不是的互動式方法<xref:System.Windows.Media.MediaPlayer>。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.VideoDrawing>
- [繪圖物件概觀](drawing-objects-overview.md)

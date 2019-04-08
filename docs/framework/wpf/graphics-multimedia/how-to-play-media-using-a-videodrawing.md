---
title: HOW TO：使用 VideoDrawing 播放媒體
ms.date: 03/30/2017
helpviewer_keywords:
- playback of media [WPF]
- classes [WPF], MediaPlayer
ms.assetid: 165d47ed-22ce-4ded-aa6a-aa9b7467de87
ms.openlocfilehash: 186c9ae8167dafd09f029418c1d23f81f7a9e906
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59203609"
---
# <a name="how-to-play-media-using-a-videodrawing"></a>HOW TO：使用 VideoDrawing 播放媒體
若要播放的音訊或視訊檔案，您使用<xref:System.Windows.Media.VideoDrawing>和<xref:System.Windows.Media.MediaPlayer>。 有兩種方法可以載入及播放媒體。 第一種是使用<xref:System.Windows.Media.MediaPlayer>並<xref:System.Windows.Media.VideoDrawing>本身，然後第二個方法是建立您自己<xref:System.Windows.Media.MediaTimeline>搭配<xref:System.Windows.Media.MediaPlayer>和<xref:System.Windows.Media.VideoDrawing>。  
  
> [!NOTE]
>  利用您的應用程式散發媒體時，您無法跟散發影像一樣，使用媒體檔案當作專案資源。 在您的專案檔中，您必須改為將媒體類型設定為 `Content`，並將 `CopyToOutputDirectory` 設定為 `PreserveNewest` 或 `Always`。  
  
## <a name="example"></a>範例  
 下列範例會使用<xref:System.Windows.Media.VideoDrawing>和<xref:System.Windows.Media.MediaPlayer>來播放視訊檔案一次。  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 若要取得其他計時控制項，透過媒體，請使用<xref:System.Windows.Media.MediaTimeline>具有<xref:System.Windows.Media.MediaPlayer>和<xref:System.Windows.Media.VideoDrawing>物件。 <xref:System.Windows.Media.MediaTimeline>可讓您指定是否應重複播放視訊。  
  
## <a name="example"></a>範例  
 下列範例會使用<xref:System.Windows.Media.MediaTimeline>具有<xref:System.Windows.Media.MediaPlayer>和<xref:System.Windows.Media.VideoDrawing>重複播放視訊的物件。  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 請注意，當您使用<xref:System.Windows.Media.MediaTimeline>，您使用的互動式<xref:System.Windows.Media.Animation.ClockController>傳回<xref:System.Windows.Media.Animation.Clock.Controller%2A>屬性<xref:System.Windows.Media.MediaClock>控制媒體播放，而不是互動的方法<xref:System.Windows.Media.MediaPlayer>。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.VideoDrawing>
- [繪圖物件概觀](drawing-objects-overview.md)

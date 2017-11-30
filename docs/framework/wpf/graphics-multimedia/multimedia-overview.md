---
title: "多媒體概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multimedia [WPF]
- media [WPF]
ms.assetid: feb25b15-d741-4ac3-818f-1b19f63a3562
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7097f5bd58573315681c61d0380e58638a4c4fb1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="multimedia-overview"></a>多媒體概觀
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中的多媒體功能可讓您將音訊和視訊整合到您的應用程式中，以增強使用者體驗。 本主題介紹 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的多媒體功能。  
  
 
  
<a name="mediaapi"></a>   
## <a name="media-api"></a>媒體 API  
 <xref:System.Windows.Controls.MediaElement>和<xref:System.Windows.Media.MediaPlayer>類別用來呈現音訊或視訊內容。 您可以透過互動式的方式或是時鐘來控制這些類別。 這些類別可以用於 [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] 10 的媒體播放控制。 使用的類別需視案例而定。  
  
 <xref:System.Windows.Controls.MediaElement>是<xref:System.Windows.UIElement>支援[配置](../../../../docs/framework/wpf/advanced/layout.md)而且可做為許多控制項的內容。 它也可用於 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 以及程式碼中。 <xref:System.Windows.Media.MediaPlayer>相反地，可供<xref:System.Windows.Media.Drawing>物件，並在不配置支援。 使用載入的媒體<xref:System.Windows.Media.MediaPlayer>可以只可以使用顯示<xref:System.Windows.Media.VideoDrawing>或直接互動<xref:System.Windows.Media.DrawingContext>。 <xref:System.Windows.Media.MediaPlayer>無法在 XAML 中使用。  
  
 如需繪圖物件和繪圖內容的詳細資訊，請參閱[繪圖物件概觀](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)。  
  
> [!NOTE]
>  在隨著您的應用程式散發媒體時，您無法使用媒體檔案做為專案資源。 在您的專案檔中，您必須改為將媒體類型設定為 `Content`，並將 `CopyToOutputDirectory` 設定為 `PreserveNewest` 或 `Always`。  
  
<a name="mediaplaybackmodes"></a>   
## <a name="media-playback-modes"></a>媒體播放模式  
  
> [!NOTE]
>  同時<xref:System.Windows.Controls.MediaElement>和<xref:System.Windows.Media.MediaPlayer>有類似的成員。 本節中的連結指向<xref:System.Windows.Controls.MediaElement>類別成員。 除非有特別註明，否則成員會連結在<xref:System.Windows.Controls.MediaElement>類別也可以在中找到<xref:System.Windows.Media.MediaPlayer>類別。  
  
 若要了解 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中的媒體播放，必須先了解不同的媒體播放模式。 同時<xref:System.Windows.Controls.MediaElement>和<xref:System.Windows.Media.MediaPlayer>可以用於兩種不同的媒體模式、 獨立模式和時鐘模式。 媒體模式由<xref:System.Windows.Controls.MediaElement.Clock%2A>屬性。 當<xref:System.Windows.Controls.MediaElement.Clock%2A>是`null`，媒體物件是在獨立模式中。 當<xref:System.Windows.Controls.MediaElement.Clock%2A>是不是 null，媒體物件處於時鐘模式。 根據預設，媒體物件是處於獨立模式。  
  
### <a name="independent-mode"></a>獨立模式  
 在獨立模式中，媒體內容會驅動媒體播放。 獨立模式提供下列選項：  
  
-   媒體的<xref:System.Uri>可以直接指定。  
  
-   可以直接控制媒體播放。  
  
-   媒體的<xref:System.Windows.Controls.MediaElement.Position%2A>和<xref:System.Windows.Controls.MediaElement.SpeedRatio%2A>可以修改屬性。  
  
 媒體載入其中一個設定<xref:System.Windows.Controls.MediaElement>物件的<xref:System.Windows.Controls.MediaElement.Source%2A>屬性或藉由呼叫<xref:System.Windows.Media.MediaPlayer>物件的<xref:System.Windows.Media.MediaPlayer.Open%2A>方法。  
  
 若要在獨立模式中控制媒體播放，可以使用媒體物件的控制方法。 使用控制方法<xref:System.Windows.Controls.MediaElement.Play%2A>， <xref:System.Windows.Controls.MediaElement.Pause%2A>， <xref:System.Windows.Controls.MediaElement.Close%2A>，和<xref:System.Windows.Controls.MediaElement.Stop%2A>。 如<xref:System.Windows.Controls.MediaElement>，互動式控制使用這些方法時，才可以使用<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>設<xref:System.Windows.Controls.MediaState.Manual>。 當媒體物件處於時鐘模式時，無法使用這些方法。  
  
 如需獨立模式的範例，請參閱[控制 MediaElement (播放、暫停、停止、音量和速度)](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md)。  
  
### <a name="clock-mode"></a>時鐘模式  
 在時鐘模式中，<xref:System.Windows.Media.MediaTimeline>播放媒體的磁碟機。 時鐘模式具有下列特性：  
  
-   媒體的<xref:System.Uri>間接透過設定<xref:System.Windows.Media.MediaTimeline>。  
  
-   可由時鐘來控制媒體播放。 無法使用媒體物件的控制方法。  
  
-   媒體載入藉由設定<xref:System.Windows.Media.MediaTimeline>物件的<xref:System.Windows.Media.MediaTimeline.Source%2A>建立時鐘時間表中，從和指派時鐘媒體物件的屬性。 媒體也載入這種方式時<xref:System.Windows.Media.MediaTimeline>內<xref:System.Windows.Media.Animation.Storyboard>目標<xref:System.Windows.Controls.MediaElement>。  
  
 在時鐘模式中，控制項媒體播放<xref:System.Windows.Media.Animation.ClockController>必須使用控制方法。 A<xref:System.Windows.Media.Animation.ClockController>取自<xref:System.Windows.Media.Animation.ClockController>屬性<xref:System.Windows.Media.MediaClock>。 如果您嘗試使用控制方法的其中一個<xref:System.Windows.Controls.MediaElement>或<xref:System.Windows.Media.MediaPlayer>時鐘模式中物件<xref:System.InvalidOperationException>就會擲回。  
  
 如需時鐘和時間軸的詳細資訊，請參閱[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。  
  
 如需時鐘模式的範例，請參閱[使用分鏡腳本控制 MediaElement](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-by-using-a-storyboard.md)。  
  
<a name="mediaelement"></a>   
## <a name="mediaelement-class"></a>MediaElement 類別  
 應用程式中加入媒體很簡單，只新增<xref:System.Windows.Controls.MediaElement>控制權傳輸至[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]應用程式，並提供<xref:System.Uri>到您要包含的媒體。 [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] 10 支援的所有媒體類型，在 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中也都支援。 下列範例顯示簡單的使用方式的<xref:System.Windows.Controls.MediaElement>中[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]。  
  
 [!code-xaml[MediaElement_snip#SimpleMediaElementUsageWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaElement_snip/CSharp/SimpleUsage.xaml#simplemediaelementusagewholepage)]  
  
 在此範例中，媒體一載入就會自動播放。 媒體播放完之後，系統就會關閉媒體並釋放所有媒體資源 (包括視訊記憶體)。 這是預設行為的<xref:System.Windows.Controls.MediaElement>物件，並受到<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>和<xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>屬性。  
  
### <a name="controlling-a-mediaelement"></a>控制 MediaElement  
 <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>和<xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>屬性控制的行為<xref:System.Windows.Controls.MediaElement>時<xref:System.Windows.FrameworkElement.IsLoaded%2A>是`true`或`false`分別。 <xref:System.Windows.Controls.MediaState>屬性會設定為影響媒體播放行為。 例如，預設值<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>是<xref:System.Windows.Controls.MediaState.Play>和預設<xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>是<xref:System.Windows.Controls.MediaState.Close>。 這表示，只要<xref:System.Windows.Controls.MediaElement>載入預載並完成時，就開始播放媒體。 一旦播放完成，系統就會關閉媒體並釋放所有媒體資源。  
  
 <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>和<xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>屬性不是唯一的方法，來控制播放媒體。 在時鐘模式中，可以控制時鐘<xref:System.Windows.Controls.MediaElement>和互動式控制方法擁有 control 時<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>是<xref:System.Windows.Controls.MediaState.Manual>。 <xref:System.Windows.Controls.MediaElement>透過評估下列優先順序處理此控制項的競爭。  
  
1.  <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>. 當媒體卸載時取得控制權。 這可確保依預設，並釋出所有媒體資源，即使<xref:System.Windows.Media.MediaClock>聯<xref:System.Windows.Controls.MediaElement>。  
  
2.  <xref:System.Windows.Media.MediaClock>. 媒體已就地<xref:System.Windows.Controls.MediaElement.Clock%2A>。 如果媒體已卸載，<xref:System.Windows.Media.MediaClock>生效，因此只要<xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>是<xref:System.Windows.Controls.MediaState.Manual>。 時鐘模式永遠會覆寫的載入的行為<xref:System.Windows.Controls.MediaElement>。  
  
3.  <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>. 當媒體載入時取得控制權。  
  
4.  互動式控制方法。 在放置時<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>是<xref:System.Windows.Controls.MediaState.Manual>。 使用控制方法<xref:System.Windows.Controls.MediaElement.Play%2A>， <xref:System.Windows.Controls.MediaElement.Pause%2A>， <xref:System.Windows.Controls.MediaElement.Close%2A>，和<xref:System.Windows.Controls.MediaElement.Stop%2A>。  
  
### <a name="displaying-a-mediaelement"></a>顯示 MediaElement  
 若要顯示<xref:System.Windows.Controls.MediaElement>必須呈現內容，而且會有其<xref:System.Windows.FrameworkElement.ActualWidth%2A>和<xref:System.Windows.FrameworkElement.ActualHeight%2A>屬性設為零，直到載入內容。 對於僅含音訊的內容，這些屬性一率為零。 如需視訊內容，一次<xref:System.Windows.Controls.MediaElement.MediaOpened>在引發事件<xref:System.Windows.FrameworkElement.ActualWidth%2A>和<xref:System.Windows.FrameworkElement.ActualHeight%2A>將報表載入的媒體大小。 這表示，直到載入媒體，<xref:System.Windows.Controls.MediaElement>將不會佔用中的任何實體空間[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]除非<xref:System.Windows.FrameworkElement.Width%2A>或<xref:System.Windows.FrameworkElement.Height%2A>屬性設定。  
  
 設定同時<xref:System.Windows.FrameworkElement.Width%2A>和<xref:System.Windows.FrameworkElement.Height%2A>屬性會導致要自動縮放以填滿區域提供的媒體<xref:System.Windows.Controls.MediaElement>。 若要保留原始外觀比例的媒體，或是<xref:System.Windows.FrameworkElement.Width%2A>或<xref:System.Windows.FrameworkElement.Height%2A>屬性應設定，但非兩者。 設定同時<xref:System.Windows.FrameworkElement.Width%2A>和<xref:System.Windows.FrameworkElement.Height%2A>屬性會導致要呈現可能不想要的固定項目大小的媒體。  
  
 若要避免產生固定大小的元素，[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 可以預載該媒體。 這是藉由設定<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>為<xref:System.Windows.Controls.MediaState.Play>或<xref:System.Windows.Controls.MediaState.Pause>。 在<xref:System.Windows.Controls.MediaState.Pause>狀態時，媒體將會預載並提供第一個框架。 在<xref:System.Windows.Controls.MediaState.Play>狀態時，媒體將會預載並開始播放。  
  
<a name="mediaplayer"></a>   
## <a name="mediaplayer-class"></a>MediaPlayer 類別  
 其中<xref:System.Windows.Controls.MediaElement>類別是架構項目的<xref:System.Windows.Media.MediaPlayer>類別設計來用於<xref:System.Windows.Media.Drawing>物件。 可以犧牲架構層級功能，以取得效能優勢或當您需要使用繪圖物件<xref:System.Windows.Freezable>功能。 <xref:System.Windows.Media.MediaPlayer>可讓您利用這些功能時提供您的應用程式中的媒體內容。 像<xref:System.Windows.Controls.MediaElement>，<xref:System.Windows.Media.MediaPlayer>可用於獨立或不時鐘模式，但是不會有<xref:System.Windows.Controls.MediaElement>物件的已卸載，並且載入狀態。 這可降低的播放控制項複雜性<xref:System.Windows.Media.MediaPlayer>。  
  
### <a name="controlling-mediaplayer"></a>控制 MediaPlayer  
 因為<xref:System.Windows.Media.MediaPlayer>是無狀態，有只有兩種方式來控制播放媒體。  
  
1.  互動式控制方法。 在獨立模式中就地 (`null` <xref:System.Windows.Media.MediaPlayer.Clock%2A>屬性)。  
  
2.  <xref:System.Windows.Media.MediaClock>. 媒體已就地<xref:System.Windows.Media.MediaPlayer.Clock%2A>。  
  
### <a name="displaying-a-mediaplayer"></a>顯示 MediaPlayer  
 技術上來說，<xref:System.Windows.Media.MediaPlayer>無法顯示，因為它有沒有實體的表示法。 不過，它可用來呈現媒體<xref:System.Windows.Media.Drawing>使用<xref:System.Windows.Media.VideoDrawing>類別。 下列範例示範如何使用<xref:System.Windows.Media.VideoDrawing>顯示媒體。  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 請參閱[繪圖物件概觀](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)如需有關<xref:System.Windows.Media.Drawing>物件。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Media.DrawingGroup>  
 [版面配置](../../../../docs/framework/wpf/advanced/layout.md)  
 [操作說明主題](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)

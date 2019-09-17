---
title: 多媒體概觀
ms.date: 03/30/2017
helpviewer_keywords:
- multimedia [WPF]
- media [WPF]
ms.assetid: feb25b15-d741-4ac3-818f-1b19f63a3562
ms.openlocfilehash: 44059fe96a0deeda18f0abd9079100b55be98e77
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929626"
---
# <a name="multimedia-overview"></a>多媒體概觀
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中的多媒體功能可讓您將音訊和視訊整合到您的應用程式中，以增強使用者體驗。 本主題介紹 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的多媒體功能。  

<a name="mediaapi"></a>   
## <a name="media-api"></a>媒體 API  
 <xref:System.Windows.Controls.MediaElement> 和<xref:System.Windows.Media.MediaPlayer>類別是用來呈現音訊或影片內容。 您可以透過互動式的方式或是時鐘來控制這些類別。 這些類別可以用於 [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] 10 的媒體播放控制。 使用的類別需視案例而定。  
  
 <xref:System.Windows.Controls.MediaElement> 是[配置](../advanced/layout.md)支援的，可做為許多控制項的內容使用。<xref:System.Windows.UIElement> 它也可用於 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 以及程式碼中。 <xref:System.Windows.Media.MediaPlayer>另一方面，是針對<xref:System.Windows.Media.Drawing>物件所設計，缺少版面配置支援。 使用載入的<xref:System.Windows.Media.MediaPlayer>媒體只能<xref:System.Windows.Media.VideoDrawing>使用來呈現，或直接與<xref:System.Windows.Media.DrawingContext>互動。 <xref:System.Windows.Media.MediaPlayer>無法在 XAML 中使用。  
  
 如需繪圖物件和繪圖內容的詳細資訊，請參閱[繪圖物件概觀](drawing-objects-overview.md)。  
  
> [!NOTE]
> 在隨著您的應用程式散發媒體時，您無法使用媒體檔案做為專案資源。 在您的專案檔中，您必須改為將媒體類型設定為 `Content`，並將 `CopyToOutputDirectory` 設定為 `PreserveNewest` 或 `Always`。  
  
<a name="mediaplaybackmodes"></a>   
## <a name="media-playback-modes"></a>媒體播放模式  
  
> [!NOTE]
> <xref:System.Windows.Controls.MediaElement> 和<xref:System.Windows.Media.MediaPlayer>都有類似的成員。 本節中的連結會參考<xref:System.Windows.Controls.MediaElement>類別成員。 除非特別注明，否則，在類別中<xref:System.Windows.Controls.MediaElement>連結至的成員也可以<xref:System.Windows.Media.MediaPlayer>在類別中找到。  
  
 若要了解 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中的媒體播放，必須先了解不同的媒體播放模式。 <xref:System.Windows.Controls.MediaElement> 和<xref:System.Windows.Media.MediaPlayer>都可以用於兩種不同的媒體模式，獨立模式和時鐘模式。 媒體模式是由<xref:System.Windows.Controls.MediaElement.Clock%2A>屬性所決定。 當<xref:System.Windows.Controls.MediaElement.Clock%2A> 為`null`時，媒體物件會處於獨立模式。 <xref:System.Windows.Controls.MediaElement.Clock%2A>當不是 null 時，媒體物件會處於時鐘模式。 根據預設，媒體物件是處於獨立模式。  
  
### <a name="independent-mode"></a>獨立模式  
 在獨立模式中，媒體內容會驅動媒體播放。 獨立模式提供下列選項：  
  
- 可以直接<xref:System.Uri>指定媒體的。  
  
- 可以直接控制媒體播放。  
  
- 可以修改<xref:System.Windows.Controls.MediaElement.Position%2A>媒體<xref:System.Windows.Controls.MediaElement.SpeedRatio%2A>的和屬性。  
  
 您可以<xref:System.Windows.Controls.MediaElement>藉由設定物件的<xref:System.Windows.Controls.MediaElement.Source%2A> <xref:System.Windows.Media.MediaPlayer>屬性或呼叫物件的<xref:System.Windows.Media.MediaPlayer.Open%2A>方法來載入媒體。  
  
 若要在獨立模式中控制媒體播放，可以使用媒體物件的控制方法。 可用的控制項方法為<xref:System.Windows.Controls.MediaElement.Play%2A>、 <xref:System.Windows.Controls.MediaElement.Pause%2A>、 <xref:System.Windows.Controls.MediaElement.Close%2A>和<xref:System.Windows.Controls.MediaElement.Stop%2A>。 針對<xref:System.Windows.Controls.MediaElement>，只有<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>當設定為<xref:System.Windows.Controls.MediaState.Manual>時，才可以使用這些方法的互動式控制項。 當媒體物件處於時鐘模式時，無法使用這些方法。  
  
 如需獨立模式的範例，請參閱[控制 MediaElement (播放、暫停、停止、音量和速度)](how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md)。  
  
### <a name="clock-mode"></a>時鐘模式  
 在時鐘模式中， <xref:System.Windows.Media.MediaTimeline>磁片磁碟機會播放媒體。 時鐘模式具有下列特性：  
  
- 媒體會透過間接設定<xref:System.Windows.Media.MediaTimeline> <xref:System.Uri> 。  
  
- 可由時鐘來控制媒體播放。 無法使用媒體物件的控制方法。  
  
- 媒體的載入方式是設定<xref:System.Windows.Media.MediaTimeline>物件的<xref:System.Windows.Media.MediaTimeline.Source%2A>屬性、從時間軸建立時鐘，以及將時鐘指派給媒體物件。 當<xref:System.Windows.Media.MediaTimeline> 位於<xref:System.Windows.Media.Animation.Storyboard>目標a<xref:System.Windows.Controls.MediaElement>內的時，也會以這種方式載入媒體。  
  
 若要控制以時鐘模式播放的<xref:System.Windows.Media.Animation.ClockController>媒體，必須使用控制方法。 是從的屬性取得<xref:System.Windows.Media.MediaClock>。 <xref:System.Windows.Media.Animation.ClockController> <xref:System.Windows.Media.Animation.ClockController> 如果您嘗試<xref:System.Windows.Controls.MediaElement> 在時鐘<xref:System.Windows.Media.MediaPlayer>模式中使用或物件的控制項方法，將會擲回。<xref:System.InvalidOperationException>  
  
 如需時鐘和時間軸的詳細資訊，請參閱[動畫概觀](animation-overview.md)。  
  
 如需時鐘模式的範例，請參閱[使用分鏡腳本控制 MediaElement](how-to-control-a-mediaelement-by-using-a-storyboard.md)。  
  
<a name="mediaelement"></a>   
## <a name="mediaelement-class"></a>MediaElement 類別  
 將媒體新增至應用程式，就像將<xref:System.Windows.Controls.MediaElement>控制項新增至應用程式的[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] ，以及將提供<xref:System.Uri>給您想要包含的媒體一樣簡單。 [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] 10 支援的所有媒體類型，在 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中也都支援。 下列範例顯示<xref:System.Windows.Controls.MediaElement>中[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]的簡單用法。  
  
 [!code-xaml[MediaElement_snip#SimpleMediaElementUsageWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaElement_snip/CSharp/SimpleUsage.xaml#simplemediaelementusagewholepage)]  
  
 在此範例中，媒體一載入就會自動播放。 媒體播放完之後，系統就會關閉媒體並釋放所有媒體資源 (包括視訊記憶體)。 這是<xref:System.Windows.Controls.MediaElement>物件的預設行為，而且是<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>由和<xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>屬性所控制。  
  
### <a name="controlling-a-mediaelement"></a>控制 MediaElement  
 <xref:System.Windows.Controls.MediaElement> 當是`true`或<xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> 時`false`，和屬性會分別控制的行為。<xref:System.Windows.FrameworkElement.IsLoaded%2A> <xref:System.Windows.Controls.MediaState>屬性會設定為影響媒體播放行為。 例如，預設<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>值是<xref:System.Windows.Controls.MediaState.Play> ，而預設值<xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>是<xref:System.Windows.Controls.MediaState.Close>。 這表示<xref:System.Windows.Controls.MediaElement>只要載入並完成預先執行，媒體就會開始播放。 一旦播放完成，系統就會關閉媒體並釋放所有媒體資源。  
  
 <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> 和<xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>屬性不是控制媒體播放的唯一方式。 在時鐘模式中，時鐘可以控制<xref:System.Windows.Controls.MediaElement> ，而且<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>當為<xref:System.Windows.Controls.MediaState.Manual>時，互動式控制項方法就具有控制權。 <xref:System.Windows.Controls.MediaElement>藉由評估下列優先順序來處理這項競賽。  
  
1. <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>. 當媒體卸載時取得控制權。 這可確保預設會釋放所有媒體資源，即使<xref:System.Windows.Media.MediaClock> <xref:System.Windows.Controls.MediaElement>與關聯。  
  
2. <xref:System.Windows.Media.MediaClock>. 當媒體具有<xref:System.Windows.Controls.MediaElement.Clock%2A>時，就會備妥。 如果卸載媒體，則只要<xref:System.Windows.Media.MediaClock> <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>為<xref:System.Windows.Controls.MediaState.Manual>，就會生效。 時鐘模式一律會覆寫的載入行為<xref:System.Windows.Controls.MediaElement>。  
  
3. <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>. 當媒體載入時取得控制權。  
  
4. 互動式控制方法。 當為<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> <xref:System.Windows.Controls.MediaState.Manual>時，就地。 可用的控制項方法為<xref:System.Windows.Controls.MediaElement.Play%2A>、 <xref:System.Windows.Controls.MediaElement.Pause%2A>、 <xref:System.Windows.Controls.MediaElement.Close%2A>和<xref:System.Windows.Controls.MediaElement.Stop%2A>。  
  
### <a name="displaying-a-mediaelement"></a>顯示 MediaElement  
 若要顯示<xref:System.Windows.Controls.MediaElement> ，它必須具有要轉譯的內容，而且在<xref:System.Windows.FrameworkElement.ActualWidth%2A>載入<xref:System.Windows.FrameworkElement.ActualHeight%2A>內容之前，其和屬性會設定為零。 對於僅含音訊的內容，這些屬性一率為零。 針對影片內容，一旦<xref:System.Windows.Controls.MediaElement.MediaOpened> <xref:System.Windows.FrameworkElement.ActualWidth%2A>引發事件，並<xref:System.Windows.FrameworkElement.ActualHeight%2A>將報告載入的媒體大小。 這表示在<xref:System.Windows.Controls.MediaElement>載入媒體之前， [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]除非設定了<xref:System.Windows.FrameworkElement.Width%2A>或<xref:System.Windows.FrameworkElement.Height%2A>屬性，否則將不會佔用中的任何實體空間。  
  
 同時<xref:System.Windows.FrameworkElement.Width%2A>設定和<xref:System.Windows.FrameworkElement.Height%2A>屬性會導致媒體延展，以填滿提供<xref:System.Windows.Controls.MediaElement>給的區域。 若要保留媒體的原始長寬比， <xref:System.Windows.FrameworkElement.Width%2A>應該設定或<xref:System.Windows.FrameworkElement.Height%2A>屬性，但不能兩者都設定。 同時<xref:System.Windows.FrameworkElement.Width%2A>設定和<xref:System.Windows.FrameworkElement.Height%2A>屬性會導致媒體出現在可能不需要的固定元素大小中。  
  
 若要避免產生固定大小的元素，[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 可以預載該媒體。 將設定<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> <xref:System.Windows.Controls.MediaState.Play>為或<xref:System.Windows.Controls.MediaState.Pause>，即可完成此作業。 <xref:System.Windows.Controls.MediaState.Pause>在狀態中，媒體將會預先進行，並會顯示第一個畫面。 <xref:System.Windows.Controls.MediaState.Play>在狀態中，媒體將會預先啟動並開始播放。  
  
<a name="mediaplayer"></a>   
## <a name="mediaplayer-class"></a>MediaPlayer 類別  
 當<xref:System.Windows.Controls.MediaElement>類別是架構元素時<xref:System.Windows.Media.MediaPlayer> ，類別是設計用於物件中<xref:System.Windows.Media.Drawing> 。 當您可以犧牲架構層級功能來取得效能優勢，或當您需要<xref:System.Windows.Freezable>功能時，會使用繪製物件。 <xref:System.Windows.Media.MediaPlayer>可讓您利用這些功能，同時在您的應用程式中提供媒體內容。 就<xref:System.Windows.Controls.MediaElement>像<xref:System.Windows.Media.MediaPlayer>一樣，可以在獨立或時鐘模式中使用， <xref:System.Windows.Controls.MediaElement>但不會有物件的卸載和載入狀態。 這可減少的播放控制複雜度<xref:System.Windows.Media.MediaPlayer>。  
  
### <a name="controlling-mediaplayer"></a>控制 MediaPlayer  
 因為<xref:System.Windows.Media.MediaPlayer>是無狀態的，所以有兩種方式可以控制媒體播放。  
  
1. 互動式控制方法。 在獨立模式（`null` <xref:System.Windows.Media.MediaPlayer.Clock%2A>屬性）中的位置。  
  
2. <xref:System.Windows.Media.MediaClock>. 當媒體具有<xref:System.Windows.Media.MediaPlayer.Clock%2A>時，就會備妥。  
  
### <a name="displaying-a-mediaplayer"></a>顯示 MediaPlayer  
 技術上而言<xref:System.Windows.Media.MediaPlayer> ，無法顯示，因為它沒有實體標記法。 不過，它可以用來在中<xref:System.Windows.Media.Drawing> <xref:System.Windows.Media.VideoDrawing>使用類別來呈現媒體。 下列範例示範<xref:System.Windows.Media.VideoDrawing>如何使用來顯示媒體。  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 如需<xref:System.Windows.Media.Drawing>物件的詳細資訊，請參閱[繪圖物件總覽](drawing-objects-overview.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.DrawingGroup>
- [版面配置](../advanced/layout.md)
- [HOW-TO 主題](audio-and-video-how-to-topics.md)

---
title: 多媒體概觀
ms.date: 03/30/2017
helpviewer_keywords:
- multimedia [WPF]
- media [WPF]
ms.assetid: feb25b15-d741-4ac3-818f-1b19f63a3562
ms.openlocfilehash: d4abf4d9fd324ffbf2737dc686c02e50ca1a8a5a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181878"
---
# <a name="multimedia-overview"></a>多媒體概觀
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中的多媒體功能可讓您將音訊和視訊整合到您的應用程式中，以增強使用者體驗。 本主題介紹 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的多媒體功能。  

<a name="mediaapi"></a>
## <a name="media-api"></a>媒體 API  
 <xref:System.Windows.Controls.MediaElement>和<xref:System.Windows.Media.MediaPlayer>類用於顯示音訊或視頻內容。 您可以透過互動式的方式或是時鐘來控制這些類別。 這些類可以在 Microsoft Windows 媒體播放機 10 控制項上用於媒體播放。 使用的類別需視案例而定。  
  
 <xref:System.Windows.Controls.MediaElement>是佈局<xref:System.Windows.UIElement>支援的 ，可以用作[Layout](../advanced/layout.md)許多控制項的內容。 它也可用於 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 以及程式碼中。 <xref:System.Windows.Media.MediaPlayer>另一方面，是為<xref:System.Windows.Media.Drawing>物件設計的，並且缺少佈局支援。 使用 載入的媒體<xref:System.Windows.Media.MediaPlayer>只能使用<xref:System.Windows.Media.VideoDrawing>或 直接與 交互顯示<xref:System.Windows.Media.DrawingContext>。 <xref:System.Windows.Media.MediaPlayer>不能在 XAML 中使用。  
  
 如需繪圖物件和繪圖內容的詳細資訊，請參閱[繪圖物件概觀](drawing-objects-overview.md)。  
  
> [!NOTE]
> 在隨著您的應用程式散發媒體時，您無法使用媒體檔案做為專案資源。 在您的專案檔中，您必須改為將媒體類型設定為 `Content`，並將 `CopyToOutputDirectory` 設定為 `PreserveNewest` 或 `Always`。  
  
<a name="mediaplaybackmodes"></a>
## <a name="media-playback-modes"></a>媒體播放模式  
  
> [!NOTE]
> 和<xref:System.Windows.Controls.MediaElement><xref:System.Windows.Media.MediaPlayer>都有類似的成員。 本節中的連結引用<xref:System.Windows.Controls.MediaElement>類成員。 除非特別注意，否則在<xref:System.Windows.Controls.MediaElement>類中連結的成員也可以在類中找到。 <xref:System.Windows.Media.MediaPlayer>  
  
 若要了解 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中的媒體播放，必須先了解不同的媒體播放模式。 <xref:System.Windows.Controls.MediaElement>和<xref:System.Windows.Media.MediaPlayer>都可以在兩種不同的媒體模式下使用，即獨立模式和時鐘模式。 媒體模式由<xref:System.Windows.Controls.MediaElement.Clock%2A>屬性確定。 當<xref:System.Windows.Controls.MediaElement.Clock%2A>`null`為 時，媒體物件處於獨立模式。 當<xref:System.Windows.Controls.MediaElement.Clock%2A>為非空時，媒體物件處於時鐘模式。 根據預設，媒體物件是處於獨立模式。  
  
### <a name="independent-mode"></a>獨立模式  
 在獨立模式中，媒體內容會驅動媒體播放。 獨立模式提供下列選項：  
  
- <xref:System.Uri>可以直接指定介質。  
  
- 可以直接控制媒體播放。  
  
- <xref:System.Windows.Controls.MediaElement.Position%2A>可以修改媒體和<xref:System.Windows.Controls.MediaElement.SpeedRatio%2A>屬性。  
  
 通過設置<xref:System.Windows.Controls.MediaElement>物件<xref:System.Windows.Controls.MediaElement.Source%2A>的屬性或調用<xref:System.Windows.Media.MediaPlayer>物件<xref:System.Windows.Media.MediaPlayer.Open%2A>的方法來載入媒體。  
  
 若要在獨立模式中控制媒體播放，可以使用媒體物件的控制方法。 可用的控制方法是<xref:System.Windows.Controls.MediaElement.Play%2A>、<xref:System.Windows.Controls.MediaElement.Pause%2A><xref:System.Windows.Controls.MediaElement.Close%2A>和<xref:System.Windows.Controls.MediaElement.Stop%2A>。 對於<xref:System.Windows.Controls.MediaElement>，使用這些方法的互動式控制項僅在 設置為<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>時才可用<xref:System.Windows.Controls.MediaState.Manual>。 當媒體物件處於時鐘模式時，無法使用這些方法。  
  
 如需獨立模式的範例，請參閱[控制 MediaElement (播放、暫停、停止、音量和速度)](how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md)。  
  
### <a name="clock-mode"></a>時鐘模式  
 在時鐘模式下，磁碟機<xref:System.Windows.Media.MediaTimeline>媒體播放。 時鐘模式具有下列特性：  
  
- 媒體的是<xref:System.Uri>間接設置通過<xref:System.Windows.Media.MediaTimeline>。  
  
- 可由時鐘來控制媒體播放。 無法使用媒體物件的控制方法。  
  
- 通過設置<xref:System.Windows.Media.MediaTimeline>物件<xref:System.Windows.Media.MediaTimeline.Source%2A>的屬性、從時間表創建時鐘以及將時鐘分配給媒體物件來載入媒體。 當<xref:System.Windows.Media.MediaTimeline>內部<xref:System.Windows.Media.Animation.Storyboard>目標 時，媒體也會以這種方式載入<xref:System.Windows.Controls.MediaElement>。  
  
 要控制時鐘模式下的媒體播放，<xref:System.Windows.Media.Animation.ClockController>必須使用控制方法。 A<xref:System.Windows.Media.Animation.ClockController>是從<xref:System.Windows.Media.Animation.ClockController>的屬性獲取的<xref:System.Windows.Media.MediaClock>。 如果在時鐘模式下嘗試使用 或<xref:System.Windows.Controls.MediaElement><xref:System.Windows.Media.MediaPlayer>物件的控制方法，將引發 。 <xref:System.InvalidOperationException>  
  
 如需時鐘和時間軸的詳細資訊，請參閱[動畫概觀](animation-overview.md)。  
  
 如需時鐘模式的範例，請參閱[使用分鏡腳本控制 MediaElement](how-to-control-a-mediaelement-by-using-a-storyboard.md)。  
  
<a name="mediaelement"></a>
## <a name="mediaelement-class"></a>MediaElement 類別  
 向應用程式添加媒體非常簡單，只需向<xref:System.Windows.Controls.MediaElement>[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]應用程式的控制項添加控制項，並向要包括的媒體提供<xref:System.Uri>一樣。 Microsoft Windows 媒體播放機 10 支援的所有媒體類型[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]。 下面的示例顯示了<xref:System.Windows.Controls.MediaElement>中[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]的簡單用法。  
  
 [!code-xaml[MediaElement_snip#SimpleMediaElementUsageWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaElement_snip/CSharp/SimpleUsage.xaml#simplemediaelementusagewholepage)]  
  
 在此範例中，媒體一載入就會自動播放。 媒體播放完之後，系統就會關閉媒體並釋放所有媒體資源 (包括視訊記憶體)。 這是物件的預設行為，<xref:System.Windows.Controls.MediaElement>由<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>和<xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>屬性控制。  
  
### <a name="controlling-a-mediaelement"></a>控制 MediaElement  
 <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>和 屬性分別控制<xref:System.Windows.Controls.MediaElement>時<xref:System.Windows.FrameworkElement.IsLoaded%2A>`true`或`false`的行為。 屬性<xref:System.Windows.Controls.MediaState>設置為影響媒體播放行為。 <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>例如，預設值<xref:System.Windows.Controls.MediaState.Play>為，預設值<xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>為<xref:System.Windows.Controls.MediaState.Close>。 這意味著，一旦<xref:System.Windows.Controls.MediaElement>載入和預卷完成，媒體開始播放。 一旦播放完成，系統就會關閉媒體並釋放所有媒體資源。  
  
 和<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A><xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>屬性不是控制媒體播放的唯一方法。 在時鐘模式下，時鐘可以控制，<xref:System.Windows.Controls.MediaElement>交互控制方法可以控制何時<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>是<xref:System.Windows.Controls.MediaState.Manual>。 <xref:System.Windows.Controls.MediaElement>通過評估以下優先順序來處理這種控制競爭。  
  
1. <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>. 當媒體卸載時取得控制權。 這可確保預設情況下釋放所有媒體資源，即使<xref:System.Windows.Media.MediaClock>與 關聯也是如此。 <xref:System.Windows.Controls.MediaElement>  
  
2. <xref:System.Windows.Media.MediaClock>. 當媒體具有 時就<xref:System.Windows.Controls.MediaElement.Clock%2A>位。 如果卸載媒體，則 只要<xref:System.Windows.Media.MediaClock><xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>是<xref:System.Windows.Controls.MediaState.Manual>， 就會生效。 時鐘模式始終覆蓋 的<xref:System.Windows.Controls.MediaElement>載入行為。  
  
3. <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>. 當媒體載入時取得控制權。  
  
4. 互動式控制方法。 在原地<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>時<xref:System.Windows.Controls.MediaState.Manual>是 。 可用的控制方法是<xref:System.Windows.Controls.MediaElement.Play%2A>、<xref:System.Windows.Controls.MediaElement.Pause%2A><xref:System.Windows.Controls.MediaElement.Close%2A>和<xref:System.Windows.Controls.MediaElement.Stop%2A>。  
  
### <a name="displaying-a-mediaelement"></a>顯示 MediaElement  
 要顯示<xref:System.Windows.Controls.MediaElement>的內容，它必須具有要呈現的內容，並且其<xref:System.Windows.FrameworkElement.ActualWidth%2A>和<xref:System.Windows.FrameworkElement.ActualHeight%2A>屬性將設置為零，直到載入內容。 對於僅含音訊的內容，這些屬性一率為零。 對於視頻內容，一旦<xref:System.Windows.Controls.MediaElement.MediaOpened>事件被引發，<xref:System.Windows.FrameworkElement.ActualWidth%2A>將<xref:System.Windows.FrameworkElement.ActualHeight%2A>報告載入介質的大小。 這意味著，在載入媒體之前<xref:System.Windows.Controls.MediaElement>，不會佔用 或[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]<xref:System.Windows.FrameworkElement.Width%2A><xref:System.Windows.FrameworkElement.Height%2A>屬性中的任何物理空間。  
  
 設置 和<xref:System.Windows.FrameworkElement.Width%2A><xref:System.Windows.FrameworkElement.Height%2A>屬性將導致媒體拉伸以填充 為 提供的區域<xref:System.Windows.Controls.MediaElement>。 為了保持媒體的原始縱橫比，應設置<xref:System.Windows.FrameworkElement.Width%2A>或<xref:System.Windows.FrameworkElement.Height%2A>屬性，但不能同時設置這兩種。 設置<xref:System.Windows.FrameworkElement.Width%2A>和<xref:System.Windows.FrameworkElement.Height%2A>屬性將導致介質以固定元素大小呈現，而該大小可能不可取。  
  
 若要避免產生固定大小的元素，[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 可以預載該媒體。 這是通過將 設置為<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>或<xref:System.Windows.Controls.MediaState.Play><xref:System.Windows.Controls.MediaState.Pause>。 在狀態<xref:System.Windows.Controls.MediaState.Pause>下，媒體將預卷並呈現第一幀。 在一<xref:System.Windows.Controls.MediaState.Play>種狀態下，媒體將預先播放並開始播放。  
  
<a name="mediaplayer"></a>
## <a name="mediaplayer-class"></a>MediaPlayer 類別  
 當<xref:System.Windows.Controls.MediaElement>類是框架元素時，<xref:System.Windows.Media.MediaPlayer>類被設計為用於<xref:System.Windows.Media.Drawing>物件。 當可以犧牲框架級別要素以獲得性能優勢時，或者在需要時<xref:System.Windows.Freezable>，使用繪圖物件。 <xref:System.Windows.Media.MediaPlayer>使您能夠利用這些功能，同時在應用程式中提供媒體內容。 喜歡<xref:System.Windows.Controls.MediaElement> <xref:System.Windows.Media.MediaPlayer> ，可以在獨立模式或時鐘模式下使用，<xref:System.Windows.Controls.MediaElement>但沒有物件的卸載和載入狀態。 這降低了 的<xref:System.Windows.Media.MediaPlayer>播放控制複雜性。  
  
### <a name="controlling-mediaplayer"></a>控制 MediaPlayer  
 因為它是<xref:System.Windows.Media.MediaPlayer>無狀態的，只有兩種方法可以控制媒體播放。  
  
1. 互動式控制方法。 在獨立模式下就位（`null`<xref:System.Windows.Media.MediaPlayer.Clock%2A>屬性）。  
  
2. <xref:System.Windows.Media.MediaClock>. 當媒體具有 時就<xref:System.Windows.Media.MediaPlayer.Clock%2A>位。  
  
### <a name="displaying-a-mediaplayer"></a>顯示 MediaPlayer  
 從技術上講，無法顯示<xref:System.Windows.Media.MediaPlayer>，因為它沒有物理表示形式。 但是，它可用於在<xref:System.Windows.Media.Drawing>使用<xref:System.Windows.Media.VideoDrawing>類中呈現媒體。 下面的示例演示了使用<xref:System.Windows.Media.VideoDrawing>顯示媒體。  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 有關<xref:System.Windows.Media.Drawing>物件的詳細資訊，請參閱[繪圖物件概述](drawing-objects-overview.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.DrawingGroup>
- [版面配置](../advanced/layout.md)
- [如何使用主題](audio-and-video-how-to-topics.md)

---
title: "多媒體概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "媒體"
  - "多媒體"
ms.assetid: feb25b15-d741-4ac3-818f-1b19f63a3562
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# 多媒體概觀
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中的多媒體功能可讓您將音訊和視訊整合至應用程式中，以強化使用者的體驗。本主題介紹 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的多媒體功能。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="mediaapi"></a>   
## 媒體 API  
 <xref:System.Windows.Controls.MediaElement> 和 <xref:System.Windows.Media.MediaPlayer> 類別都用於呈現音訊或視訊內容。  這兩個類別都以互動方式或以時脈控制。  這些類別可用在 [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] 10 的媒體播放控制項。應採用哪個類別，依據案例而定。  
  
 <xref:System.Windows.Controls.MediaElement> 是由 [配置](../../../../docs/framework/wpf/advanced/layout.md) 支援的 <xref:System.Windows.UIElement>，可取用為許多控制項的內容。  這個項目也可用於[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 和程式碼。另一方面，<xref:System.Windows.Media.MediaPlayer> 則是針對 <xref:System.Windows.Media.Drawing> 物件所設計，因此缺少配置支援。  使用 <xref:System.Windows.Media.MediaPlayer> 載入的媒體只能使用 <xref:System.Windows.Media.VideoDrawing> 呈現，或經由直接與 <xref:System.Windows.Media.DrawingContext> 互動來呈現。  <xref:System.Windows.Media.MediaPlayer> 無法用於 XAML 中。  
  
 如需繪圖物件和繪圖內容的詳細資訊，請參閱[繪圖物件概觀](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)。  
  
> [!NOTE]
>  使用您的應用程式散發媒體時，您不能將媒體檔案當做專案資源來使用。  在專案檔中，您必須改為將媒體類型設為 `Content`，並將 `CopyToOutputDirectory` 設為 `PreserveNewest` 或 `Always`。  
  
<a name="mediaplaybackmodes"></a>   
## 媒體播放模式  
  
> [!NOTE]
>  <xref:System.Windows.Controls.MediaElement> 和 <xref:System.Windows.Media.MediaPlayer> 兩者具有類似的成員。  本節中的連結會參考 <xref:System.Windows.Controls.MediaElement> 類別成員。  除非特別註明，否則也可在 <xref:System.Windows.Media.MediaPlayer> 類別中找到連結至 <xref:System.Windows.Controls.MediaElement> 類別的成員。  
  
 若要了解 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中的媒體播放，一定要了解可用以播放媒體的不同模式。  <xref:System.Windows.Controls.MediaElement> 和 <xref:System.Windows.Media.MediaPlayer> 都可用於兩種不同的媒體模式：獨立模式和時脈模式。  媒體模式是由 <xref:System.Windows.Controls.MediaElement.Clock%2A> 屬性所決定。  當 <xref:System.Windows.Controls.MediaElement.Clock%2A> 為 `null` 時，媒體物件為獨立模式。  當 <xref:System.Windows.Controls.MediaElement.Clock%2A> 不是 null 時，媒體物件則為時脈模式。  媒體物件預設為獨立模式。  
  
### 獨立模式  
 在獨立模式中，媒體內容會驅動媒體播放。  獨立模式提供下列選項：  
  
-   可以直接指定媒體的 <xref:System.Uri>。  
  
-   可以直接控制媒體播放。  
  
-   可以修改媒體的 <xref:System.Windows.Controls.MediaElement.Position%2A> 和 <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> 屬性。  
  
 設定 <xref:System.Windows.Controls.MediaElement> 物件的 <xref:System.Windows.Controls.MediaElement.Source%2A> 屬性或呼叫 <xref:System.Windows.Media.MediaPlayer> 物件的 <xref:System.Windows.Media.MediaPlayer.Open%2A> 方法，便會載入媒體。  
  
 若要在獨立模式中控制媒體播放，可以使用媒體物件的控制方法。  可用的控制方法為 <xref:System.Windows.Controls.MediaElement.Play%2A>、<xref:System.Windows.Controls.MediaElement.Pause%2A>、<xref:System.Windows.Controls.MediaElement.Close%2A> 和 <xref:System.Windows.Controls.MediaElement.Stop%2A>。  若為 <xref:System.Windows.Controls.MediaElement>，當 <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> 設為 <xref:System.Windows.Controls.MediaState> 時，才能使用採用這些方法的互動式控制。  當媒體物件為時脈模式時，則無法使用這些方法。  
  
 如需獨立模式的範例，請參閱 [控制 MediaElement \(播放、暫停、停止、音量和速度\)](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md)。  
  
### 時脈模式  
 在時脈模式中，<xref:System.Windows.Media.MediaTimeline> 會驅動媒體播放。  時脈模式具有下列特性：  
  
-   會透過 <xref:System.Windows.Media.MediaTimeline> 間接設定媒體的 <xref:System.Uri>。  
  
-   時脈可以控制媒體播放。  但無法使用媒體物件的控制方法。  
  
-   設定 <xref:System.Windows.Media.MediaTimeline> 物件的 <xref:System.Windows.Media.MediaTimeline.Source%2A> 屬性、從時刻表建立時脈，並指定時脈給媒體物件，便會載入媒體。  當 <xref:System.Windows.Media.Animation.Storyboard> 內的 <xref:System.Windows.Media.MediaTimeline> 將目標設定為 <xref:System.Windows.Controls.MediaElement> 時，也可用此方式載入媒體。  
  
 若要在時脈模式中控制媒體播放，必須使用 <xref:System.Windows.Media.Animation.ClockController> 控制方法。  <xref:System.Windows.Media.Animation.ClockController> 是從 <xref:System.Windows.Media.MediaClock> 的 <xref:System.Windows.Media.Animation.ClockController> 屬性取得。  如果您在時脈模式中嘗試使用 <xref:System.Windows.Controls.MediaElement> 或 <xref:System.Windows.Media.MediaPlayer> 物件的控制方法，將會擲回 <xref:System.InvalidOperationException>。  
  
 如需時脈和時刻表的詳細資訊，請參閱[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。  
  
 如需時脈模式的範例，請參閱 [使用腳本控制 MediaElement](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-by-using-a-storyboard.md)。  
  
<a name="mediaelement"></a>   
## MediaElement 類別  
 將媒體加入至應用程式，就如同將 <xref:System.Windows.Controls.MediaElement> 控制項加入至應用程式的[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 及提供 <xref:System.Uri> 給您要包含的媒體一樣簡單。  [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 可支援 [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] 10 支援的所有媒體類型。下列範例顯示 <xref:System.Windows.Controls.MediaElement> 在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 中的簡單用法。  
  
 [!code-xml[MediaElement_snip#SimpleMediaElementUsageWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaElement_snip/CSharp/SimpleUsage.xaml#simplemediaelementusagewholepage)]  
  
 在此範例中，媒體會在載入後立即自動播放。  一旦媒體完成播放，就會關閉該媒體並釋放所有媒體資訊 \(包含視訊記憶體\)。  這是 <xref:System.Windows.Controls.MediaElement> 物件的預設行為，而且由 <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> 和 <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> 屬性所控制。  
  
### 控制 MediaElement  
 當 <xref:System.Windows.FrameworkElement.IsLoaded%2A> 分別為 `true` 或 `false` 時，<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> 和 <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> 屬性會控制 <xref:System.Windows.Controls.MediaElement> 的行為。  設定 <xref:System.Windows.Controls.MediaState> 屬性會影響媒體播放行為。  例如，預設 <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> 為 <xref:System.Windows.Controls.MediaState>，而預設 <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> 為 <xref:System.Windows.Controls.MediaState>。  這表示載入 <xref:System.Windows.Controls.MediaElement> 和完成[預轉](GTMT)後，就會立即開始播放媒體。  一旦播放完成，就會關閉媒體並釋放所有媒體資訊。  
  
 <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> 和 <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> 屬性並非控制媒體播放的唯一方法。  在時脈模式中，時脈可以控制 <xref:System.Windows.Controls.MediaElement>，而當 <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> 為 <xref:System.Windows.Controls.MediaState> 時，互動式控制方法具有控制權。  <xref:System.Windows.Controls.MediaElement> 會評估下列優先順序，以處理這種控制權競爭。  
  
1.  <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>.  適用於未載入媒體時。  這可確保會依預設釋放所有的媒體資源，即使 <xref:System.Windows.Media.MediaClock> 已與 <xref:System.Windows.Controls.MediaElement> 相關聯時也是如此。  
  
2.  <xref:System.Windows.Media.MediaClock>.  適用於媒體具有 <xref:System.Windows.Controls.MediaElement.Clock%2A> 時。  如果未載入媒體，只要 <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> 為 <xref:System.Windows.Controls.MediaState>，<xref:System.Windows.Media.MediaClock> 就會生效。  時脈模式一律會覆寫 <xref:System.Windows.Controls.MediaElement> 的載入行為。  
  
3.  <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>.  適用於已載入媒體時。  
  
4.  互動式控制方法：  適用於 <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> 為 <xref:System.Windows.Controls.MediaState> 時。  可用的控制方法為 <xref:System.Windows.Controls.MediaElement.Play%2A>、<xref:System.Windows.Controls.MediaElement.Pause%2A>、<xref:System.Windows.Controls.MediaElement.Close%2A> 和 <xref:System.Windows.Controls.MediaElement.Stop%2A>。  
  
### 顯示 MediaElement  
 若要顯示 <xref:System.Windows.Controls.MediaElement>，它必須有要呈現的內容，而且在載入內容以前，其 <xref:System.Windows.FrameworkElement.ActualWidth%2A> 和 <xref:System.Windows.FrameworkElement.ActualHeight%2A> 屬性會設為零。  對於僅包含音訊的內容，這些屬性永遠為零。  對於視訊內容，一旦引發 <xref:System.Windows.Controls.MediaElement.MediaOpened> 事件，<xref:System.Windows.FrameworkElement.ActualWidth%2A> 和 <xref:System.Windows.FrameworkElement.ActualHeight%2A> 就會回報所載入媒體的大小。  這表示在載入媒體前，除非已設定 <xref:System.Windows.FrameworkElement.Width%2A> 或 <xref:System.Windows.FrameworkElement.Height%2A> 屬性，否則 <xref:System.Windows.Controls.MediaElement> 不會在[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 中佔用任何實體空間。  
  
 同時設定 <xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.Height%2A> 屬性會導致媒體延伸填滿為 <xref:System.Windows.Controls.MediaElement> 所提供的區域。  若要保留媒體的原始[外觀比例](GTMT)，應設定 <xref:System.Windows.FrameworkElement.Width%2A> 或 <xref:System.Windows.FrameworkElement.Height%2A> 屬性 \(但不要同時設定\)。  同時設定 <xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.Height%2A> 屬性將導致媒體以固定的項目大小呈現，而這可能不是您需要的大小。  
  
 若要避免大小固定的項目，[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 可以[預轉](GTMT)媒體。  將 <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> 設定為 <xref:System.Windows.Controls.MediaState> 或 <xref:System.Windows.Controls.MediaState>，就可以達成這項作業。  在 <xref:System.Windows.Controls.MediaState> 狀態中，媒體將會預轉並呈現第一個畫面格。  在 <xref:System.Windows.Controls.MediaState> 狀態中，媒體將會[預轉](GTMT)並開始播放。  
  
<a name="mediaplayer"></a>   
## MediaPlayer 類別  
 雖然 <xref:System.Windows.Controls.MediaElement> 類別是架構項目，但 <xref:System.Windows.Media.MediaPlayer> 類別會設計成用於 <xref:System.Windows.Media.Drawing> 物件中。  繪製物件是在您可以犧牲架構層級功能以取得效能優點，或當您需要 <xref:System.Windows.Freezable> 功能時使用。  <xref:System.Windows.Media.MediaPlayer> 可讓您利用這些功能，同時在您的應用程式中提供媒體內容。  像 <xref:System.Windows.Controls.MediaElement> 一樣，<xref:System.Windows.Media.MediaPlayer> 可用於獨立或時脈模式中，但是沒有 <xref:System.Windows.Controls.MediaElement> 物件的未載入和已載入狀態。  這可降低 <xref:System.Windows.Media.MediaPlayer> 的播放控制複雜度。  
  
### 控制 MediaPlayer  
 因為 <xref:System.Windows.Media.MediaPlayer> 沒有狀態 \(Stateless\)，所以只有兩種方法可以控制媒體播放。  
  
1.  互動式控制方法：  適用於處於獨立模式時 \(`null` <xref:System.Windows.Media.MediaPlayer.Clock%2A> 屬性\)。  
  
2.  <xref:System.Windows.Media.MediaClock>.  適用於媒體具有 <xref:System.Windows.Media.MediaPlayer.Clock%2A> 時。  
  
### 顯示 MediaPlayer  
 在技術上，因為 <xref:System.Windows.Media.MediaPlayer> 沒有實體表示，所以無法顯示。  但是，可以使用 <xref:System.Windows.Media.VideoDrawing> 類別在 <xref:System.Windows.Media.Drawing> 中呈現媒體。  下列範例會示範如何使用 <xref:System.Windows.Media.VideoDrawing> 來顯示媒體。  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 如需 <xref:System.Windows.Media.Drawing> 物件的詳細資訊，請參閱[繪圖物件概觀](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)。  
  
## 請參閱  
 <xref:System.Windows.Media.DrawingGroup>   
 [配置](../../../../docs/framework/wpf/advanced/layout.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)
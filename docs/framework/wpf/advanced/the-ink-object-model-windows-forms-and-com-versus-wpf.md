---
title: "Ink 物件模型：Windows Form 和 COM 與 WPF 的比較 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "啟用筆墨"
  - "事件, Tablet 畫筆"
  - "Ink 物件模型"
  - "筆墨, 啟用"
  - "InkCanvas 控制項"
  - "Tablet 畫筆, 事件"
ms.assetid: 577835be-b145-4226-8570-1d309e9b3901
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Ink 物件模型：Windows Form 和 COM 與 WPF 的比較
目前，有三種平台支援數位筆墨，包括：Tablet PC Windows Forms 平台、Tablet PC COM 平台和 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] 平台。  Windows Forms 和 COM 平台會共用類似的物件模型，但 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 平台則有極大差異。  本主題會討論這些高階功能的差異，好讓操作任一物件模型的開發人員可以深入了解其他的物件模型。  
  
## 啟用應用程式中的筆墨  
 這三個平台都已隨附物件和控制項，讓應用程式可以接收來自平板電腦手寫筆的輸入。  Windows Forms 和 COM 平台隨附 <xref:Microsoft.Ink.InkPicture>、<xref:Microsoft.Ink.InkEdit>、<xref:Microsoft.Ink.InkOverlay> 和 <xref:Microsoft.Ink.InkCollector> 類別。  您可以把 <xref:Microsoft.Ink.InkPicture> 和 <xref:Microsoft.Ink.InkEdit> 這兩個控制項加到應用程式中，進行筆墨收集。  <xref:Microsoft.Ink.InkOverlay> 和 <xref:Microsoft.Ink.InkCollector> 可附加至現有的視窗、啟用筆墨的視窗和自訂控制項。  
  
 WPF 平台包含 <xref:System.Windows.Controls.InkCanvas> 控制項。  您可以將 <xref:System.Windows.Controls.InkCanvas> 加入至應用程式並立即開始收集筆墨。  使用者可以透過 <xref:System.Windows.Controls.InkCanvas>，複製、選取並調整筆墨大小。  您可以將其他控制項加入 <xref:System.Windows.Controls.InkCanvas>，而使用者也透過手寫覆寫那些控制項。  您可以將 <xref:System.Windows.Controls.InkPresenter> 加入至已啟用筆墨功能的自訂控制項並收集其手寫筆的點，來建立自訂控制項。  
  
 請參閱下表，進一步了解在應用程式中啟用筆墨的資訊：  
  
|如要完成這項工作…|在 WPF 平台上…|在 Windows Forms\/COM 平台上…|  
|---------------|----------------|-------------------------------|  
|將已啟用筆墨功能的控制項加入應用程式|請參閱[筆墨入門](../../../../docs/framework/wpf/advanced/getting-started-with-ink.md)。|請參閱[Auto Claims Form Sample](http://msdn.microsoft.com/zh-tw/bec4333a-62ca-4254-a39b-04bc2c556992)|  
|啟用自訂控制項上的比跡|請參閱[建立筆墨輸入控制項](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md)。|請參閱[Ink Clipboard Sample](http://msdn.microsoft.com/zh-tw/a0c42f1c-543d-44f8-83d9-fe810de410ff)。|  
  
## 筆墨資料  
 在 Windows Forms 和 COM 平台上，<xref:Microsoft.Ink.InkCollector>、<xref:Microsoft.Ink.InkOverlay>、<xref:Microsoft.Ink.InkEdit> 和  <xref:Microsoft.Ink.InkPicture>，任一個都會公開 <xref:Microsoft.Ink.Ink?displayProperty=fullName> 物件。  <xref:Microsoft.Ink.Ink> 物件包含一或多個 <xref:Microsoft.Ink.Stroke?displayProperty=fullName> 物件的資料，並會公開常見的方法和屬性，以管理和操作那些筆劃。  <xref:Microsoft.Ink.Ink> 物件會管理其所包含之筆劃的存留期，<xref:Microsoft.Ink.Ink> 物件會建立和刪除其所有的筆劃。  每個 <xref:Microsoft.Ink.Stroke> 都有其父 <xref:Microsoft.Ink.Ink> 物件中唯一的識別項。  
  
 在 WPF 平台上，<xref:System.Windows.Ink.Stroke?displayProperty=fullName> 類別會擁有並管理其所有的存留期。  可將 <xref:System.Windows.Ink.Stroke> 物件群組收集在 <xref:System.Windows.Ink.StrokeCollection> 中，可提供常見筆墨資料管理作業的方法，例如點擊測試、清除、轉換和序列化筆墨。  在任何指定的時間中，<xref:System.Windows.Ink.Stroke>可以屬於零個、一個或多個 <xref:System.Windows.Ink.StrokeCollection> 物件。  <xref:System.Windows.Controls.InkCanvas> 和 <xref:System.Windows.Controls.InkPresenter> 會包含 <xref:System.Windows.Ink.StrokeCollection?displayProperty=fullName>，而不需要 <xref:Microsoft.Ink.Ink?displayProperty=fullName> 物件。  
  
 下列圖例配對會比較筆墨資料物件模型。  在 Windows Forms 和 COM 平台上，<xref:Microsoft.Ink.Ink?displayProperty=fullName> 物件會限制 <xref:Microsoft.Ink.Stroke?displayProperty=fullName> 物件的存留期，且手寫筆封包會屬於個別筆畫。  兩或多個筆畫可參考相同 <xref:Microsoft.Ink.DrawingAttributes?displayProperty=fullName> 的物件，如下圖所示。  
  
 ![COM&#47;Winforms 之 Ink 物件模型的圖表。](../../../../docs/framework/wpf/advanced/media/ink-inkownsstrokes.png "Ink\_InkOwnsStrokes")  
  
 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 上，只要某項目包含 <xref:System.Windows.Ink.Stroke?displayProperty=fullName> 的參考，則其都會是 Common Language Runtime 物件。  每個 <xref:System.Windows.Ink.Stroke> 都會參考 <xref:System.Windows.Input.StylusPointCollection> 和 <xref:System.Windows.Ink.DrawingAttributes?displayProperty=fullName> 物件，這些也都是 Common Language Runtime 物件。  
  
 ![WPF 之 Ink 物件模型的圖表。](../../../../docs/framework/wpf/advanced/media/ink-wpfinkobjectmodel.png "Ink\_WPFInkObjectModel")  
  
 下表會比較如何在 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 平台和 Windows Forms 和 COM 平台上完成某些共同工作的作法。  
  
|工作|Windows Presentation Foundation|Windows Forms 和 COM|  
|--------|-------------------------------------|-------------------------|  
|儲存筆墨|<xref:System.Windows.Ink.StrokeCollection.Save%2A>|<xref:Microsoft.Ink.Ink.Save%2A>|  
|載入筆墨|使用 <xref:System.Windows.Ink.StrokeCollection.%23ctor%28System.IO.Stream%29?displayProperty=fullName> 建構函式建立 <xref:System.Windows.Ink.StrokeCollection>。|[M:Microsoft.Ink.Ink.Load\(System.Byte\<xref:Microsoft.Ink.Ink.Load%2A>|  
|點擊測試|<xref:System.Windows.Ink.StrokeCollection.HitTest%2A>|<xref:Microsoft.Ink.Ink.HitTest%2A>|  
|複製筆墨|<xref:System.Windows.Controls.InkCanvas.CopySelection%2A>|<xref:Microsoft.Ink.Ink.ClipboardCopy%2A>|  
|貼上筆墨|<xref:System.Windows.Controls.InkCanvas.Paste%2A>|<xref:Microsoft.Ink.Ink.ClipboardPaste%2A>|  
|存取筆劃集合上的自訂屬性|<xref:System.Windows.Ink.StrokeCollection.AddPropertyData%2A> \(內部存取的屬性且透過 <xref:System.Windows.Ink.StrokeCollection.AddPropertyData%2A>、<xref:System.Windows.Ink.StrokeCollection.RemovePropertyData%2A> 和 <xref:System.Windows.Ink.StrokeCollection.ContainsPropertyData%2A> 存取\)|使用 <xref:Microsoft.Ink.Ink.ExtendedProperties%2A>|  
  
### 在平台之間共用筆墨  
 雖然平台具有筆墨資料的不同物件模型，但是在平台之間共用筆墨非常容易。  下列範例會從 Windows Forms 應用程式儲存筆墨，並將筆墨載入 Windows Presentation Foundation 應用程式。  
  
 [!code-csharp[WinFormWPFInk#UsingWinforms](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwinforms)]
 [!code-vb[WinFormWPFInk#UsingWinforms](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwinforms)]  
[!code-csharp[WinFormWPFInk#SaveWinforms](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#savewinforms)]
[!code-vb[WinFormWPFInk#SaveWinforms](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#savewinforms)]  
  
 [!code-csharp[WinFormWPFInk#UsingWPF](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwpf)]
 [!code-vb[WinFormWPFInk#UsingWPF](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwpf)]  
[!code-csharp[WinFormWPFInk#LoadWPF](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#loadwpf)]
[!code-vb[WinFormWPFInk#LoadWPF](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#loadwpf)]  
  
 下列範例會從 Windows Presentation Foundation 應用程式儲存筆墨，並將筆墨載入 Windows Forms 應用程式。  
  
 [!code-csharp[WinFormWPFInk#UsingWPF](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwpf)]
 [!code-vb[WinFormWPFInk#UsingWPF](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwpf)]  
[!code-csharp[WinFormWPFInk#SaveWPF](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#savewpf)]
[!code-vb[WinFormWPFInk#SaveWPF](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#savewpf)]  
  
 [!code-csharp[WinFormWPFInk#UsingWinforms](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwinforms)]
 [!code-vb[WinFormWPFInk#UsingWinforms](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwinforms)]  
[!code-csharp[WinFormWPFInk#LoadWinforms](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#loadwinforms)]
[!code-vb[WinFormWPFInk#LoadWinforms](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#loadwinforms)]  
  
## Tablet 畫筆中的事件  
 當使用者輸入畫筆資訊時，Windows Forms 和 COM 平台上的 <xref:Microsoft.Ink.InkOverlay>、<xref:Microsoft.Ink.InkCollector> 和 <xref:Microsoft.Ink.InkPicture> 便會接收事件。  <xref:Microsoft.Ink.InkOverlay> 或 <xref:Microsoft.Ink.InkCollector> 會附加至視窗或控制項，而且可以訂閱由 Tablet 輸入資料引發的事件。  事件發生的執行緒取決於事件是否由畫筆、滑鼠或以程式設計方式引發。  如需關於這些事件之執行緒的詳細資訊，請參閱[General Threading Considerations](http://msdn.microsoft.com/zh-tw/cf35724f-5f80-4b3e-992a-a9d5ea99aae9)和[Threads on Which an Event Can Fire](http://msdn.microsoft.com/zh-tw/d1a5ab9b-d474-4ed7-9aa8-b5bdb771934f)。  
  
 在 Windows Presentation Foundation 平台上，<xref:System.Windows.UIElement> 類別具有畫筆輸入的事件。  這代表每個控制項會公開一組完整的手寫筆事件。  手寫筆事件具有通道版本和反昇版本事件配對，而且一定會在應用程式執行緒上進行。  如需詳細資訊，請參閱[路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)。  
  
 下列圖表會顯示引發手寫筆事件之類別的物件模型比較。  Windows Presentation Foundation 物件模型只會顯示反昇事件，而不會顯示通道事件對應項目。  
  
 ![WPF 和 Winforms 中 Stylus 事件的比較圖表](../../../../docs/framework/wpf/advanced/media/ink-stylusevents.png "Ink\_StylusEvents")  
  
## 畫筆資料  
 這三個平台提供攔截和管理來自於 Tablet 畫筆之資料的方法。  在 Windows Forms 和 COM 平台上，可建立 <xref:Microsoft.StylusInput.RealTimeStylus>、將視窗或控制項複製到其中，以及建立實作 <xref:Microsoft.StylusInput.IStylusSyncPlugin> 或 <xref:Microsoft.StylusInput.IStylusAsyncPlugin> 介面的類別來達到這個作業。  然後，則會將自訂外掛程式加入至 <xref:Microsoft.StylusInput.RealTimeStylus> 的外掛程式集合。  如需此物件模型的詳細資訊，請參閱[Architecture of the StylusInput APIs](http://msdn.microsoft.com/zh-tw/88bab0ab-df9f-4813-9a9f-9a137813f0b4)。  
  
 在 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 平台上，<xref:System.Windows.UIElement> 類別會公開外掛程式的集合，此集合的設計與 <xref:Microsoft.StylusInput.RealTimeStylus> 十分類似。  若要攔截畫筆資料，請建立從 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> 繼承的類別，並將物件加入至 <xref:System.Windows.UIElement> 的 <xref:System.Windows.UIElement.StylusPlugIns%2A> 集合。  如需有關這個互動的詳細資訊，請參閱[攔截手寫筆的輸入](../../../../docs/framework/wpf/advanced/intercepting-input-from-the-stylus.md)。  
  
 在所有平台上，執行緒集區會透過手寫筆事件接收筆墨資料，並將之傳送到應用程式執行緒。  如需有關 COM 和 Windows 平台上執行緒的詳細資訊，請參閱[Threading Considerations for the StylusInput APIs](http://msdn.microsoft.com/zh-tw/5d98768a-c60b-4bb0-8640-9bf38254d41f)。  如需有關 Windows Presentation Software 上執行緒的詳細資訊，請參閱[筆墨執行緒模型](../../../../docs/framework/wpf/advanced/the-ink-threading-model.md)。  
  
 下列圖示會比較類別的物件模型，這些類別會接收畫筆執行緒集區的畫筆資料。  
  
 ![WPF 和 Winforms 中 StylusPlugin 模型的比較圖表。](../../../../docs/framework/wpf/advanced/media/ink-stylusplugins.png "Ink\_StylusPlugins")
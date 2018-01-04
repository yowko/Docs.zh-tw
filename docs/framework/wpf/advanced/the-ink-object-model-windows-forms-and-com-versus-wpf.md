---
title: "Ink 物件模型：Windows Form 和 COM 與 WPF 的比較"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-wpf
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- enabling ink [WPF]
- InkCanvas control [WPF]
- ink object model [WPF]
- tablet pen [WPF], events [WPF]
- ink [WPF], enabling
- events [WPF], tablet pen
ms.assetid: 577835be-b145-4226-8570-1d309e9b3901
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 38c7692d433fb91584718984ef2ad81e563517db
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="the-ink-object-model-windows-forms-and-com-versus-wpf"></a>Ink 物件模型：Windows Form 和 COM 與 WPF 的比較

有基本上是三個支援的平台數位筆跡： Tablet PC Windows Form 平台、 Tablet PC COM 平台和[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]平台。  類似的物件模型，但是物件的模型的 Windows Form 和 COM 平台共用[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]平台是本質上不同。  本主題討論在高層次的差異，讓已使用過了一個物件模型的開發人員可更了解其他。  
  
## <a name="enabling-ink-in-an-application"></a>啟用應用程式中的筆墨  
 物件和控制項，讓應用程式接收來自 tablet 畫筆輸入，將傳送所有的三個平台。  Windows Form 和 COM 平台將獍旓[Microsoft.Ink.InkPicture](https://msdn.microsoft.com/library/aa514604.aspx)， [Microsoft.Ink.InkEdit](https://msdn.microsoft.com/library/ms835842.aspx)， [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/ms833057.aspx)和[Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/ms836493.aspx)類別。  [Microsoft.Ink.InkPicture](https://msdn.microsoft.com/library/aa514604.aspx)和[Microsoft.Ink.InkEdit](https://msdn.microsoft.com/library/ms835842.aspx)是控制項，您可以加入至應用程式以收集筆墨。  [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/ms833057.aspx)和[Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/ms836493.aspx)可以附加到現有的視窗功能的筆墨視窗和自訂控制項。  
  
 WPF 平台包括<xref:System.Windows.Controls.InkCanvas>控制項。  您可以加入<xref:System.Windows.Controls.InkCanvas>您的應用程式並開始立即收集筆墨。 與<xref:System.Windows.Controls.InkCanvas>，使用者可以複製、 選取及調整大小的筆墨。  您可以將其他控制項加入<xref:System.Windows.Controls.InkCanvas>，以及使用者可以太手寫透過其他控制項。  您可以建立已啟用筆墨的自訂控制項加入<xref:System.Windows.Controls.InkPresenter>並收集其手寫筆的點。  
  
 下表列出可讓您以深入了解啟用應用程式中的筆墨：  
  
|若要這樣做...|WPF 平台上...|Windows Form/COM 平台上...|  
|-----------------|--------------------------|------------------------------------------|  
|將啟用筆墨的控制項新增至應用程式|請參閱[入門筆墨](../../../../docs/framework/wpf/advanced/getting-started-with-ink.md)。|請參閱[自動宣告形成範例](http://msdn.microsoft.com/bec4333a-62ca-4254-a39b-04bc2c556992)|  
|啟用自訂控制項上的筆墨|請參閱[建立筆跡輸入控制項](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md)。|請參閱[筆墨剪貼簿範例](http://msdn.microsoft.com/a0c42f1c-543d-44f8-83d9-fe810de410ff)。|  
  
## <a name="ink-data"></a>筆墨資料  
 在 Windows Form 和 COM 的平台， [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/ms836493.aspx)， [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/ms833057.aspx)， [Microsoft.Ink.InkEdit](https://msdn.microsoft.com/library/ms835842.aspx)，和[Microsoft.Ink.InkPicture](https://msdn.microsoft.com/library/aa514604.aspx)每個公開[Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx?displayProperty=nameWithType)物件。 [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx)物件包含一或多個資料[Microsoft.Ink.Stroke](https://msdn.microsoft.com/library/ms827842.aspx?displayProperty=nameWithType)物件，並公開 （expose） 通用的方法和屬性來管理和操作筆劃。  [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx)物件管理內含的筆劃的存留期間[Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx)物件會建立和刪除其擁有的筆劃。  每個[Microsoft.Ink.Stroke](https://msdn.microsoft.com/library/ms827842.aspx)具有與其父系中是唯一的識別項[Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx)物件。  
  
 WPF 平台上<xref:System.Windows.Ink.Stroke?displayProperty=nameWithType>類別擁有及管理其本身的存留期。 一組<xref:System.Windows.Ink.Stroke>物件可以一起收集在<xref:System.Windows.Ink.StrokeCollection>，提供一般筆墨的方法的資料管理作業例如點擊測試、 清除、 轉換及序列化筆跡。 A<xref:System.Windows.Ink.Stroke>零、 一或多個可以屬於<xref:System.Windows.Ink.StrokeCollection>物件在任何授與的時間。  而不需[Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx?displayProperty=nameWithType)物件<xref:System.Windows.Controls.InkCanvas>和<xref:System.Windows.Controls.InkPresenter>包含<xref:System.Windows.Ink.StrokeCollection?displayProperty=nameWithType>。  
  
 下列圖例組比較筆墨資料物件模型。  在 Windows Form 和 COM 的平台， [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx?displayProperty=nameWithType)物件限制的存留期[Microsoft.Ink.Stroke](https://msdn.microsoft.com/library/ms827842.aspx?displayProperty=nameWithType)物件，與屬於個別筆劃的手寫筆封包。  兩個或多個筆劃可以參考相同[Microsoft.Ink.DrawingAttributes](https://msdn.microsoft.com/library/ms837931.aspx?displayProperty=nameWithType)物件，在下圖所示。  
  
 ![COM &#47; 之 Ink 物件模型的圖表Winforms。] (../../../../docs/framework/wpf/advanced/media/ink-inkownsstrokes.png "Ink_InkOwnsStrokes")  
  
 在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，每個<xref:System.Windows.Ink.Stroke?displayProperty=nameWithType>已存在，前提是必須的參考 common language runtime 物件。  每個<xref:System.Windows.Ink.Stroke>參考<xref:System.Windows.Input.StylusPointCollection>和<xref:System.Windows.Ink.DrawingAttributes?displayProperty=nameWithType>物件，也是 common language runtime 物件。  
  
 ![Wpf 之 Ink 物件模型的圖表。] (../../../../docs/framework/wpf/advanced/media/ink-wpfinkobjectmodel.png "Ink_WPFInkObjectModel")  
  
 下表比較如何完成一些常見的工作上[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]平台和 Windows Form 和 COM 的平台。  
  
|工作|Windows Presentation Foundation|Windows Form 和 COM|  
|----------|-------------------------------------|---------------------------|  
|儲存筆跡|<xref:System.Windows.Ink.StrokeCollection.Save%2A>|[Microsoft.Ink.Ink.Save](https://technet.microsoft.com/library/security/microsoft.ink.ink.save(v=vs.90))|  
|載入筆墨|建立<xref:System.Windows.Ink.StrokeCollection>與<xref:System.Windows.Ink.StrokeCollection.%23ctor%2A>建構函式。|[Microsoft.Ink.Ink.Load](https://msdn.microsoft.com/library/microsoft.ink.ink.load(v=vs.90).aspx)|  
|點擊的測試|<xref:System.Windows.Ink.StrokeCollection.HitTest%2A>|[Microsoft.Ink.Ink.HitTest](https://msdn.microsoft.com/library/aa515934.aspx)|  
|複製筆墨|<xref:System.Windows.Controls.InkCanvas.CopySelection%2A>|[Microsoft.Ink.Ink.ClipboardCopy](https://msdn.microsoft.com/library/microsoft.ink.ink.clipboardcopy(v=vs.100).aspx)|  
|貼上筆墨|<xref:System.Windows.Controls.InkCanvas.Paste%2A>|[Microsoft.Ink.Ink.ClipboardPaste](https://msdn.microsoft.com/library/microsoft.ink.ink.clipboardpaste(v=vs.100).aspx)|  
|存取自訂屬性集合的筆劃|<xref:System.Windows.Ink.StrokeCollection.AddPropertyData%2A>(在內部儲存及存取透過屬性<xref:System.Windows.Ink.StrokeCollection.AddPropertyData%2A>， <xref:System.Windows.Ink.StrokeCollection.RemovePropertyData%2A>，和<xref:System.Windows.Ink.StrokeCollection.ContainsPropertyData%2A>)|使用[Microsoft.Ink.Ink.ExtendedProperties](https://msdn.microsoft.com/library/microsoft.ink.ink.extendedproperties(v=vs.100).aspx)|  
  
### <a name="sharing-ink-between-platforms"></a>共用平台之間的筆墨  
 雖然平台的筆墨資料不同的物件模型，但共用平台之間的資料是很容易。 下列範例會從 Windows Forms 應用程式中儲存筆墨，並載入 Windows Presentation Foundation 應用程式中的筆跡。  
  
 [!code-csharp[WinFormWPFInk#UsingWinforms](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwinforms)]
 [!code-vb[WinFormWPFInk#UsingWinforms](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwinforms)]  
[!code-csharp[WinFormWPFInk#SaveWinforms](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#savewinforms)]
[!code-vb[WinFormWPFInk#SaveWinforms](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#savewinforms)]  
  
 [!code-csharp[WinFormWPFInk#UsingWPF](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwpf)]
 [!code-vb[WinFormWPFInk#UsingWPF](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwpf)]  
[!code-csharp[WinFormWPFInk#LoadWPF](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#loadwpf)]
[!code-vb[WinFormWPFInk#LoadWPF](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#loadwpf)]  
  
 下列範例會從 Windows Presentation Foundation 應用程式中儲存筆墨，並載入 Windows Form 應用程式中的筆跡。  
  
 [!code-csharp[WinFormWPFInk#UsingWPF](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwpf)]
 [!code-vb[WinFormWPFInk#UsingWPF](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwpf)]  
[!code-csharp[WinFormWPFInk#SaveWPF](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#savewpf)]
[!code-vb[WinFormWPFInk#SaveWPF](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#savewpf)]  
  
 [!code-csharp[WinFormWPFInk#UsingWinforms](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwinforms)]
 [!code-vb[WinFormWPFInk#UsingWinforms](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwinforms)]  
[!code-csharp[WinFormWPFInk#LoadWinforms](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#loadwinforms)]
[!code-vb[WinFormWPFInk#LoadWinforms](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#loadwinforms)]
## <a name="events-from-the-tablet-pen"></a>從 Tablet 畫筆事件  
 [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/ms833057.aspx)， [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/ms836493.aspx)，和[Microsoft.Ink.InkPicture](https://msdn.microsoft.com/library/aa514604.aspx)在 Windows Form 和 COM 平台會收到事件時的使用者輸入畫筆資料。  [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/ms833057.aspx)或[Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/ms836493.aspx)會附加到視窗或控制項，而且可以訂閱 tablet 輸入資料所引發的事件。  這些事件發生所在的執行緒，取決於是否會引發事件的畫筆、 滑鼠，或以程式設計的方式。  如需執行緒相對於這些事件的詳細資訊，請參閱[一般執行緒考量](http://msdn.microsoft.com/cf35724f-5f80-4b3e-992a-a9d5ea99aae9)和[執行緒上引發的事件可以](http://msdn.microsoft.com/d1a5ab9b-d474-4ed7-9aa8-b5bdb771934f)。  
  
 Windows Presentation Foundation 平台上<xref:System.Windows.UIElement>類別具有畫筆輸入的事件。 這表示每個控制項會公開一組完整的手寫筆事件。  手寫筆事件的通道/反昇事件組，而且一定會在應用程式的執行緒上。  如需詳細資訊，請參閱[路由傳送事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)。  
  
 下圖顯示比較的物件模型引發手寫筆事件的類別。 Windows Presentation Foundation 物件模型會顯示只反昇事件，不對應通道的事件。  
  
 ![WPF 和 Winforms 中 Stylus 事件的圖表。] (../../../../docs/framework/wpf/advanced/media/ink-stylusevents.png "Ink_StylusEvents")  
  
## <a name="pen-data"></a>畫筆資料  
 所有的三個平台為您提供方式以攔截並處理來自 tablet 畫筆的資料。  在 Windows Form 及 COM 的平台，這藉由建立[Microsoft.StylusInput.RealTimeStylus](https://msdn.microsoft.com/library/microsoft.stylusinput.realtimestylus(v=vs.100).aspx)、 附加視窗或控制項，並建立的類別，實作[Microsoft.StylusInput.IStylusSyncPlugin](https://msdn.microsoft.com/library/microsoft.stylusinput.istylussyncplugin(v=vs.100).aspx)或[Microsoft.StylusInput.IStylusAsyncPlugin](https://msdn.microsoft.com/library/microsoft.stylusinput.istylusasyncplugin(v=vs.100).aspx)介面。 然後加入自訂外掛程式的外掛程式集合[Microsoft.StylusInput.RealTimeStylus](https://msdn.microsoft.com/library/microsoft.stylusinput.realtimestylus(v=vs.100).aspx)。 如需此物件模型的詳細資訊，請參閱[StylusInput Api 架構](http://msdn.microsoft.com/88bab0ab-df9f-4813-9a9f-9a137813f0b4)。  
  
 在[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]平台，<xref:System.Windows.UIElement>類別公開的外掛程式，在要設計類似集合[Microsoft.StylusInput.RealTimeStylus](https://msdn.microsoft.com/library/microsoft.stylusinput.realtimestylus(v=vs.100).aspx)。  若要攔截畫筆資料，建立繼承自類別<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>並將物件加入至<xref:System.Windows.UIElement.StylusPlugIns%2A>集合<xref:System.Windows.UIElement>。 如需這個互動的詳細資訊，請參閱[攔截手寫筆輸入](../../../../docs/framework/wpf/advanced/intercepting-input-from-the-stylus.md)。  
  
 所有平台上，執行緒集區會接收到的筆墨資料透過手寫筆事件，並將它傳送至應用程式執行緒。  如需執行緒的 COM 和 Windows 平台上的詳細資訊，請參閱[StylusInput 應用程式開發介面的執行緒考量](http://msdn.microsoft.com/5d98768a-c60b-4bb0-8640-9bf38254d41f)。  如需執行緒的 Windows Presentation 軟體的詳細資訊，請參閱[筆跡執行緒模型](../../../../docs/framework/wpf/advanced/the-ink-threading-model.md)。  
  
 下圖比較的物件模型，接收畫筆的畫筆執行緒集區資料的類別。  
  
 ![StylusPlugin 模型 WPF 和 Winforms 的圖表。] (../../../../docs/framework/wpf/advanced/media/ink-stylusplugins.png "Ink_StylusPlugins")

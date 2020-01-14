---
title: Ink 物件模型：Windows Forms 和 COM 與 WPF 的比較
ms.date: 03/30/2017
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
ms.openlocfilehash: 2c0d155d320bab2f0114280e962c8f2f0b559681
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636415"
---
# <a name="the-ink-object-model-windows-forms-and-com-versus-wpf"></a>Ink 物件模型：Windows Forms 和 COM 與 WPF 的比較

基本上有三種平臺支援數位筆跡： Tablet PC Windows Forms 平臺、Tablet PC COM 平臺，以及 Windows Presentation Foundation （WPF）平臺。  Windows Forms 和 COM 平臺共用類似的物件模型，但 WPF 平臺的物件模型卻截然不同。  本主題將討論高階的差異，讓已處理一個物件模型的開發人員可以更瞭解另一個物件模型。  
  
## <a name="enabling-ink-in-an-application"></a>在應用程式中啟用筆墨  
 這三個平臺都出貨物件和控制項，讓應用程式能夠接收來自 tablet 畫筆的輸入。  Windows Forms 和 COM 平臺都隨附于 [Microsoft.Ink.InkPicture](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583740(v=vs.90))、[Microsoft.Ink.InkEdit](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552265(v=vs.90))、[Microsoft.Ink.InkOverlay](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552322(v=vs.90))類別，以及 [Microsoft.Ink.InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90))類別中的一種。  [InkPicture](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583740(v=vs.90))和[InkEdit](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552265(v=vs.90))是您可以加入至應用程式以收集筆跡的控制項。  [InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90))可以附加至現有的[視窗，以](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552322(v=vs.90))啟用筆墨的 windows 和自訂控制項。  
  
 WPF 平臺包含 <xref:System.Windows.Controls.InkCanvas> 控制項。  您可以將 <xref:System.Windows.Controls.InkCanvas> 新增至應用程式，並立即開始收集筆跡。 有了 <xref:System.Windows.Controls.InkCanvas>，使用者就可以複製、選取和調整筆跡大小。  您可以將其他控制項新增至 <xref:System.Windows.Controls.InkCanvas>，而使用者也可以手寫這些控制項。  您可以藉由在其中加入 <xref:System.Windows.Controls.InkPresenter> 並收集手寫筆點，建立已啟用筆墨的自訂控制項。  
  
 下表列出可在何處深入瞭解如何在應用程式中啟用筆墨：  
  
|若要執行此動作 。|在 WPF 平臺上 。|在 Windows Forms/COM 平臺上 。|  
|-----------------|--------------------------|------------------------------------------|  
|將啟用筆墨的控制項新增至應用程式|請參閱[使用筆墨消費者入門](getting-started-with-ink.md)。|請參閱[自動宣告表單範例](/windows/desktop/tablet/auto-claims-form-sample)|  
|在自訂控制項上啟用筆墨|請參閱[建立筆墨輸入控制項](creating-an-ink-input-control.md)。|請參閱[筆墨剪貼簿範例](/windows/desktop/tablet/ink-clipboard-sample)。|  
  
## <a name="ink-data"></a>筆墨資料  
 在 Windows Forms 和 COM 平臺上， [InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90))、 [InkEdit](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552265(v=vs.90))和[InkPicture](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583740(v=vs.90))都是公開一個[Microsoft ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90))物件的一[種，分別](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552322(v=vs.90))會顯示在其中。 [Microsoft ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90))物件包含一個或多個[microsoft ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552692(v=vs.90))物件的資料，並且會公開常用的方法和屬性來管理和操作這些筆劃。  [Microsoft ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90))物件會管理其所包含之筆劃的存留期;[Microsoft ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90))物件會建立並刪除它所擁有的筆劃。  每個[Microsoft ink. 筆觸](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552692(v=vs.90))的識別碼在其父系的[microsoft ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90))物件中是唯一的。  
  
 在 WPF 平臺上，<xref:System.Windows.Ink.Stroke?displayProperty=nameWithType> 類別擁有並管理它自己的存留期。 一組 <xref:System.Windows.Ink.Stroke> 物件可以一起收集在 <xref:System.Windows.Ink.StrokeCollection>中，以提供常用筆墨資料管理作業的方法，例如點擊測試、清除、轉換和序列化筆跡。 <xref:System.Windows.Ink.Stroke> 在任何給定時間都可以屬於零個、一個或多個 <xref:System.Windows.Ink.StrokeCollection> 物件。  <xref:System.Windows.Controls.InkCanvas> 和 <xref:System.Windows.Controls.InkPresenter> 包含 <xref:System.Windows.Ink.StrokeCollection?displayProperty=nameWithType>，而不是擁有[Microsoft ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90))物件。  
  
 下列圖例配對會比較筆墨資料物件模型。  在 Windows Forms 和 COM 平臺上， [Microsoft ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90))物件會限制[microsoft 筆墨](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552692(v=vs.90))物件的存留期，而手寫筆封包則屬於個別的筆劃。  兩個或多個筆劃可以參考相同的[DrawingAttributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583636(v=vs.90))物件，如下圖所示。  
  
 ![COM&#47;Winforms 的筆墨物件模型圖表。](./media/ink-inkownsstrokes.png "Ink_InkOwnsStrokes")  
  
 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]上，每個 <xref:System.Windows.Ink.Stroke?displayProperty=nameWithType> 都是通用語言執行時間物件，只要有內容的參考，就會存在。  每個 <xref:System.Windows.Ink.Stroke> 都會參考一個 <xref:System.Windows.Input.StylusPointCollection> 和 <xref:System.Windows.Ink.DrawingAttributes?displayProperty=nameWithType> 物件，也就是通用語言執行時間物件。  
  
 ![WPF 的筆墨物件模型圖表。](./media/ink-wpfinkobjectmodel.png "Ink_WPFInkObjectModel")  
  
 下表比較如何完成 WPF 平臺和 Windows Forms 和 COM 平臺上的一些一般工作。  
  
|工作|Windows Presentation Foundation|Windows Forms 和 COM|  
|----------|-------------------------------------|---------------------------|  
|儲存筆墨|<xref:System.Windows.Ink.StrokeCollection.Save%2A>|[Microsoft Ink。儲存](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms571335(v=vs.90))|  
|載入筆跡|使用 <xref:System.Windows.Ink.StrokeCollection.%23ctor%2A> 的「函式」來建立 <xref:System.Windows.Ink.StrokeCollection>。|[Microsoft Ink。載入](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms569609(v=vs.90))|  
|點擊測試|<xref:System.Windows.Ink.StrokeCollection.HitTest%2A>|[Microsoft.Ink.Ink.HitTest](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms571330(v=vs.90))|  
|複製筆墨|<xref:System.Windows.Controls.InkCanvas.CopySelection%2A>|[ClipboardCopy。](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms571316(v=vs.90))|  
|貼上筆墨|<xref:System.Windows.Controls.InkCanvas.Paste%2A>|[ClipboardPaste。](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms571318(v=vs.90))|  
|存取筆劃集合上的自訂屬性|<xref:System.Windows.Ink.StrokeCollection.AddPropertyData%2A> （屬性會儲存在內部並透過 <xref:System.Windows.Ink.StrokeCollection.AddPropertyData%2A>、<xref:System.Windows.Ink.StrokeCollection.RemovePropertyData%2A>和 <xref:System.Windows.Ink.StrokeCollection.ContainsPropertyData%2A>存取）|使用[ExtendedProperties。](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms582214(v=vs.90))|  
  
### <a name="sharing-ink-between-platforms"></a>在平臺之間共用筆跡  
 雖然這些平臺的筆跡資料有不同的物件模型，但是在平臺之間共用資料非常簡單。 下列範例會從 Windows Forms 應用程式儲存筆墨，並將筆墨載入 Windows Presentation Foundation 應用程式中。  
  
 [!code-csharp[WinFormWPFInk#UsingWinforms](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwinforms)]
 [!code-vb[WinFormWPFInk#UsingWinforms](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwinforms)]  
[!code-csharp[WinFormWPFInk#SaveWinforms](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#savewinforms)]
[!code-vb[WinFormWPFInk#SaveWinforms](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#savewinforms)]  
  
 [!code-csharp[WinFormWPFInk#UsingWPF](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwpf)]
 [!code-vb[WinFormWPFInk#UsingWPF](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwpf)]  
[!code-csharp[WinFormWPFInk#LoadWPF](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#loadwpf)]
[!code-vb[WinFormWPFInk#LoadWPF](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#loadwpf)]  
  
 下列範例會從 Windows Presentation Foundation 應用程式儲存筆墨，並將筆墨載入 Windows Forms 應用程式中。  
  
 [!code-csharp[WinFormWPFInk#UsingWPF](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwpf)]
 [!code-vb[WinFormWPFInk#UsingWPF](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwpf)]  
[!code-csharp[WinFormWPFInk#SaveWPF](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#savewpf)]
[!code-vb[WinFormWPFInk#SaveWPF](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#savewpf)]  
  
 [!code-csharp[WinFormWPFInk#UsingWinforms](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwinforms)]
 [!code-vb[WinFormWPFInk#UsingWinforms](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwinforms)]  
[!code-csharp[WinFormWPFInk#LoadWinforms](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#loadwinforms)]
[!code-vb[WinFormWPFInk#LoadWinforms](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#loadwinforms)]
## <a name="events-from-the-tablet-pen"></a>來自 Tablet 畫筆的事件  

 當使用者輸入手寫筆資料時，Windows Forms 和 COM 平臺上的[InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90))和[InkPicture](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583740(v=vs.90))會[接收到的](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552322(v=vs.90))事件。 [InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90))會附加至視窗或控制項，並可訂閱平板電腦輸入資料所引發的事件（可能為[）。](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552322(v=vs.90)) 發生這些事件的執行緒取決於事件是以畫筆、滑鼠還是以程式設計方式引發。 如需有關執行緒與這些事件相關的詳細資訊，請參閱[一般執行緒考慮](/windows/desktop/tablet/general-threading-considerations)和[可引發事件的執行緒](/windows/desktop/tablet/threads-on-which-an-event-can-fire)。  
  
 在 Windows Presentation Foundation 平臺上，<xref:System.Windows.UIElement> 類別具有手寫筆輸入的事件。 這表示每個控制項都會公開一組完整的手寫筆事件。  手寫筆事件具有通道/反升事件配對，而且一律會在應用程式執行緒上發生。  如需詳細資訊，請參閱[路由事件總覽](routed-events-overview.md)。  
  
 下圖顯示會比較引發手寫筆事件之類別的物件模型。 Windows Presentation Foundation 物件模型只會顯示反升事件，而不是通道事件對應項。  
  
 ![WPF 中手寫筆事件的圖表與 Winforms。](./media/ink-stylusevents.png "Ink_StylusEvents")  
  
## <a name="pen-data"></a>畫筆資料  
 這三個平臺都提供您攔截和操作來自 tablet 畫筆之資料的方式。  在 Windows Forms 和 COM 平臺上，這是藉由建立[StylusInput](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms585724(v=vs.90))、將視窗或控制項附加至該檔案，以及建立可執行[IStylusSyncPlugin](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms575201(v=vs.90))或[StylusInput IStylusAsyncPlugin](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms575194(v=vs.90))介面的類別來達成。 然後，自訂外掛程式會新增至[StylusInput](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms585724(v=vs.90))的外掛程式集合。 如需此物件模型的詳細資訊，請參閱[StylusInput api 的架構](/windows/desktop/tablet/architecture-of-the-stylusinput-apis)。  
  
 在 WPF 平臺上，<xref:System.Windows.UIElement> 類別會公開外掛程式的集合，與[StylusInput](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms585724(v=vs.90))的設計類似。  若要攔截畫筆資料，請建立繼承自 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> 的類別，並將物件加入至 <xref:System.Windows.UIElement>的 <xref:System.Windows.UIElement.StylusPlugIns%2A> 集合。 如需此互動的詳細資訊，請參閱[從手寫筆攔截輸入](intercepting-input-from-the-stylus.md)。  
  
 在所有平臺上，執行緒集區會透過手寫筆事件接收筆墨資料，並將其傳送至應用程式執行緒。  如需有關 COM 和 Windows 平臺上執行緒的詳細資訊，請參閱[StylusInput api 的執行緒考慮](/windows/desktop/tablet/threading-considerations-for-the-stylusinput-apis)。  如需有關 Windows 簡報軟體上執行緒的詳細資訊，請參閱[筆跡執行緒模型](the-ink-threading-model.md)。  
  
 下圖會比較在畫筆執行緒集區上接收畫筆資料之類別的物件模型。  
  
 ![StylusPlugin 模型 WPF 與 Winforms 的圖表。](./media/ink-stylusplugins.png "Ink_StylusPlugins")

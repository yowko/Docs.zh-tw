---
title: WPF 圖形轉譯概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rendering
- rendering graphics [WPF]
ms.assetid: 6dec9657-4d8c-4e46-8c54-40fb80008265
ms.openlocfilehash: 09f5f026ed320aaa253d8cdf6e0b271235aff604
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004176"
---
# <a name="wpf-graphics-rendering-overview"></a>WPF 圖形轉譯概觀
本主題提供 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 視覺圖層的概觀。 它著重于 @no__t 1 模型中轉譯支援的 @no__t 0 類別的角色。  

<a name="role_of_visual_object"></a>   
## <a name="role-of-the-visual-object"></a>視覺物件的角色  
 @No__t 0 類別是衍生每個 <xref:System.Windows.FrameworkElement> 物件的基本抽象概念。 它也作為在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中撰寫新控制項的進入點，且在許多方面，可以視為 Win32 應用程式模型中的視窗控制代碼 (HWND)。  
  
 @No__t 0 物件是核心的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 物件，其主要角色是提供轉譯支援。 使用者介面控制項（例如 <xref:System.Windows.Controls.Button> 和 <xref:System.Windows.Controls.TextBox>）衍生自 @no__t 2 類別，並使用它來保存其轉譯資料。 @No__t 0 物件提供下列支援：  
  
- 輸出顯示：呈現視覺效果的保存、序列化繪製內容。  
  
- 轉變在視覺效果上執行轉換。  
  
- 裁剪提供視覺效果的裁剪區域支援。  
  
- 點擊測試：判斷座標或幾何是否包含在視覺效果的範圍內。  
  
- 周框方塊計算：判斷視覺效果的周框。  
  
 不過，<xref:System.Windows.Media.Visual> 物件不包括對非轉譯功能的支援，例如：  
  
- 事件處理  
  
- 配置  
  
- 樣式  
  
- 資料繫結  
  
- 全球化  
  
 <xref:System.Windows.Media.Visual> 會公開為必須從中衍生子類別的公用抽象類別。 下圖顯示 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中公開之視覺物件的階層。  
  
 ![衍生自 Visual 物件之類別的圖表](./media/wpf-graphics-rendering-overview/classes-derived-visual-object.png)    
  
### <a name="drawingvisual-class"></a>DrawingVisual 類別  
 @No__t-0 是輕量繪圖類別，可用來呈現圖形、影像或文字。 此類別之所以被視為輕量型，是因為它不提供版面配置或事件處理，而這會改善其執行階段效能。 基於此原因，繪圖適合背景或美工圖案。 @No__t-0 可以用來建立自訂視覺物件。 如需詳細資訊，請參閱[使用 DrawingVisual 物件](using-drawingvisual-objects.md)。  
  
### <a name="viewport3dvisual-class"></a>Viewport3DVisual 類別  
 @No__t-0 提供 2D <xref:System.Windows.Media.Visual> 與 @no__t 2 物件之間的橋樑。 @No__t-0 類別是所有3D 視覺元素的基類。 @No__t-0 會要求您定義 <xref:System.Windows.Media.Media3D.Viewport3DVisual.Camera%2A> 值和 @no__t 2 值。 相機可讓您檢視場景。 檢視區會建立投影到 2D 平面上的對應位置。 如需 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中 3D 的詳細資訊，請參閱 [3D 圖形概觀](3-d-graphics-overview.md)。  
  
### <a name="containervisual-class"></a>ContainerVisual 類別  
 @No__t-0 類別是用來做為 @no__t 1 物件集合的容器。 @No__t 0 類別衍生自 <xref:System.Windows.Media.ContainerVisual> 類別，讓它包含視覺物件的集合。  
  
### <a name="drawing-content-in-visual-objects"></a>視覺物件中的繪圖內容  
 @No__t 0 物件會將其轉譯資料儲存為**向量圖形指示清單**。 指示清單中的每個項目代表一組低階圖形資料和相關聯的序列化格式的資源。 可包含繪圖內容的轉譯資料有四種不同的類型。  
  
|繪圖內容類型|描述|  
|--------------------------|-----------------|  
|向量圖形|表示向量圖形資料，以及任何相關聯的 <xref:System.Windows.Media.Brush> 和 @no__t 1 資訊。|  
|Image|代表區域內的影像，由 <xref:System.Windows.Rect> 所定義。|  
|圖像|表示呈現 <xref:System.Windows.Media.GlyphRun> 的繪圖，這是來自指定字型資源的一系列字元。 這是文字的表現方式。|  
|視訊|代表轉譯視訊的繪圖。|  
  
 @No__t-0 可讓您以視覺內容填入 <xref:System.Windows.Media.Visual>。 當您使用 @no__t 0 物件的繪製命令時，您實際上是儲存一組轉譯資料，稍後會供圖形系統使用;您不會即時繪製到螢幕上。  
  
 當您建立 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項（例如 <xref:System.Windows.Controls.Button>）時，控制項會隱含地產生繪製本身的轉譯資料。 例如，設定 <xref:System.Windows.Controls.Button> 的 <xref:System.Windows.Controls.ContentControl.Content%2A> 屬性會導致控制項儲存圖像的呈現表示。  
  
 @No__t-0 會將其內容描述為包含在 <xref:System.Windows.Media.DrawingGroup> 中的一或多個 @no__t 1 物件。 @No__t-0 也會描述不透明度遮罩、轉換、點陣圖效果，以及套用至其內容的其他作業。 轉譯內容時，會以下列順序套用 <xref:System.Windows.Media.DrawingGroup> 作業： <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>、<xref:System.Windows.Media.DrawingGroup.Opacity%2A>、<xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>、<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>、<xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>，然後 <xref:System.Windows.Media.DrawingGroup.Transform%2A>。  
  
 下圖顯示在轉譯順序期間套用 @no__t 0 作業的順序。  
  
 ![作業 graphcismm_drawinggroup_order 的 DrawingGroup 順序](./media/graphcismm-drawinggroup-order.png " ")  
DrawingGroup 作業的順序  
  
 如需詳細資訊，請參閱[繪製物件概觀](drawing-objects-overview.md)。  
  
#### <a name="drawing-content-at-the-visual-layer"></a>視覺圖層的繪圖內容  
 您永遠不會直接具現化 <xref:System.Windows.Media.DrawingContext>;不過，您可以從特定方法（例如 <xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType> 和 <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType>）取得繪圖內容。 下列範例會從 <xref:System.Windows.Media.DrawingVisual> 抓取 <xref:System.Windows.Media.DrawingContext>，並使用它來繪製矩形。  
  
 [!code-csharp[drawingvisualsample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[drawingvisualsample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
#### <a name="enumerating-drawing-content-at-the-visual-layer"></a>列舉視覺圖層的繪圖內容  
 除了其他用途之外，@no__t 0 物件也會提供物件模型來列舉 <xref:System.Windows.Media.Visual> 的內容。  
  
> [!NOTE]
> 當您列舉視覺效果的內容時，您會抓取 <xref:System.Windows.Media.Drawing> 物件，而不是以向量圖形指示清單形式呈現資料的基礎標記法。  
  
 下列範例會使用 <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> 方法來取出 <xref:System.Windows.Media.Visual> 的 <xref:System.Windows.Media.DrawingGroup> 值並加以列舉。  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
<a name="how_visual_objects_are_used_to_build_controls"></a>   
## <a name="how-visual-objects-are-used-to-build-controls"></a>視覺物件如何用來建置控制項  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的許多物件是由其他視覺物件所組成，這表示它們可以包含不同的子系物件階層。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的許多使用者介面元素 (例如控制項) 是由多個視覺物件所組成，代表不同類型的轉譯元素。 例如，@no__t 0 控制項可以包含一些其他物件，包括 <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>、<xref:System.Windows.Controls.ContentPresenter> 和 <xref:System.Windows.Controls.TextBlock>。  
  
 下列程式碼顯示在標記中定義的 @no__t 0 控制項。  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet1)]  
  
 如果您要列舉組成預設 <xref:System.Windows.Controls.Button> 控制項的視覺物件，您會發現視覺物件的階層，如下所示：  
  
 ![視覺化樹狀階層架構的圖表](./media/wpf-graphics-rendering-overview/visual-object-diagram.gif) 
  
 @No__t-0 控制項包含 @no__t 1 專案，而後者又包含 <xref:System.Windows.Controls.ContentPresenter> 元素。 @No__t-0 元素負責繪製 <xref:System.Windows.Controls.Button> 的框線和背景。 @No__t-0 元素負責顯示 <xref:System.Windows.Controls.Button> 的內容。 在此情況下，因為您要顯示文字，所以 <xref:System.Windows.Controls.ContentPresenter> 元素包含 @no__t 1 元素。 @No__t 0 控制項使用 <xref:System.Windows.Controls.ContentPresenter> 表示內容可能會由其他專案表示，例如 <xref:System.Windows.Controls.Image> 或幾何，例如 <xref:System.Windows.Media.EllipseGeometry> 的專案。  
  
### <a name="control-templates"></a>控制項範本  
 將控制項展開為控制項階層的關鍵在於 <xref:System.Windows.Controls.ControlTemplate>。 控制項範本會指定控制項的預設視覺階層。 當您明確地參考控制項時，您會以隱含方式參考其視覺階層。 您可以覆寫控制項範本的預設值，以針對控制項建立自訂視覺外觀。 例如，您可以修改 <xref:System.Windows.Controls.Button> 控制項的背景色彩值，使其使用線性漸層色彩值，而不是純色值。 如需詳細資訊，請參閱[按鈕樣式和範本](../controls/button-styles-and-templates.md)。  
  
 使用者介面專案（例如 @no__t 0 控制項）包含數個向量圖形指示清單，描述控制項的整個呈現定義。 下列程式碼顯示在標記中定義的 @no__t 0 控制項。  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet2)]  
  
 如果您要列舉組成 <xref:System.Windows.Controls.Button> 控制項的視覺物件和向量圖形指示清單，您會找到如下所示的物件階層：  
  
 ![視覺化樹狀結構和轉譯資料的圖表](./media/wpf-graphics-rendering-overview/visual-tree-rendering-data.png)  
  
 @No__t-0 控制項包含 @no__t 1 專案，而後者又包含 <xref:System.Windows.Controls.ContentPresenter> 元素。 @No__t-0 元素負責繪製組成按鈕框線和背景的所有離散圖形元素。 @No__t-0 元素負責顯示 <xref:System.Windows.Controls.Button> 的內容。 在此情況下，由於您要顯示影像，@no__t 0 元素包含 @no__t 1 元素。  
  
 關於視覺物件的階層和向量圖形指示清單，有幾點需要注意：  
  
- 階層中的順序代表繪製資訊的轉譯順序。 子元素會由左至右、由上而下從根視覺元素周遊。 如果某元素具有視覺化子元素，則會在元素的同層級元素之前周遊這些子元素。  
  
- 階層中的非分葉節點元素（例如 <xref:System.Windows.Controls.ContentPresenter>）是用來包含子專案，而不包含指令清單。  
  
- 如果視覺元素同時包含向量圖形指示清單與視覺子元素，父系視覺元素中的指示清單就會在任何視覺子元素物件中的繪圖之前轉譯。  
  
- 向量圖形指示清單中的項目會由左至右轉譯。  
  
<a name="visual_tree"></a>   
## <a name="visual-tree"></a>視覺化樹狀結構  
 視覺化樹狀結構包含應用程式使用者介面中所使用的所有視覺元素。 由於視覺元素包含持續性繪圖資訊，您可以將視覺化樹狀結構想像為場景圖形，其中包含將輸出撰寫至顯示裝置所需的所有轉譯資訊。 此樹狀結構是直接由應用程式所建立 (不論是以程式碼或標記) 的所有視覺元素累積而成。 視覺化樹狀結構也包含由元素 (例如控制項和資料物件) 的範本展開所建立的所有視覺元素。  
  
 下列程式碼顯示在標記中定義的 @no__t 0 元素。  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet3)]  
  
 如果您要列舉標記範例中組成 <xref:System.Windows.Controls.StackPanel> 元素的視覺物件，您會找到視覺物件的階層架構，如下所示：  
  
 ![視覺化樹狀階層架構的圖表](./media/wpf-graphics-rendering-overview/visual-tree-hierarchy.gif)  
  
### <a name="rendering-order"></a>轉譯順序  
 視覺化樹狀結構會決定 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 視覺物件和繪圖物件的轉譯順序。 周遊順序會從根視覺物件開始，這是視覺化樹狀結構的最上層節點。 然後，會由左至右周遊根視覺物件的子系。 如果視覺物件具有子系，則會在該視覺物件的同層級項目之前周遊其子系。 這表示子視覺物件的內容會在視覺物件本身的內容前面轉譯。  
  
 ![視覺化樹狀結構轉譯順序的圖表](./media/wpf-graphics-rendering-overview/visual-tree-rendering-order.gif) 
  
### <a name="root-visual"></a>根視覺物件  
 「根視覺物件」是視覺化樹狀結構階層中最上層的元素。 在大部分的應用程式中，根視覺效果的基類都是 <xref:System.Windows.Window> 或 <xref:System.Windows.Navigation.NavigationWindow>。 不過，如果您已在 Win32 應用程式中裝載視覺物件，根視覺物件是您在 Win32 視窗中裝載的最上層視覺物件。 如需詳細資訊，請參閱[教學課程：在 Win32 應用程式中裝載視覺物件 @ no__t-0。  
  
### <a name="relationship-to-the-logical-tree"></a>邏輯樹狀結構的關聯性  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的邏輯樹狀結構代表執行階段應用程式的元素。 雖然您不會直接操作此樹狀結構，但應用程式的這個檢視適合用來了解屬性繼承和事件路由。 與視覺化樹狀結構不同的是，邏輯樹狀結構可以代表非視覺化的資料物件，例如 <xref:System.Windows.Documents.ListItem>。 在許多案例中，邏輯樹狀結構會非常密切地對應至應用程式的標記定義。 下列程式碼顯示在標記中定義的 @no__t 0 元素。  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet5)]  
  
 如果您要列舉標記範例中組成 <xref:System.Windows.Controls.DockPanel> 元素的邏輯物件，您會找到邏輯物件的階層，如下所示：  
  
 ![樹狀圖表](./media/tree1-wcp.gif "Tree1_wcp")  
邏輯樹狀結構的圖表  
  
 視覺化樹狀結構和邏輯樹狀結構會與目前的應用程式元素集合同步處理，以反映元素的任何新增、刪除或修改。 不過，樹狀結構會呈現不同的應用程式檢視。 與視覺化樹狀結構不同的是，邏輯樹狀結構並不會展開控制項的 <xref:System.Windows.Controls.ContentPresenter> 元素。 這表示針對相同的物件集合，邏輯樹狀結構和視覺化樹狀結構之間沒有直接的一對一對應。 事實上，使用與參數相同的專案叫用**system.windows.logicaltreehelper>** 物件的 <xref:System.Windows.LogicalTreeHelper.GetChildren%2A> 方法和**VisualTreeHelper**物件的 <xref:System.Windows.Media.VisualTreeHelper.GetChild%2A> 方法，會產生不同的結果。  
  
 如需有關邏輯樹狀結構的詳細資訊，請參閱 [WPF 中的樹狀結構](../advanced/trees-in-wpf.md)。  
  
### <a name="viewing-the-visual-tree-with-xamlpad"></a>使用 XamlPad 檢視視覺化樹狀結構  
 @No__t 0 工具 XamlPad 提供了一個選項，可讓您查看和流覽對應至目前定義之 XAML 內容的視覺化樹狀結構。 按一下功能表列上的 [顯示視覺化樹狀結構] 按鈕以顯示視覺化樹狀結構。 下圖說明在 XamlPad 的 [**視覺化樹狀 Explorer** ] 面板中，將 XAML 內容擴充至視覺化樹狀節點：  
  
 ![XamlPad 中的視覺化樹狀結構總管面板](./media/wpf-graphics-rendering-overview/visual-tree-explorer.png)  

 請注意，<xref:System.Windows.Controls.Label>、<xref:System.Windows.Controls.TextBox> 和 @no__t 2 控制項各自在 XamlPad 的 [**視覺化樹狀檢視器**] 面板中顯示個別的視覺物件階層。 這是因為 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項具有 <xref:System.Windows.Controls.ControlTemplate>，其中包含該控制項的視覺化樹狀結構。 當您明確地參考控制項時，您會以隱含方式參考其視覺階層。  
  
### <a name="profiling-visual-performance"></a>分析視覺效能  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供一套效能分析工具，可讓您分析應用程式的執行階段行為，並判斷您可以套用的效能最佳化類型。 Visual Profiler 工具透過直接對應至應用程式的視覺化樹狀結構，提供豐富的效能資料的圖形化檢視。 在這個螢幕擷取畫面中，Visual Profiler 的 [CPU 使用量] 區段可提供您物件使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 服務的精確分析，例如轉譯和版面配置。  
  
 ![Visual Profiler 顯示輸出](./media/wpfperf-visualprofiler-04.png "WPFPerf_VisualProfiler_04")  
Visual Profiler 顯示輸出  
  
<a name="visual_rendering_behavior"></a>   
## <a name="visual-rendering-behavior"></a>Visual 轉譯行為  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 導入幾個會影響視覺物件轉譯行為的功能：保留模式圖形、向量圖形和裝置獨立圖形。  
  
### <a name="retained-mode-graphics"></a>保留模式圖形  
 了解視覺物件角色的其中一個關鍵就是要了解「直接模式」和「保留模式」圖形系統之間的差異。 以 GDI 或 GDI+ 為基礎的標準 Win32 應用程式使用直接模式圖形系統。 這表示應用程式負責重新繪製因為像是重新調整視窗大小或者物件正在變更其視覺外觀等動作而無效的用戶端區域部分。  
  
 ![Win32 轉譯序列的圖表](./media/wpf-graphics-rendering-overview/win32-rendering-squence.png)  
  
 相反地，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 使用保留模式系統。 這表示具有視覺外觀的應用程式物件會定義一組序列化繪圖資料。 一旦定義繪圖資料，系統此後就會負責回應轉譯應用程式物件的所有重新繪製要求。 即使在執行階段，您也可以修改或建立應用程式物件，並仍需依賴系統以回應繪製要求。 保留模式圖形系統的能力在於繪製資訊一律由應用程式以序列化狀態持續保存，但是轉譯的責任屬於系統。 下圖顯示應用程式如何依賴 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 來回應繪製要求。  
  
 ![WPF 轉譯序列的圖表](./media/wpf-graphics-rendering-overview/wpf-rendering-sequence.png)  

#### <a name="intelligent-redrawing"></a>智慧型重新繪製  
 使用保留模式圖形的一個最大的優點就是 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 可以有效地最佳化應用程式中需要重新繪製的項目。 即使您有一個具有不同層級不透明度的複雜場景，通常也不需要撰寫特殊用途程式碼來最佳化重新繪製作業。 與 Win32 程式設計比較，在 Win32 程式設計中您可能會花費大量精力，透過將更新區域中重新繪製的次數降至最低，來最佳化您的應用程式上。 如需在 Win32 應用程式中最佳化重新繪製所牽涉之複雜性類型的範例，請參閱[在更新區域中重新繪製](/windows/desktop/gdi/redrawing-in-the-update-region)。  
  
### <a name="vector-graphics"></a>向量圖形  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 使用「向量圖形」作為其轉譯資料格式。 向量圖形 (包含可縮放向量圖形 (SVG)、Windows 中繼檔案 (.wmf) 和 TrueType 字型) 會儲存轉譯資料並將它以說明如何使用圖形基元重新建立影像的指示清單來傳輸。 例如，TrueType 字型是邊框字型，可描述一組線條、曲線和命令，而非像素陣列。 向量圖形的其中一個主要優點就是能夠縮放為任何大小和解析度。  
  
 與向量圖形不同，點陣圖圖形將轉譯資料儲存為影像的逐像素 (pixel-by-pixel) 表示法，針對特定解析度預先轉譯。 點陣和向量圖形格式之間的其中一個主要差異是原始來源影像的逼真度。 例如，當來源影像的的大小經過修改，點陣圖圖形系統會伸展影像，而向量圖形系統則是縮放影像，因此保留影像逼真度。  
  
 下圖顯示已將大小調整為 300% 的來源影像。 請注意，當來源影像是以點陣圖圖形影像伸展而非以向量圖形影像縮放時，會出現扭曲。  
  
 ![點陣圖形和向量圖形之間的差異](./media/wpf-graphics-rendering-overview/raster-vector-differences.png)  
  
 下列標記會顯示兩個已定義的 @no__t 0 個元素。 第二個元素會使用 <xref:System.Windows.Media.ScaleTransform>，將第一個元素的繪圖指示調整為 300%。 請注意，<xref:System.Windows.Shapes.Path> 元素中的繪圖指示會保持不變。  
  
 [!code-xaml[VectorGraphicsSnippets#VectorGraphicsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/VectorGraphicsSnippets/CS/PageOne.xaml#vectorgraphicssnippet1)]  
  
### <a name="about-resolution-and-device-independent-graphics"></a>有關解析度和裝置獨立圖形  
 決定螢幕上文字和圖形大小的系統因素有兩個：解析度和 DPI。 解析度描述螢幕上顯示的像素數目。 解析度越高，像素越小，使得圖形和文字看起來比較小。 顯示在設定為 1024 x 768 的監視器上的圖形，當解析度變更為 1600 x 1200 時，看起來會更小。  
  
 另一個系統設定 DPI 則描述以像素為單位的畫面英吋大小。 大部分的 Windows 系統都有96的 DPI，這表示螢幕的解析度是96圖元。 提高 DPI 設定會讓畫面英吋更大；降低 DPI 則讓畫面英吋更小。 這表示畫面英吋與實際英吋不相同，在大部分的系統上，通常都不相同。 當您提高 DPI，DPI 感知的圖形和文字會變得更大，因為您已經提高畫面英吋的大小。 提高 DPI 可讓文字更方便閱讀，特別是在高解析度時。  
  
 並非所有應用程式都是 DPI 感知：某些應用程式使用硬體像素作為主要度量單位；變更系統 DPI 不會影響這些應用程式。 許多其他的應用程式會使用 DPI 感知單位來描述字型大小，但是使用像素來描述所有其他項目。 DPI 太小或太大可能造成這些應用程式的版面配置問題，因為應用程式的文字是隨著系統的 DPI 設定縮放，但應用程式的 UI 則否。 針對使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 開發的應用程式，此問題已解決。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 支援自動縮放，方法是使用裝置獨立像素作為其主要度量單位，而非硬體像素；圖形和文字會適當地縮放，應用程式開發人員不需要執行任何額外工作。 下圖顯示以不同 DPI 設定顯示 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 文字和圖形之方式的範例。  
  
 ![不同 DPI 設定的圖形和文字](./media/graphicsmm-dpi-setting-examples.png "graphicsmm_DPI_setting_examples")  
不同 DPI 設定時的圖形和文字  
  
<a name="visualtreehelper_class"></a>   
## <a name="visualtreehelper-class"></a>VisualTreeHelper 類別  
 @No__t 0 類別是靜態協助程式類別，可提供在視覺物件層級進行程式設計的低層級功能，這在非常特定的案例中很有用，例如開發高效能的自訂控制項。 在大部分情況下，較高層級的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] framework 物件（例如 @no__t 1 和 @no__t 2）提供更大的彈性和易用性。  
  
### <a name="hit-testing"></a>點擊測試  
 當預設的點擊測試支援不符合您的需求時，@no__t 0 類別會提供針對視覺物件進行點擊測試的方法。 您可以使用 <xref:System.Windows.Media.VisualTreeHelper> 類別中的 <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> 方法，來判斷幾何或點座標值是否在指定物件的界限內，例如控制項或圖形元素。 例如，您可以使用點擊測試來判斷物件的週框矩形內的滑鼠點擊是否落於圓形的幾何內。您也可以選擇覆寫預設點擊測試實作，以執行您的自訂點擊測試計算。  
  
 如需點擊測試的詳細資訊，請參閱[視覺分層中的點擊測試](hit-testing-in-the-visual-layer.md)。  
  
### <a name="enumerating-the-visual-tree"></a>列舉視覺化樹狀結構  
 @No__t 0 類別提供列舉視覺化樹狀結構成員的功能。 若要取出父系，請呼叫 <xref:System.Windows.Media.VisualTreeHelper.GetParent%2A> 方法。 若要取出視覺物件的子系或直接下階，請呼叫 <xref:System.Windows.Media.VisualTreeHelper.GetChild%2A> 方法。 這個方法會在指定的索引處傳回父系的子 <xref:System.Windows.Media.Visual>。  
  
 下列範例示範如何列舉視覺物件的所有子系，如果您對將視覺物件階層的所有轉譯資訊序列化感興趣，這也會是您想要使用的技術。  
  
 [!code-csharp[VisualsOverview#101](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#101)]
 [!code-vb[VisualsOverview#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#101)]  
  
 在大部分案例中，邏輯樹狀結構是 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式中更有用的元素表示法。 雖然您不會直接修改邏輯樹狀結構，但應用程式的這個檢視適合用來了解屬性繼承和事件路由。 與視覺化樹狀結構不同的是，邏輯樹狀結構可以代表非視覺化的資料物件，例如 <xref:System.Windows.Documents.ListItem>。 如需有關邏輯樹狀結構的詳細資訊，請參閱 [WPF 中的樹狀結構](../advanced/trees-in-wpf.md)。  
  
 @No__t 0 類別提供方法來傳回視覺物件的周框。 您可以藉由呼叫 <xref:System.Windows.Media.VisualTreeHelper.GetContentBounds%2A>，傳回視覺物件的周框。 您可以藉由呼叫 <xref:System.Windows.Media.VisualTreeHelper.GetDescendantBounds%2A>，傳回視覺物件所有下階的周框，包括視覺物件本身。 下列程式碼示範如何計算視覺物件及其所有子系的週框矩形。  
  
 [!code-csharp[VisualsOverview#102](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#102)]
 [!code-vb[VisualsOverview#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#102)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Visual>
- <xref:System.Windows.Media.VisualTreeHelper>
- <xref:System.Windows.Media.DrawingVisual>
- [2D 圖形和影像處理](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [視覺分層中的點擊測試](hit-testing-in-the-visual-layer.md)
- [使用 DrawingVisual 物件](using-drawingvisual-objects.md)
- [教學課程：在 Win32 應用程式中裝載視覺物件 @ no__t-0
- [最佳化 WPF 應用程式效能](../advanced/optimizing-wpf-application-performance.md)

---
title: 圖形呈現概述
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rendering
- rendering graphics [WPF]
ms.assetid: 6dec9657-4d8c-4e46-8c54-40fb80008265
ms.openlocfilehash: 9d58aa973f7de6c073611e13f2889913ff26dd55
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111916"
---
# <a name="wpf-graphics-rendering-overview"></a>WPF 圖形轉譯概觀
本主題提供 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 視覺圖層的概觀。 它側重于<xref:System.Windows.Media.Visual>類在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]模型中呈現支援的角色。  

<a name="role_of_visual_object"></a>
## <a name="role-of-the-visual-object"></a>視覺物件的角色  
 類<xref:System.Windows.Media.Visual>是每個<xref:System.Windows.FrameworkElement>物件派生的基本抽象。 它也作為在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中撰寫新控制項的進入點，且在許多方面，可以視為 Win32 應用程式模型中的視窗控制代碼 (HWND)。  
  
 物件<xref:System.Windows.Media.Visual>是核心[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]物件，其主要角色是提供呈現支援。 使用者介面控制項（如<xref:System.Windows.Controls.Button>和<xref:System.Windows.Controls.TextBox>） 派生自<xref:System.Windows.Media.Visual>類，並使用它來保留其呈現資料。 該<xref:System.Windows.Media.Visual>物件支援：  
  
- 輸出顯示︰轉譯視覺物件已保存、序列化的繪圖內容。  
  
- 轉換︰執行視覺物件的轉換。  
  
- 裁剪：提供視覺物件的裁剪區域支援。  
  
- 點擊測試︰判斷座標或幾何是否包含於視覺物件的範圍內。  
  
- 週框方塊計算︰判斷視覺物件的週框矩形。  
  
 但是，該<xref:System.Windows.Media.Visual>物件不包括對非渲染功能的支援，例如：  
  
- 事件處理  
  
- 版面配置  
  
- 樣式  
  
- 資料繫結  
  
- 全球化  
  
 <xref:System.Windows.Media.Visual>作為公共抽象類別公開，必須從中派生子類。 下圖顯示 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中公開之視覺物件的階層。  
  
 ![衍生自 Visual 物件之類別的圖表](./media/wpf-graphics-rendering-overview/classes-derived-visual-object.png)
  
### <a name="drawingvisual-class"></a>DrawingVisual 類別  
 是<xref:System.Windows.Media.DrawingVisual>用於渲染形狀、圖像或文本的羽量級繪圖類。 此類別之所以被視為輕量型，是因為它不提供版面配置或事件處理，而這會改善其執行階段效能。 基於此原因，它適合用於背景或美工圖案繪圖。 <xref:System.Windows.Media.DrawingVisual>可用於創建自訂可視物件。 如需詳細資訊，請參閱[使用 DrawingVisual 物件](using-drawingvisual-objects.md)。  
  
### <a name="viewport3dvisual-class"></a>Viewport3DVisual 類別  
 在<xref:System.Windows.Media.Media3D.Viewport3DVisual>2D<xref:System.Windows.Media.Visual>和<xref:System.Windows.Media.Media3D.Visual3D>物件之間提供橋接器。 類<xref:System.Windows.Media.Media3D.Visual3D>是所有 3D 可視元素的基類。 要求<xref:System.Windows.Media.Media3D.Viewport3DVisual>定義<xref:System.Windows.Media.Media3D.Viewport3DVisual.Camera%2A>值和<xref:System.Windows.Media.Media3D.Viewport3DVisual.Viewport%2A>值。 相機可讓您檢視場景。 檢視區會建立投影到 2D 平面上的對應位置。 有關 3D 的更多資訊[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，請參閱[3D 圖形概述](3-d-graphics-overview.md)。  
  
### <a name="containervisual-class"></a>ContainerVisual 類別  
 類<xref:System.Windows.Media.ContainerVisual>用作物件集合的<xref:System.Windows.Media.Visual>容器。 類<xref:System.Windows.Media.DrawingVisual>派生自類<xref:System.Windows.Media.ContainerVisual>，允許它包含可視物件的集合。  
  
### <a name="drawing-content-in-visual-objects"></a>視覺物件中的繪圖內容  
 <xref:System.Windows.Media.Visual>物件將其渲染資料存儲為**向量圖形指令清單**。 指示清單中的每個項目代表一組低階圖形資料和相關聯的序列化格式的資源。 可包含繪圖內容的轉譯資料有四種不同的類型。  
  
|繪圖內容類型|描述|  
|--------------------------|-----------------|  
|向量圖形|表示向量圖形資料以及任何關聯<xref:System.Windows.Media.Brush>和資訊<xref:System.Windows.Media.Pen>。|  
|映像|表示由 定義的區域內的圖像<xref:System.Windows.Rect>。|  
|圖像|表示呈現<xref:System.Windows.Media.GlyphRun>的圖形，該圖形是來自指定字體資源的字形序列。 這是文字的表現方式。|  
|影片|代表轉譯視訊的繪圖。|  
  
 <xref:System.Windows.Media.DrawingContext>允許您使用可視內容填充<xref:System.Windows.Media.Visual>。 使用<xref:System.Windows.Media.DrawingContext>物件的繪製命令時，實際上存儲了一組渲染資料，圖形系統稍後將使用這些資料。您沒有即時繪製到螢幕。  
  
 創建[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]控制項（如 ）<xref:System.Windows.Controls.Button>時，控制項隱式生成繪製本身的呈現資料。 例如，<xref:System.Windows.Controls.ContentControl.Content%2A>設置 屬性<xref:System.Windows.Controls.Button>會導致控制項存儲字形的呈現表示形式。  
  
 將<xref:System.Windows.Media.Visual>其內容描述為包含在 中的一個或多個<xref:System.Windows.Media.Drawing>物件<xref:System.Windows.Media.DrawingGroup>。 A<xref:System.Windows.Media.DrawingGroup>還描述了應用於其內容的不一市場性蒙版、變換、點陣圖效果和其他操作。 <xref:System.Windows.Media.DrawingGroup>呈現內容時按以下<xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>順序應用操作： 、 <xref:System.Windows.Media.DrawingGroup.Opacity%2A> <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>、 <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>、 <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>、 、 <xref:System.Windows.Media.DrawingGroup.Transform%2A>、 ， 然後 .  
  
 下圖顯示了在渲染序列中應用<xref:System.Windows.Media.DrawingGroup>操作的順序。  
  
 ![DrawingGroup 作業的順序](./media/graphcismm-drawinggroup-order.png "graphcismm_drawinggroup_order")  
DrawingGroup 作業的順序  
  
 如需詳細資訊，請參閱[繪製物件概觀](drawing-objects-overview.md)。  
  
#### <a name="drawing-content-at-the-visual-layer"></a>視覺圖層的繪圖內容  
 你從來沒有直接具現化; <xref:System.Windows.Media.DrawingContext>但是，可以從某些方法（如 和<xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType><xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType>獲取繪圖上下文）獲取繪圖上下文。 下面的示例從 中檢索<xref:System.Windows.Media.DrawingContext> <xref:System.Windows.Media.DrawingVisual> a，並用它來繪製矩形。  
  
 [!code-csharp[drawingvisualsample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[drawingvisualsample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
#### <a name="enumerating-drawing-content-at-the-visual-layer"></a>列舉視覺圖層的繪圖內容  
 除了其他用途外，<xref:System.Windows.Media.Drawing>物件還提供用於枚舉 的物件模型。 <xref:System.Windows.Media.Visual>  
  
> [!NOTE]
> 枚舉視覺物件的內容時，將檢索<xref:System.Windows.Media.Drawing>物件，而不是將渲染資料作為向量圖形指令清單的基礎資料表示形式。  
  
 下面的示例使用 方法<xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A>檢索<xref:System.Windows.Media.DrawingGroup>的值<xref:System.Windows.Media.Visual>並枚舉它。  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
<a name="how_visual_objects_are_used_to_build_controls"></a>
## <a name="how-visual-objects-are-used-to-build-controls"></a>視覺物件如何用來建置控制項  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的許多物件是由其他視覺物件所組成，這表示它們可以包含不同的子系物件階層。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的許多使用者介面元素 (例如控制項) 是由多個視覺物件所組成，代表不同類型的轉譯元素。 例如，<xref:System.Windows.Controls.Button>控制項可以包含許多其他物件，包括<xref:Microsoft.Windows.Themes.ClassicBorderDecorator>和<xref:System.Windows.Controls.ContentPresenter>。 <xref:System.Windows.Controls.TextBlock>  
  
 以下代碼顯示在標記<xref:System.Windows.Controls.Button>中定義的控制項。  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet1)]  
  
 如果要枚舉構成預設<xref:System.Windows.Controls.Button>控制項的可視物件，將找到如下圖所示的可視物件的層次結構：  
  
 ![視覺化樹狀階層架構的圖表](./media/wpf-graphics-rendering-overview/visual-object-diagram.gif)
  
 控制項<xref:System.Windows.Controls.Button>包含一個<xref:Microsoft.Windows.Themes.ClassicBorderDecorator>元素，該元素又包含一個<xref:System.Windows.Controls.ContentPresenter>元素。 元素<xref:Microsoft.Windows.Themes.ClassicBorderDecorator>負責繪製 邊框和 背景<xref:System.Windows.Controls.Button>。 元素<xref:System.Windows.Controls.ContentPresenter>負責顯示 的內容<xref:System.Windows.Controls.Button>。 在這種情況下，由於您顯示文本，元素<xref:System.Windows.Controls.ContentPresenter>包含一個<xref:System.Windows.Controls.TextBlock>元素。 <xref:System.Windows.Controls.Button>控制項使用 的事實<xref:System.Windows.Controls.ContentPresenter>意味著內容可以由其他元素（如 或<xref:System.Windows.Controls.Image>幾何體）（如<xref:System.Windows.Media.EllipseGeometry>） 表示。  
  
### <a name="control-templates"></a>控制項範本  
 將控制項擴展到控制項層次結構的關鍵是<xref:System.Windows.Controls.ControlTemplate>。 控制項範本會指定控制項的預設視覺階層。 當您明確地參考控制項時，您會以隱含方式參考其視覺階層。 您可以覆寫控制項範本的預設值，以針對控制項建立自訂視覺外觀。 例如，您可以修改<xref:System.Windows.Controls.Button>控制項的背景顏色值，以便它使用線性漸層顏色值而不是純色值。 如需詳細資訊，請參閱[按鈕樣式和範本](../controls/button-styles-and-templates.md)。  
  
 使用者介面元素（如<xref:System.Windows.Controls.Button>控制項）包含多個描述控制項的整個呈現定義的向量圖形指令清單。 以下代碼顯示在標記<xref:System.Windows.Controls.Button>中定義的控制項。  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet2)]  
  
 如果要枚舉構成<xref:System.Windows.Controls.Button>控制項的可視物件和向量圖形指令清單，則會發現下面所示的物件層次結構：  
  
 ![視覺化樹狀結構和轉譯資料的圖表](./media/wpf-graphics-rendering-overview/visual-tree-rendering-data.png)  
  
 控制項<xref:System.Windows.Controls.Button>包含一個<xref:Microsoft.Windows.Themes.ClassicBorderDecorator>元素，該元素又包含一個<xref:System.Windows.Controls.ContentPresenter>元素。 該<xref:Microsoft.Windows.Themes.ClassicBorderDecorator>元素負責繪製構成按鈕邊框和背景的所有離散圖形元素。 元素<xref:System.Windows.Controls.ContentPresenter>負責顯示 的內容<xref:System.Windows.Controls.Button>。 在這種情況下，由於您要顯示圖像，因此<xref:System.Windows.Controls.ContentPresenter>元素包含一個<xref:System.Windows.Controls.Image>元素。  
  
 關於視覺物件的階層和向量圖形指示清單，有幾點需要注意：  
  
- 階層中的順序代表繪製資訊的轉譯順序。 子元素會由左至右、由上而下從根視覺元素周遊。 如果某元素具有視覺化子元素，則會在元素的同層級元素之前周遊這些子元素。  
  
- 層次結構中的非葉節點元素（如<xref:System.Windows.Controls.ContentPresenter>）用於包含子項目，它們不包含指令清單。  
  
- 如果視覺元素同時包含向量圖形指示清單與視覺子元素，父系視覺元素中的指示清單就會在任何視覺子元素物件中的繪圖之前轉譯。  
  
- 向量圖形指示清單中的項目會由左至右轉譯。  
  
<a name="visual_tree"></a>
## <a name="visual-tree"></a>視覺化樹狀結構  
 視覺化樹狀結構包含應用程式使用者介面中所使用的所有視覺元素。 由於視覺元素包含持續性繪圖資訊，您可以將視覺化樹狀結構想像為場景圖形，其中包含將輸出撰寫至顯示裝置所需的所有轉譯資訊。 此樹狀結構是直接由應用程式所建立 (不論是以程式碼或標記) 的所有視覺元素累積而成。 視覺化樹狀結構也包含由元素 (例如控制項和資料物件) 的範本展開所建立的所有視覺元素。  
  
 以下代碼顯示在標記<xref:System.Windows.Controls.StackPanel>中定義的元素。  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet3)]  
  
 如果要枚舉標記示例中包含<xref:System.Windows.Controls.StackPanel>元素的可視物件，則會發現如下圖所示的可視物件的層次結構：  
  
 ![視覺化樹狀階層架構的圖表](./media/wpf-graphics-rendering-overview/visual-tree-hierarchy.gif)  
  
### <a name="rendering-order"></a>轉譯順序  
 視覺化樹狀結構會決定 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 視覺物件和繪圖物件的轉譯順序。 周遊順序會從根視覺物件開始，這是視覺化樹狀結構的最上層節點。 然後，會由左至右周遊根視覺物件的子系。 如果視覺物件具有子系，則會在該視覺物件的同層級項目之前周遊其子系。 這表示子視覺物件的內容會在視覺物件本身的內容前面轉譯。  
  
 ![視覺化樹呈現順序圖](./media/wpf-graphics-rendering-overview/visual-tree-rendering-order.gif)
  
### <a name="root-visual"></a>根視覺物件  
 「根視覺物件」**** 是視覺化樹狀結構階層中最上層的元素。 在大多數應用程式中，根視覺物件的基本類為 或<xref:System.Windows.Window><xref:System.Windows.Navigation.NavigationWindow>。 不過，如果您已在 Win32 應用程式中裝載視覺物件，根視覺物件是您在 Win32 視窗中裝載的最上層視覺物件。 如需詳細資訊，請參閱[教學課程︰在 Win32 應用程式中裝載視覺物件](tutorial-hosting-visual-objects-in-a-win32-application.md)。  
  
### <a name="relationship-to-the-logical-tree"></a>邏輯樹狀結構的關聯性  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的邏輯樹狀結構代表執行階段應用程式的元素。 雖然您不會直接操作此樹狀結構，但應用程式的這個檢視適合用來了解屬性繼承和事件路由。 與視覺化樹不同，邏輯樹可以表示非可視資料物件，如<xref:System.Windows.Documents.ListItem>。 在許多案例中，邏輯樹狀結構會非常密切地對應至應用程式的標記定義。 以下代碼顯示在標記<xref:System.Windows.Controls.DockPanel>中定義的元素。  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet5)]  
  
 如果要枚舉標記示例中包含<xref:System.Windows.Controls.DockPanel>元素的邏輯物件，則會發現如下圖所示的邏輯物件的層次結構：  
  
 ![樹狀結構圖表](./media/tree1-wcp.gif "Tree1_wcp")  
邏輯樹狀結構的圖表  
  
 視覺化樹狀結構和邏輯樹狀結構會與目前的應用程式元素集合同步處理，以反映元素的任何新增、刪除或修改。 不過，樹狀結構會呈現不同的應用程式檢視。 與視覺化樹不同，邏輯樹不會展開控制項的元素<xref:System.Windows.Controls.ContentPresenter>。 這表示針對相同的物件集合，邏輯樹狀結構和視覺化樹狀結構之間沒有直接的一對一對應。 事實上，調用**邏輯樹説明器**物件<xref:System.Windows.LogicalTreeHelper.GetChildren%2A>的方法和使用與參數相同的元素的<xref:System.Windows.Media.VisualTreeHelper.GetChild%2A> **VisualTreeHelper**物件的方法會產生不同的結果。  
  
 如需邏輯樹狀結構的詳細資訊，請參閱 [WPF 中的樹狀結構](../advanced/trees-in-wpf.md)。  
  
### <a name="viewing-the-visual-tree-with-xamlpad"></a>使用 XamlPad 檢視視覺化樹狀結構  
 該工具[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]XamlPad 提供了一個選項，用於查看和探索與當前定義的 XAML 內容對應的視覺化樹。 按一下功能表列上的 [顯示視覺化樹狀結構]**** 按鈕以顯示視覺化樹狀結構。 下面演示了 Xaml 內容擴展到 XamlPad**的視覺化樹資源管理器**面板中的視覺化樹節點：  
  
 ![XamlPad 中的視覺化樹狀結構總管面板](./media/wpf-graphics-rendering-overview/visual-tree-explorer.png)  

 <xref:System.Windows.Controls.Label>請注意，<xref:System.Windows.Controls.TextBox>和<xref:System.Windows.Controls.Button>控制項在 XamlPad 的**視覺化樹資源管理器**面板中如何顯示單獨的可視物件層次結構。 這是因為[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]控制項具有包含該控制項<xref:System.Windows.Controls.ControlTemplate>的可視樹的 。 當您明確地參考控制項時，您會以隱含方式參考其視覺階層。  
  
### <a name="profiling-visual-performance"></a>分析視覺效能  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供一套效能分析工具，可讓您分析應用程式的執行階段行為，並判斷您可以套用的效能最佳化類型。 Visual Profiler 工具透過直接對應至應用程式的視覺化樹狀結構，提供豐富的效能資料的圖形化檢視。 在這個螢幕擷取畫面中，Visual Profiler 的 [CPU 使用量]**** 區段可提供您物件使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 服務的精確分析，例如轉譯和版面配置。  
  
 ![Visual Profiler 顯示輸出](./media/wpfperf-visualprofiler-04.png "WPFPerf_VisualProfiler_04")  
Visual Profiler 顯示輸出  
  
<a name="visual_rendering_behavior"></a>
## <a name="visual-rendering-behavior"></a>Visual 轉譯行為  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 導入幾個會影響視覺物件轉譯行為的功能：保留模式圖形、向量圖形和裝置獨立圖形。  
  
### <a name="retained-mode-graphics"></a>保留模式圖形  
 了解視覺物件角色的其中一個關鍵就是要了解「直接模式」**** 和「保留模式」**** 圖形系統之間的差異。 以 GDI 或 GDI+ 為基礎的標準 Win32 應用程式使用直接模式圖形系統。 這表示應用程式負責重新繪製因為像是重新調整視窗大小或者物件正在變更其視覺外觀等動作而無效的用戶端區域部分。  
  
 ![Win32 轉譯序列的圖表](./media/wpf-graphics-rendering-overview/win32-rendering-squence.png)  
  
 相反地，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 使用保留模式系統。 這表示具有視覺外觀的應用程式物件會定義一組序列化繪圖資料。 一旦定義繪圖資料，系統此後就會負責回應轉譯應用程式物件的所有重新繪製要求。 即使在執行階段，您也可以修改或建立應用程式物件，並仍需依賴系統以回應繪製要求。 保留模式圖形系統的能力在於繪製資訊一律由應用程式以序列化狀態持續保存，但是轉譯的責任屬於系統。 下圖顯示應用程式如何依賴 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 來回應繪製要求。  
  
 ![WPF 轉譯序列的圖表](./media/wpf-graphics-rendering-overview/wpf-rendering-sequence.png)  

#### <a name="intelligent-redrawing"></a>智慧型重新繪製  
 使用保留模式圖形的一個最大的優點就是 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 可以有效地最佳化應用程式中需要重新繪製的項目。 即使您有一個具有不同層級不透明度的複雜場景，通常也不需要撰寫特殊用途程式碼來最佳化重新繪製作業。 與 Win32 程式設計比較，在 Win32 程式設計中您可能會花費大量精力，透過將更新區域中重新繪製的次數降至最低，來最佳化您的應用程式上。 如需在 Win32 應用程式中最佳化重新繪製所牽涉之複雜性類型的範例，請參閱[在更新區域中重新繪製](/windows/desktop/gdi/redrawing-in-the-update-region)。  
  
### <a name="vector-graphics"></a>向量圖形  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 使用「向量圖形」**** 作為其轉譯資料格式。 向量圖形 (包含可縮放向量圖形 (SVG)、Windows 中繼檔案 (.wmf) 和 TrueType 字型) 會儲存轉譯資料並將它以說明如何使用圖形基元重新建立影像的指示清單來傳輸。 例如，TrueType 字型是邊框字型，可描述一組線條、曲線和命令，而非像素陣列。 向量圖形的其中一個主要優點就是能夠縮放為任何大小和解析度。  
  
 與向量圖形不同，點陣圖圖形將轉譯資料儲存為影像的逐像素 (pixel-by-pixel) 表示法，針對特定解析度預先轉譯。 點陣和向量圖形格式之間的其中一個主要差異是原始來源影像的逼真度。 例如，當來源影像的的大小經過修改，點陣圖圖形系統會伸展影像，而向量圖形系統則是縮放影像，因此保留影像逼真度。  
  
 下圖顯示已將大小調整為 300% 的來源影像。 請注意，當來源影像是以點陣圖圖形影像伸展而非以向量圖形影像縮放時，會出現扭曲。  
  
 ![點陣圖形和向量圖形之間的差異](./media/wpf-graphics-rendering-overview/raster-vector-differences.png)  
  
 下面的標記顯示了定義的兩<xref:System.Windows.Shapes.Path>個元素。 第二個<xref:System.Windows.Media.ScaleTransform>元素使用 將第一個元素的繪圖指令調整大小 300%。 請注意，元素中的<xref:System.Windows.Shapes.Path>繪圖說明保持不變。  
  
 [!code-xaml[VectorGraphicsSnippets#VectorGraphicsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/VectorGraphicsSnippets/CS/PageOne.xaml#vectorgraphicssnippet1)]  
  
### <a name="about-resolution-and-device-independent-graphics"></a>有關解析度和裝置獨立圖形  
 決定螢幕上文字和圖形大小的系統因素有兩個：解析度和 DPI。 解析度描述螢幕上顯示的像素數目。 解析度越高，像素越小，使得圖形和文字看起來比較小。 顯示在設定為 1024 x 768 的監視器上的圖形，當解析度變更為 1600 x 1200 時，看起來會更小。  
  
 另一個系統設定 DPI 則描述以像素為單位的畫面英吋大小。 大多數 Windows 系統的 DPI 為 96，這意味著螢幕英寸為 96 圖元。 提高 DPI 設定會讓畫面英吋更大；降低 DPI 則讓畫面英吋更小。 這表示畫面英吋與實際英吋不相同，在大部分的系統上，通常都不相同。 當您提高 DPI，DPI 感知的圖形和文字會變得更大，因為您已經提高畫面英吋的大小。 提高 DPI 可讓文字更方便閱讀，特別是在高解析度時。  
  
 並非所有應用程式都是 DPI 感知：某些應用程式使用硬體像素作為主要度量單位；變更系統 DPI 不會影響這些應用程式。 許多其他的應用程式會使用 DPI 感知單位來描述字型大小，但是使用像素來描述所有其他項目。 DPI 太小或太大可能造成這些應用程式的版面配置問題，因為應用程式的文字是隨著系統的 DPI 設定縮放，但應用程式的 UI 則否。 針對使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 開發的應用程式，此問題已解決。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 支援自動縮放，方法是使用裝置獨立像素作為其主要度量單位，而非硬體像素；圖形和文字會適當地縮放，應用程式開發人員不需要執行任何額外工作。 下圖顯示以不同 DPI 設定顯示 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 文字和圖形之方式的範例。  
  
 ![不同 DPI 設定時的圖形和文字](./media/graphicsmm-dpi-setting-examples.png "graphicsmm_DPI_setting_examples")  
不同 DPI 設定時的圖形和文字  
  
<a name="visualtreehelper_class"></a>
## <a name="visualtreehelper-class"></a>VisualTreeHelper 類別  
 類<xref:System.Windows.Media.VisualTreeHelper>是一個靜態説明器類，它為視覺化物件級別的程式設計提供低級功能，這在非常具體的方案中非常有用，例如開發高性能的自訂控制項。 在大多數情況下，高級[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]框架物件（如<xref:System.Windows.Controls.Canvas>和<xref:System.Windows.Controls.TextBlock>）提供了更大的靈活性和易用性。  
  
### <a name="hit-testing"></a>點擊測試  
 當<xref:System.Windows.Media.VisualTreeHelper>預設點擊測試支援不能滿足您的需要時，該類提供了對可視物件進行點擊測試的方法。 可以使用類中<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A><xref:System.Windows.Media.VisualTreeHelper>的方法來確定幾何或點座標值是否位於給定物件的邊界內，例如控制項或圖形元素。 例如，您可以使用點擊測試來判斷物件的週框矩形內的滑鼠點擊是否落於圓形的幾何內。您也可以選擇覆寫預設點擊測試實作，以執行您的自訂點擊測試計算。  
  
 如需點擊測試的詳細資訊，請參閱[視覺分層中的點擊測試](hit-testing-in-the-visual-layer.md)。  
  
### <a name="enumerating-the-visual-tree"></a>列舉視覺化樹狀結構  
 類<xref:System.Windows.Media.VisualTreeHelper>提供枚舉視覺化樹成員的功能。 若要檢索父級，請調用<xref:System.Windows.Media.VisualTreeHelper.GetParent%2A>方法。 若要檢索可視物件的子物件或直接後代，請調用 方法<xref:System.Windows.Media.VisualTreeHelper.GetChild%2A>。 此方法在指定的索引處<xref:System.Windows.Media.Visual>返回父項的子級。  
  
 下列範例示範如何列舉視覺物件的所有子系，如果您對將視覺物件階層的所有轉譯資訊序列化感興趣，這也會是您想要使用的技術。  
  
 [!code-csharp[VisualsOverview#101](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#101)]
 [!code-vb[VisualsOverview#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#101)]  
  
 在大部分案例中，邏輯樹狀結構是 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式中更有用的元素表示法。 雖然您不會直接修改邏輯樹狀結構，但應用程式的這個檢視適合用來了解屬性繼承和事件路由。 與視覺化樹不同，邏輯樹可以表示非可視資料物件，如<xref:System.Windows.Documents.ListItem>。 如需邏輯樹狀結構的詳細資訊，請參閱 [WPF 中的樹狀結構](../advanced/trees-in-wpf.md)。  
  
 類<xref:System.Windows.Media.VisualTreeHelper>提供返回可視物件的邊界矩形的方法。 可以通過調用<xref:System.Windows.Media.VisualTreeHelper.GetContentBounds%2A>返回可視物件的邊界矩形。 可以通過調用<xref:System.Windows.Media.VisualTreeHelper.GetDescendantBounds%2A>返回可視物件的所有後代（包括可視物件本身）的邊界矩形。 下列程式碼示範如何計算視覺物件及其所有子系的週框矩形。  
  
 [!code-csharp[VisualsOverview#102](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#102)]
 [!code-vb[VisualsOverview#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#102)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Visual>
- <xref:System.Windows.Media.VisualTreeHelper>
- <xref:System.Windows.Media.DrawingVisual>
- [2D 圖形和影像處理](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [視覺分層中的點擊測試](hit-testing-in-the-visual-layer.md)
- [使用 DrawingVisual 物件](using-drawingvisual-objects.md)
- [教學課程：在 Win32 應用程式中裝載視覺物件](tutorial-hosting-visual-objects-in-a-win32-application.md)
- [最佳化 WPF 應用程式效能](../advanced/optimizing-wpf-application-performance.md)

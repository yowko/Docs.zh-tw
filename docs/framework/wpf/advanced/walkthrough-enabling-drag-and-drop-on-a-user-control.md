---
title: "逐步解說：在使用者控制項上啟用拖放功能 | Microsoft Docs"
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
  - "拖放功能 [WPF], 逐步解說"
  - "逐步解說 [WPF], 拖放"
ms.assetid: cc844419-1a77-4906-95d9-060d79107fc7
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 逐步解說：在使用者控制項上啟用拖放功能
這個逐步解說會示範如何建立可在 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中參與拖放資料傳輸的自訂使用者控制項。  
  
 在此逐步解說中，您會建立一個代表圓形的自訂 WPF <xref:System.Windows.Controls.UserControl>。  您會在此控制項上實作功能，以便透過拖放動作在其上進行資料傳輸。  例如，如果您從一個 Circle 控制項拖曳至另一個 Circle 控制項，便會從來源 Circle 複製填滿色彩資料至目標 Circle。  如果您從 Circle 控制項拖曳至 <xref:System.Windows.Controls.TextBox>，則會將填滿色彩的字串表示複製至 <xref:System.Windows.Controls.TextBox>。  您也將建立一個小型應用程式，其中包含兩個面板控制項和一個 <xref:System.Windows.Controls.TextBox>，用來測試拖放功能。  您會撰寫程式碼，讓面板可以處理所放置的 Circle 資料，使您可以從一個面板的 Children 集合移動或複製 Circle 至另一個面板。  
  
 這個逐步解說將說明下列工作：  
  
-   建立自訂使用者控制項。  
  
-   啟用使用者控制項做為拖曳來源。  
  
-   啟用使用者控制項做為置放目標。  
  
-   啟用面板，接收從使用者控制項放置過來的資料。  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   Visual Studio 2010  
  
## 建立應用程式專案  
 在本節中，您會建立應用程式基礎結構，包括一個內有兩個面板和一個 <xref:System.Windows.Controls.TextBox> 的主頁面。  
  
### 若要建立專案  
  
1.  在 Visual Basic 或 Visual C\# 中，建立名為 `DragDropExample` 的新 WPF 應用程式專案。  如需詳細資訊，請參閱 [HOW TO：建立新的 WPF 應用程式專案](http://msdn.microsoft.com/zh-tw/1f6aea7a-33e1-4d3f-8555-1daa42e95d82)。  
  
2.  開啟 MainWindow.xaml。  
  
3.  在開頭和結尾 <xref:System.Windows.Controls.Grid> 標記 \(Tag\) 之間，加入下列標記 \(Markup\)。  
  
     此標記 \(Markup\) 會建立測試應用程式的使用者介面。  
  
     [!code-xml[DragDropWalkthrough#PanelsStep1XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep1xaml)]  
  
## 將新的使用者控制項加入至專案  
 在本節中，您會將新的使用者控制項加入至專案。  
  
### 若要加入新的使用者控制項  
  
1.  從 \[專案\] 功能表中選取 \[**加入使用者控制項**\]。  
  
2.  在 \[加入新項目\] 對話方塊中，將名稱變更為 `Circle.xaml`，然後按一下 \[**加入**\]。  
  
     Circle.xaml 和它的程式碼後置就會加入至專案。  
  
3.  開啟 Circle.xaml。  
  
     這個檔案包含使用者控制項的使用者介面項目。  
  
4.  將下列標記加入至根 <xref:System.Windows.Controls.Grid>，建立有一個藍色圓形做為其 UI 的簡單使用者控制項。  
  
     [!code-xml[DragDropWalkthrough#EllipseXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#ellipsexaml)]  
  
5.  開啟 Circle.xaml.cs 或 Circle.xaml.vb。  
  
6.  在 C\# 中，將下列程式碼加到預設建構函式後面，以建立複製建構函式。  在 Visual Basic 中，加入下列程式碼，以同時建立預設建構函式和複製建構函式。  
  
     為了讓使用者控制項可以被複製，您會在程式碼後置檔案中加入複製建構函式方法。  在此簡化的 Circle 使用者控制項中，您只會複製使用者控制項的填滿和大小資料。  
  
     [!code-csharp[DragDropWalkthrough#CopyCtor](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#copyctor)]
     [!code-vb[DragDropWalkthrough#CopyCtor](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#copyctor)]  
  
### 若要將使用者控制項加入至主視窗  
  
1.  開啟 MainWindow.xaml。  
  
2.  將下列 XAML 加入至開頭 <xref:System.Windows.Window> 標記，以建立對目前應用程式的 XML 命名空間參考。  
  
    ```  
    xmlns:local="clr-namespace:DragDropExample"  
    ```  
  
3.  在第一個 <xref:System.Windows.Controls.StackPanel> 中，加入下列 XAML 以在第一個面板中建立 Circle 使用者控制項的兩個執行個體。  
  
     [!code-xml[DragDropWalkthrough#CirclesXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#circlesxaml)]  
  
     此面板的完整 XAML 看起來如下所示。  
  
     [!code-xml[DragDropWalkthrough#PanelsStep2XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep2xaml)]  
  
## 在使用者控制項中實作拖曳來源事件  
 在本節中，您會覆寫 <xref:System.Windows.UIElement.OnMouseMove%2A> 方法並啟始拖放作業。  
  
 如果有人開始拖曳 \(按下滑鼠按鍵並移動滑鼠\)，要傳輸的資料會封裝成 <xref:System.Windows.DataObject>。  在此例中，Circle 控制項會封裝三個資料項目：其填滿色彩的字串表示、其高度的雙精確度表示，以及本身複本。  
  
### 若要啟始拖放作業  
  
1.  開啟 Circle.xaml.cs 或 Circle.xaml.vb。  
  
2.  加入下列 <xref:System.Windows.UIElement.OnMouseMove%2A> 覆寫，以提供 <xref:System.Windows.UIElement.MouseMove> 事件的類別處理。  
  
     [!code-csharp[DragDropWalkthrough#OnMouseMove](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#onmousemove)]
     [!code-vb[DragDropWalkthrough#OnMouseMove](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#onmousemove)]  
  
     此 <xref:System.Windows.UIElement.OnMouseMove%2A> 覆寫會執行下列工作：  
  
    -   檢查當滑鼠移動時，是否已按下滑鼠左鍵。  
  
    -   將 Circle 資料封裝成 <xref:System.Windows.DataObject>。  在此例中，Circle 控制項會封裝三個資料項目：其填滿色彩的字串表示、其高度的雙精確度表示，以及本身複本。  
  
    -   呼叫靜態 <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=fullName> 方法來啟始拖放作業。  您會將下列三個參數傳遞給 <xref:System.Windows.DragDrop.DoDragDrop%2A> 方法：  
  
        -   `dragSource` – 此控制項的參考。  
  
        -   `data` \- 在先前程式碼中建立的 <xref:System.Windows.DataObject>。  
  
        -   `allowedEffects` – 允許進行的拖放作業，即 <xref:System.Windows.DragDropEffects> 或 <xref:System.Windows.DragDropEffects>。  
  
3.  按 F5 建置並執行應用程式。  
  
4.  按其中一個 Circle 控制項，然後將它拖曳至面板、另一個 Circle，再到 <xref:System.Windows.Controls.TextBox>。  拖曳至 <xref:System.Windows.Controls.TextBox> 時，游標會改變以表示移動狀態。  
  
5.  將 Circle 拖曳至 <xref:System.Windows.Controls.TextBox> 時，按住 CTRL 鍵。  請注意游標如何改變以表示複製狀態。  
  
6.  將 Circle 拖放至 <xref:System.Windows.Controls.TextBox>。  Circle 填滿色彩的字串表示會附加至 <xref:System.Windows.Controls.TextBox>。  
  
     ![Circle 之填滿色彩的字串表示](../../../../docs/framework/wpf/advanced/media/dragdrop-colorstring.png "DragDrop\_ColorString")  
  
 根據預設，拖放作業期間的游標會改變，以指出放置資料的效果將為何。  您可以處理 <xref:System.Windows.UIElement.GiveFeedback> 事件並設定不同游標，以自訂向使用者顯示的回應。  
  
### 若要向使用者顯示回應  
  
1.  開啟 Circle.xaml.cs 或 Circle.xaml.vb。  
  
2.  加入下列 <xref:System.Windows.UIElement.OnGiveFeedback%2A> 覆寫，以提供 <xref:System.Windows.UIElement.GiveFeedback> 事件的類別處理。  
  
     [!code-csharp[DragDropWalkthrough#OnGiveFeedback](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ongivefeedback)]
     [!code-vb[DragDropWalkthrough#OnGiveFeedback](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ongivefeedback)]  
  
     此 <xref:System.Windows.UIElement.OnGiveFeedback%2A> 覆寫會執行下列工作：  
  
    -   檢查置放目標之 <xref:System.Windows.UIElement.DragOver> 事件處理常式中設定的 <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> 值。  
  
    -   根據 <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> 值來設定自訂游標。  游標是用來向使用者顯示放置資料將有之效果的視覺化回應。  
  
3.  按 F5 建置並執行應用程式。  
  
4.  拖曳其中一個 Circle 控制項至面板、另一個 Circle，再到 <xref:System.Windows.Controls.TextBox>。  請注意，游標現在變成您在 <xref:System.Windows.UIElement.OnGiveFeedback%2A> 覆寫中指定的自訂游標。  
  
     ![以自訂游標執行拖放作業](../../../../docs/framework/wpf/advanced/media/dragdrop-customcursor.png "DragDrop\_CustomCursor")  
  
5.  從 <xref:System.Windows.Controls.TextBox> 中選取文字 `green`。  
  
6.  將 `green` 文字拖曳至 Circle 控制項。  請注意，現在會顯示預設游標，以指出拖放作業的效果。  回應游標一律由拖曳來源設定。  
  
## 在使用者控制項中實作置放目標事件  
 在本節中，您會指定使用者控制項做為置放目標、覆寫啟用使用者控制項做為置放目標的方法，並處理放置於其上的資料。  
  
### 若要啟用使用者控制項做為置放目標  
  
1.  開啟 Circle.xaml。  
  
2.  在開頭 <xref:System.Windows.Controls.UserControl> 標記中，加入 <xref:System.Windows.UIElement.AllowDrop%2A> 屬性並設定為 `true`。  
  
     [!code-xml[DragDropWalkthrough#UCTagXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#uctagxaml)]  
  
 當 <xref:System.Windows.UIElement.AllowDrop%2A> 屬性設為 `true`，而且拖曳來源的資料被放置在 Circle 使用者控制項上，就會呼叫 <xref:System.Windows.UIElement.OnDrop%2A> 方法。  在這個方法中，您會處理所放置的資料並將資料套用至 Circle。  
  
### 若要處理所放置的資料  
  
1.  開啟 Circle.xaml.cs 或 Circle.xaml.vb。  
  
2.  加入下列 <xref:System.Windows.UIElement.OnDrop%2A> 覆寫，以提供 <xref:System.Windows.UIElement.Drop> 事件的類別處理。  
  
     [!code-csharp[DragDropWalkthrough#OnDrop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondrop)]
     [!code-vb[DragDropWalkthrough#OnDrop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondrop)]  
  
     此 <xref:System.Windows.UIElement.OnDrop%2A> 覆寫會執行下列工作：  
  
    -   使用 <xref:System.Windows.DataObject.GetDataPresent%2A> 方法以檢查拖曳資料是否包含字串物件。  
  
    -   使用 <xref:System.Windows.DataObject.GetData%2A> 方法以擷取字串資料 \(若有的話\)。  
  
    -   使用 <xref:System.Windows.Media.BrushConverter> 以嘗試將字串轉換為 <xref:System.Windows.Media.Brush>。  
  
    -   如果可以順利轉換，則將筆刷套用至提供 Circle 控制項 UI 之 <xref:System.Windows.Shapes.Ellipse> 的 <xref:System.Windows.Shapes.Shape.Fill%2A>。  
  
    -   將 <xref:System.Windows.UIElement.Drop> 事件標記為已處理。  您應將置放事件標記為已處理，收到此事件的其他項目才會知道 Circle 使用者控制項已經處理該事件了。  
  
3.  按 F5 建置並執行應用程式。  
  
4.  在 <xref:System.Windows.Controls.TextBox> 中選取文字 `green`。  
  
5.  將文字拖曳至 Circle 控制項並放下。  Circle 會從藍色變更為綠色。  
  
     ![將字串轉換成筆刷](../../../../docs/framework/wpf/advanced/media/dragdrop-dropgreentext.png "DragDrop\_DropGreenText")  
  
6.  在 <xref:System.Windows.Controls.TextBox> 中輸入文字 `green`。  
  
7.  在 <xref:System.Windows.Controls.TextBox> 中選取文字 `gre`。  
  
8.  將它拖曳至 Circle 控制項並放下。  請注意游標會改變以表示允許放置動作，但 Circle 的色彩不會改變，因為 `gre` 不是有效顏色。  
  
9. 從綠色 Circle 控制項拖曳並放置到藍色 Circle 控制項上。  Circle 會從藍色變更為綠色。  請注意，所顯示的游標取決於拖曳來源是 <xref:System.Windows.Controls.TextBox> 還是 Circle。  
  
 若要啟用項目做為置放目標，所需步驟只有將 <xref:System.Windows.UIElement.AllowDrop%2A> 屬性設定為 `true`，以及處理所放置的資料。  不過，若想提供更佳的使用者體驗，您還應該處理 <xref:System.Windows.UIElement.DragEnter>、<xref:System.Windows.UIElement.DragLeave> 和 <xref:System.Windows.UIElement.DragOver> 事件。  在這些事件中，您可以在放置資料前執行檢查，以及向使用者顯示其他回應。  
  
 將資料拖曳至 Circle 使用者控制項時，控制項應通知拖曳來源它是否可以處理所拖曳的資料。  如果控制項不知道如何處理資料，則應拒絕放置。  若要這麼做，您需要處理 <xref:System.Windows.UIElement.DragOver> 事件並設定 <xref:System.Windows.DragEventArgs.Effects%2A> 屬性。  
  
### 若要確認允許資料放置  
  
1.  開啟 Circle.xaml.cs 或 Circle.xaml.vb。  
  
2.  加入下列 <xref:System.Windows.UIElement.OnDragOver%2A> 覆寫，以提供 <xref:System.Windows.UIElement.DragOver> 事件的類別處理。  
  
     [!code-csharp[DragDropWalkthrough#OnDragOver](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragover)]
     [!code-vb[DragDropWalkthrough#OnDragOver](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragover)]  
  
     此 <xref:System.Windows.UIElement.OnDragOver%2A> 覆寫會執行下列工作：  
  
    -   將 <xref:System.Windows.DragEventArgs.Effects%2A> 屬性設定為 <xref:System.Windows.DragDropEffects>。  
  
    -   執行與 <xref:System.Windows.UIElement.OnDrop%2A> 方法中相同的檢查，以判斷 Circle 使用者控制項是否可以處理所拖曳的資料。  
  
    -   如果使用者控制項可以處理資料，則將 <xref:System.Windows.DragEventArgs.Effects%2A> 屬性設定為 <xref:System.Windows.DragDropEffects> 或 <xref:System.Windows.DragDropEffects>。  
  
3.  按 F5 建置並執行應用程式。  
  
4.  在 <xref:System.Windows.Controls.TextBox> 中選取文字 `gre`。  
  
5.  將文字拖曳至 Circle 控制項。  請注意現在游標會改變以表示不允許放置動作，因為 `gre` 不是有效顏色。  
  
 您可以套用放置作業的預覽，進一步增強使用者體驗。  在 Circle 使用者控制項，您需要覆寫 <xref:System.Windows.UIElement.OnDragEnter%2A> 和 <xref:System.Windows.UIElement.OnDragLeave%2A> 方法。  拖曳資料至控制項時，會將目前背景 <xref:System.Windows.Shapes.Shape.Fill%2A> 儲存至預存位置變數。  接著會將字串轉換為筆刷，並套用至提供 Circle UI 的 <xref:System.Windows.Shapes.Ellipse>。  如果拖曳資料至 Circle 外 \(但沒有放置\)，則會將原始 <xref:System.Windows.Shapes.Shape.Fill%2A> 値重新套用至 Circle。  
  
### 若要預覽拖放作業的效果  
  
1.  開啟 Circle.xaml.cs 或 Circle.xaml.vb。  
  
2.  在 Circle 類別中宣告名為 `_previousFill` 的私用 <xref:System.Windows.Media.Brush> 變數，並將它初始化為 `null`。  
  
     [!code-csharp[DragDropWalkthrough#Brush](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#brush)]
     [!code-vb[DragDropWalkthrough#Brush](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#brush)]  
  
3.  加入下列 <xref:System.Windows.UIElement.OnDragEnter%2A> 覆寫，以提供 <xref:System.Windows.UIElement.DragEnter> 事件的類別處理。  
  
     [!code-csharp[DragDropWalkthrough#OnDragEnter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragenter)]
     [!code-vb[DragDropWalkthrough#OnDragEnter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragenter)]  
  
     此 <xref:System.Windows.UIElement.OnDragEnter%2A> 覆寫會執行下列工作：  
  
    -   在 `_previousFill` 變數中儲存 <xref:System.Windows.Shapes.Ellipse> 的 <xref:System.Windows.Shapes.Shape.Fill%2A> 屬性。  
  
    -   執行與 <xref:System.Windows.UIElement.OnDrop%2A> 方法中相同的檢查，以判斷資料是否可以轉換成 <xref:System.Windows.Media.Brush>。  
  
    -   如果資料已轉換為有效 <xref:System.Windows.Media.Brush>，則將它套用至 <xref:System.Windows.Shapes.Ellipse> 的 <xref:System.Windows.Shapes.Shape.Fill%2A>。  
  
4.  加入下列 <xref:System.Windows.UIElement.OnDragLeave%2A> 覆寫，以提供 <xref:System.Windows.UIElement.DragLeave> 事件的類別處理。  
  
     [!code-csharp[DragDropWalkthrough#OnDragLeave](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragleave)]
     [!code-vb[DragDropWalkthrough#OnDragLeave](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragleave)]  
  
     此 <xref:System.Windows.UIElement.OnDragLeave%2A> 覆寫會執行下列工作：  
  
    -   將 `_previousFill` 變數中儲存的 <xref:System.Windows.Media.Brush>，套用至提供 Circle 使用者控制項 UI 之 <xref:System.Windows.Shapes.Ellipse> 的 <xref:System.Windows.Shapes.Shape.Fill%2A>。  
  
5.  按 F5 建置並執行應用程式。  
  
6.  在 <xref:System.Windows.Controls.TextBox> 中選取文字 `green`。  
  
7.  將文字拖曳至 Circle 控制項，但不放下。  Circle 會從藍色變更為綠色。  
  
     ![預覽拖放作業的效果](../../../../docs/framework/wpf/advanced/media/dragdrop-previeweffects.png "DragDrop\_PreviewEffects")  
  
8.  將文字拖曳離開 Circle 控制項。  Circle 會從綠色變回為藍色。  
  
## 啟用面板以接收所置放的資料  
 在本節中，您會啟用裝載 Circle 使用者控制項的面板，做為所拖曳 Circle 資料的置放目標。  您會實作程式碼，讓您可以在不同面板間移動 Circle，或是透過在拖曳 Circle 同時按住 CTRL 鍵來複製 Circle 控制項。  
  
### 若要啟用面板做為置放目標  
  
1.  開啟 MainWindow.xaml。  
  
2.  如下列 XAML 所示，在每個 <xref:System.Windows.Controls.StackPanel> 控制項中，加入 <xref:System.Windows.UIElement.DragOver> 和 <xref:System.Windows.UIElement.Drop> 事件的處理常式。  將 <xref:System.Windows.UIElement.DragOver> 事件處理常式命名為 `panel_DragOver`，並將 <xref:System.Windows.UIElement.Drop> 事件處理常式命名為 `panel_Drop`。  
  
     [!code-xml[DragDropWalkthrough#PanelsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml#panelsxaml)]  
  
3.  開啟 MainWindows.xaml.cs 或 MainWindow.xaml.vb。  
  
4.  將下列程式碼加入 <xref:System.Windows.UIElement.DragOver> 事件處理常式。  
  
     [!code-csharp[DragDropWalkthrough#PanelDragOver](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldragover)]
     [!code-vb[DragDropWalkthrough#PanelDragOver](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldragover)]  
  
     此 <xref:System.Windows.UIElement.DragOver> 事件處理常式會執行下列工作：  
  
    -   確定所拖曳資料是否包含 Circle 使用者控制項封裝在 <xref:system.Windows.DataObject> 中，並在 <xref:System.Windows.DragDrop.DoDragDrop%2A> 呼叫中傳遞的 "Object" 資料。  
  
    -   如果有 "Object" 資料，則檢查是否已按下 CTRL 鍵。  
  
    -   如果已按下 CTRL 鍵，則將 <xref:System.Windows.DragEventArgs.Effects%2A> 屬性設定為 <xref:System.Windows.DragDropEffects>。  否則，將 <xref:System.Windows.DragEventArgs.Effects%2A> 屬性設定為 <xref:System.Windows.DragDropEffects>。  
  
5.  將下列程式碼加入 <xref:System.Windows.UIElement.Drop> 事件處理常式。  
  
     [!code-csharp[DragDropWalkthrough#PanelDrop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldrop)]
     [!code-vb[DragDropWalkthrough#PanelDrop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldrop)]  
  
     此 <xref:System.Windows.UIElement.Drop> 事件處理常式會執行下列工作：  
  
    -   檢查是否已經處理 <xref:System.Windows.UIElement.Drop> 事件。  例如，如果將 Circle 放置在另一個處理 <xref:System.Windows.UIElement.Drop> 事件的 Circle 上，您不會希望包含 Circle 的面板也對此事件進行處理。  
  
    -   如果尚未處理 <xref:System.Windows.UIElement.Drop> 事件，檢查是否已按下 CTRL 鍵。  
  
    -   如果當 <xref:System.Windows.UIElement.Drop> 發生時已按下 CTRL 鍵，則複製 Circle 控制項並將複本加入至 <xref:System.Windows.Controls.StackPanel> 的 <xref:System.Windows.Controls.Panel.Children%2A> 集合。  
  
    -   如果未按下 CTRL 鍵，則將 Circle 從其父面板的 <xref:System.Windows.Controls.Panel.Children%2A> 集合移動至放置此 Circle 所在之面板的 <xref:System.Windows.Controls.Panel.Children%2A> 集合。  
  
    -   設定 <xref:System.Windows.DragEventArgs.Effects%2A> 屬性以通知 <xref:System.Windows.DragDrop.DoDragDrop%2A> 方法已執行移動或是複製作業。  
  
6.  按 F5 建置並執行應用程式。  
  
7.  從 <xref:System.Windows.Controls.TextBox> 中選取文字 `green`。  
  
8.  將文字拖曳至 Circle 控制項並放下。  
  
9. 從左面板拖曳 Circle 控制項至右面板並放下。  Circle 會從左面板的 <xref:System.Windows.Controls.Panel.Children%2A> 集合中移除，並加入至右面板的 Children 集合。  
  
10. 按住 CTRL 鍵，同時將 Circle 控制項從所在面板拖曳至另一個面板並放下。  如此會複製 Circle，並將複本加入至接收面板的 <xref:System.Windows.Controls.Panel.Children%2A> 集合。  
  
     ![拖曳 Circle 時按住 CTRL 鍵](../../../../docs/framework/wpf/advanced/media/dragdrop-paneldrop.png "DragDrop\_PanelDrop")  
  
## 請參閱  
 [拖放概觀](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)
---
title: "逐步解說：WPF 使用者入門 | Microsoft Docs"
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
  - "使用者入門, WPF"
  - "WPF, 使用者入門"
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
caps.latest.revision: 71
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 68
---
# 逐步解說：WPF 使用者入門
<a name="introduction"></a> 本逐步解說介紹 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] 應用程式的開發，包括大多數 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式都會用到的項目：[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 標記、程式碼後置、應用程式定義、控制項、配置、資料繫結和樣式。  
  
 本逐步解說會透過下列步驟帶領您逐步開發出一個簡單的 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式。  
  
-   定義 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，以設計應用程式的[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 外觀。  
  
-   撰寫程式碼，以建置應用程式的行為。  
  
-   建立應用程式定義，以管理應用程式。  
  
-   加入控制項和建立配置，以建立應用程式 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。  
  
-   建立樣式，以建立一致的應用程式 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 外觀。  
  
-   將 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 繫結至資料以用資料填入 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，並使資料和 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 保持同步。  
  
 當您完成本逐步解說時，即建置好一支獨立的 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] 應用程式，可以讓使用者檢視所選取人員的經費支出報表。  應用程式將由數個 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 頁面組成，這些頁面裝載在類似瀏覽器的視窗中。  
  
 用來建構此逐步解說的範例程式碼有 [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)] 和 [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] 兩種版本；請參閱[建置 WPF 應用程式簡介](http://go.microsoft.com/fwlink/?LinkID=160008) \(英文\)。  
  
<a name="Requirements"></a>   
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]  
  
 如需安裝 [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] 的詳細資訊，請參閱 [安裝 Visual Studio](../Topic/Install%20Visual%20Studio%202015.md)。  
  
<a name="Create_The_Application_Code_Files"></a>   
## 建立應用程式專案  
 在本節中，您會建立應用程式基礎結構，包括一個應用程式定義、兩個頁面和一個影像。  
  
1.  在 Visual Basic 或 Visual C\# 中，建立名為 `ExpenseIt` 的新 WPF 應用程式專案。  如需詳細資訊，請參閱 [HOW TO：建立新的 WPF 應用程式專案](http://msdn.microsoft.com/zh-tw/1f6aea7a-33e1-4d3f-8555-1daa42e95d82)。  
  
    > [!NOTE]
    >  這個逐步解說使用的 <xref:System.Windows.Controls.DataGrid> 控制項只適用於 .NET Framework 4。  請確定您的專案是以 .NET Framework 4 為目標。  如需詳細資訊，請參閱 [如何：以 .NET Framework 版本為目標](../Topic/How%20to:%20Target%20a%20Version%20of%20the%20.NET%20Framework.md)。  
  
2.  開啟 Application.xaml \(Visual Basic\) 或 App.xaml \(C\#\)。  
  
     這個 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案定義 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式和任何應用程式資源。您也可以使用這個檔案，指定會在應用程式啟動時自動顯示的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]；在這個範例中，這個檔案是 MainWindow.xaml。  
  
     您的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 在 Visual Basic 中看起來應該如下所示：  
  
     [!code-xml[ExpenseIt#1_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]  
  
     或在 C\# 中如下所示：  
  
     [!code-xml[ExpenseIt#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]  
  
3.  開啟 MainWindow.xaml。  
  
     這個 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案是應用程式的主視窗，可以分頁顯示建立的內容。  <xref:System.Windows.Window> 類別會定義視窗的屬性 \(例如其標題、大小或圖示\)，並且處理關閉或隱藏等事件。  
  
4.  將 <xref:System.Windows.Window> 項目變更為 <xref:System.Windows.Navigation.NavigationWindow>。  
  
     這個應用程式會隨使用者所做的互動，巡覽至不同的內容。  因此，主要 <xref:System.Windows.Window> 需要變更為 <xref:System.Windows.Navigation.NavigationWindow>。  <xref:System.Windows.Navigation.NavigationWindow> 會繼承 <xref:System.Windows.Window> 的所有屬性。  XAML 檔中的 <xref:System.Windows.Navigation.NavigationWindow> 項目會建立 <xref:System.Windows.Navigation.NavigationWindow> 類別的執行個體。  如需詳細資訊，請參閱 [巡覽概觀](../../../../docs/framework/wpf/app-development/navigation-overview.md)。  
  
5.  變更 <xref:System.Windows.Navigation.NavigationWindow> 項目上的下列屬性：  
  
    -   將 <xref:System.Windows.Window.Title%2A> 屬性設定為 "ExpenseIt"。  
  
    -   將 <xref:System.Windows.FrameworkElement.Width%2A> 屬性設定為 500 像素。  
  
    -   將 <xref:System.Windows.FrameworkElement.Height%2A> 屬性設定為 350 像素。  
  
    -   移除 <xref:System.Windows.Navigation.NavigationWindow> 標籤之間的 <xref:System.Windows.Controls.Grid> 項目。  
  
     您的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 在 Visual Basic 中看起來應該如下所示：  
  
     [!code-xml[ExpenseIt#2_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]  
  
     或在 C\# 中如下所示：  
  
     [!code-xml[ExpenseIt#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]  
  
6.  開啟 MainWindow.xaml.vb 或 MainWindow.xaml.cs。  
  
     這個檔案是程式碼後置的檔案，其包含的程式碼要處理在 MainWindow.xaml 中宣告的事件。  這個檔案包含 XAML 中定義之視窗的部分類別。  
  
7.  如果您使用的是 C\#，請將 `MainWindow` 類別變更為衍生自 <xref:System.Windows.Navigation.NavigationWindow>。  
  
     在 Visual Basic 中，當您在 XAML 中變更此視窗時，會自動執行這個動作。  
  
     您的程式碼應該像這樣。  
  
     [!code-csharp[ExpenseIt#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml.cs#3)]
     [!code-vb[ExpenseIt#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml.vb#3)]  
  
<a name="add_files_to_the_application"></a>   
## 將檔案加入至應用程式  
 在本節中，您會將兩個頁面和一個影像加入至應用程式。  
  
1.  將新頁面 \(WPF\) 加入至名為 `ExpenseItHome.xaml` 的專案。  如需詳細資訊，請參閱 [HOW TO：加入新項目至 WPF 專案](http://msdn.microsoft.com/zh-tw/17e6b238-fc32-4385-98ef-2f66ca09d9ad)。  
  
     這個頁面會是應用程式啟動時顯示的第一頁。  它會顯示一份人員清單，使用者可從中選取一名人員查看其經費支出報表。  
  
2.  開啟 ExpenseItHome.xaml。  
  
3.  將 <xref:System.Windows.Controls.Page.Title%2A> 設定為 "ExpenseIt \- Home"。  
  
     您的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 在 Visual Basic 中看起來應該如下所示：  
  
     [!code-xml[ExpenseIt#6_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]  
  
     或在 C\# 中如下所示：  
  
     [!code-xml[ExpenseIt#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]  
  
4.  開啟 MainWindow.xaml。  
  
5.  將 <xref:System.Windows.Navigation.NavigationWindow> 上的 <xref:System.Windows.Navigation.NavigationWindow.Source%2A> 屬性設定為 "ExpenseItHome.xaml"。  
  
     這會將 ExpenseItHome.xaml 設定為應用程式啟動時開啟的第一頁。  您的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 在 Visual Basic 中看起來應該如下所示：  
  
     [!code-xml[ExpenseIt#7_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]  
  
     或在 C\# 中如下所示：  
  
     [!code-xml[ExpenseIt#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]  
  
6.  將新分頁 \(WPF\) 加入至名為 `ExpenseReportPage.xaml` 的專案。  
  
     這個頁面將顯示從 ExpenseItHome.xaml 中選取之人員的經費支出報表。  
  
7.  開啟 ExpenseReportPage.xaml。  
  
8.  將 <xref:System.Windows.Controls.Page.Title%2A> 設定為 "ExpenseIt \- View Expense"。  
  
     您的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 在 Visual Basic 中看起來應該如下所示：  
  
     [!code-xml[ExpenseIt#4_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]  
  
     或在 C\# 中如下所示：  
  
     [!code-xml[ExpenseIt#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]  
  
9. 開啟 ExpenseItHome.xaml.vb 和 ExpenseReportPage.xaml.vb，或開啟 ExpenseItHome.xaml.cs 和 ExpenseReportPage.xaml.cs。  
  
     當您建立新的分頁檔時，Visual Studio 會自動建立程式碼後置檔案。  這些程式碼後置檔案會處理用於回應使用者輸入的邏輯。  
  
     您的程式碼應該像這樣。  
  
     [!code-csharp[ExpenseIt#2_5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]
     [!code-vb[ExpenseIt#2_5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]  
  
     [!code-csharp[ExpenseIt#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]
     [!code-vb[ExpenseIt#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]  
  
10. 將名為 watermark.png 的影像加入至專案。  您可以建立自己的影像，或是複製範例程式碼中的檔案。  如需詳細資訊，請參閱 [NIB:How to: Add Existing Items to a Project](http://msdn.microsoft.com/zh-tw/15f4cfb7-78ab-457f-9f14-099a25a6a2d3)。  
  
<a name="Build_The_Application"></a>   
## 建置和執行應用程式  
 此本節中，您會建置和執行應用程式。  
  
1.  按 F5 或是選取 \[**偵錯**\] 功能表中的 \[**開始偵錯**\]，以建置和執行應用程式。  
  
     下圖顯示具有 <xref:System.Windows.Navigation.NavigationWindow> 按鈕的應用程式。  
  
     ![ExpenseIt 範例螢幕擷取畫面](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure1.png "GettingStartedFigure1")  
  
2.  關閉應用程式以回到 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]。  
  
<a name="Add_Layout"></a>   
## 建立配置  
 配置提供一種有次序的放置 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 項目的方式，並且管理調整 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 大小時這些項目的大小和位置。  您通常會建立具有下列其中一個控制項的配置：  
  
-   <xref:System.Windows.Controls.Canvas>  
  
-   <xref:System.Windows.Controls.DockPanel>  
  
-   <xref:System.Windows.Controls.Grid>  
  
-   <xref:System.Windows.Controls.StackPanel>  
  
-   <xref:System.Windows.Controls.VirtualizingStackPanel>  
  
-   <xref:System.Windows.Controls.WrapPanel>  
  
 以上這些配置控制項都支援一種用於其子項目的特殊配置類型。  ExpenseIt 頁面的大小可以調整，各頁面都有項目會沿著其他項目水平和垂直排列。  因此，<xref:System.Windows.Controls.Grid> 是應用程式理想的配置項目。  
  
> [!NOTE]
>  如需 <xref:System.Windows.Controls.Panel> 項目的詳細資訊，請參閱[面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)。  如需配置的詳細資訊，請參閱[配置](../../../../docs/framework/wpf/advanced/layout.md)。  
  
 在本節中，您會將欄和列定義加入至 ExpenseItHome.xaml 中的 <xref:System.Windows.Controls.Grid>，以建立含有一欄三列、邊界為 10 個像素的表格。  
  
1.  開啟 ExpenseItHome.xaml。  
  
2.  將 <xref:System.Windows.Controls.Grid> 項目上的 <xref:System.Windows.FrameworkElement.Margin%2A> 屬性設定為 "10,0,10,10"，以對應上、下、左、右邊界。  
  
3.  將下列 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 加入至 <xref:System.Windows.Controls.Grid> 標籤之間，以建立列和欄定義。  
  
     [!code-xml[ExpenseIt#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]  
  
     有兩列的 <xref:System.Windows.Controls.RowDefinition.Height%2A> 會設定為 <xref:System.Windows.GridLength.Auto%2A>，這表示這些列會根據列中的內容調整大小。  預設 <xref:System.Windows.Controls.RowDefinition.Height%2A> 為 <xref:System.Windows.GridUnitType> 大小，這表示列的大小會是其在可用空間的加權比例。  例如，如果有兩列的高度都是 "\*"，則每列的高度會各佔可用空間的一半。  
  
     您的 <xref:System.Windows.Controls.Grid> 現在應該如下列 XAML 所示：  
  
     [!code-xml[ExpenseIt#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]  
  
<a name="Add_Controls"></a>   
## 加入控制項  
 在本節中，會將首頁 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 更新成顯示人員清單，讓使用者可從中選取人員以顯示所選取人員的經費支出報表。  控制項是使用者藉以與您的應用程式互動的 UI 物件。  如需詳細資訊，請參閱[控制項](../../../../docs/framework/wpf/controls/index.md)。  
  
 為了建立這個 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，下列項目會加入至 ExpenseItHome.xaml：  
  
-   <xref:System.Windows.Controls.ListBox> \(用於人員的清單\)。  
  
-   <xref:System.Windows.Controls.Label> \(用於清單標題\)。  
  
-   <xref:System.Windows.Controls.Button> \(按一下即可檢視從清單中選取的人員的經費支出報表\)。  
  
 每個控制項都是藉由設定 <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=fullName> 附加屬性的方式，放置在 <xref:System.Windows.Controls.Grid> 的列中。  如需附加屬性的詳細資訊，請參閱[附加屬性概觀](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)。  
  
1.  開啟 ExpenseItHome.xaml。  
  
2.  在 <xref:System.Windows.Controls.Grid> 標籤之間加入下列 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。  
  
     [!code-xml[ExpenseIt#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]  
  
3.  建置並執行應用程式。  
  
 下圖顯示本節中的 XAML 所建立的控制項。  
  
 ![ExpenseIt 範例螢幕擷取畫面](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure2.png "GettingStartedFigure2")  
  
<a name="Add_an_Image"></a>   
## 加入影像和標題  
 在本節中，會使用影像和頁面標題更新首頁 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。  
  
1.  開啟 ExpenseItHome.xaml。  
  
2.  將具有 230 像素固定 <xref:System.Windows.Controls.ColumnDefinition.Width%2A> 的另一欄，加入至 <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A>。  
  
     [!code-xml[ExpenseIt#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11)]  
  
3.  將另一列加入至 <xref:System.Windows.Controls.Grid.RowDefinitions%2A>。  
  
     [!code-xml[ExpenseIt#11b](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11b)]  
  
4.  將 <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=fullName> 設定為 1，以將控制項移至第二欄。  將 <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=fullName> 加 1，以將每個控制項下移一列。  
  
     [!code-xml[ExpenseIt#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]  
  
5.  將 <xref:System.Windows.Controls.Grid> 的 <xref:System.Windows.Controls.Panel.Background%2A> 設定為 watermark.png 影像檔。  
  
     [!code-xml[ExpenseIt#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]  
  
6.  在 <xref:System.Windows.Controls.Border> 之前，加入內容為 "View Expense Report" 的 <xref:System.Windows.Controls.Label> 做為頁面的標題。  
  
     [!code-xml[ExpenseIt#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]  
  
7.  建置並執行應用程式。  
  
 下圖顯示本節的結果。  
  
 ![ExpenseIt 範例螢幕擷取畫面](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure3.png "GettingStartedFigure3")  
  
<a name="Add_Code_to_Process_Events"></a>   
## 加入程式碼以處理事件  
  
1.  開啟 ExpenseItHome.xaml。  
  
2.  將 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件處理常式加入至 <xref:System.Windows.Controls.Button> 項目。  如需詳細資訊，請參閱 [HOW TO：建立簡單的事件處理常式](http://msdn.microsoft.com/zh-tw/b1456e07-9dec-4354-99cf-18666b64f480)。  
  
     [!code-xml[ExpenseIt#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]  
  
3.  開啟 ExpenseItHome.xaml.vb 或 ExpenseItHome.xaml.cs。  
  
4.  將下列程式碼加入至 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件處理常式，這個程式碼會使視窗巡覽至 ExpenseReportPage.xaml 檔案。  
  
     [!code-csharp[ExpenseIt#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
     [!code-vb[ExpenseIt#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]  
  
<a name="Create_the_UI_for_Pane2"></a>   
## 建立 ExpenseReportPage 的 UI  
 ExpenseReportPage.xaml 將顯示從 ExpenseItHome.xaml 中選取之人員的經費支出報表。  本節會加入控制項並建立 ExpenseReportPage.xaml 的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。  同時也會將背景和填滿色彩加入至各個 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 項目。  
  
1.  開啟 ExpenseReportPage.xaml。  
  
2.  在 <xref:System.Windows.Controls.Grid> 標籤之間加入下列 XAML。  
  
     這個 UI 與 ExpenseItHome.xaml 上建立的 UI 類似，只不過報告資料是顯示在 <xref:System.Windows.Controls.DataGrid> 中。  
  
     [!code-xml[ExpenseIt#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]  
  
3.  建置並執行應用程式。  
  
    > [!NOTE]
    >  如果您收到 <xref:System.Windows.Controls.DataGrid> 找不到或不存在的錯誤，請確認您的專案目標是 .NET Framework 4。  如需詳細資訊，請參閱 [如何：以 .NET Framework 版本為目標](../Topic/How%20to:%20Target%20a%20Version%20of%20the%20.NET%20Framework.md)。  
  
4.  按一下 \[**檢視**\] 按鈕。  
  
     支出報告頁面隨即出現。  
  
 下圖顯示加入至 ExpenseReportPage.xaml 的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 項目。  請注意，上一頁巡覽按鈕已啟用。  
  
 ![ExpenseIt 範例螢幕擷取畫面](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure4.png "GettingStartedFigure4")  
  
<a name="Add_Code_to_Style_a_Control"></a>   
## 樣式控制項  
 在 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 中有各種項目，其中所有同類型的項目外觀通常一樣。  [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 利用樣式使多個項目可重複使用同一外觀。  重複使用樣式可以簡化 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 的建立和管理。  如需樣式的詳細資訊，請參閱[設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)。  本節會將先前步驟中定義的個別項目屬性 \(Attribute\) 取代為樣式。  
  
1.  開啟 Application.xaml 或 App.xaml。  
  
2.  在 <xref:System.Windows.Application.Resources%2A?displayProperty=fullName> 標籤之間加入下列 XAML：  
  
     [!code-xml[ExpenseIt#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]  
  
     這個 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 會加入下列樣式：  
  
    -   `headerTextStyle`：設定頁面標題 <xref:System.Windows.Controls.Label> 的格式。  
  
    -   `labelStyle`：設定 <xref:System.Windows.Controls.Label> 控制項的格式。  
  
    -   `columnHeaderStyle`：格式化 <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>。  
  
    -   `listHeaderStyle`：設定清單標題 <xref:System.Windows.Controls.Border> 控制項的格式。  
  
    -   `listHeaderTextStyle`：設定清單標題 <xref:System.Windows.Controls.Label> 的格式。  
  
    -   `buttonStyle`：設定 ExpenseItHome.xaml 上 <xref:System.Windows.Controls.Button> 的格式。  
  
     請注意，樣式是 <xref:System.Windows.Application.Resources%2A?displayProperty=fullName> 屬性 \(Property\) 項目的資源和子系。  在這裡，樣式會套用至應用程式中的所有項目。  如需在 [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] 應用程式中使用資源的範例，請參閱[使用應用程式資源](../../../../docs/framework/wpf/advanced/how-to-use-application-resources.md)。  
  
3.  開啟 ExpenseItHome.xaml。  
  
4.  以下列 XAML 取代 <xref:System.Windows.Controls.Grid> 項目之間的一切內容。  
  
     [!code-xml[ExpenseIt#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]  
  
     <xref:System.Windows.VerticalAlignment> 和 <xref:System.Windows.Media.FontFamily> 等用於定義每個控制項之外觀的屬性，會因套用樣式而遭移除和取代。  例如，`headerTextStyle` 就會套用至 "View Expense Report" 這個 <xref:System.Windows.Controls.Label>。  
  
5.  開啟 ExpenseReportPage.xaml。  
  
6.  以下列 XAML 取代 <xref:System.Windows.Controls.Grid> 項目之間的一切內容。  
  
     [!code-xml[ExpenseIt#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]  
  
     這麼做會將樣式加入至 <xref:System.Windows.Controls.Label> 和 <xref:System.Windows.Controls.Border> 項目。  
  
7.  建置並執行應用程式。  
  
     加入本節中的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 標記後，應用程式看起來和更新成樣式之前一樣。  
  
<a name="Bind_Data_to_a_Control"></a>   
## 將資料繫結至控制項  
 在本節中，您會建立繫結至各個控制項的 [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] 資料。  
  
1.  開啟 ExpenseItHome.xaml。  
  
2.  在開頭 <xref:System.Windows.Controls.Grid> 項目後面，加入下列 XAML 以建立含有各人資料的 <xref:System.Windows.Data.XmlDataProvider>。  
  
     此資料是建立成 <xref:System.Windows.Controls.Grid> 資源。  此資料通常會以檔案形式載入，但是為求簡單，此資料會以內嵌方式加入。  
  
     [!code-xml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]  
    [!code-xml[ExpenseIt#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#23)]  
    [!code-xml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]  
  
3.  在 <xref:System.Windows.Controls.Grid> 資源中，加入下列 <xref:System.Windows.DataTemplate>，以定義在 <xref:System.Windows.Controls.ListBox> 中顯示資料的方式。  如需資料範本的詳細資訊，請參閱[資料範本化概觀](../../../../docs/framework/wpf/data/data-templating-overview.md)。  
  
     [!code-xml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]  
    [!code-xml[ExpenseIt#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#24)]  
    [!code-xml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]  
  
4.  以下列 XAML 取代現有的 <xref:System.Windows.Controls.ListBox>。  
  
     [!code-xml[ExpenseIt#25](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]  
  
     此 XAML 會將 <xref:System.Windows.Controls.ListBox> 的 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 屬性繫結至資料來源，並套用資料範本做為 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>。  
  
<a name="Connect_Data_to_Controls"></a>   
## 將資料連接到控制項  
 在本節中，您會撰寫程式碼來擷取目前在 ExpenseItHome.xaml 頁面的人員清單中選取的項目，並且在執行個體化期間將該項目的參考傳遞至 `ExpenseReportPage` 的建構函式。  `ExpenseReportPage` 會以傳遞的項目設定自己的資料內容，而這也就是 ExpenseReportPage.xaml 中定義的控制項將繫結的項目。  
  
1.  開啟 ExpenseReportPage.xaml.vb 或 ExpenseReportPage.xaml.cs。  
  
2.  加入接受一個物件的建構函式，以便您可以傳遞所選人員的經費支出報表資料。  
  
     [!code-csharp[ExpenseIt#26](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
     [!code-vb[ExpenseIt#26](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]  
  
3.  開啟 ExpenseItHome.xaml.vb 或 ExpenseItHome.xaml.cs。  
  
4.  變更 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件處理常式，以呼叫這個會傳遞所選人員之經費支出報表資料的新建構函式。  
  
     [!code-csharp[ExpenseIt#27](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
     [!code-vb[ExpenseIt#27](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]  
  
<a name="Add_Style_to_Data"></a>   
## 使用資料範本設定資料的樣式  
 在本節中，您會使用資料範本來更新資料繫結清單中每個項目的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]：  
  
1.  開啟 ExpenseReportPage.xaml。  
  
2.  將 "Name" 和 "Department" 這兩個 <xref:System.Windows.Controls.Label> 項目的內容繫結至適當的資料來源屬性 \(Property\)。  如需資料繫結的詳細資訊，請參閱[資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)。  
  
     [!code-xml[ExpenseIt#31](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]  
  
3.  在 <xref:System.Windows.Controls.Grid> 起始項目之後，加入下列資料範本，以定義顯示經費支出報表資料的方式。  
  
     [!code-xml[ExpenseIt#30](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]  
  
4.  將範本套用至會顯示經費支出報表資料的 <xref:System.Windows.Controls.DataGrid> 資料行。  
  
     [!code-xml[ExpenseIt#32](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]  
  
5.  建置並執行應用程式。  
  
6.  選取人員並按一下 \[**檢視**\] 按鈕。  
  
 下圖顯示 ExpenseIt 應用程式套用控制項、配置、樣式、資料繫結和資料範本後的兩個頁面。  
  
 ![ExpenseIt 範例螢幕擷取畫面](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure5.png "GettingStartedFigure5")  
  
<a name="Best_Practices"></a>   
## 最佳作法  
 這個範例示範 WPF 的特定功能，因此並未遵循應用程式開發的最佳作法。  如需 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和 [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] 應用程式開發最佳做法的完整內容，請依適當情況參閱下列主題：  
  
-   協助工具 \- [協助工具最佳作法](../../../../docs/framework/ui-automation/accessibility-best-practices.md)  
  
-   安全性 \- [安全性](../../../../docs/framework/wpf/security-wpf.md)  
  
-   當地語系化 \- [WPF 全球化和當地語系化概觀](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)  
  
-   效能 \- [最佳化 WPF 應用程式效能](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
  
<a name="Whats_Next"></a>   
## 下一步  
 現在您已經具備了用 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 建立 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的幾個技巧，您可以隨意運用。  您也應該對資料繫結 [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] 應用程式的基本建置組塊有了更深的了解。  很明顯的，這個主題並未詳盡說明一切方法，但是希望您在學得本主題的技巧後，能夠獲得一些概念，以探索更多可能性。  
  
 如需 WPF 架構和程式撰寫模型的詳細資訊，請參閱下列主題：  
  
-   [WPF 架構](../../../../docs/framework/wpf/advanced/wpf-architecture.md)  
  
-   [XAML 概觀 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
  
-   [相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
  
-   [配置](../../../../docs/framework/wpf/advanced/layout.md)  
  
 如需建立應用程式的詳細資訊，請參閱下列主題：  
  
-   [應用程式開發](../../../../docs/framework/wpf/app-development/index.md)  
  
-   [控制項](../../../../docs/framework/wpf/controls/index.md)  
  
-   [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)  
  
-   [圖形和多媒體](../../../../docs/framework/wpf/graphics-multimedia/index.md)  
  
-   [WPF 中的文件](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
  
## 請參閱  
 [面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)   
 [資料範本化概觀](../../../../docs/framework/wpf/data/data-templating-overview.md)   
 [建置 WPF 應用程式](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)   
 [樣式和範本](../../../../docs/framework/wpf/controls/styles-and-templates.md)
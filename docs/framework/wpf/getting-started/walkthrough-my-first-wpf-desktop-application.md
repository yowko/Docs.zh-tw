---
title: 逐步解說：我的第一個 WPF 桌面應用程式
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting started [WPF], WPF
- WPF [WPF], getting started
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
caps.latest.revision: 71
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3725e96b514b0204f10f6b5c45ed2bbec1d892de
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a>逐步解說：我的第一個 WPF 桌面應用程式
本逐步解說提供的應用程式開發簡介[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]包含項目通用於大多數的應用程式[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]應用程式：[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]標記、 程式碼後置、 應用程式定義、 控制項、 版面配置，資料繫結和樣式。 
  
本逐步解說會引導您完成簡單的開發[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]應用程式使用下列步驟。 
  
-   定義[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]設計的應用程式的外觀[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]。 
  
-   撰寫程式碼以建置應用程式的行為。 
  
-   建立應用程式定義以管理應用程式。 
  
-   加入控制項，並建立來撰寫應用程式配置[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。 
  
-   建立樣式來建立應用程式的外觀的一致性[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。 
  
-   繫結[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]兩者的資料填入[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]資料和保留資料及[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]同步處理。 
  
本逐步解說結束時，您會建立獨立[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]應用程式，讓使用者選取的人員檢視經費支出報表。 應用程式將由數個[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]裝載在瀏覽器樣式視窗中的頁面。 
  
用來建立這個逐步解說的範例程式碼都可用[!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)]和[!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)]在[建置 WPF 應用程式簡介](http://go.microsoft.com/fwlink/?LinkID=160008)。 

## <a name="prerequisites"></a>必要條件  

- [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)] (含) 以後版本

如需安裝最新版本的 Visual Studio 的詳細資訊，請參閱[安裝 Visual Studio](/visualstudio/install/install-visual-studio)。
  
## <a name="creating-the-application-project"></a>建立應用程式專案  
在本節中，您會建立應用程式基礎結構，包括一個應用程式定義、兩個頁面和一個影像。 
  
1. 在 Visual Basic 或 Visual C# 中，建立名為 `ExpenseIt` 的新 WPF 應用程式專案。 如需詳細資訊，請參閱[如何：建立新的 WPF 應用程式專案](http://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82)。 
  
    > [!NOTE]
    >  本逐步解說使用<xref:System.Windows.Controls.DataGrid>使用.NET Framework 4 中的控制項。 為確定您的專案目標.NET Framework 4 或更新版本。 如需詳細資訊，請參閱[如何：以 .NET Framework 版本為目標](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework)。 
  
2. 開啟 Application.xaml (Visual Basic) 或 App.xaml (C#)。 
  
     這[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案會定義[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]應用程式和應用程式的任何資源。 您也使用此檔案來指定[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]也會自動顯示在應用程式啟動; 在此情況下，將 MainWindow.xaml。 
  
     您[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]應該在 Visual Basic 中看起來像這樣：  
  
    [!code-xaml[ExpenseIt#1_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]  
  
     或在 C# 中如下所示：  
  
    [!code-xaml[ExpenseIt#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]  
  
3. 開啟 MainWindow.xaml。 
  
     這[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案是您的應用程式的主視窗，並顯示在頁面中建立的內容。 <xref:System.Windows.Window>類別定義的視窗中，其標題、 大小或圖示，例如屬性和處理事件，例如關閉或隱藏。 
  
4. 變更<xref:System.Windows.Window>元素<xref:System.Windows.Navigation.NavigationWindow>。 
  
     這個應用程式會根據使用者的互動巡覽至不同的內容。 因此，主要<xref:System.Windows.Window>需要變更以<xref:System.Windows.Navigation.NavigationWindow>。 <xref:System.Windows.Navigation.NavigationWindow> 繼承的所有屬性<xref:System.Windows.Window>。 <xref:System.Windows.Navigation.NavigationWindow> XAML 檔案中的項目建立的執行個體<xref:System.Windows.Navigation.NavigationWindow>類別。 如需詳細資訊，請參閱[覽概觀](../../../../docs/framework/wpf/app-development/navigation-overview.md)。 
  
5. 變更下列屬性上<xref:System.Windows.Navigation.NavigationWindow>項目：  
  
    -   設定<xref:System.Windows.Window.Title%2A>"ExpenseIt"的屬性。 
  
    -   設定<xref:System.Windows.FrameworkElement.Width%2A>500 像素為單位的屬性。 
  
    -   設定<xref:System.Windows.FrameworkElement.Height%2A>350 像素為單位的屬性。 
  
    -   移除<xref:System.Windows.Controls.Grid>之間的項目<xref:System.Windows.Navigation.NavigationWindow>標記。 
  
     您[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]應該在 Visual Basic 中看起來像這樣：  
  
    [!code-xaml[ExpenseIt#2_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]  
  
     或在 C# 中如下所示：  
  
    [!code-xaml[ExpenseIt#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]  
  
6. 開啟 MainWindow.xaml.vb 或 MainWindow.xaml.cs。 
  
     這個檔案是程式碼後置檔案，其中包含的程式碼可處理 MainWindow.xaml 中所宣告的事件。 這個檔案包含 XAML 中定義之視窗的部分類別。 
  
7. 如果您使用的 C#，變更`MainWindow`類別衍生自<xref:System.Windows.Navigation.NavigationWindow>。 
  
     在 Visual Basic 中，當您在 XAML 中變更視窗時會自動發生。 
  
     您的程式碼應該如下所示。 
  
    [!code-csharp[ExpenseIt#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml.cs#3)]
    [!code-vb[ExpenseIt#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml.vb#3)]  
  
## <a name="adding-files-to-the-application"></a>將檔案加入應用程式  
在本節中，您要加入兩個頁面及一個影像到應用程式中。 
  
1. 將新的頁面 (WPF) 加入至名為專案`ExpenseItHome.xaml`。 如需詳細資訊，請參閱[如何： 加入新項目加入至 WPF 專案](http://msdn.microsoft.com/library/17e6b238-fc32-4385-98ef-2f66ca09d9ad)。 
  
     這個頁面是應用程式啟動時顯示的第一個頁面。 它會顯示一份人員清單，使用者可從中選取一名人員查看其費用報表。 
  
2. 開啟 ExpenseItHome.xaml。 
  
3. 設定<xref:System.Windows.Controls.Page.Title%2A>至 「 ExpenseIt-首頁 」。 
  
     您[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]應該在 Visual Basic 中看起來像這樣：  
  
    [!code-xaml[ExpenseIt#6_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]  
  
     或在 C# 中如下所示：  
  
    [!code-xaml[ExpenseIt#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]  
  
4. 開啟 MainWindow.xaml。 
  
5. 設定<xref:System.Windows.Navigation.NavigationWindow.Source%2A>屬性<xref:System.Windows.Navigation.NavigationWindow>至 「 ExpenseItHome.xaml"。 
  
     這會將 ExpenseItHome.xaml 設成應用程式啟動時開啟的第一個頁面。 您[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]應該在 Visual Basic 中看起來像這樣：  
  
    [!code-xaml[ExpenseIt#7_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]  
  
     或在 C# 中如下所示：  
  
    [!code-xaml[ExpenseIt#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]  
  
6. 將新的頁面 (WPF) 加入至名為專案`ExpenseReportPage.xaml`。 
  
     這個頁面會顯示 ExpenseItHome.xaml 中所選取之人員的費用報表。 
  
7. 開啟 ExpenseReportPage.xaml。 
  
8. 設定<xref:System.Windows.Controls.Page.Title%2A>至 「 ExpenseIt-檢視費用報表 」。 
  
     您[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]應該在 Visual Basic 中看起來像這樣：  
  
    [!code-xaml[ExpenseIt#4_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]  
  
     或在 C# 中如下所示：  
  
    [!code-xaml[ExpenseIt#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]  
  
9. 開啟 ExpenseItHome.xaml.vb 和 ExpenseReportPage.xaml.vb，或是 ExpenseItHome.xaml.cs 和 ExpenseReportPage.xaml.cs。 
  
     當您建立新的頁面檔案時，Visual Studio 會自動建立程式碼後置檔案。 這些程式碼後置檔案會處理用於回應使用者輸入的邏輯。 
  
     您的程式碼應該如下所示。 
  
    [!code-csharp[ExpenseIt#2_5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]
    [!code-vb[ExpenseIt#2_5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]  
  
    [!code-csharp[ExpenseIt#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]
    [!code-vb[ExpenseIt#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]  
  
10. 加入名為影像*watermark.png*至專案。 您可以建立自己的影像，或是從範例程式碼複製檔案。 如需詳細資訊，請參閱[如何： 加入現有項目加入至專案](/previous-versions/visualstudio/visual-studio-2008/9f4t9t92(v=vs.90))。 

## <a name="building-and-running-the-application"></a>建置和執行應用程式  
在本節中，您會建置和執行應用程式。 
  
1. 建置並執行應用程式，請按 F5 或選取**開始偵錯**從**偵錯**功能表。 
  
     下圖顯示應用程式與<xref:System.Windows.Navigation.NavigationWindow>按鈕。 
  
     ![ExpenseIt 範例螢幕擷取畫面](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure1.png "GettingStartedFigure1")  
  
2. 關閉應用程式以返回[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]。 
  
## <a name="creating-the-layout"></a>建立版面配置  
版面配置會按照的順序放置[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]項目，以及管理的大小和位置的項目時[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]重新調整大小。 您通常會建立具有下列其中一個版面配置控制項的版面配置：  
  
-   <xref:System.Windows.Controls.Canvas>  
  
-   <xref:System.Windows.Controls.DockPanel>  
  
-   <xref:System.Windows.Controls.Grid>  
  
-   <xref:System.Windows.Controls.StackPanel>  
  
-   <xref:System.Windows.Controls.VirtualizingStackPanel>  
  
-   <xref:System.Windows.Controls.WrapPanel>  
  
這些版面配置控制項都支援其子元素的特殊版面配置類型。 ExpenseIt 頁面可以調整大小，而且每個頁面都有元素會沿著其他元素水平和垂直排列。 因此，<xref:System.Windows.Controls.Grid>為應用程式的理想的版面配置項目。 
  
> [!NOTE]
>  如需有關<xref:System.Windows.Controls.Panel>項目，請參閱[面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)。 如需有關配置的詳細資訊，請參閱[配置](../../../../docs/framework/wpf/advanced/layout.md)。 
  
在區段中，您建立單一資料行的資料表具有三個資料列和 10 個像素邊界藉由新增資料行和資料列定義，以<xref:System.Windows.Controls.Grid>ExpenseItHome.xaml 中。 
  
1. 開啟 ExpenseItHome.xaml。 
  
2. 設定<xref:System.Windows.FrameworkElement.Margin%2A>屬性<xref:System.Windows.Controls.Grid>"10,0,10,10 」 對應到左框線、 頂端、 右側和底部邊界的項目。 
  
3. 加入下列[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]之間<xref:System.Windows.Controls.Grid>標籤來建立資料列和資料行定義。 
  
    [!code-xaml[ExpenseIt#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]  
  
     <xref:System.Windows.Controls.RowDefinition.Height%2A>兩個資料列設<xref:System.Windows.GridLength.Auto%2A>表示將調整大小之資料列的基礎資料列中的內容。 預設值<xref:System.Windows.Controls.RowDefinition.Height%2A>是<xref:System.Windows.GridUnitType.Star>調整大小，這表示的資料列會在可用空間的加權的比例。 例如，如果有兩列的高度都是 "*"，則每列的高度會各佔可用空間的一半。  
  
     您<xref:System.Windows.Controls.Grid>現在應該看起來像下列 XAML:  
  
    [!code-xaml[ExpenseIt#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]  
  
## <a name="adding-controls"></a>加入控制項  
在此區段中，在首頁上[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]會更新以顯示使用者可以選取從，以顯示所選人員的經費支出報表的人員清單。 控制項是可讓使用者與您應用程式互動的 UI 物件。 如需詳細資訊，請參閱 [控制項](../../../../docs/framework/wpf/controls/index.md)。 
  
若要建立這個[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，下列項目會加入 ExpenseItHome.xaml:  
  
-   <xref:System.Windows.Controls.ListBox> （適用於的人員清單）。 
  
-   <xref:System.Windows.Controls.Label> （適用於清單標頭）。 
  
-   <xref:System.Windows.Controls.Button> （可以按一下清單中選取的人員檢視經費支出報表）。 
  
中的資料列位於每個控制項<xref:System.Windows.Controls.Grid>藉由設定<xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType>附加屬性。 如需附加屬性的詳細資訊，請參閱[附加屬性概觀](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)。 
  
1. 開啟 ExpenseItHome.xaml。 
  
2. 加入下列[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]之間<xref:System.Windows.Controls.Grid>標記。 
  
    [!code-xaml[ExpenseIt#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]  
  
3. 建置並執行應用程式。 
  
下圖顯示本節中的 XAML 所建立的控制項。 
  
![ExpenseIt 範例螢幕擷取畫面](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure2.png "GettingStartedFigure2")  
  
## <a name="adding-an-image-and-a-title"></a>加入的映像和標題  
在此區段中，在首頁上[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]會更新為映像和頁面標題。 
  
1. 開啟 ExpenseItHome.xaml。 
  
2. 加入另一個資料行，<xref:System.Windows.Controls.Grid.ColumnDefinitions%2A>固定<xref:System.Windows.Controls.ColumnDefinition.Width%2A>的 230 個像素。 
  
    [!code-xaml[ExpenseIt#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11)]  
  
3. 加入至另一個資料列<xref:System.Windows.Controls.Grid.RowDefinitions%2A>。 
  
    [!code-xaml[ExpenseIt#11b](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11b)]  
  
4. 將控制項移到第二個資料行中，藉由設定<xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType>設為 1。 下移一列中中的每個控制項，藉由增加<xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType>1。 
  
    [!code-xaml[ExpenseIt#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]  
  
5. 設定<xref:System.Windows.Controls.Panel.Background%2A>的<xref:System.Windows.Controls.Grid>watermark.png 映像檔。 
  
    [!code-xaml[ExpenseIt#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]  
  
6. 之前<xref:System.Windows.Controls.Border>，新增<xref:System.Windows.Controls.Label>以內容為頁面的標題的 [檢視費用報表]。 
  
    [!code-xaml[ExpenseIt#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]  
  
7. 建置並執行應用程式。 
  
下圖顯示本節的結果。 
  
![ExpenseIt 範例螢幕擷取畫面](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure3.png "GettingStartedFigure3")  
  
## <a name="adding-code-to-handle-events"></a>加入程式碼，來處理事件  
  
1. 開啟 ExpenseItHome.xaml。 
  
2. 新增<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件處理常式來<xref:System.Windows.Controls.Button>項目。 如需詳細資訊，請參閱[How to： 建立簡單的事件處理常式](http://msdn.microsoft.com/library/b1456e07-9dec-4354-99cf-18666b64f480)。 
  
    [!code-xaml[ExpenseIt#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]  
  
3. 開啟 ExpenseItHome.xaml.vb 或 ExpenseItHome.xaml.cs。 
  
4. 將下列程式碼加入<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件處理常式，會造成視窗巡覽至 ExpenseReportPage.xaml 檔案。 
  
    [!code-csharp[ExpenseIt#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]  
  
## <a name="creating-the-ui-for-expensereportpage"></a>建立 ExpenseReportPage 的 UI  
ExpenseReportPage.xaml 會顯示在 ExpenseItHome.xaml 上選取之人員的費用報表。 這一節加入的控制項，並建立[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]ExpenseReportPage.xaml 的。 本章節也會將背景色彩和填滿色彩加入至各種[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]項目。 
  
1. 開啟 ExpenseReportPage.xaml。 
  
2. 在 <xref:System.Windows.Controls.Grid> 標記之間加入下列 XAML。 
  
     此 UI 很類似，除了報表資料會顯示在 ExpenseItHome.xaml 上建立的 ui <xref:System.Windows.Controls.DataGrid>。 
  
    [!code-xaml[ExpenseIt#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]  
  
3. 建置並執行應用程式。 
  
    > [!NOTE]
    >  如果您收到錯誤，<xref:System.Windows.Controls.DataGrid>找不到或不存在，請確定您的專案以.NET Framework 4 或更新版本為目標。 如需詳細資訊，請參閱[如何：以 .NET Framework 版本為目標](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework)。 
  
4. 按一下**檢視** 按鈕。 
  
     報表頁面隨即出現。 
  
下圖顯示[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]ExpenseReportPage.xaml 所加入的項目。 請注意，已啟用向後巡覽按鈕。 
  
![ExpenseIt 範例螢幕擷取畫面](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure4.png "GettingStartedFigure4")  
  
## <a name="styling-controls"></a>設定控制項的樣式  
各種項目的外觀通常可以在相同型別的所有項目的相同[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 可使用樣式，使多個元素可重複使用外觀。 重複使用性的樣式有助於簡化[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]建立和管理。 如需有關樣式的詳細資訊，請參閱[設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)。 本節會將先前步驟中定義的個別元素屬性 (Attribute) 取代為樣式。 
  
1. 開啟 Application.xaml 或 App.xaml。 
  
2. 加入下列 XAML 之間<xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>標記：  
  
    [!code-xaml[ExpenseIt#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]  
  
     這[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]會加入下列樣式：  
  
    -  `headerTextStyle`：格式化頁面標題 <xref:System.Windows.Controls.Label>。 
  
    -  `labelStyle`：格式化 <xref:System.Windows.Controls.Label> 控制項。 
  
    -  `columnHeaderStyle`：格式化 <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>。 
  
    -  `listHeaderStyle`：格式化清單標頭 <xref:System.Windows.Controls.Border> 控制項。 
  
    -  `listHeaderTextStyle`： 若要格式化清單標頭<xref:System.Windows.Controls.Label>。 
  
    -  `buttonStyle`： 若要格式化<xref:System.Windows.Controls.Button>ExpenseItHome.xaml 上。 
  
     請注意，樣式資源和子系<xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>屬性項目。 在這裡，樣式會套用至應用程式中的所有元素。 如需範例的使用中的資源[!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)]應用程式，請參閱[使用應用程式資源](../../../../docs/framework/wpf/advanced/how-to-use-application-resources.md)。 
  
3. 開啟 ExpenseItHome.xaml。 
  
4. 取代之間的所有內容<xref:System.Windows.Controls.Grid>以下列 XAML 項目。 
  
    [!code-xaml[ExpenseIt#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]  
  
     套用樣式會移除並取代諸如 <xref:System.Windows.VerticalAlignment> 和 <xref:System.Windows.Media.FontFamily> 這類會定義每個控制項外觀的屬性。 例如，`headerTextStyle`套用至 [檢視費用報表] <xref:System.Windows.Controls.Label>。 
  
5. 開啟 ExpenseReportPage.xaml。 
  
6. 取代之間的所有內容<xref:System.Windows.Controls.Grid>以下列 XAML 項目。 
  
    [!code-xaml[ExpenseIt#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]  
  
     這樣會將樣式加入 <xref:System.Windows.Controls.Label> 和 <xref:System.Windows.Controls.Border> 項目。 
  
7. 建置並執行應用程式。 
  
     在新增之後[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]本節中，應用程式看起來都一樣使用樣式正在更新之前一樣。 
  
## <a name="binding-data-to-a-control"></a>資料繫結至控制項  
在本節中，您會建立[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]資料繫結至不同的控制項。 
  
1. 開啟 ExpenseItHome.xaml。 
  
2. 在開啟之後<xref:System.Windows.Controls.Grid>項目，加入下列 XAML 建立<xref:System.Windows.Data.XmlDataProvider>其中包含每個人員的資料。 
  
     資料會建立為<xref:System.Windows.Controls.Grid>資源。 這通常會載入為檔案，但為求簡化會內嵌資料。 
  
    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]  
    [!code-xaml[ExpenseIt#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#23)]  
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]  
  
3. 在<xref:System.Windows.Controls.Grid>資源，加入下列<xref:System.Windows.DataTemplate>，而後者可定義如何顯示資料的<xref:System.Windows.Controls.ListBox>。 如需資料範本的詳細資訊，請參閱[資料範本化概觀](../../../../docs/framework/wpf/data/data-templating-overview.md)。 
  
    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]  
    [!code-xaml[ExpenseIt#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#24)]  
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]  
  
4. 取代現有<xref:System.Windows.Controls.ListBox>以下列 XAML。 
  
    [!code-xaml[ExpenseIt#25](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]  
  
     這個 XAML 會繫結<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>屬性<xref:System.Windows.Controls.ListBox>到資料來源，並套用資料範本做為<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>。 
  
## <a name="connecting-data-to-controls"></a>資料連接至控制項  
在本節中，您撰寫可擷取目前的項目已選取 [ExpenseItHome.xaml] 頁面上的使用者清單中，並傳遞其參考的建構函式的程式碼`ExpenseReportPage`具現化。 `ExpenseReportPage` 會以傳遞的項目設定其資料內容，而這就是 ExpenseReportPage.xaml 中定義的控制項將繫結的項目。 
  
1. 開啟 ExpenseReportPage.xaml.vb 或 ExpenseReportPage.xaml.cs。 
  
2. 加入一個可接受物件的建構函式，如此您就可以傳遞選取之人員的費用報表資料。 
  
    [!code-csharp[ExpenseIt#26](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]  
  
3. 開啟 ExpenseItHome.xaml.vb 或 ExpenseItHome.xaml.cs。 
  
4. 變更<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件處理常式呼叫新的建構函式傳遞所選人員的經費支出報表資料。 
  
    [!code-csharp[ExpenseIt#27](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]  
  
## <a name="styling-data-with-data-templates"></a>使用資料範本的樣式設定資料  
在本節中，您會更新[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]對資料中的每個項目繫結使用的資料範本的清單。 
  
1. 開啟 ExpenseReportPage.xaml。 
  
2. 繫結內容的 「 名稱 」 和 「 部門 」<xref:System.Windows.Controls.Label>項目以適當的資料來源屬性。 如需資料繫結的詳細資訊，請參閱[資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)。 
  
    [!code-xaml[ExpenseIt#31](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]  
  
3. 在開啟之後<xref:System.Windows.Controls.Grid>項目，加入下列的資料範本，其中定義經費支出報表資料顯示方式。  
    [!code-xaml[ExpenseIt#30](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]  
  
4. 將範本套用至<xref:System.Windows.Controls.DataGrid>資料行，顯示 費用報表資料。 
  
    [!code-xaml[ExpenseIt#32](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]  
  
5. 建置並執行應用程式。 
  
6. 選取 人員，然後按一下**檢視** 按鈕。 
  
 下圖顯示套用了控制項、配置、樣式、資料繫結和資料範本的 ExpenseIt 應用程式的兩頁頁面。 
  
 ![ExpenseIt 範例螢幕擷取畫面](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure5.png "GettingStartedFigure5")  
  
## <a name="best-practices"></a>最佳作法  
這個範例示範 WPF 的特定功能，因此並未遵循應用程式開發的最佳做法。 完整涵蓋範圍的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]和[!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)]應用程式開發最佳作法，視需要參閱下列主題：  
  
-   協助工具： [協助工具最佳作法](../../../../docs/framework/ui-automation/accessibility-best-practices.md)  
  
-   安全性-[安全性](../../../../docs/framework/wpf/security-wpf.md)  
  
-   當地語系化： [WPF 全球化和當地語系化概觀](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)  
  
-   效能： [最佳化 WPF 應用程式效能](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
  
## <a name="whats-next"></a>後續步驟  
現在您有一些技術來建立達成[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]使用[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]。 您現在應該有廣泛的了解的資料繫結的基本建置組塊[!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)]應用程式。 本主題並不詳盡，但希望您有一些概念，可以自行發掘本主題所述技術之外的可能性。 
  
 如需 WPF 架構和程式設計模型的詳細資訊，請參閱下列主題：  
  
-   [WPF 架構](../../../../docs/framework/wpf/advanced/wpf-architecture.md)  
  
-   [XAML 概觀 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
  
-   [相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
  
-   [版面配置](../../../../docs/framework/wpf/advanced/layout.md)  
  
 如需建立應用程式的詳細資訊，請參閱下列主題：  
  
-   [應用程式開發](../../../../docs/framework/wpf/app-development/index.md)  
  
-   [控制項](../../../../docs/framework/wpf/controls/index.md)  
  
-   [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)  
  
-   [圖形和多媒體](../../../../docs/framework/wpf/graphics-multimedia/index.md)  
  
-   [WPF 中的文件](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
  
## <a name="see-also"></a>另請參閱  
 [面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [資料範本化概觀](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [建置 WPF 應用程式](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)  
 [樣式和範本](../../../../docs/framework/wpf/controls/styles-and-templates.md)

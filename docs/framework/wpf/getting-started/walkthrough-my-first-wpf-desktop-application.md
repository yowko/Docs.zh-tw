---
title: 教學課程：在 Visual Studio 2019 中建立您的第一個 WPF 應用程式-.NET Framework
ms.date: 09/06/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting started [WPF], WPF
- WPF [WPF], getting started
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
ms.topic: tutorial
ms.custom: vs-dotnet
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b2c8e36c1b8185f28a7ec20402e385f3a1ddf5ce
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991763"
---
# <a name="tutorial-create-your-first-wpf-application-in-visual-studio-2019"></a>教學課程：在 Visual Studio 2019 中建立您的第一個 WPF 應用程式

本文說明如何開發 Windows Presentation Foundation （WPF）桌面應用程式，其中包含大部分 WPF 應用程式通用的元素：Extensible Application Markup Language （XAML）標記、程式碼後置、應用程式定義、控制項、版面配置、資料系結和樣式。 若要開發應用程式，您將使用 Visual Studio。 

在本教學課程中，您將了解如何：
> [!div class="checklist"]
>
> - 建立 WPF 專案。
> - 使用 XAML 來設計應用程式的使用者介面（UI）的外觀。
> - 撰寫程式碼來建立應用程式的行為。
> - 建立應用程式定義來管理應用程式。
> - 新增控制項，並建立配置來撰寫應用程式 UI。
> - 建立應用程式 UI 中一致外觀的樣式。
> - 將 UI 系結至資料，以從資料填入 UI，以及保持資料和 UI 同步。

在本教學課程結束時，您將會建立獨立的 Windows 應用程式，讓使用者可以查看所選人員的費用報表。 應用程式是由數個以瀏覽器樣式視窗主控的 WPF 頁面所組成。

> [!TIP]
> 本教學課程中使用的範例程式碼適用于 Visual Basic 和C# [教學課程 WPF 應用程式範例程式碼](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp)。
>
> 您可以使用此頁面頂端的 [語言選取器C# ]，切換和 Visual Basic 之間的範例程式碼語言。

## <a name="prerequisites"></a>必要條件

- 已安裝 **.net 桌面開發**工作負載的[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) 。

   如需安裝最新版本 Visual Studio 的詳細資訊，請參閱[Install Visual Studio](/visualstudio/install/install-visual-studio)。

## <a name="create-the-application-project"></a>建立應用程式專案

第一個步驟是建立應用程式基礎結構，其中包含應用程式定義、兩頁和影像。

1. 在 Visual Basic 或 Visual C# 中名為建立新的 WPF 應用程式專案 **`ExpenseIt`** :

   1. 開啟 Visual Studio，然後選取 [**開始**使用] 功能表底下的 [**建立新專案**]。

      [**建立新專案**] 對話方塊隨即開啟。

   2. 在 **語言** 下拉式清單中**C#** ，選取或**Visual Basic**。
      
   3. 選取 [ **WPF 應用程式（.NET Framework）** ] 範本，然後選取 **[下一步]** 。 
     
      ![[建立新專案] 對話方塊](./media/walkthrough-my-first-wpf-desktop-application/create-new-project-dialog.png)
    
      [**設定您的新專案**] 對話方塊隨即開啟。

   4. 輸入專案名稱 **`ExpenseIt`** ，然後選取**建立**。

      ![[設定新專案] 對話方塊](./media/walkthrough-my-first-wpf-desktop-application/configure-new-project-dialog.png)

      Visual Studio 會建立專案，並開啟名為**mainwindow.xaml**之預設應用程式視窗的設計工具。

2. 開啟*應用程式 .xaml* （Visual Basic）或*app.xaml* （C#）。

    此 XAML 檔案會定義 WPF 應用程式和任何應用程式資源。 您也可以使用這個檔案來指定在應用程式啟動時自動顯示的 UI （在此案例中為*mainwindow.xaml*）。

    在 Visual Basic 中，您的 XAML 看起來應該如下所示：

    [!code-xaml[ExpenseIt#1_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    和如下所示C#：

    [!code-xaml[ExpenseIt#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. 開啟*mainwindow.xaml*。

    此 XAML 檔案是應用程式的主視窗，會顯示在頁面中建立的內容。 <xref:System.Windows.Window>類別會定義視窗的屬性，例如其標題、大小或圖示，以及處理事件（例如關閉或隱藏）。

4. 將元素變更<xref:System.Windows.Navigation.NavigationWindow>為，如下列 XAML 所示： <xref:System.Windows.Window>

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   此應用程式會根據使用者輸入，流覽至不同的內容。 這就是為什麼主要<xref:System.Windows.Window>需要變更為的<xref:System.Windows.Navigation.NavigationWindow>原因。 <xref:System.Windows.Navigation.NavigationWindow>繼承的所有屬性<xref:System.Windows.Window>。 XAML <xref:System.Windows.Navigation.NavigationWindow>檔案中的元素會建立<xref:System.Windows.Navigation.NavigationWindow>類別的實例。 如需詳細資訊，請參閱[導覽總覽](../app-development/navigation-overview.md)。

5. 移除<xref:System.Windows.Controls.Grid> 標記<xref:System.Windows.Navigation.NavigationWindow>之間的元素。

6. 在專案的 XAML 程式<xref:System.Windows.Navigation.NavigationWindow>代碼中變更下列屬性：

    - 將屬性設定為 "`ExpenseIt`"。 <xref:System.Windows.Window.Title%2A>

    - <xref:System.Windows.FrameworkElement.Height%2A>將屬性設定為350圖元。

    - <xref:System.Windows.FrameworkElement.Width%2A>將屬性設定為500圖元。

    Visual Basic 的 XAML 看起來應該如下所示：

    [!code-xaml[ExpenseIt#2_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    和如下所示C#：

    [!code-xaml[ExpenseIt#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

7. 開啟*mainwindow.xaml*或*MainWindow.xaml.cs*。

    這個檔案是程式碼後置檔案，其中包含處理*mainwindow.xaml*中所宣告之事件的程式碼。 這個檔案包含 XAML 中定義之視窗的部分類別。

8. 如果您使用C#的`MainWindow`是，請將類別變更為<xref:System.Windows.Navigation.NavigationWindow>衍生自。 （在 Visual Basic 中，這會在您以 XAML 變更視窗時自動發生）。您C#的程式碼現在看起來應該像這樣：

   [!code-csharp[ExpenseIt#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/MainWindow.xaml.cs?highlight=21)]

## <a name="add-files-to-the-application"></a>將檔案新增至應用程式

在本節中，您要在應用程式中加入兩頁網頁和一個影像。

1. 將新頁面加入至專案，並將它命名 *`ExpenseItHome.xaml`* :

   1. 在 [**方案總管] 中**，以滑鼠右鍵按一下 **`ExpenseIt`** 專案節點，然後選擇**新增** > **頁面**。

   1. 在 [**加入新專案**] 對話方塊中，已選取 [**頁面（WPF）** ] 範本。 輸入名稱 **`ExpenseItHome`** ，然後選取**新增**。

    此頁面是應用程式啟動時所顯示的第一個頁面。 它會顯示要從中選取的人員清單，以顯示的費用報表。

1. 開啟 *`ExpenseItHome.xaml`* 。

1. 將設定`ExpenseIt - Home`為 ""。 <xref:System.Windows.Controls.Page.Title%2A>

1. `DesignWidth`將設定`DesignHeight`為350圖元，並將設為500圖元。

    XAML 現在會以下列方式顯示 Visual Basic：

    [!code-xaml[ExpenseIt#6_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    和如下所示C#：

    [!code-xaml[ExpenseIt#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

1. 開啟*mainwindow.xaml*。

1. 將屬性加入<xref:System.Windows.Navigation.NavigationWindow>至專案，並將其設定為`ExpenseItHome.xaml`""。 <xref:System.Windows.Navigation.NavigationWindow.Source%2A>

    這會設定 *`ExpenseItHome.xaml`* 是第一頁開啟 應用程式啟動時。 

    Visual Basic 中的 XAML 範例：

    [!code-xaml[ExpenseIt#7_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    在 C#:

    [!code-xaml[ExpenseIt#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > 您也可以在 [**屬性**] 視窗的 [**其他**] 分類中設定 [**來源**] 屬性。
   >
   > ![屬性視窗中的來源屬性](./media/properties-source.png)

1. 將另一個新的 WPF 頁面加入至專案，並將它命名為*expensereportpage.xaml。 xaml*：：

   1. 在 [**方案總管] 中**，以滑鼠右鍵按一下 **`ExpenseIt`** 專案節點，然後選擇**新增** > **頁面**。

   1. 在 [**加入新專案**] 對話方塊中，選取 [**頁面（WPF）** ] 範本。 輸入名稱**expensereportpage.xaml**，然後選取 [**新增**]。

    此頁面會顯示在所選取之人員的費用報表 **`ExpenseItHome`** 頁面。

1. 開啟 *ExpenseReportPage.xaml*。

1. 將設定`ExpenseIt - View Expense`為 ""。 <xref:System.Windows.Controls.Page.Title%2A>

1. `DesignWidth`將設定`DesignHeight`為350圖元，並將設為500圖元。 

    *Expensereportpage.xaml*現在在 Visual Basic 中看起來會像下面這樣：

    [!code-xaml[ExpenseIt#4_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    和如下所示C#：

    [!code-xaml[ExpenseIt#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

1. 開啟*expenseithome.xaml.vb*和*expensereportpage.xaml*，或*ExpenseItHome.xaml.cs*和*ExpenseReportPage.xaml.cs*。

    當您建立新的分頁檔時，Visual Studio 會自動建立其程式*代碼後*置檔案。 這些程式碼後置檔案會處理用於回應使用者輸入的邏輯。

    您的程式碼應該看起來如下所示 **`ExpenseItHome`** :

    [!code-csharp[ExpenseIt#2_5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]

    [!code-vb[ExpenseIt#2_5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    **Expensereportpage.xaml**的和如下所示：

    [!code-csharp[ExpenseIt#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]

    [!code-vb[ExpenseIt#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

1. 將名為 [*浮水印 .png* ] 的影像加入至專案。 您可以建立自己的映射、從範例程式碼複製檔案，或從[microsoft/WPF 範例](https://raw.githubusercontent.com/microsoft/WPF-Samples/master/Getting%20Started/WalkthroughFirstWPFApp/csharp/watermark.png)GitHub 存放庫取得。

    1. 以滑鼠右鍵按一下專案節點，然後選取 [**加入** > **現有專案**]，或按**Shift** + **Alt** + **A**。

    2. 在 [**加入現有專案**] 對話方塊中，將檔案篩選器設為 [**所有**檔案] 或 [**影像檔**]，流覽至您要使用的影像檔案，然後選取 [**新增**]。

## <a name="build-and-run-the-application"></a>建立和執行應用程式

1. 若要建立並執行應用程式，請按**F5**或從 [**調試**程式] 功能表中選取 [**開始調試**]。

    下圖顯示具有<xref:System.Windows.Navigation.NavigationWindow>下列按鈕的應用程式：

    ![應用程式建立並執行之後。](./media/walkthrough-my-first-wpf-desktop-application/build-run-application.png)

2. 關閉應用程式以返回 Visual Studio。

## <a name="create-the-layout"></a>建立版面配置

版面配置提供排序的方式來放置 UI 元素，並在調整 UI 大小時，管理這些元素的大小和位置。 您通常會建立具有下列其中一個版面配置控制項的版面配置：

- <xref:System.Windows.Controls.Canvas>-定義一個區域，您可以在其中使用相對於畫布區域的座標，明確地定位子專案。
- <xref:System.Windows.Controls.DockPanel>-定義可讓您以水準或垂直方式排列子專案的區域（相對於彼此）。
- <xref:System.Windows.Controls.Grid>-定義包含資料行和資料列的彈性方格區域。
- <xref:System.Windows.Controls.StackPanel>-將子項目排列成可水準或垂直方向的單一行。
- <xref:System.Windows.Controls.VirtualizingStackPanel>-在以水準或垂直方式導向的單一線條上排列和虛擬化內容。
- <xref:System.Windows.Controls.WrapPanel>-從左至右將子專案放在順序位置，將內容細分為包含方塊邊緣的下一行。 後續的順序會依方向屬性的值，從上到下或由右至左進行排序。

這些版面配置控制項都支援其子項目的特定版面配置類型。 `ExpenseIt`頁面可以調整大小，而且每個頁面都有與其他元素一起水準和垂直排列的元素。 在此範例中， <xref:System.Windows.Controls.Grid>是用來做為應用程式的 layout 元素。

> [!TIP]
> 如需<xref:System.Windows.Controls.Panel>元素的詳細資訊，請參閱[面板總覽](../controls/panels-overview.md)。 如需版面配置的詳細資訊，請參閱[版面](../advanced/layout.md)配置。

在本節中，您建立單欄資料表具有三個資料列和 10 個像素邊界藉由新增資料行和資料列定義，以<xref:System.Windows.Controls.Grid>中 *`ExpenseItHome.xaml`* 。

1. 在 *`ExpenseItHome.xaml`* 中，將<xref:System.Windows.FrameworkElement.Margin%2A> <xref:System.Windows.Controls.Grid>元素上的屬性設定為 "10，0，10，10"，其對應于左、上、右和下邊界：

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > 您也可以在 [**屬性**] 視窗的 [**版面**配置] 分類底下設定**邊界**值：
   >
   > ![屬性視窗中的邊界值](./media/properties-margin.png)

2. 在<xref:System.Windows.Controls.Grid>標記之間加入下列 XAML，以建立資料列和資料行定義：

    [!code-xaml[ExpenseIt#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    兩個數據列的會設定<xref:System.Windows.GridLength.Auto%2A>為，這表示資料列會根據資料列中的內容進行大小調整。 <xref:System.Windows.Controls.RowDefinition.Height%2A> 預設值<xref:System.Windows.Controls.RowDefinition.Height%2A>為<xref:System.Windows.GridUnitType.Star> [調整大小]，表示資料列高度是可用空間的加權比例。 例如，如果兩個數據列都<xref:System.Windows.Controls.RowDefinition.Height%2A>有 "*" 的，則它們的高度為可用空間的一半。

    您<xref:System.Windows.Controls.Grid>現在應該包含下列 XAML：

    [!code-xaml[ExpenseIt#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a>加入控制項

在本節中，您將更新首頁 UI 以顯示人員清單，您可以在其中選取一個人員來顯示其費用報表。 控制項是可讓使用者與您應用程式互動的 UI 物件。 如需詳細資訊，請參閱 [控制項](../controls/index.md)。

若要建立此 UI，您會新增下列項目，來 *`ExpenseItHome.xaml`* :

- <xref:System.Windows.Controls.ListBox> （適用于人員清單）。
- <xref:System.Windows.Controls.Label> （適用于清單標頭）。
- A <xref:System.Windows.Controls.Button> （按一下即可查看清單中所選人員的費用報表）。

藉<xref:System.Windows.Controls.Grid> 由<xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType>設定附加屬性，每個控制項都會放在的資料列中。 如需附加屬性的詳細資訊，請參閱[附加屬性總覽](../advanced/attached-properties-overview.md)。

1. 在 *`ExpenseItHome.xaml`* 中，于<xref:System.Windows.Controls.Grid>標記之間的位置新增下列 XAML：

   [!code-xaml[ExpenseIt#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > 您也可以將控制項從 [**工具箱**] 視窗拖曳至 [設計] 視窗，然後在 [**屬性**] 視窗中設定其屬性，以建立它們。

2. 建置並執行應用程式。

    下圖顯示您所建立的控制項：

![ExpenseIt 範例螢幕擷取畫面，顯示名稱清單](./media/walkthrough-my-first-wpf-desktop-application/add-application-controls.png)

## <a name="add-an-image-and-a-title"></a>新增影像和標題

在本節中，您將使用影像和頁面標題來更新首頁 UI。

1. 在 *`ExpenseItHome.xaml`* 中，將另一個資料<xref:System.Windows.Controls.Grid.ColumnDefinitions%2A>行加入至<xref:System.Windows.Controls.ColumnDefinition.Width%2A> ，其固定為230圖元：

    [!code-xaml[ExpenseIt#11](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=52-55)]

2. 將另一個資料列<xref:System.Windows.Controls.Grid.RowDefinitions%2A>新增至，總計四個數據列：

    [!code-xaml[ExpenseIt#11b](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=57-62)]

3. 將控制項移至第二個數據行， <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType>方法是在三個控制項（框線、清單方塊和按鈕）中，將屬性設定為1。

4. 將每個控制項向下移動一個資料<xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType>列，方法是針對三個控制項（框線、清單方塊和按鈕）和 Border 元素的每一個值遞增1。

   這三個控制項的 XAML 現在看起來如下所示：

    [!code-xaml[ExpenseIt#12](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

5. 藉由在`<Grid>`和標記`</Grid>`之間的任何位置新增下列 XAML，將 屬性設定為浮水印.png圖像<xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType>檔：

    [!code-xaml[ExpenseIt#14](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

6. 在專案之前， <xref:System.Windows.Controls.Label>加入具有「查看費用報表」內容的。 <xref:System.Windows.Controls.Border> 此標籤是頁面的標題。

    [!code-xaml[ExpenseIt#13](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

7. 建置並執行應用程式。

下圖顯示您剛新增的結果：

![ExpenseIt 範例螢幕擷取畫面，其中顯示新的影像背景和頁面標題](./media/walkthrough-my-first-wpf-desktop-application/add-application-image-title.png)

## <a name="add-code-to-handle-events"></a>新增程式碼來處理事件

1. 在 *`ExpenseItHome.xaml`* 中， <xref:System.Windows.Controls.Primitives.ButtonBase.Click>將事件處理常式新增<xref:System.Windows.Controls.Button>至元素。 如需詳細資訊，請參閱[如何：建立簡單的事件處理](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100))程式。

    [!code-xaml[ExpenseIt#15](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

2. 開啟 *`ExpenseItHome.xaml.vb`* 或是 *`ExpenseItHome.xaml.cs`* 。

3. 將下列程式碼新增至`ExpenseItHome`類別，以新增按鈕 click 事件處理常式。 事件處理常式會開啟 [ **expensereportpage.xaml** ] 頁面。

    [!code-csharp[ExpenseIt#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a>建立 Expensereportpage.xaml 的 UI

*ExpenseReportPage.xaml*上選取的人員顯示的經費支出報表 **`ExpenseItHome`** 頁面。 在本節中，您將建立**expensereportpage.xaml**的 UI。 您也會將背景和填滿色彩新增至各種 UI 元素。

1. 開啟 *ExpenseReportPage.xaml*。

2. 在<xref:System.Windows.Controls.Grid>標記之間加入下列 XAML：

    [!code-xaml[ExpenseIt#17](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    此 UI 很類似 *`ExpenseItHome.xaml`* ，但報表資料會顯示在<xref:System.Windows.Controls.DataGrid>。

3. 建置並執行應用程式。

4. 選取 [ **View** ] \ （編輯 \）按鈕。

    報表頁面隨即出現。 另請注意，[上一頁] 瀏覽按鈕已啟用。

下圖顯示新增至*expensereportpage.xaml*的 UI 元素。

![ExpenseIt 範例螢幕擷取畫面，其中顯示剛剛為 Expensereportpage.xaml 建立的 UI。](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

## <a name="style-controls"></a>樣式控制項

針對 UI 中相同類型的所有元素，各種元素的外觀通常都相同。 UI 會使用[樣式](../controls/styling-and-templating.md)，讓多個元素的外觀可重複使用。 樣式的重複利用有助於簡化 XAML 的建立和管理。 本節會將先前步驟中定義的個別元素屬性 (Attribute) 取代為樣式。

1. 開啟 app.xaml 或*App.xaml* *應用程式*。

2. 在<xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>標記之間加入下列 XAML：

    [!code-xaml[ExpenseIt#18](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    這個 XAML 會加入下列樣式：

    - `headerTextStyle`：設定頁面標題<xref:System.Windows.Controls.Label>的格式。

    - `labelStyle`：設定控制項的<xref:System.Windows.Controls.Label>格式。

    - `columnHeaderStyle`：以格式化<xref:System.Windows.Controls.Primitives.DataGridColumnHeader>。

    - `listHeaderStyle`：格式化清單標頭<xref:System.Windows.Controls.Border>控制項。

    - `listHeaderTextStyle`：以格式化清單標頭<xref:System.Windows.Controls.Label>。

    - `buttonStyle`：要格式化的<xref:System.Windows.Controls.Button>。 `ExpenseItHome.xaml`

    請注意，樣式是<xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>屬性元素的資源和子系。 在這裡，樣式會套用至應用程式中的所有元素。 如需在 .NET 應用程式中使用資源的範例，請參閱[使用應用程式資源](../advanced/how-to-use-application-resources.md)。

3. 在 *`ExpenseItHome.xaml`* 中，以下列 XAML <xref:System.Windows.Controls.Grid>取代元素之間的所有內容：

    [!code-xaml[ExpenseIt#19](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    套用樣式會移除並取代諸如 <xref:System.Windows.VerticalAlignment> 和 <xref:System.Windows.Media.FontFamily> 這類會定義每個控制項外觀的屬性。 例如， `headerTextStyle`會套用至「查看費用<xref:System.Windows.Controls.Label>報表」。

4. 開啟 *ExpenseReportPage.xaml*。

5. 以下列 XAML 取代<xref:System.Windows.Controls.Grid>元素之間的所有內容：

    [!code-xaml[ExpenseIt#20](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    這個 XAML 會將樣式加入<xref:System.Windows.Controls.Label>至<xref:System.Windows.Controls.Border>和元素。

6. 建置並執行應用程式。 視窗外觀與先前相同。

    ![使用與上一節相同的外觀，ExpenseIt 範例螢幕擷取畫面。](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

7. 關閉應用程式以返回 Visual Studio。

## <a name="bind-data-to-a-control"></a>將資料系結至控制項

在本節中，您將建立系結至各種控制項的 XML 資料。

1. 中 *`ExpenseItHome.xaml`* ，在開啟之後<xref:System.Windows.Controls.Grid>項目，加入下列 XAML 來建立<xref:System.Windows.Data.XmlDataProvider>包含的每個人資料：

    [!code-xaml[ExpenseIt#23](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,16-40,49)]

    資料會建立為<xref:System.Windows.Controls.Grid>資源。 一般來說，這項資料會載入為檔案，但為了簡單起見，會以內嵌方式加入資料。

2. 在專案中，加入下列`<xref:System.Windows.DataTemplate>`專案，此專案會定義如何`<XmlDataProvider>`在的專案之後<xref:System.Windows.Controls.ListBox>顯示中的資料： `<Grid.Resources>`

    [!code-xaml[ExpenseIt#24](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,43-46,49)]

    如需資料範本的詳細資訊，請參閱[資料範本化總覽](../data/data-templating-overview.md)。

3. 以下列 XAML <xref:System.Windows.Controls.ListBox>取代現有的：

    [!code-xaml[ExpenseIt#25](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    這個 XAML <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>會將的屬性<xref:System.Windows.Controls.ListBox>系結至資料來源，並套用資料範本做為<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>。

## <a name="connect-data-to-controls"></a>將資料連線至控制項

接下來，您要在其中加入程式碼，以擷取名稱上選取 **`ExpenseItHome`** 頁面上，並將它傳遞給建構函式**ExpenseReportPage**。 **Expensereportpage.xaml**會使用傳遞的專案來設定其資料內容，這就是*expensereportpage.xaml*中定義的控制項。

1. 開啟 *ExpenseReportPage.xaml.vb* 或 *ExpenseReportPage.xaml.cs*。

2. 加入一個可接受物件的建構函式，如此您就可以傳遞選取之人員的費用報表資料。

    [!code-csharp[ExpenseIt#26](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. 開啟 *`ExpenseItHome.xaml.vb`* 或是 *`ExpenseItHome.xaml.cs`* 。

4. <xref:System.Windows.Controls.Primitives.ButtonBase.Click>變更事件處理常式，以呼叫新的函式，以傳遞所選人員的費用報表資料。

    [!code-csharp[ExpenseIt#27](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a>使用資料範本的樣式資料

在本節中，您將使用資料範本來更新資料系結清單中每個專案的 UI。

1. 開啟 *ExpenseReportPage.xaml*。

2. 將「名稱」和「部門<xref:System.Windows.Controls.Label> 」元素的內容系結至適當的資料來源屬性。 如需資料系結的詳細資訊，請參閱資料系結[總覽](../data/data-binding-overview.md)。

    [!code-xaml[ExpenseIt#31](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. 在開啟<xref:System.Windows.Controls.Grid>的專案之後，新增下列資料範本，以定義如何顯示費用報表資料：

    [!code-xaml[ExpenseIt#30](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. 以元素底下的<xref:System.Windows.Controls.DataGridTemplateColumn> 元素取代，並將範本套用至這些專案。<xref:System.Windows.Controls.DataGridTextColumn> <xref:System.Windows.Controls.DataGrid>

    [!code-xaml[ExpenseIt#32](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. 建置並執行應用程式。

6. 選取人員，然後選取 [ **View** ] \ （編輯 \）按鈕。

下圖顯示`ExpenseIt`應用程式的兩個頁面，其中已套用控制項、配置、樣式、資料系結和資料範本：

![應用程式的兩個頁面會顯示 [名稱] 清單和費用報表。](./media/walkthrough-my-first-wpf-desktop-application/application-data-templates.png)

> [!NOTE]
> 這個範例會示範 WPF 的特定功能，並不會遵循安全性、當地語系化和協助工具等專案的所有最佳作法。 如需 WPF 和 .NET 應用程式開發最佳作法的完整涵蓋範圍，請參閱下列主題：
>
> - [協助工具選項](../../ui-automation/accessibility-best-practices.md)
> - [Security](../security-wpf.md)
> - [WPF 全球化和當地語系化](../advanced/wpf-globalization-and-localization-overview.md)
> - [WPF 效能](../advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a>後續步驟

在本逐步解說中，您已瞭解使用 Windows Presentation Foundation （WPF）來建立 UI 的數種技術。 您現在應該對資料系結 .NET 應用程式的建立區塊有基本瞭解。 如需 WPF 架構和程式設計模型的詳細資訊，請參閱下列主題：

- [WPF 架構](../advanced/wpf-architecture.md)
- [XAML 概觀 (WPF)](../advanced/xaml-overview-wpf.md)
- [相依性屬性總覽](../advanced/dependency-properties-overview.md)
- [版面配置](../advanced/layout.md)

如需建立應用程式的詳細資訊，請參閱下列主題：

- [應用程式開發](../app-development/index.md)
- [控制項](../controls/index.md)
- [資料繫結概觀](../data/data-binding-overview.md)
- [圖形和多媒體](../graphics-multimedia/index.md)
- [WPF 中的文件](../advanced/documents-in-wpf.md)

## <a name="see-also"></a>另請參閱

- [面板總覽](../controls/panels-overview.md)
- [資料範本化總覽](../data/data-templating-overview.md)
- [建立 WPF 應用程式](../app-development/building-a-wpf-application-wpf.md)
- [樣式和範本](../controls/styles-and-templates.md)

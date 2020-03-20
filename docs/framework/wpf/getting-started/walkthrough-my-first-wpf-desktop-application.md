---
title: 在 Visual Studio 2019 - .NET 框架中創建您的第一個 WPF 應用
titleSuffix: ''
ms.date: 09/06/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting started [WPF], WPF
- WPF [WPF], getting started
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
ms.topic: tutorial
ms.custom: mvc,vs-dotnet
ms.openlocfilehash: 65b6fe31e86380162e90820c2cf118a9d1b96b4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186591"
---
# <a name="tutorial-create-your-first-wpf-application-in-visual-studio-2019"></a>教程：在 Visual Studio 2019 中創建您的第一個 WPF 應用程式

本文介紹如何開發 Windows 演示文稿基礎 （WPF） 桌面應用程式，該應用程式包含大多數 WPF 應用程式共有的元素：可擴展的應用程式標記語言 （XAML） 標記、代碼後面、應用程式定義、控制項、佈局、資料繫結和樣式。 要開發該應用程式，您將使用視覺化工作室。

在本教學課程中，您會了解如何：
> [!div class="checklist"]
>
> - 創建 WPF 專案。
> - 使用 XAML 設計應用程式的使用者介面 （UI） 的外觀。
> - 編寫代碼以生成應用程式的行為。
> - 創建應用程式定義來管理應用程式。
> - 添加控制項並創建佈局以組成應用程式 UI。
> - 在整個應用程式的 UI 中創建一致外觀的樣式。
> - 將 UI 綁定到資料，以便從資料中填充 UI 並保持資料和 UI 同步。

在本教程結束時，您將構建一個獨立的 Windows 應用程式，允許使用者查看所選人員的費用報告。 該應用程式由託管在瀏覽器樣式視窗中的多個 WPF 頁面組成。

> [!TIP]
> 本教程中使用的示例代碼可用於[教程 WPF 應用示例代碼](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp)中的 Visual Basic 和 C#。
>
> 您可以使用此頁面頂部的語言選擇器在 C# 和 Visual Basic 之間切換示例代碼的代碼語言。

## <a name="prerequisites"></a>必要條件

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)安裝 **.NET 桌面開發**工作負載。

   有關安裝最新版本的視覺化工作室的詳細資訊，請參閱[安裝視覺化工作室](/visualstudio/install/install-visual-studio)。

## <a name="create-the-application-project"></a>創建應用程式專案

第一步是創建應用程式基礎結構，其中包括應用程式定義、兩頁和一個映射。

1. 在名為**`ExpenseIt`**"可視基本"或"視覺化 C#的視覺化 C# 中創建新的 WPF 應用程式專案：

   1. 打開視覺化工作室，在"**開始"** 功能表下選擇 **"創建新專案**"。

      將打開"**創建新專案**"對話方塊。

   2. 在 **"語言**"下拉清單中，選擇**C#** 或**視覺化基本**。

   3. 選擇**WPF 應用 （.NET 框架）** 範本，然後選擇 **"下一步**"。

      ![創建新專案對話方塊](./media/walkthrough-my-first-wpf-desktop-application/create-new-project-dialog.png)

      將打開"**配置新專案**"對話方塊。

   4. 輸入專案名稱**`ExpenseIt`**，然後選擇 **"創建**"。

      ![配置新專案對話方塊](./media/walkthrough-my-first-wpf-desktop-application/configure-new-project-dialog.png)

      Visual Studio 創建專案並打開名為**MainWindow.xaml**的預設應用程式視窗的設計器。

2. 打開*應用程式.xaml（* 視覺基本）或*App.xaml* （C#）。

    此 XAML 檔定義 WPF 應用程式和任何應用程式資源。 您還可以使用此檔指定 UI，在本例中*為 MainWindow.xaml，* 在應用程式啟動時自動顯示。

    您的 XAML 在視覺化基礎知識中應如下所示：

    [!code-xaml[ExpenseIt#1_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    和以下 C#：

    [!code-xaml[ExpenseIt#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. 打開*主視窗.xaml*。

    此 XAML 檔是應用程式的主視窗，並顯示在頁面中創建的內容。 類<xref:System.Windows.Window>定義視窗的屬性，如其標題、大小或圖示，並處理事件，如關閉或隱藏。

4. 將<xref:System.Windows.Window>元素更改為 ，<xref:System.Windows.Navigation.NavigationWindow>如以下 XAML 所示：

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   此應用根據使用者輸入導航到不同的內容。 這就是為什麼需要將主要<xref:System.Windows.Window>需要更改為 。 <xref:System.Windows.Navigation.NavigationWindow> <xref:System.Windows.Navigation.NavigationWindow>繼承<xref:System.Windows.Window>的所有屬性。 XAML<xref:System.Windows.Navigation.NavigationWindow>檔中的元素創建類的<xref:System.Windows.Navigation.NavigationWindow>實例。 有關詳細資訊，請參閱[導航概述](../app-development/navigation-overview.md)。

5. 從<xref:System.Windows.Navigation.NavigationWindow>標記<xref:System.Windows.Controls.Grid>之間刪除元素。

6. 更改<xref:System.Windows.Navigation.NavigationWindow>元素的 XAML 代碼中的以下屬性：

    - 將<xref:System.Windows.Window.Title%2A>屬性設置為""。`ExpenseIt`

    - 將<xref:System.Windows.FrameworkElement.Height%2A>屬性設置為 350 圖元。

    - 將<xref:System.Windows.FrameworkElement.Width%2A>屬性設置為 500 圖元。

    對於視覺化基本版，您的 XAML 應如下所示：

    [!code-xaml[ExpenseIt#2_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    與以下 C# 類似：

    [!code-xaml[ExpenseIt#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

7. 打開*主視窗.xaml.vb*或*MainWindow.xaml.cs*。

    此檔是一個代碼背後的檔，其中包含用於處理*MainWindow.xaml*中聲明的事件的代碼。 這個檔案包含 XAML 中定義之視窗的部分類別。

8. 如果使用 C#，則更改從 派生`MainWindow`的<xref:System.Windows.Navigation.NavigationWindow>類。 （在視覺化基本版中，當您在 XAML 中更改視窗時，會自動發生這種情況。您的 C# 代碼現在應如下所示：

   [!code-csharp[ExpenseIt#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/MainWindow.xaml.cs?highlight=21)]

## <a name="add-files-to-the-application"></a>將檔添加到應用程式

在本節中，您要在應用程式中加入兩頁網頁和一個影像。

1. 向專案添加新頁面，並命名為*`ExpenseItHome.xaml`*：

   1. 在**解決方案資源管理器****`ExpenseIt`** 中，按右鍵專案節點並選擇 **"添加** > **頁面**"。

   1. 在"**添加新專案"** 對話方塊中，已選擇**頁面 （WPF）** 範本。 輸入名稱**`ExpenseItHome`**，然後選擇 **"添加**"。

    此頁是應用程式啟動時顯示的第一頁。 它將顯示要從中選擇的人員清單，以顯示其支出報表。

1. 打開*`ExpenseItHome.xaml`*。

1. 將<xref:System.Windows.Controls.Page.Title%2A>設置為""。`ExpenseIt - Home`

1. 將`DesignHeight`設置為 350 圖元，`DesignWidth`將 設置為 500 圖元。

    XAML 現在顯示如下視覺基礎：

    [!code-xaml[ExpenseIt#6_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    與以下 C# 類似：

    [!code-xaml[ExpenseIt#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

1. 打開*主視窗.xaml*。

1. 將屬性<xref:System.Windows.Navigation.NavigationWindow.Source%2A>添加到元素並將其<xref:System.Windows.Navigation.NavigationWindow>設置為""。`ExpenseItHome.xaml`

    這將集*`ExpenseItHome.xaml`* 為應用程式啟動時打開的第一頁。

    視覺化基礎知識中的 XAML 示例：

    [!code-xaml[ExpenseIt#7_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    在 C# 中：

    [!code-xaml[ExpenseIt#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > 您還可以在 **"屬性"** 視窗的 **"雜項**"類別中設置 **"源**"屬性。
   >
   > ![屬性視窗中的源屬性](./media/properties-source.png)

1. 向專案添加另一個新 WPF 頁面，並將其命名為 *"費用報告頁.xaml：：*

   1. 在**解決方案資源管理器****`ExpenseIt`** 中，按右鍵專案節點並選擇 **"添加** > **頁面**"。

   1. 在"**添加新專案"** 對話方塊中，選擇**頁面 （WPF）** 範本。 輸入名稱 **"支出報告頁**"，然後選擇 **"添加**"。

    此頁將顯示**`ExpenseItHome`** 頁面上所選人員的費用報表。

1. 打開*費用報告頁.xaml*。

1. 將<xref:System.Windows.Controls.Page.Title%2A>設置為""。`ExpenseIt - View Expense`

1. 將`DesignHeight`設置為 350 圖元，`DesignWidth`將 設置為 500 圖元。

    *支出報告頁.xaml*現在在視覺化基礎知識中如下所示：

    [!code-xaml[ExpenseIt#4_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    和以下 C#：

    [!code-xaml[ExpenseIt#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

1. 打開*費用它Home.xaml.vb*和*費用報告頁.xaml.vb，* 或*ExpenseItHome.xaml.cs*和*ExpenseReportPage.xaml.cs。*

    創建新的 Page 檔時，Visual Studio 會自動創建其*代碼背後的*檔。 這些程式碼後置檔案會處理用於回應使用者輸入的邏輯。

    對於 ： 的代碼應如下所示**`ExpenseItHome`**：

    [!code-csharp[ExpenseIt#2_5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]

    [!code-vb[ExpenseIt#2_5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    和下面的**費用報告頁**：

    [!code-csharp[ExpenseIt#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]

    [!code-vb[ExpenseIt#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

1. 向專案添加名為*浮水印.png*的圖像。 您可以創建自己的映射、從示例代碼複製檔或從[Microsoft/WPF-示例](https://raw.githubusercontent.com/microsoft/WPF-Samples/master/Getting%20Started/WalkthroughFirstWPFApp/csharp/watermark.png)GitHub 存儲庫獲取該檔。

    1. 按右鍵專案節點並選擇"**添加** > **現有專案**"，或按 **"移動**+**Alt**+**A**"。

    2. 在"**添加現有專案"** 對話方塊中，將檔篩選器設置為 **"所有檔**"或 **"影像檔**"，流覽到要使用的影像檔，然後選擇"**添加**"。

## <a name="build-and-run-the-application"></a>建置並執行應用程式

1. 要生成和運行應用程式，請按**F5**或從**調試**功能表中選擇 **"開始調試**"。

    下圖顯示了帶有<xref:System.Windows.Navigation.NavigationWindow>按鈕的應用程式：

    ![生成並運行應用程式後。](./media/walkthrough-my-first-wpf-desktop-application/build-run-application.png)

2. 關閉應用程式以返回到視覺化工作室。

## <a name="create-the-layout"></a>創建佈局

佈局提供了放置 UI 元素的有序方式，並在調整 UI 大小時管理這些元素的大小和位置。 您通常會建立具有下列其中一個版面配置控制項的版面配置：

- <xref:System.Windows.Controls.Canvas>- 定義一個區域，您可以在其中使用與"畫布"區域相關的座標顯式定位子項目。
- <xref:System.Windows.Controls.DockPanel>- 定義一個區域，您可以在其中水準或垂直排列子項目，彼此相對。
- <xref:System.Windows.Controls.Grid>- 定義由列和行組成的靈活網格區域。
- <xref:System.Windows.Controls.StackPanel>- 將子項目排列成一條可以水準或垂直方向的直線。
- <xref:System.Windows.Controls.VirtualizingStackPanel>- 在水準或垂直方向的一條線上排列和虛擬化內容。
- <xref:System.Windows.Controls.WrapPanel>- 將子項目從左向右定位在順序位置，將內容分解到包含框邊緣的下一行。 後續排序按順序從上到下或從右向左進行，具體取決於方向屬性的值。

每個佈局控制項都支援其子項目的特定類型的佈局。 `ExpenseIt`頁面可以調整大小，並且每個頁面都有與其他元素一起水準和垂直排列的元素。 在此示例中，<xref:System.Windows.Controls.Grid>用作應用程式的佈局元素。

> [!TIP]
> 有關<xref:System.Windows.Controls.Panel>元素的詳細資訊，請參閱[面板概述](../controls/panels-overview.md)。 有關佈局的詳細資訊，請參閱[佈局](../advanced/layout.md)。

在本節中，通過將列和行定義添加到 in，<xref:System.Windows.Controls.Grid>*`ExpenseItHome.xaml`* 可以創建包含三行和 10 圖元邊距的單清單。

1. 在*`ExpenseItHome.xaml`* 中，<xref:System.Windows.FrameworkElement.Margin%2A>將元素的屬性<xref:System.Windows.Controls.Grid>設置為"10，0，10，10"，對應于左、上、右和下邊距：

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > 您還可以在"**屬性**"視窗中的 **"佈局"** 類別下設置 **"邊距**"值：
   >
   > ![屬性視窗中的邊距值](./media/properties-margin.png)

2. 在<xref:System.Windows.Controls.Grid>標記之間添加以下 XAML 以創建行和列定義：

    [!code-xaml[ExpenseIt#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    兩<xref:System.Windows.Controls.RowDefinition.Height%2A>行的 設置為<xref:System.Windows.GridLength.Auto%2A>，這意味著行的大小基於行中的內容。 預設值<xref:System.Windows.Controls.RowDefinition.Height%2A>為<xref:System.Windows.GridUnitType.Star>大小調整，這意味著行高度是可用空間的加權比例。 例如，如果兩行各有一個<xref:System.Windows.Controls.RowDefinition.Height%2A>"*"，則它們每個行的高度是可用空間的一半。

    您<xref:System.Windows.Controls.Grid>現在應該包含以下 XAML：

    [!code-xaml[ExpenseIt#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a>新增控制項

在本節中，您將更新主頁 UI 以顯示人員清單，其中選擇一個人來顯示其支出報表。 控制項是可讓使用者與您應用程式互動的 UI 物件。 有關詳細資訊，請參閱[控制項](../controls/index.md)。

要創建此 UI，您將將以下元素添加到*`ExpenseItHome.xaml`*：

- A（<xref:System.Windows.Controls.ListBox>用於人員清單）。
- A（<xref:System.Windows.Controls.Label>對於清單標頭）。
- （<xref:System.Windows.Controls.Button>按一下以查看清單中所選人員的支出報表）。

通過設置附加屬性，將每個控制項放置在<xref:System.Windows.Controls.Grid>的一<xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType>行中。 有關附加屬性的詳細資訊，請參閱[附加屬性概述](../advanced/attached-properties-overview.md)。

1. 在*`ExpenseItHome.xaml`* 中，在<xref:System.Windows.Controls.Grid>標記之間添加以下 XAML：

   [!code-xaml[ExpenseIt#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > 還可以通過將控制項從 **"工具箱"** 視窗拖動到設計視窗，然後在 **"屬性"** 視窗中設置其屬性來創建控制項。

2. 建置並執行應用程式。

    下圖顯示了您創建的控制項：

![支出它示例螢幕截圖顯示名稱清單](./media/walkthrough-my-first-wpf-desktop-application/add-application-controls.png)

## <a name="add-an-image-and-a-title"></a>添加圖像和標題

在本節中，您將使用圖像和頁面標題更新主頁 UI。

1. 在*`ExpenseItHome.xaml`* 中，將另一<xref:System.Windows.Controls.Grid.ColumnDefinitions%2A>列添加到固定<xref:System.Windows.Controls.ColumnDefinition.Width%2A>為 230 圖元的 列：

    [!code-xaml[ExpenseIt#11](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=52-55)]

2. 向 添加<xref:System.Windows.Controls.Grid.RowDefinitions%2A>另一行，共四行：

    [!code-xaml[ExpenseIt#11b](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=57-62)]

3. 通過將<xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType>屬性設置為三個控制項（邊框、ListBox 和 Button）中每個控制項中的 1，將控制項移動到第二列。

4. 將每個控制項向下移動一行，將<xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType>三個控制項（邊框、ListBox 和 Button）和"邊框"元素的值分別增加 1。

   三個控制項的 XAML 現在如下所示：

    [!code-xaml[ExpenseIt#12](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

5. 通過將以下<xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType>XAML 添加到 和`<Grid>``</Grid>`標記之間的任意位置，將屬性設置為*浮水印.png*影像檔：

    [!code-xaml[ExpenseIt#14](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

6. 在元素<xref:System.Windows.Controls.Border>之前，添加包含<xref:System.Windows.Controls.Label>內容"查看支出報表"的 。 此標籤是頁面的標題。

    [!code-xaml[ExpenseIt#13](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

7. 建置並執行應用程式。

下圖顯示了您剛剛添加的內容的結果：

![費用它示例螢幕截圖，顯示新的圖像背景和頁面標題](./media/walkthrough-my-first-wpf-desktop-application/add-application-image-title.png)

## <a name="add-code-to-handle-events"></a>添加代碼以處理事件

1. 在*`ExpenseItHome.xaml`* 中，<xref:System.Windows.Controls.Primitives.ButtonBase.Click>向<xref:System.Windows.Controls.Button>元素添加事件處理常式。 有關詳細資訊，請參閱[操作：創建一個簡單的事件處理常式](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100))。

    [!code-xaml[ExpenseIt#15](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

2. 打開*`ExpenseItHome.xaml.vb`* 或*`ExpenseItHome.xaml.cs`*。

3. 將以下代碼添加到類以`ExpenseItHome`添加按鈕按一下事件處理常式。 事件處理常式將打開 **"支出報告頁"** 頁。

    [!code-csharp[ExpenseIt#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a>為支出報表頁創建 UI

*支出報告Page.xaml*顯示**`ExpenseItHome`** 頁面上所選人員的費用報表。 在本節中，您將為**支出報表頁**創建 UI。 您還將向各種 UI 元素添加背景和填充顏色。

1. 打開*費用報告頁.xaml*。

2. 在<xref:System.Windows.Controls.Grid>標記之間添加以下 XAML：

    [!code-xaml[ExpenseIt#17](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    此 UI 與*`ExpenseItHome.xaml`* 類似，但報表資料顯示在 中<xref:System.Windows.Controls.DataGrid>。

3. 建置並執行應用程式。

4. 選擇 **"查看**"按鈕。

    報表頁面隨即出現。 另請注意，後退導覽按鈕已啟用。

下圖顯示了添加到*支出報表Page.xaml*的 UI 元素。

![支出它示例螢幕截圖，顯示剛剛為支出報告頁創建的 UI。](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

## <a name="style-controls"></a>樣式控制項

對於 UI 中相同類型的所有元素，各種元素的外觀通常相同。 UI 使用[樣式](../controls/styling-and-templating.md)使外觀可跨多個元素重用。 樣式的再使用性有助於簡化 XAML 的創建和管理。 本節會將先前步驟中定義的個別元素屬性 (Attribute) 取代為樣式。

1. 打開*應用程式.xaml*或*App.xaml*。

2. 在<xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>標記之間添加以下 XAML：

    [!code-xaml[ExpenseIt#18](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    這個 XAML 會加入下列樣式：

    - `headerTextStyle`：格式化頁面標題 <xref:System.Windows.Controls.Label>。

    - `labelStyle`：格式化 <xref:System.Windows.Controls.Label> 控制項。

    - `columnHeaderStyle`：格式化 <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>。

    - `listHeaderStyle`：格式化清單標頭 <xref:System.Windows.Controls.Border> 控制項。

    - `listHeaderTextStyle`：格式化清單標頭<xref:System.Windows.Controls.Label>。

    - `buttonStyle`：格式化<xref:System.Windows.Controls.Button>on `ExpenseItHome.xaml`。

    請注意，樣式是屬性元素的資源和子項目<xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>。 在這裡，樣式會套用至應用程式中的所有元素。 有關在 .NET 應用中使用資源的示例，請參閱[使用應用程式資源](../advanced/how-to-use-application-resources.md)。

3. 在*`ExpenseItHome.xaml`* 中，將<xref:System.Windows.Controls.Grid>元素之間的所有內容替換為以下 XAML：

    [!code-xaml[ExpenseIt#19](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    套用樣式會移除並取代諸如 <xref:System.Windows.VerticalAlignment> 和 <xref:System.Windows.Media.FontFamily> 這類會定義每個控制項外觀的屬性。 例如，`headerTextStyle`應用於"查看費用報表"。 <xref:System.Windows.Controls.Label>

4. 打開*費用報告頁.xaml*。

5. 將<xref:System.Windows.Controls.Grid>元素之間的所有內容替換為以下 XAML：

    [!code-xaml[ExpenseIt#20](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    此 XAML 向<xref:System.Windows.Controls.Label>和<xref:System.Windows.Controls.Border>元素添加樣式。

6. 建置並執行應用程式。 視窗外觀與以前相同。

    ![支出它示例螢幕截圖的外觀與上一節相同。](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

7. 關閉應用程式以返回到視覺化工作室。

## <a name="bind-data-to-a-control"></a>將資料繫結到控制項

在本節中，您將創建綁定到各種控制項的 XML 資料。

1. 在*`ExpenseItHome.xaml`* 打開<xref:System.Windows.Controls.Grid>元素之後，添加以下 XAML 以創建包含每個人<xref:System.Windows.Data.XmlDataProvider>資料的 a：

    [!code-xaml[ExpenseIt#23](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,16-40,49)]

    資料作為<xref:System.Windows.Controls.Grid>資源創建。 通常，此資料將作為檔載入，但為了簡單起見，資料將內聯添加。

2. 在`<Grid.Resources>`元素中，添加以下`<xref:System.Windows.DataTemplate>`元素，該元素定義如何在<xref:System.Windows.Controls.ListBox>`<XmlDataProvider>`元素之後在 中顯示資料：

    [!code-xaml[ExpenseIt#24](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,43-46,49)]

    有關資料範本的詳細資訊，請參閱[資料範本概述](../data/data-templating-overview.md)。

3. 將現有<xref:System.Windows.Controls.ListBox>替換為以下 XAML：

    [!code-xaml[ExpenseIt#25](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    此 XAML 將<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>的屬性<xref:System.Windows.Controls.ListBox>綁定到資料來源，並將資料範本應用為 。 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>

## <a name="connect-data-to-controls"></a>將資料連線到控制項

接下來，您將添加代碼來檢索**`ExpenseItHome`** 頁面上選擇的名稱，並將其傳遞給**費用報表頁的**建構函式。 **支出報告頁**將其資料上下文與傳遞的項設置，這是*支出報告頁.xaml*中定義的控制項綁定到的。

1. 打開*費用報告頁.xaml.vb*或*ExpenseReportPage.xaml.cs*。

2. 加入一個可接受物件的建構函式，如此您就可以傳遞選取之人員的費用報表資料。

    [!code-csharp[ExpenseIt#26](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. 打開*`ExpenseItHome.xaml.vb`* 或*`ExpenseItHome.xaml.cs`*。

4. 更改<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件處理常式以調用新的建構函式，傳遞所選人員的費用報表資料。

    [!code-csharp[ExpenseIt#27](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a>使用資料範本對資料進行樣式設置資料

在本節中，您將使用資料繫結清單中的每個專案更新 UI。

1. 打開*費用報告頁.xaml*。

2. 將"名稱"和"部門"<xref:System.Windows.Controls.Label>元素的內容綁定到相應的資料來源屬性。 有關資料繫結的詳細資訊，請參閱[資料繫結概述](../../../desktop-wpf/data/data-binding-overview.md)。

    [!code-xaml[ExpenseIt#31](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. 在打開<xref:System.Windows.Controls.Grid>元素之後，添加以下資料範本，這些範本定義如何顯示支出報表資料：

    [!code-xaml[ExpenseIt#30](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. 將<xref:System.Windows.Controls.DataGridTextColumn>元素替換為元素<xref:System.Windows.Controls.DataGridTemplateColumn>，<xref:System.Windows.Controls.DataGrid>並將範本應用於它們。

    [!code-xaml[ExpenseIt#32](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. 建置並執行應用程式。

6. 選擇人員，然後選擇 **"查看**"按鈕。

下圖顯示了應用控制項、佈局、樣式`ExpenseIt`、資料繫結和資料範本的應用程式兩頁：

![顯示名稱清單和支出報表的應用兩個頁面。](./media/walkthrough-my-first-wpf-desktop-application/application-data-templates.png)

> [!NOTE]
> 此示例演示了 WPF 的特定功能，並且不遵循安全、當地語系化和可訪問性等所有最佳實踐。 有關 WPF 和 .NET 應用開發最佳實踐的全面覆蓋，請參閱以下主題：
>
> - [協助工具](../../ui-automation/accessibility-best-practices.md)
> - [安全性](../security-wpf.md)
> - [WPF 全球化和當地語系化](../advanced/wpf-globalization-and-localization-overview.md)
> - [WPF 性能](../advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a>後續步驟

在本演練中，您學習了使用 Windows 演示文稿基礎 （WPF） 創建 UI 的多種技術。 現在，您應該對資料繫結 .NET 應用的構建基塊有基本的瞭解。 如需 WPF 架構和程式設計模型的詳細資訊，請參閱下列主題：

- [WPF 架構](../advanced/wpf-architecture.md)
- [XAML 概述 （WPF）](../advanced/xaml-overview-wpf.md)
- [依賴項屬性概述](../advanced/dependency-properties-overview.md)
- [版面配置](../advanced/layout.md)

如需建立應用程式的詳細資訊，請參閱下列主題：

- [應用程式開發](../app-development/index.md)
- [控制](../controls/index.md)
- [資料繫結概觀](../../../desktop-wpf/data/data-binding-overview.md)
- [圖形與多媒體](../graphics-multimedia/index.md)
- [WPF 中的文件](../advanced/documents-in-wpf.md)

## <a name="see-also"></a>另請參閱

- [面板概述](../controls/panels-overview.md)
- [資料範本概述](../data/data-templating-overview.md)
- [構建 WPF 應用程式](../app-development/building-a-wpf-application-wpf.md)
- [樣式和範本](../controls/styles-and-templates.md)

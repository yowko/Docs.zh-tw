---
title: 逐步解說：繫結至混合應用程式中的資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- data binding [WPF interoperability]
ms.assetid: 18997e71-745a-4425-9c69-2cbce1d8669e
ms.openlocfilehash: ef5f14cdbecab8bc780cb7b2a642429970a25316
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972283"
---
# <a name="walkthrough-binding-to-data-in-hybrid-applications"></a>逐步解說：繫結至混合應用程式中的資料

無論您使用[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]或[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], 將資料來源系結至控制項, 都是為使用者提供基礎資料的存取權時不可或缺的。 本逐步解說會示範如何在包含[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]和[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]控制項的混合式應用程式中使用資料系結。

這個逐步解說中所述的工作包括：

- 建立專案。

- 定義資料範本。

- 指定表單版面配置。

- 指定資料繫結。

- 使用交互操作來顯示資料。

- 將資料來源新增至專案。

- 繫結至資料來源。

如需本逐步解說中所述工作的完整程式代碼清單, 請參閱[混合式應用程式中的資料](https://go.microsoft.com/fwlink/?LinkID=159983)系結範例。

完成後，您就會了解混合應用程式中的資料繫結功能。

## <a name="prerequisites"></a>必要條件

您需要下列元件才能完成此逐步解說：

- Visual Studio。

- 在 Microsoft SQL Server 上執行之 Northwind 範例資料庫的存取權。

## <a name="creating-the-project"></a>建立專案

### <a name="to-create-and-set-up-the-project"></a>建立並設定專案

1. 建立名為`WPFWithWFAndDatabinding`的 WPF 應用程式專案。

2. 在 [方案總管] 中，加入下列組件的參考。

    - WindowsFormsIntegration

    - System.Windows.Forms

3. 在中[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]開啟 mainwindow.xaml。

4. 在元素中, 新增下列[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]命名空間對應。 <xref:System.Windows.Window>

    ```xaml
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"
    ```

5. 藉由指派<xref:System.Windows.Controls.Grid> `mainGrid` 屬性來<xref:System.Windows.FrameworkElement.Name%2A>命名預設元素。

     [!code-xaml[WPFWithWFAndDatabinding#8](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#8)]

## <a name="defining-the-data-template"></a>定義資料範本

客戶的主要清單會顯示在<xref:System.Windows.Controls.ListBox>控制項中。 下列程式碼範例會定義<xref:System.Windows.DataTemplate>名為`ListItemsTemplate`的物件, 以控制<xref:System.Windows.Controls.ListBox>控制項的視覺化樹狀結構。 這<xref:System.Windows.DataTemplate>會指派<xref:System.Windows.Controls.ListBox>給控制項的<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>屬性。

### <a name="to-define-the-data-template"></a>定義資料範本

- 將下列 XAML 複製到<xref:System.Windows.Controls.Grid>元素的宣告中。

     [!code-xaml[WPFWithWFAndDatabinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#3)]

## <a name="specifying-the-form-layout"></a>指定表單版面配置

表單的版面配置定義具有三個資料列和三個資料行的格線。 <xref:System.Windows.Controls.Label>系統會提供控制項來識別 Customers 資料表中的每個資料行。

### <a name="to-set-up-the-grid-layout"></a>設定格線版面配置

- 將下列 XAML 複製到<xref:System.Windows.Controls.Grid>元素的宣告中。

     [!code-xaml[WPFWithWFAndDatabinding#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#4)]

### <a name="to-set-up-the-label-controls"></a>設定 Label 控制項

- 將下列 XAML 複製到<xref:System.Windows.Controls.Grid>元素的宣告中。

     [!code-xaml[WPFWithWFAndDatabinding#5](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#5)]

## <a name="specifying-data-bindings"></a>指定資料繫結

客戶的主要清單會顯示在<xref:System.Windows.Controls.ListBox>控制項中。 附加`ListItemsTemplate` `ContactName`會將控制項系結至資料庫中的欄位。 <xref:System.Windows.Controls.TextBlock>

每筆客戶記錄的詳細資料會顯示在<xref:System.Windows.Controls.TextBox>數個控制項中。

### <a name="to-specify-data-bindings"></a>指定資料繫結

- 將下列 XAML 複製到<xref:System.Windows.Controls.Grid>元素的宣告中。

     <xref:System.Windows.Data.Binding>類別會將控制項系結至資料庫<xref:System.Windows.Controls.TextBox>中的適當欄位。

     [!code-xaml[WPFWithWFAndDatabinding#6](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#6)]

## <a name="displaying-data-by-using-interoperation"></a>使用交互操作來顯示資料

對應至所選客戶的訂單會顯示在名<xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType>為`dataGridView1`的控制項中。 `dataGridView1`控制項系結至程式碼後置檔案中的資料來源。 控制項是這個[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項的父系。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>

### <a name="to-display-data-in-the-datagridview-control"></a>在 DataGridView 控制項中顯示資料

- 將下列 XAML 複製到<xref:System.Windows.Controls.Grid>元素的宣告中。

     [!code-xaml[WPFWithWFAndDatabinding#7](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#7)]

## <a name="adding-the-data-source-to-the-project"></a>將資料來源新增至專案

有了 Visual Studio, 您就可以輕鬆地將資料來源加入至您的專案。 此程序會將強型別的資料集新增至專案。 也會新增數個其他支援類別，例如每個所選擇資料表的資料表配置器。

### <a name="to-add-the-data-source"></a>若要新增資料來源

1. 從 [**資料**] 功能表中, 選取 [**加入新的資料來源**]。

2. 在 [**資料來源設定向導]** 中, 使用資料集建立與 Northwind 資料庫的連接。 如需詳細資訊，請參閱[如何：連接至資料庫](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fxk9yw1t(v=vs.120))中的資料。

3. 當**資料來源設定向導**提示您時, 請將連接字串儲存為`NorthwindConnectionString`。

4. 當系統提示您選擇資料庫物件時, 請選取`Customers`和`Orders`資料表, 並將產生的資料集`NorthwindDataSet`命名為。

## <a name="binding-to-the-data-source"></a>繫結至資料來源

<xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType>元件提供應用程式資料來源的統一介面。 繫結至資料來源是在程式碼後置檔案中進行實作。

### <a name="to-bind-to-the-data-source"></a>繫結至資料來源

1. 開啟程式碼後置檔案，命名為 MainWindow.xaml.vb 或 MainWindow.xaml.cs。

2. 將下列程式碼複製到`MainWindow`類別定義中。

     此程式碼會<xref:System.Windows.Forms.BindingSource>宣告連接至資料庫的元件和相關聯的 helper 類別。

     [!code-csharp[WPFWithWFAndDatabinding#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#11)]
     [!code-vb[WPFWithWFAndDatabinding#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#11)]

3. 將下列程式碼複製至建構函式。

     此程式碼會建立並<xref:System.Windows.Forms.BindingSource>初始化元件。

     [!code-csharp[WPFWithWFAndDatabinding#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#12)]
     [!code-vb[WPFWithWFAndDatabinding#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#12)]

4. 開啟 MainWindow.xaml。

5. 在設計檢視或 XAML 視圖中, 選取<xref:System.Windows.Window>元素。

6. 在 屬性視窗中, 按一下 **事件** 索引標籤。

7. <xref:System.Windows.FrameworkElement.Loaded>按兩下事件。

8. 將下列程式碼複製到<xref:System.Windows.FrameworkElement.Loaded>事件處理常式。

     此程式碼會<xref:System.Windows.Forms.BindingSource>將元件指派為數據內容, 並`Customers`填入`Orders`和介面卡物件。

     [!code-csharp[WPFWithWFAndDatabinding#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#13)]
     [!code-vb[WPFWithWFAndDatabinding#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#13)]

9. 將下列程式碼複製到`MainWindow`類別定義中。

     這個方法會處理<xref:System.Windows.Data.CollectionView.CurrentChanged>事件, 並更新資料系結的目前專案。

     [!code-csharp[WPFWithWFAndDatabinding#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#14)]
     [!code-vb[WPFWithWFAndDatabinding#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#14)]

10. 按 F5 鍵建置並執行應用程式。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [在 Visual Studio 中設計 XAML](/visualstudio/designers/designing-xaml-in-visual-studio)
- [混合式應用程式中的資料系結範例](https://go.microsoft.com/fwlink/?LinkID=159983)
- [逐步解說：在 WPF 中裝載 Windows Forms 複合控制項](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [逐步解說：在 Windows Forms 中裝載 WPF 複合控制項](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)

---
title: 如何：在 DataGrid 控制項中分組、排序和篩選資料
description: 瞭解如何將 Windows Presentation Foundation DataGrid 控制項系結至支援在 views 中分組、排序和篩選資料的 CollectionView。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], sort
- DataGrid [WPF], group
- DataGrid [WPF], filter
ms.assetid: 03345e85-89e3-4aec-9ed0-3b80759df770
ms.openlocfilehash: 072e5a104a91faa40bb54f2a3fc4ed6188e1112e
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167667"
---
# <a name="how-to-group-sort-and-filter-data-in-the-datagrid-control"></a>如何：在 DataGrid 控制項中分組、排序和篩選資料

透過 <xref:System.Windows.Controls.DataGrid> 分組、排序和篩選資料，以不同的方式來查看中的資料通常很有用。 若要在中分組、排序和篩選資料 <xref:System.Windows.Controls.DataGrid> ，您可以將它系結至 <xref:System.Windows.Data.CollectionView> 支援這些函數的。 然後，您可以在中使用資料， <xref:System.Windows.Data.CollectionView> 而不會影響基礎來源資料。 集合視圖中的變更會反映在 <xref:System.Windows.Controls.DataGrid> 使用者介面（UI）中。

<xref:System.Windows.Data.CollectionView>類別會針對實作為介面的資料來源，提供群組和排序功能 <xref:System.Collections.IEnumerable> 。 <xref:System.Windows.Data.CollectionViewSource>類別可讓您從 XAML 設定的屬性 <xref:System.Windows.Data.CollectionView> 。

在此範例中，物件的集合會系結 `Task` 至 <xref:System.Windows.Data.CollectionViewSource> 。 <xref:System.Windows.Data.CollectionViewSource>是用來做 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 為的 <xref:System.Windows.Controls.DataGrid> 。 群組、排序和篩選會在上執行， <xref:System.Windows.Data.CollectionViewSource> 並顯示在 UI 中 <xref:System.Windows.Controls.DataGrid> 。

![DataGrid 中的群組資料](././media/wpf-datagridgroups.png "WPF_DataGridGroups")DataGrid 中的群組資料

## <a name="using-a-collectionviewsource-as-an-itemssource"></a>使用 CollectionViewSource 做為 ItemsSource

若要對控制項中的資料進行分組、排序和篩選 <xref:System.Windows.Controls.DataGrid> ，您可以將系結 <xref:System.Windows.Controls.DataGrid> 至支援這些函式的 <xref:System.Windows.Data.CollectionView> 。 在此範例中， <xref:System.Windows.Controls.DataGrid> 會系結至為 <xref:System.Windows.Data.CollectionViewSource> 物件提供這些函式 <xref:System.Collections.Generic.List%601> 的 `Task` 。

### <a name="to-bind-a-datagrid-to-a-collectionviewsource"></a>將 DataGrid 系結至 CollectionViewSource

1. 建立可實作為介面的資料集合 <xref:System.Collections.IEnumerable> 。

    如果您使用 <xref:System.Collections.Generic.List%601> 來建立集合，您應該建立繼承自的新類別， <xref:System.Collections.Generic.List%601> 而不是具現化的實例 <xref:System.Collections.Generic.List%601> 。 這可讓您將資料系結至 XAML 中的集合。

    > [!NOTE]
    > 集合中的物件必須執行 <xref:System.ComponentModel.INotifyPropertyChanged> 已變更的介面和 <xref:System.ComponentModel.IEditableObject> 介面， <xref:System.Windows.Controls.DataGrid> 才能正確回應屬性變更和編輯。 如需詳細資訊，請參閱[實作屬性變更通知](../data/how-to-implement-property-change-notification.md)。

    [!code-csharp[DataGrid_GroupSortFilter#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#101)]
    [!code-vb[DataGrid_GroupSortFilter#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#101)]

2. 在 XAML 中，建立集合類別的實例，並設定[x：Key](../../../desktop-wpf/xaml-services/xkey-directive.md)指示詞。

3. 在 XAML 中，建立類別的實例 <xref:System.Windows.Data.CollectionViewSource> 、設定[x：Key](../../../desktop-wpf/xaml-services/xkey-directive.md)指示詞，並將集合類別的實例設定為 <xref:System.Windows.Data.CollectionViewSource.Source%2A> 。

    [!code-xaml[DataGrid_GroupSortFilter#201](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml#201)]

4. 建立類別的實例 <xref:System.Windows.Controls.DataGrid> ，並將 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 屬性設定為 <xref:System.Windows.Data.CollectionViewSource> 。

    [!code-xaml[DataGrid_GroupSortFilter#002](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#002)]

5. 若要 <xref:System.Windows.Data.CollectionViewSource> 從您的程式碼存取，請使用 <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> 方法來取得的參考 <xref:System.Windows.Data.CollectionViewSource> 。

    [!code-csharp[DataGrid_GroupSortFilter#102](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#102)]
    [!code-vb[DataGrid_GroupSortFilter#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#102)]

## <a name="grouping-items-in-a-datagrid"></a>群組 DataGrid 中的專案

若要指定專案在中的分組方式 <xref:System.Windows.Controls.DataGrid> ，您可以使用類型，將 <xref:System.Windows.Data.PropertyGroupDescription> 來源視圖中的專案分組。

### <a name="to-group-items-in-a-datagrid-using-xaml"></a>使用 XAML 將 DataGrid 中的專案分組

1. 建立 <xref:System.Windows.Data.PropertyGroupDescription> ，以指定要分組依據的屬性。 您可以在 XAML 或程式碼中指定屬性。

   1. 在 XAML 中，將設 <xref:System.Windows.Data.PropertyGroupDescription.PropertyName%2A> 為要分組依據的屬性名稱。

   2. 在程式碼中，將要分組的屬性名稱傳遞給此函式。

2. 將加入 <xref:System.Windows.Data.PropertyGroupDescription> 至 <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A?displayProperty=nameWithType> 集合。

3. 將的其他實例新增 <xref:System.Windows.Data.PropertyGroupDescription> 至 <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> 集合，以加入更多層級的群組。

    [!code-xaml[DataGrid_GroupSortFilter#012](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#012)]
    [!code-csharp[DataGrid_GroupSortFilter#112](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#112)]
    [!code-vb[DataGrid_GroupSortFilter#112](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#112)]

4. 若要移除群組，請 <xref:System.Windows.Data.PropertyGroupDescription> 從集合中移除 <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> 。

5. 若要移除所有群組，請呼叫 <xref:System.Collections.ObjectModel.Collection%601.Clear%2A> 集合的方法 <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> 。

    [!code-csharp[DataGrid_GroupSortFilter#114](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#114)]
    [!code-vb[DataGrid_GroupSortFilter#114](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#114)]

當專案在中分組時 <xref:System.Windows.Controls.DataGrid> ，您可以定義，以 <xref:System.Windows.Controls.GroupStyle> 指定每個群組的外觀。 您可以將 <xref:System.Windows.Controls.GroupStyle> 它新增至 DataGrid 的 <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> 集合來套用。 如果您有多個層級的群組，您可以將不同的樣式套用至每個群組層級。 樣式會依照其定義的順序套用。 例如，如果您定義兩個樣式，第一個會套用至最上層的資料列群組。 第二種樣式會套用到第二層級的所有資料列群組，並在較低的位置套用。 的 <xref:System.Windows.FrameworkElement.DataContext%2A> <xref:System.Windows.Controls.GroupStyle> 是 <xref:System.Windows.Data.CollectionViewGroup> 群組代表的。

### <a name="to-change-the-appearance-of-row-group-headers"></a>若要變更資料列群組標頭的外觀

1. 建立 <xref:System.Windows.Controls.GroupStyle> 定義資料列群組外觀的。

2. 將放在 <xref:System.Windows.Controls.GroupStyle> `<DataGrid.GroupStyle>` 標記內。

    [!code-xaml[DataGrid_GroupSortFilter#003](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#003)]

## <a name="sorting-items-in-a-datagrid"></a>排序 DataGrid 中的專案

若要指定專案在中的排序方式 <xref:System.Windows.Controls.DataGrid> ，您可以使用 <xref:System.ComponentModel.SortDescription> 類型來排序來源視圖中的專案。

### <a name="to-sort-items-in-a-datagrid"></a>排序 DataGrid 中的專案

1. 建立 <xref:System.ComponentModel.SortDescription> ，指定要排序的屬性。 您可以在 XAML 或程式碼中指定屬性。

    1. 在 XAML 中，將設定 <xref:System.ComponentModel.SortDescription.PropertyName%2A> 為要排序的屬性名稱。

    2. 在程式碼中，將屬性的名稱傳遞給排序依據，並將 <xref:System.ComponentModel.ListSortDirection> 設為。

2. 將加入 <xref:System.ComponentModel.SortDescription> 至 <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A?displayProperty=nameWithType> 集合。

3. 將的其他實例新增 <xref:System.ComponentModel.SortDescription> 至 <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A> 集合，以依其他屬性排序。

    [!code-xaml[DataGrid_GroupSortFilter#011](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#011)]
    [!code-csharp[DataGrid_GroupSortFilter#211](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml.cs#211)]
    [!code-vb[DataGrid_GroupSortFilter#211](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#211)]

## <a name="filtering-items-in-a-datagrid"></a>篩選 DataGrid 中的專案

若要使用來篩選中的專案 <xref:System.Windows.Controls.DataGrid> <xref:System.Windows.Data.CollectionViewSource> ，您可以在事件的處理常式中提供篩選邏輯 <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> 。

### <a name="to-filter-items-in-a-datagrid"></a>若要篩選 DataGrid 中的專案

1. 加入事件的處理常式 <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> 。

2. 在 <xref:System.Windows.Data.CollectionViewSource.Filter> 事件處理常式中，定義篩選邏輯。

    每次重新整理視圖時，就會套用此篩選。

    [!code-xaml[DataGrid_GroupSortFilter#013](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#013)]
    [!code-csharp[DataGrid_GroupSortFilter#113](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#113)]
    [!code-vb[DataGrid_GroupSortFilter#113](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#113)]

或者，您可以藉 <xref:System.Windows.Controls.DataGrid> 由建立提供篩選邏輯的方法，並設定要套用篩選的屬性，來篩選中的專案 <xref:System.Windows.Data.CollectionView.Filter%2A?displayProperty=nameWithType> 。 若要查看此方法的範例，請參閱[在視圖中篩選資料](../data/how-to-filter-data-in-a-view.md)。

## <a name="example"></a>範例

下列範例示範如何在中分組、排序和篩選 `Task` 資料， <xref:System.Windows.Data.CollectionViewSource> 並在中顯示已分組、已排序和已篩選的 `Task` 資料 <xref:System.Windows.Controls.DataGrid> 。 <xref:System.Windows.Data.CollectionViewSource>是用來做 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 為的 <xref:System.Windows.Controls.DataGrid> 。 群組、排序和篩選會在上執行， <xref:System.Windows.Data.CollectionViewSource> 並顯示在 UI 中 <xref:System.Windows.Controls.DataGrid> 。

若要測試此範例，您必須調整 DGGroupSortFilterExample 名稱以符合您的專案名稱。 如果您使用 Visual Basic，則必須將的類別名稱變更為 <xref:System.Windows.Window> 下列。

`<Window x:Class="MainWindow"`

[!code-xaml[DataGrid_GroupSortFilter#000](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#000)]
[!code-csharp[DataGrid_GroupSortFilter#100](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#100)]
[!code-vb[DataGrid_GroupSortFilter#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#100)]

## <a name="see-also"></a>另請參閱

- [資料系結總覽](../../../desktop-wpf/data/data-binding-overview.md)
- [建立並系結至 ObservableCollection](../data/how-to-create-and-bind-to-an-observablecollection.md)
- [篩選視圖中的資料](../data/how-to-filter-data-in-a-view.md)
- [排序視圖中的資料](../data/how-to-sort-data-in-a-view.md)
- [使用 XAML 中的視圖排序和分組資料](../data/how-to-sort-and-group-data-using-a-view-in-xaml.md)

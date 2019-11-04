---
title: 如何：在 DataGrid 控制項中分組、排序和篩選資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], sort
- DataGrid [WPF], group
- DataGrid [WPF], filter
ms.assetid: 03345e85-89e3-4aec-9ed0-3b80759df770
ms.openlocfilehash: 2632566b5b55ae641d2750e903bf94cdc681f8f8
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460234"
---
# <a name="how-to-group-sort-and-filter-data-in-the-datagrid-control"></a>如何：在 DataGrid 控制項中分組、排序和篩選資料

藉由分組、排序和篩選資料，以不同的方式來查看 <xref:System.Windows.Controls.DataGrid> 中的資料通常很有用。 若要對 <xref:System.Windows.Controls.DataGrid>中的資料進行分組、排序和篩選，您可以將它系結至支援這些函數的 <xref:System.Windows.Data.CollectionView>。 然後您可以使用 <xref:System.Windows.Data.CollectionView> 中的資料，而不會影響基礎來源資料。 集合視圖中的變更會反映在 <xref:System.Windows.Controls.DataGrid> 的使用者介面（UI）中。

<xref:System.Windows.Data.CollectionView> 類別會針對實 <xref:System.Collections.IEnumerable> 介面的資料來源，提供群組和排序功能。 <xref:System.Windows.Data.CollectionViewSource> 類別可讓您從 XAML 設定 <xref:System.Windows.Data.CollectionView> 的屬性。

在此範例中，`Task` 物件的集合會系結至 <xref:System.Windows.Data.CollectionViewSource>。 <xref:System.Windows.Data.CollectionViewSource> 可用來做為 <xref:System.Windows.Controls.DataGrid>的 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>。 分組、排序和篩選會在 <xref:System.Windows.Data.CollectionViewSource> 上執行，並顯示在 <xref:System.Windows.Controls.DataGrid> UI 中。

![DataGrid 中的群組資料](././media/wpf-datagridgroups.png "WPF_DataGridGroups")DataGrid 中的群組資料

## <a name="using-a-collectionviewsource-as-an-itemssource"></a>使用 CollectionViewSource 做為 ItemsSource

若要對 <xref:System.Windows.Controls.DataGrid> 控制項中的資料進行分組、排序和篩選，您可以將 <xref:System.Windows.Controls.DataGrid> 系結至支援這些函式的 <xref:System.Windows.Data.CollectionView>。 在此範例中，<xref:System.Windows.Controls.DataGrid> 系結至 <xref:System.Windows.Data.CollectionViewSource>，為 `Task` 物件 <xref:System.Collections.Generic.List%601> 提供這些函式。

### <a name="to-bind-a-datagrid-to-a-collectionviewsource"></a>將 DataGrid 系結至 CollectionViewSource

1. 建立可執行 <xref:System.Collections.IEnumerable> 介面的資料收集。

    如果您使用 <xref:System.Collections.Generic.List%601> 來建立集合，您應該建立繼承自 <xref:System.Collections.Generic.List%601> 的新類別，而不是具現化 <xref:System.Collections.Generic.List%601>的實例。 這可讓您將資料系結至 XAML 中的集合。

    > [!NOTE]
    > 集合中的物件必須實 <xref:System.ComponentModel.INotifyPropertyChanged> 變更的介面和 <xref:System.ComponentModel.IEditableObject> 介面，才能讓 <xref:System.Windows.Controls.DataGrid> 正確地回應屬性變更和編輯。 如需詳細資訊，請參閱[實作屬性變更通知](../data/how-to-implement-property-change-notification.md)。

    [!code-csharp[DataGrid_GroupSortFilter#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#101)]
    [!code-vb[DataGrid_GroupSortFilter#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#101)]

2. 在 XAML 中，建立集合類別的實例，並設定[x：Key](../../xaml-services/x-key-directive.md)指示詞。

3. 在 XAML 中，建立 <xref:System.Windows.Data.CollectionViewSource> 類別的實例、設定[x：Key](../../xaml-services/x-key-directive.md)指示詞，並將集合類別的實例設定為 <xref:System.Windows.Data.CollectionViewSource.Source%2A>。

    [!code-xaml[DataGrid_GroupSortFilter#201](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml#201)]

4. 建立 <xref:System.Windows.Controls.DataGrid> 類別的實例，並將 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 屬性設定為 <xref:System.Windows.Data.CollectionViewSource>。

    [!code-xaml[DataGrid_GroupSortFilter#002](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#002)]

5. 若要從您的程式碼存取 <xref:System.Windows.Data.CollectionViewSource>，請使用 <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> 方法來取得 <xref:System.Windows.Data.CollectionViewSource>的參考。

    [!code-csharp[DataGrid_GroupSortFilter#102](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#102)]
    [!code-vb[DataGrid_GroupSortFilter#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#102)]

## <a name="grouping-items-in-a-datagrid"></a>群組 DataGrid 中的專案

若要指定如何在 <xref:System.Windows.Controls.DataGrid>中分組專案，您可以使用 <xref:System.Windows.Data.PropertyGroupDescription> 類型，將來源視圖中的專案分組。

### <a name="to-group-items-in-a-datagrid-using-xaml"></a>使用 XAML 將 DataGrid 中的專案分組

1. 建立 <xref:System.Windows.Data.PropertyGroupDescription>，指定要分組依據的屬性。 您可以在 XAML 或程式碼中指定屬性。

   1. 在 XAML 中，將 <xref:System.Windows.Data.PropertyGroupDescription.PropertyName%2A> 設定為要分組依據的屬性名稱。

   2. 在程式碼中，將要分組的屬性名稱傳遞給此函式。

2. 將 <xref:System.Windows.Data.PropertyGroupDescription> 新增至 <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A?displayProperty=nameWithType> 集合。

3. 將 <xref:System.Windows.Data.PropertyGroupDescription> 的其他實例新增至 <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> 集合，以加入更多層級的群組。

    [!code-xaml[DataGrid_GroupSortFilter#012](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#012)]
    [!code-csharp[DataGrid_GroupSortFilter#112](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#112)]
    [!code-vb[DataGrid_GroupSortFilter#112](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#112)]

4. 若要移除群組，請從 <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> 集合中移除 <xref:System.Windows.Data.PropertyGroupDescription>。

5. 若要移除所有群組，請呼叫 <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> 集合的 <xref:System.Collections.ObjectModel.Collection%601.Clear%2A> 方法。

    [!code-csharp[DataGrid_GroupSortFilter#114](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#114)]
    [!code-vb[DataGrid_GroupSortFilter#114](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#114)]

當專案在 <xref:System.Windows.Controls.DataGrid>中分組時，您可以定義指定每個群組外觀的 <xref:System.Windows.Controls.GroupStyle>。 您可以藉由將 <xref:System.Windows.Controls.GroupStyle> 新增至 DataGrid 的 <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> 集合來套用。 如果您有多個層級的群組，您可以將不同的樣式套用至每個群組層級。 樣式會依照其定義的順序套用。 例如，如果您定義兩個樣式，第一個會套用至最上層的資料列群組。 第二種樣式會套用到第二層級的所有資料列群組，並在較低的位置套用。 <xref:System.Windows.Controls.GroupStyle> 的 <xref:System.Windows.FrameworkElement.DataContext%2A> 是群組所代表的 <xref:System.Windows.Data.CollectionViewGroup>。

### <a name="to-change-the-appearance-of-row-group-headers"></a>若要變更資料列群組標頭的外觀

1. 建立定義資料列群組外觀的 <xref:System.Windows.Controls.GroupStyle>。

2. 將 <xref:System.Windows.Controls.GroupStyle> 放在 `<DataGrid.GroupStyle>` 標記內。

    [!code-xaml[DataGrid_GroupSortFilter#003](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#003)]

## <a name="sorting-items-in-a-datagrid"></a>排序 DataGrid 中的專案

若要指定如何在 <xref:System.Windows.Controls.DataGrid>中排序專案，您可以使用 <xref:System.ComponentModel.SortDescription> 類型來排序來源視圖中的專案。

### <a name="to-sort-items-in-a-datagrid"></a>排序 DataGrid 中的專案

1. 建立指定排序依據之屬性的 <xref:System.ComponentModel.SortDescription>。 您可以在 XAML 或程式碼中指定屬性。

    1. 在 XAML 中，將 <xref:System.ComponentModel.SortDescription.PropertyName%2A> 設定為要排序的屬性名稱。

    2. 在程式碼中，傳遞要排序之屬性的名稱，並將 <xref:System.ComponentModel.ListSortDirection> 到該函式。

2. 將 <xref:System.ComponentModel.SortDescription> 新增至 <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A?displayProperty=nameWithType> 集合。

3. 將 <xref:System.ComponentModel.SortDescription> 的其他實例新增至 <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A> 集合，以依其他屬性排序。

    [!code-xaml[DataGrid_GroupSortFilter#011](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#011)]
    [!code-csharp[DataGrid_GroupSortFilter#211](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml.cs#211)]
    [!code-vb[DataGrid_GroupSortFilter#211](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#211)]

## <a name="filtering-items-in-a-datagrid"></a>篩選 DataGrid 中的專案

若要使用 <xref:System.Windows.Data.CollectionViewSource>來篩選 <xref:System.Windows.Controls.DataGrid> 中的專案，您可以在 <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> 事件的處理常式中提供篩選邏輯。

### <a name="to-filter-items-in-a-datagrid"></a>若要篩選 DataGrid 中的專案

1. 加入 <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> 事件的處理常式。

2. 在 <xref:System.Windows.Data.CollectionViewSource.Filter> 事件處理常式中，定義篩選邏輯。

    每次重新整理視圖時，就會套用此篩選。

    [!code-xaml[DataGrid_GroupSortFilter#013](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#013)]
    [!code-csharp[DataGrid_GroupSortFilter#113](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#113)]
    [!code-vb[DataGrid_GroupSortFilter#113](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#113)]

或者，您可以藉由建立提供篩選邏輯的方法，並設定 <xref:System.Windows.Data.CollectionView.Filter%2A?displayProperty=nameWithType> 屬性來套用篩選器，來篩選 <xref:System.Windows.Controls.DataGrid> 中的專案。 若要查看此方法的範例，請參閱[在視圖中篩選資料](../data/how-to-filter-data-in-a-view.md)。

## <a name="example"></a>範例

下列範例示範如何分組、排序和篩選 <xref:System.Windows.Data.CollectionViewSource> 中的 `Task` 資料，並在 <xref:System.Windows.Controls.DataGrid>中顯示已分組、已排序和已篩選的 `Task` 資料。 <xref:System.Windows.Data.CollectionViewSource> 可用來做為 <xref:System.Windows.Controls.DataGrid>的 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>。 分組、排序和篩選會在 <xref:System.Windows.Data.CollectionViewSource> 上執行，並顯示在 <xref:System.Windows.Controls.DataGrid> UI 中。

若要測試此範例，您必須調整 DGGroupSortFilterExample 名稱以符合您的專案名稱。 如果您使用 Visual Basic，則必須將 <xref:System.Windows.Window> 的類別名稱變更為下列各項。

`<Window x:Class="MainWindow"`

[!code-xaml[DataGrid_GroupSortFilter#000](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#000)]
[!code-csharp[DataGrid_GroupSortFilter#100](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#100)]
[!code-vb[DataGrid_GroupSortFilter#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#100)]

## <a name="see-also"></a>請參閱

- [資料繫結概觀](../../../desktop-wpf/data/data-binding-overview.md)
- [建立和繫結至 ObservableCollection](../data/how-to-create-and-bind-to-an-observablecollection.md)
- [篩選檢視中的資料](../data/how-to-filter-data-in-a-view.md)
- [排序檢視中的資料](../data/how-to-sort-data-in-a-view.md)
- [使用 XAML 中的檢視排序和群組資料](../data/how-to-sort-and-group-data-using-a-view-in-xaml.md)

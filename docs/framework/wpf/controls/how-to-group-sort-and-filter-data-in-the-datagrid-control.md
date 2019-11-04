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
# <a name="how-to-group-sort-and-filter-data-in-the-datagrid-control"></a><span data-ttu-id="1e774-102">如何：在 DataGrid 控制項中分組、排序和篩選資料</span><span class="sxs-lookup"><span data-stu-id="1e774-102">How to: Group, sort, and filter data in the DataGrid control</span></span>

<span data-ttu-id="1e774-103">藉由分組、排序和篩選資料，以不同的方式來查看 <xref:System.Windows.Controls.DataGrid> 中的資料通常很有用。</span><span class="sxs-lookup"><span data-stu-id="1e774-103">It is often useful to view data in a <xref:System.Windows.Controls.DataGrid> in different ways by grouping, sorting, and filtering the data.</span></span> <span data-ttu-id="1e774-104">若要對 <xref:System.Windows.Controls.DataGrid>中的資料進行分組、排序和篩選，您可以將它系結至支援這些函數的 <xref:System.Windows.Data.CollectionView>。</span><span class="sxs-lookup"><span data-stu-id="1e774-104">To group, sort, and filter the data in a <xref:System.Windows.Controls.DataGrid>, you bind it to a <xref:System.Windows.Data.CollectionView> that supports these functions.</span></span> <span data-ttu-id="1e774-105">然後您可以使用 <xref:System.Windows.Data.CollectionView> 中的資料，而不會影響基礎來源資料。</span><span class="sxs-lookup"><span data-stu-id="1e774-105">You can then work with the data in the <xref:System.Windows.Data.CollectionView> without affecting the underlying source data.</span></span> <span data-ttu-id="1e774-106">集合視圖中的變更會反映在 <xref:System.Windows.Controls.DataGrid> 的使用者介面（UI）中。</span><span class="sxs-lookup"><span data-stu-id="1e774-106">The changes in the collection view are reflected in the <xref:System.Windows.Controls.DataGrid> user interface (UI).</span></span>

<span data-ttu-id="1e774-107"><xref:System.Windows.Data.CollectionView> 類別會針對實 <xref:System.Collections.IEnumerable> 介面的資料來源，提供群組和排序功能。</span><span class="sxs-lookup"><span data-stu-id="1e774-107">The <xref:System.Windows.Data.CollectionView> class provides grouping and sorting functionality for a data source that implements the <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="1e774-108"><xref:System.Windows.Data.CollectionViewSource> 類別可讓您從 XAML 設定 <xref:System.Windows.Data.CollectionView> 的屬性。</span><span class="sxs-lookup"><span data-stu-id="1e774-108">The <xref:System.Windows.Data.CollectionViewSource> class enables you to set the properties of a <xref:System.Windows.Data.CollectionView> from XAML.</span></span>

<span data-ttu-id="1e774-109">在此範例中，`Task` 物件的集合會系結至 <xref:System.Windows.Data.CollectionViewSource>。</span><span class="sxs-lookup"><span data-stu-id="1e774-109">In this example, a collection of `Task` objects is bound to a <xref:System.Windows.Data.CollectionViewSource>.</span></span> <span data-ttu-id="1e774-110"><xref:System.Windows.Data.CollectionViewSource> 可用來做為 <xref:System.Windows.Controls.DataGrid>的 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>。</span><span class="sxs-lookup"><span data-stu-id="1e774-110">The <xref:System.Windows.Data.CollectionViewSource> is used as the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> for the <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="1e774-111">分組、排序和篩選會在 <xref:System.Windows.Data.CollectionViewSource> 上執行，並顯示在 <xref:System.Windows.Controls.DataGrid> UI 中。</span><span class="sxs-lookup"><span data-stu-id="1e774-111">Grouping, sorting, and filtering are performed on the <xref:System.Windows.Data.CollectionViewSource> and are displayed in the <xref:System.Windows.Controls.DataGrid> UI.</span></span>

<span data-ttu-id="1e774-112">![DataGrid 中的群組資料](././media/wpf-datagridgroups.png "WPF_DataGridGroups")DataGrid 中的群組資料</span><span class="sxs-lookup"><span data-stu-id="1e774-112">![Grouped data in a DataGrid](././media/wpf-datagridgroups.png "WPF_DataGridGroups") Grouped data in a DataGrid</span></span>

## <a name="using-a-collectionviewsource-as-an-itemssource"></a><span data-ttu-id="1e774-113">使用 CollectionViewSource 做為 ItemsSource</span><span class="sxs-lookup"><span data-stu-id="1e774-113">Using a CollectionViewSource as an ItemsSource</span></span>

<span data-ttu-id="1e774-114">若要對 <xref:System.Windows.Controls.DataGrid> 控制項中的資料進行分組、排序和篩選，您可以將 <xref:System.Windows.Controls.DataGrid> 系結至支援這些函式的 <xref:System.Windows.Data.CollectionView>。</span><span class="sxs-lookup"><span data-stu-id="1e774-114">To group, sort, and filter data in a <xref:System.Windows.Controls.DataGrid> control, you bind the <xref:System.Windows.Controls.DataGrid> to a <xref:System.Windows.Data.CollectionView> that supports these functions.</span></span> <span data-ttu-id="1e774-115">在此範例中，<xref:System.Windows.Controls.DataGrid> 系結至 <xref:System.Windows.Data.CollectionViewSource>，為 `Task` 物件 <xref:System.Collections.Generic.List%601> 提供這些函式。</span><span class="sxs-lookup"><span data-stu-id="1e774-115">In this example, the <xref:System.Windows.Controls.DataGrid> is bound to a <xref:System.Windows.Data.CollectionViewSource> that provides these functions for a <xref:System.Collections.Generic.List%601> of `Task` objects.</span></span>

### <a name="to-bind-a-datagrid-to-a-collectionviewsource"></a><span data-ttu-id="1e774-116">將 DataGrid 系結至 CollectionViewSource</span><span class="sxs-lookup"><span data-stu-id="1e774-116">To bind a DataGrid to a CollectionViewSource</span></span>

1. <span data-ttu-id="1e774-117">建立可執行 <xref:System.Collections.IEnumerable> 介面的資料收集。</span><span class="sxs-lookup"><span data-stu-id="1e774-117">Create a data collection that implements the <xref:System.Collections.IEnumerable> interface.</span></span>

    <span data-ttu-id="1e774-118">如果您使用 <xref:System.Collections.Generic.List%601> 來建立集合，您應該建立繼承自 <xref:System.Collections.Generic.List%601> 的新類別，而不是具現化 <xref:System.Collections.Generic.List%601>的實例。</span><span class="sxs-lookup"><span data-stu-id="1e774-118">If you use <xref:System.Collections.Generic.List%601> to create your collection, you should create a new class that inherits from <xref:System.Collections.Generic.List%601> instead of instantiating an instance of <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="1e774-119">這可讓您將資料系結至 XAML 中的集合。</span><span class="sxs-lookup"><span data-stu-id="1e774-119">This enables you to data bind to the collection in XAML.</span></span>

    > [!NOTE]
    > <span data-ttu-id="1e774-120">集合中的物件必須實 <xref:System.ComponentModel.INotifyPropertyChanged> 變更的介面和 <xref:System.ComponentModel.IEditableObject> 介面，才能讓 <xref:System.Windows.Controls.DataGrid> 正確地回應屬性變更和編輯。</span><span class="sxs-lookup"><span data-stu-id="1e774-120">The objects in the collection must implement the <xref:System.ComponentModel.INotifyPropertyChanged> changed interface and the <xref:System.ComponentModel.IEditableObject> interface in order for the <xref:System.Windows.Controls.DataGrid> to respond correctly to property changes and edits.</span></span> <span data-ttu-id="1e774-121">如需詳細資訊，請參閱[實作屬性變更通知](../data/how-to-implement-property-change-notification.md)。</span><span class="sxs-lookup"><span data-stu-id="1e774-121">For more information, see [Implement Property Change Notification](../data/how-to-implement-property-change-notification.md).</span></span>

    [!code-csharp[DataGrid_GroupSortFilter#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#101)]
    [!code-vb[DataGrid_GroupSortFilter#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#101)]

2. <span data-ttu-id="1e774-122">在 XAML 中，建立集合類別的實例，並設定[x：Key](../../xaml-services/x-key-directive.md)指示詞。</span><span class="sxs-lookup"><span data-stu-id="1e774-122">In XAML, create an instance of the collection class and set the [x:Key Directive](../../xaml-services/x-key-directive.md).</span></span>

3. <span data-ttu-id="1e774-123">在 XAML 中，建立 <xref:System.Windows.Data.CollectionViewSource> 類別的實例、設定[x：Key](../../xaml-services/x-key-directive.md)指示詞，並將集合類別的實例設定為 <xref:System.Windows.Data.CollectionViewSource.Source%2A>。</span><span class="sxs-lookup"><span data-stu-id="1e774-123">In XAML, create an instance of the <xref:System.Windows.Data.CollectionViewSource> class, set the [x:Key Directive](../../xaml-services/x-key-directive.md), and set the instance of your collection class as the <xref:System.Windows.Data.CollectionViewSource.Source%2A>.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#201](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml#201)]

4. <span data-ttu-id="1e774-124">建立 <xref:System.Windows.Controls.DataGrid> 類別的實例，並將 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 屬性設定為 <xref:System.Windows.Data.CollectionViewSource>。</span><span class="sxs-lookup"><span data-stu-id="1e774-124">Create an instance of the <xref:System.Windows.Controls.DataGrid> class, and set the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property to the <xref:System.Windows.Data.CollectionViewSource>.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#002](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#002)]

5. <span data-ttu-id="1e774-125">若要從您的程式碼存取 <xref:System.Windows.Data.CollectionViewSource>，請使用 <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> 方法來取得 <xref:System.Windows.Data.CollectionViewSource>的參考。</span><span class="sxs-lookup"><span data-stu-id="1e774-125">To access the <xref:System.Windows.Data.CollectionViewSource> from your code, use the <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> method to get a reference to the <xref:System.Windows.Data.CollectionViewSource>.</span></span>

    [!code-csharp[DataGrid_GroupSortFilter#102](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#102)]
    [!code-vb[DataGrid_GroupSortFilter#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#102)]

## <a name="grouping-items-in-a-datagrid"></a><span data-ttu-id="1e774-126">群組 DataGrid 中的專案</span><span class="sxs-lookup"><span data-stu-id="1e774-126">Grouping items in a DataGrid</span></span>

<span data-ttu-id="1e774-127">若要指定如何在 <xref:System.Windows.Controls.DataGrid>中分組專案，您可以使用 <xref:System.Windows.Data.PropertyGroupDescription> 類型，將來源視圖中的專案分組。</span><span class="sxs-lookup"><span data-stu-id="1e774-127">To specify how items are grouped in a <xref:System.Windows.Controls.DataGrid>, you use the <xref:System.Windows.Data.PropertyGroupDescription> type to group the items in the source view.</span></span>

### <a name="to-group-items-in-a-datagrid-using-xaml"></a><span data-ttu-id="1e774-128">使用 XAML 將 DataGrid 中的專案分組</span><span class="sxs-lookup"><span data-stu-id="1e774-128">To group items in a DataGrid using XAML</span></span>

1. <span data-ttu-id="1e774-129">建立 <xref:System.Windows.Data.PropertyGroupDescription>，指定要分組依據的屬性。</span><span class="sxs-lookup"><span data-stu-id="1e774-129">Create a <xref:System.Windows.Data.PropertyGroupDescription> that specifies the property to group by.</span></span> <span data-ttu-id="1e774-130">您可以在 XAML 或程式碼中指定屬性。</span><span class="sxs-lookup"><span data-stu-id="1e774-130">You can specify the property in XAML or in code.</span></span>

   1. <span data-ttu-id="1e774-131">在 XAML 中，將 <xref:System.Windows.Data.PropertyGroupDescription.PropertyName%2A> 設定為要分組依據的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="1e774-131">In XAML, set the <xref:System.Windows.Data.PropertyGroupDescription.PropertyName%2A> to the name of the property to group by.</span></span>

   2. <span data-ttu-id="1e774-132">在程式碼中，將要分組的屬性名稱傳遞給此函式。</span><span class="sxs-lookup"><span data-stu-id="1e774-132">In code, pass the name of the property to group by to the constructor.</span></span>

2. <span data-ttu-id="1e774-133">將 <xref:System.Windows.Data.PropertyGroupDescription> 新增至 <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A?displayProperty=nameWithType> 集合。</span><span class="sxs-lookup"><span data-stu-id="1e774-133">Add the <xref:System.Windows.Data.PropertyGroupDescription> to the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A?displayProperty=nameWithType> collection.</span></span>

3. <span data-ttu-id="1e774-134">將 <xref:System.Windows.Data.PropertyGroupDescription> 的其他實例新增至 <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> 集合，以加入更多層級的群組。</span><span class="sxs-lookup"><span data-stu-id="1e774-134">Add additional instances of <xref:System.Windows.Data.PropertyGroupDescription> to the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> collection to add more levels of grouping.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#012](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#012)]
    [!code-csharp[DataGrid_GroupSortFilter#112](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#112)]
    [!code-vb[DataGrid_GroupSortFilter#112](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#112)]

4. <span data-ttu-id="1e774-135">若要移除群組，請從 <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> 集合中移除 <xref:System.Windows.Data.PropertyGroupDescription>。</span><span class="sxs-lookup"><span data-stu-id="1e774-135">To remove a group, remove the <xref:System.Windows.Data.PropertyGroupDescription> from the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> collection.</span></span>

5. <span data-ttu-id="1e774-136">若要移除所有群組，請呼叫 <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> 集合的 <xref:System.Collections.ObjectModel.Collection%601.Clear%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="1e774-136">To remove all groups, call the <xref:System.Collections.ObjectModel.Collection%601.Clear%2A> method of the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> collection.</span></span>

    [!code-csharp[DataGrid_GroupSortFilter#114](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#114)]
    [!code-vb[DataGrid_GroupSortFilter#114](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#114)]

<span data-ttu-id="1e774-137">當專案在 <xref:System.Windows.Controls.DataGrid>中分組時，您可以定義指定每個群組外觀的 <xref:System.Windows.Controls.GroupStyle>。</span><span class="sxs-lookup"><span data-stu-id="1e774-137">When items are grouped in the <xref:System.Windows.Controls.DataGrid>, you can define a <xref:System.Windows.Controls.GroupStyle> that specifies the appearance of each group.</span></span> <span data-ttu-id="1e774-138">您可以藉由將 <xref:System.Windows.Controls.GroupStyle> 新增至 DataGrid 的 <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> 集合來套用。</span><span class="sxs-lookup"><span data-stu-id="1e774-138">You apply the <xref:System.Windows.Controls.GroupStyle> by adding it to the <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> collection of the DataGrid.</span></span> <span data-ttu-id="1e774-139">如果您有多個層級的群組，您可以將不同的樣式套用至每個群組層級。</span><span class="sxs-lookup"><span data-stu-id="1e774-139">If you have multiple levels of grouping, you can apply different styles to each group level.</span></span> <span data-ttu-id="1e774-140">樣式會依照其定義的順序套用。</span><span class="sxs-lookup"><span data-stu-id="1e774-140">Styles are applied in the order in which they are defined.</span></span> <span data-ttu-id="1e774-141">例如，如果您定義兩個樣式，第一個會套用至最上層的資料列群組。</span><span class="sxs-lookup"><span data-stu-id="1e774-141">For example, if you define two styles, the first will be applied to top level row groups.</span></span> <span data-ttu-id="1e774-142">第二種樣式會套用到第二層級的所有資料列群組，並在較低的位置套用。</span><span class="sxs-lookup"><span data-stu-id="1e774-142">The second style will be applied to all row groups at the second level and lower.</span></span> <span data-ttu-id="1e774-143"><xref:System.Windows.Controls.GroupStyle> 的 <xref:System.Windows.FrameworkElement.DataContext%2A> 是群組所代表的 <xref:System.Windows.Data.CollectionViewGroup>。</span><span class="sxs-lookup"><span data-stu-id="1e774-143">The <xref:System.Windows.FrameworkElement.DataContext%2A> of the <xref:System.Windows.Controls.GroupStyle> is the <xref:System.Windows.Data.CollectionViewGroup> that the group represents.</span></span>

### <a name="to-change-the-appearance-of-row-group-headers"></a><span data-ttu-id="1e774-144">若要變更資料列群組標頭的外觀</span><span class="sxs-lookup"><span data-stu-id="1e774-144">To change the appearance of row group headers</span></span>

1. <span data-ttu-id="1e774-145">建立定義資料列群組外觀的 <xref:System.Windows.Controls.GroupStyle>。</span><span class="sxs-lookup"><span data-stu-id="1e774-145">Create a <xref:System.Windows.Controls.GroupStyle> that defines the appearance of the row group.</span></span>

2. <span data-ttu-id="1e774-146">將 <xref:System.Windows.Controls.GroupStyle> 放在 `<DataGrid.GroupStyle>` 標記內。</span><span class="sxs-lookup"><span data-stu-id="1e774-146">Put the <xref:System.Windows.Controls.GroupStyle> inside the `<DataGrid.GroupStyle>` tags.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#003](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#003)]

## <a name="sorting-items-in-a-datagrid"></a><span data-ttu-id="1e774-147">排序 DataGrid 中的專案</span><span class="sxs-lookup"><span data-stu-id="1e774-147">Sorting items in a DataGrid</span></span>

<span data-ttu-id="1e774-148">若要指定如何在 <xref:System.Windows.Controls.DataGrid>中排序專案，您可以使用 <xref:System.ComponentModel.SortDescription> 類型來排序來源視圖中的專案。</span><span class="sxs-lookup"><span data-stu-id="1e774-148">To specify how items are sorted in a <xref:System.Windows.Controls.DataGrid>, you use the <xref:System.ComponentModel.SortDescription> type to sort the items in the source view.</span></span>

### <a name="to-sort-items-in-a-datagrid"></a><span data-ttu-id="1e774-149">排序 DataGrid 中的專案</span><span class="sxs-lookup"><span data-stu-id="1e774-149">To sort items in a DataGrid</span></span>

1. <span data-ttu-id="1e774-150">建立指定排序依據之屬性的 <xref:System.ComponentModel.SortDescription>。</span><span class="sxs-lookup"><span data-stu-id="1e774-150">Create a <xref:System.ComponentModel.SortDescription> that specifies the property to sort by.</span></span> <span data-ttu-id="1e774-151">您可以在 XAML 或程式碼中指定屬性。</span><span class="sxs-lookup"><span data-stu-id="1e774-151">You can specify the property in XAML or in code.</span></span>

    1. <span data-ttu-id="1e774-152">在 XAML 中，將 <xref:System.ComponentModel.SortDescription.PropertyName%2A> 設定為要排序的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="1e774-152">In XAML, set the <xref:System.ComponentModel.SortDescription.PropertyName%2A> to the name of the property to sort by.</span></span>

    2. <span data-ttu-id="1e774-153">在程式碼中，傳遞要排序之屬性的名稱，並將 <xref:System.ComponentModel.ListSortDirection> 到該函式。</span><span class="sxs-lookup"><span data-stu-id="1e774-153">In code, pass the name of the property to sort by and the <xref:System.ComponentModel.ListSortDirection> to the constructor.</span></span>

2. <span data-ttu-id="1e774-154">將 <xref:System.ComponentModel.SortDescription> 新增至 <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A?displayProperty=nameWithType> 集合。</span><span class="sxs-lookup"><span data-stu-id="1e774-154">Add the <xref:System.ComponentModel.SortDescription> to the <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A?displayProperty=nameWithType> collection.</span></span>

3. <span data-ttu-id="1e774-155">將 <xref:System.ComponentModel.SortDescription> 的其他實例新增至 <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A> 集合，以依其他屬性排序。</span><span class="sxs-lookup"><span data-stu-id="1e774-155">Add additional instances of <xref:System.ComponentModel.SortDescription> to the <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A> collection to sort by additional properties.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#011](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#011)]
    [!code-csharp[DataGrid_GroupSortFilter#211](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml.cs#211)]
    [!code-vb[DataGrid_GroupSortFilter#211](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#211)]

## <a name="filtering-items-in-a-datagrid"></a><span data-ttu-id="1e774-156">篩選 DataGrid 中的專案</span><span class="sxs-lookup"><span data-stu-id="1e774-156">Filtering items in a DataGrid</span></span>

<span data-ttu-id="1e774-157">若要使用 <xref:System.Windows.Data.CollectionViewSource>來篩選 <xref:System.Windows.Controls.DataGrid> 中的專案，您可以在 <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> 事件的處理常式中提供篩選邏輯。</span><span class="sxs-lookup"><span data-stu-id="1e774-157">To filter items in a <xref:System.Windows.Controls.DataGrid> using a <xref:System.Windows.Data.CollectionViewSource>, you provide the filtering logic in the handler for the <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> event.</span></span>

### <a name="to-filter-items-in-a-datagrid"></a><span data-ttu-id="1e774-158">若要篩選 DataGrid 中的專案</span><span class="sxs-lookup"><span data-stu-id="1e774-158">To filter items in a DataGrid</span></span>

1. <span data-ttu-id="1e774-159">加入 <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> 事件的處理常式。</span><span class="sxs-lookup"><span data-stu-id="1e774-159">Add a handler for the <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> event.</span></span>

2. <span data-ttu-id="1e774-160">在 <xref:System.Windows.Data.CollectionViewSource.Filter> 事件處理常式中，定義篩選邏輯。</span><span class="sxs-lookup"><span data-stu-id="1e774-160">In the <xref:System.Windows.Data.CollectionViewSource.Filter> event handler, define the filtering logic.</span></span>

    <span data-ttu-id="1e774-161">每次重新整理視圖時，就會套用此篩選。</span><span class="sxs-lookup"><span data-stu-id="1e774-161">The filter will be applied every time the view is refreshed.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#013](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#013)]
    [!code-csharp[DataGrid_GroupSortFilter#113](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#113)]
    [!code-vb[DataGrid_GroupSortFilter#113](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#113)]

<span data-ttu-id="1e774-162">或者，您可以藉由建立提供篩選邏輯的方法，並設定 <xref:System.Windows.Data.CollectionView.Filter%2A?displayProperty=nameWithType> 屬性來套用篩選器，來篩選 <xref:System.Windows.Controls.DataGrid> 中的專案。</span><span class="sxs-lookup"><span data-stu-id="1e774-162">Alternatively, you can filter items in a <xref:System.Windows.Controls.DataGrid> by creating a method that provides the filtering logic and setting the <xref:System.Windows.Data.CollectionView.Filter%2A?displayProperty=nameWithType> property to apply the filter.</span></span> <span data-ttu-id="1e774-163">若要查看此方法的範例，請參閱[在視圖中篩選資料](../data/how-to-filter-data-in-a-view.md)。</span><span class="sxs-lookup"><span data-stu-id="1e774-163">To see an example of this method, see [Filter Data in a View](../data/how-to-filter-data-in-a-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="1e774-164">範例</span><span class="sxs-lookup"><span data-stu-id="1e774-164">Example</span></span>

<span data-ttu-id="1e774-165">下列範例示範如何分組、排序和篩選 <xref:System.Windows.Data.CollectionViewSource> 中的 `Task` 資料，並在 <xref:System.Windows.Controls.DataGrid>中顯示已分組、已排序和已篩選的 `Task` 資料。</span><span class="sxs-lookup"><span data-stu-id="1e774-165">The following example demonstrates grouping, sorting, and filtering `Task` data in a <xref:System.Windows.Data.CollectionViewSource> and displaying the grouped, sorted, and filtered `Task` data in a <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="1e774-166"><xref:System.Windows.Data.CollectionViewSource> 可用來做為 <xref:System.Windows.Controls.DataGrid>的 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>。</span><span class="sxs-lookup"><span data-stu-id="1e774-166">The <xref:System.Windows.Data.CollectionViewSource> is used as the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> for the <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="1e774-167">分組、排序和篩選會在 <xref:System.Windows.Data.CollectionViewSource> 上執行，並顯示在 <xref:System.Windows.Controls.DataGrid> UI 中。</span><span class="sxs-lookup"><span data-stu-id="1e774-167">Grouping, sorting, and filtering are performed on the <xref:System.Windows.Data.CollectionViewSource> and are displayed in the <xref:System.Windows.Controls.DataGrid> UI.</span></span>

<span data-ttu-id="1e774-168">若要測試此範例，您必須調整 DGGroupSortFilterExample 名稱以符合您的專案名稱。</span><span class="sxs-lookup"><span data-stu-id="1e774-168">To test this example, you will need to adjust the DGGroupSortFilterExample name to match your project name.</span></span> <span data-ttu-id="1e774-169">如果您使用 Visual Basic，則必須將 <xref:System.Windows.Window> 的類別名稱變更為下列各項。</span><span class="sxs-lookup"><span data-stu-id="1e774-169">If you are using Visual Basic, you will need to change the class name for <xref:System.Windows.Window> to the following.</span></span>

`<Window x:Class="MainWindow"`

[!code-xaml[DataGrid_GroupSortFilter#000](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#000)]
[!code-csharp[DataGrid_GroupSortFilter#100](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#100)]
[!code-vb[DataGrid_GroupSortFilter#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#100)]

## <a name="see-also"></a><span data-ttu-id="1e774-170">請參閱</span><span class="sxs-lookup"><span data-stu-id="1e774-170">See also</span></span>

- [<span data-ttu-id="1e774-171">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="1e774-171">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="1e774-172">建立和繫結至 ObservableCollection</span><span class="sxs-lookup"><span data-stu-id="1e774-172">Create and Bind to an ObservableCollection</span></span>](../data/how-to-create-and-bind-to-an-observablecollection.md)
- [<span data-ttu-id="1e774-173">篩選檢視中的資料</span><span class="sxs-lookup"><span data-stu-id="1e774-173">Filter Data in a View</span></span>](../data/how-to-filter-data-in-a-view.md)
- [<span data-ttu-id="1e774-174">排序檢視中的資料</span><span class="sxs-lookup"><span data-stu-id="1e774-174">Sort Data in a View</span></span>](../data/how-to-sort-data-in-a-view.md)
- [<span data-ttu-id="1e774-175">使用 XAML 中的檢視排序和群組資料</span><span class="sxs-lookup"><span data-stu-id="1e774-175">Sort and Group Data Using a View in XAML</span></span>](../data/how-to-sort-and-group-data-using-a-view-in-xaml.md)

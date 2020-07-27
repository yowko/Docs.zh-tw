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
# <a name="how-to-group-sort-and-filter-data-in-the-datagrid-control"></a><span data-ttu-id="f1da4-103">如何：在 DataGrid 控制項中分組、排序和篩選資料</span><span class="sxs-lookup"><span data-stu-id="f1da4-103">How to: Group, sort, and filter data in the DataGrid control</span></span>

<span data-ttu-id="f1da4-104">透過 <xref:System.Windows.Controls.DataGrid> 分組、排序和篩選資料，以不同的方式來查看中的資料通常很有用。</span><span class="sxs-lookup"><span data-stu-id="f1da4-104">It is often useful to view data in a <xref:System.Windows.Controls.DataGrid> in different ways by grouping, sorting, and filtering the data.</span></span> <span data-ttu-id="f1da4-105">若要在中分組、排序和篩選資料 <xref:System.Windows.Controls.DataGrid> ，您可以將它系結至 <xref:System.Windows.Data.CollectionView> 支援這些函數的。</span><span class="sxs-lookup"><span data-stu-id="f1da4-105">To group, sort, and filter the data in a <xref:System.Windows.Controls.DataGrid>, you bind it to a <xref:System.Windows.Data.CollectionView> that supports these functions.</span></span> <span data-ttu-id="f1da4-106">然後，您可以在中使用資料， <xref:System.Windows.Data.CollectionView> 而不會影響基礎來源資料。</span><span class="sxs-lookup"><span data-stu-id="f1da4-106">You can then work with the data in the <xref:System.Windows.Data.CollectionView> without affecting the underlying source data.</span></span> <span data-ttu-id="f1da4-107">集合視圖中的變更會反映在 <xref:System.Windows.Controls.DataGrid> 使用者介面（UI）中。</span><span class="sxs-lookup"><span data-stu-id="f1da4-107">The changes in the collection view are reflected in the <xref:System.Windows.Controls.DataGrid> user interface (UI).</span></span>

<span data-ttu-id="f1da4-108"><xref:System.Windows.Data.CollectionView>類別會針對實作為介面的資料來源，提供群組和排序功能 <xref:System.Collections.IEnumerable> 。</span><span class="sxs-lookup"><span data-stu-id="f1da4-108">The <xref:System.Windows.Data.CollectionView> class provides grouping and sorting functionality for a data source that implements the <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="f1da4-109"><xref:System.Windows.Data.CollectionViewSource>類別可讓您從 XAML 設定的屬性 <xref:System.Windows.Data.CollectionView> 。</span><span class="sxs-lookup"><span data-stu-id="f1da4-109">The <xref:System.Windows.Data.CollectionViewSource> class enables you to set the properties of a <xref:System.Windows.Data.CollectionView> from XAML.</span></span>

<span data-ttu-id="f1da4-110">在此範例中，物件的集合會系結 `Task` 至 <xref:System.Windows.Data.CollectionViewSource> 。</span><span class="sxs-lookup"><span data-stu-id="f1da4-110">In this example, a collection of `Task` objects is bound to a <xref:System.Windows.Data.CollectionViewSource>.</span></span> <span data-ttu-id="f1da4-111"><xref:System.Windows.Data.CollectionViewSource>是用來做 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 為的 <xref:System.Windows.Controls.DataGrid> 。</span><span class="sxs-lookup"><span data-stu-id="f1da4-111">The <xref:System.Windows.Data.CollectionViewSource> is used as the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> for the <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="f1da4-112">群組、排序和篩選會在上執行， <xref:System.Windows.Data.CollectionViewSource> 並顯示在 UI 中 <xref:System.Windows.Controls.DataGrid> 。</span><span class="sxs-lookup"><span data-stu-id="f1da4-112">Grouping, sorting, and filtering are performed on the <xref:System.Windows.Data.CollectionViewSource> and are displayed in the <xref:System.Windows.Controls.DataGrid> UI.</span></span>

<span data-ttu-id="f1da4-113">![DataGrid 中的群組資料](././media/wpf-datagridgroups.png "WPF_DataGridGroups")DataGrid 中的群組資料</span><span class="sxs-lookup"><span data-stu-id="f1da4-113">![Grouped data in a DataGrid](././media/wpf-datagridgroups.png "WPF_DataGridGroups") Grouped data in a DataGrid</span></span>

## <a name="using-a-collectionviewsource-as-an-itemssource"></a><span data-ttu-id="f1da4-114">使用 CollectionViewSource 做為 ItemsSource</span><span class="sxs-lookup"><span data-stu-id="f1da4-114">Using a CollectionViewSource as an ItemsSource</span></span>

<span data-ttu-id="f1da4-115">若要對控制項中的資料進行分組、排序和篩選 <xref:System.Windows.Controls.DataGrid> ，您可以將系結 <xref:System.Windows.Controls.DataGrid> 至支援這些函式的 <xref:System.Windows.Data.CollectionView> 。</span><span class="sxs-lookup"><span data-stu-id="f1da4-115">To group, sort, and filter data in a <xref:System.Windows.Controls.DataGrid> control, you bind the <xref:System.Windows.Controls.DataGrid> to a <xref:System.Windows.Data.CollectionView> that supports these functions.</span></span> <span data-ttu-id="f1da4-116">在此範例中， <xref:System.Windows.Controls.DataGrid> 會系結至為 <xref:System.Windows.Data.CollectionViewSource> 物件提供這些函式 <xref:System.Collections.Generic.List%601> 的 `Task` 。</span><span class="sxs-lookup"><span data-stu-id="f1da4-116">In this example, the <xref:System.Windows.Controls.DataGrid> is bound to a <xref:System.Windows.Data.CollectionViewSource> that provides these functions for a <xref:System.Collections.Generic.List%601> of `Task` objects.</span></span>

### <a name="to-bind-a-datagrid-to-a-collectionviewsource"></a><span data-ttu-id="f1da4-117">將 DataGrid 系結至 CollectionViewSource</span><span class="sxs-lookup"><span data-stu-id="f1da4-117">To bind a DataGrid to a CollectionViewSource</span></span>

1. <span data-ttu-id="f1da4-118">建立可實作為介面的資料集合 <xref:System.Collections.IEnumerable> 。</span><span class="sxs-lookup"><span data-stu-id="f1da4-118">Create a data collection that implements the <xref:System.Collections.IEnumerable> interface.</span></span>

    <span data-ttu-id="f1da4-119">如果您使用 <xref:System.Collections.Generic.List%601> 來建立集合，您應該建立繼承自的新類別， <xref:System.Collections.Generic.List%601> 而不是具現化的實例 <xref:System.Collections.Generic.List%601> 。</span><span class="sxs-lookup"><span data-stu-id="f1da4-119">If you use <xref:System.Collections.Generic.List%601> to create your collection, you should create a new class that inherits from <xref:System.Collections.Generic.List%601> instead of instantiating an instance of <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="f1da4-120">這可讓您將資料系結至 XAML 中的集合。</span><span class="sxs-lookup"><span data-stu-id="f1da4-120">This enables you to data bind to the collection in XAML.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f1da4-121">集合中的物件必須執行 <xref:System.ComponentModel.INotifyPropertyChanged> 已變更的介面和 <xref:System.ComponentModel.IEditableObject> 介面， <xref:System.Windows.Controls.DataGrid> 才能正確回應屬性變更和編輯。</span><span class="sxs-lookup"><span data-stu-id="f1da4-121">The objects in the collection must implement the <xref:System.ComponentModel.INotifyPropertyChanged> changed interface and the <xref:System.ComponentModel.IEditableObject> interface in order for the <xref:System.Windows.Controls.DataGrid> to respond correctly to property changes and edits.</span></span> <span data-ttu-id="f1da4-122">如需詳細資訊，請參閱[實作屬性變更通知](../data/how-to-implement-property-change-notification.md)。</span><span class="sxs-lookup"><span data-stu-id="f1da4-122">For more information, see [Implement Property Change Notification](../data/how-to-implement-property-change-notification.md).</span></span>

    [!code-csharp[DataGrid_GroupSortFilter#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#101)]
    [!code-vb[DataGrid_GroupSortFilter#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#101)]

2. <span data-ttu-id="f1da4-123">在 XAML 中，建立集合類別的實例，並設定[x：Key](../../../desktop-wpf/xaml-services/xkey-directive.md)指示詞。</span><span class="sxs-lookup"><span data-stu-id="f1da4-123">In XAML, create an instance of the collection class and set the [x:Key Directive](../../../desktop-wpf/xaml-services/xkey-directive.md).</span></span>

3. <span data-ttu-id="f1da4-124">在 XAML 中，建立類別的實例 <xref:System.Windows.Data.CollectionViewSource> 、設定[x：Key](../../../desktop-wpf/xaml-services/xkey-directive.md)指示詞，並將集合類別的實例設定為 <xref:System.Windows.Data.CollectionViewSource.Source%2A> 。</span><span class="sxs-lookup"><span data-stu-id="f1da4-124">In XAML, create an instance of the <xref:System.Windows.Data.CollectionViewSource> class, set the [x:Key Directive](../../../desktop-wpf/xaml-services/xkey-directive.md), and set the instance of your collection class as the <xref:System.Windows.Data.CollectionViewSource.Source%2A>.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#201](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml#201)]

4. <span data-ttu-id="f1da4-125">建立類別的實例 <xref:System.Windows.Controls.DataGrid> ，並將 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 屬性設定為 <xref:System.Windows.Data.CollectionViewSource> 。</span><span class="sxs-lookup"><span data-stu-id="f1da4-125">Create an instance of the <xref:System.Windows.Controls.DataGrid> class, and set the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property to the <xref:System.Windows.Data.CollectionViewSource>.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#002](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#002)]

5. <span data-ttu-id="f1da4-126">若要 <xref:System.Windows.Data.CollectionViewSource> 從您的程式碼存取，請使用 <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> 方法來取得的參考 <xref:System.Windows.Data.CollectionViewSource> 。</span><span class="sxs-lookup"><span data-stu-id="f1da4-126">To access the <xref:System.Windows.Data.CollectionViewSource> from your code, use the <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> method to get a reference to the <xref:System.Windows.Data.CollectionViewSource>.</span></span>

    [!code-csharp[DataGrid_GroupSortFilter#102](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#102)]
    [!code-vb[DataGrid_GroupSortFilter#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#102)]

## <a name="grouping-items-in-a-datagrid"></a><span data-ttu-id="f1da4-127">群組 DataGrid 中的專案</span><span class="sxs-lookup"><span data-stu-id="f1da4-127">Grouping items in a DataGrid</span></span>

<span data-ttu-id="f1da4-128">若要指定專案在中的分組方式 <xref:System.Windows.Controls.DataGrid> ，您可以使用類型，將 <xref:System.Windows.Data.PropertyGroupDescription> 來源視圖中的專案分組。</span><span class="sxs-lookup"><span data-stu-id="f1da4-128">To specify how items are grouped in a <xref:System.Windows.Controls.DataGrid>, you use the <xref:System.Windows.Data.PropertyGroupDescription> type to group the items in the source view.</span></span>

### <a name="to-group-items-in-a-datagrid-using-xaml"></a><span data-ttu-id="f1da4-129">使用 XAML 將 DataGrid 中的專案分組</span><span class="sxs-lookup"><span data-stu-id="f1da4-129">To group items in a DataGrid using XAML</span></span>

1. <span data-ttu-id="f1da4-130">建立 <xref:System.Windows.Data.PropertyGroupDescription> ，以指定要分組依據的屬性。</span><span class="sxs-lookup"><span data-stu-id="f1da4-130">Create a <xref:System.Windows.Data.PropertyGroupDescription> that specifies the property to group by.</span></span> <span data-ttu-id="f1da4-131">您可以在 XAML 或程式碼中指定屬性。</span><span class="sxs-lookup"><span data-stu-id="f1da4-131">You can specify the property in XAML or in code.</span></span>

   1. <span data-ttu-id="f1da4-132">在 XAML 中，將設 <xref:System.Windows.Data.PropertyGroupDescription.PropertyName%2A> 為要分組依據的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="f1da4-132">In XAML, set the <xref:System.Windows.Data.PropertyGroupDescription.PropertyName%2A> to the name of the property to group by.</span></span>

   2. <span data-ttu-id="f1da4-133">在程式碼中，將要分組的屬性名稱傳遞給此函式。</span><span class="sxs-lookup"><span data-stu-id="f1da4-133">In code, pass the name of the property to group by to the constructor.</span></span>

2. <span data-ttu-id="f1da4-134">將加入 <xref:System.Windows.Data.PropertyGroupDescription> 至 <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A?displayProperty=nameWithType> 集合。</span><span class="sxs-lookup"><span data-stu-id="f1da4-134">Add the <xref:System.Windows.Data.PropertyGroupDescription> to the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A?displayProperty=nameWithType> collection.</span></span>

3. <span data-ttu-id="f1da4-135">將的其他實例新增 <xref:System.Windows.Data.PropertyGroupDescription> 至 <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> 集合，以加入更多層級的群組。</span><span class="sxs-lookup"><span data-stu-id="f1da4-135">Add additional instances of <xref:System.Windows.Data.PropertyGroupDescription> to the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> collection to add more levels of grouping.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#012](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#012)]
    [!code-csharp[DataGrid_GroupSortFilter#112](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#112)]
    [!code-vb[DataGrid_GroupSortFilter#112](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#112)]

4. <span data-ttu-id="f1da4-136">若要移除群組，請 <xref:System.Windows.Data.PropertyGroupDescription> 從集合中移除 <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> 。</span><span class="sxs-lookup"><span data-stu-id="f1da4-136">To remove a group, remove the <xref:System.Windows.Data.PropertyGroupDescription> from the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> collection.</span></span>

5. <span data-ttu-id="f1da4-137">若要移除所有群組，請呼叫 <xref:System.Collections.ObjectModel.Collection%601.Clear%2A> 集合的方法 <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> 。</span><span class="sxs-lookup"><span data-stu-id="f1da4-137">To remove all groups, call the <xref:System.Collections.ObjectModel.Collection%601.Clear%2A> method of the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> collection.</span></span>

    [!code-csharp[DataGrid_GroupSortFilter#114](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#114)]
    [!code-vb[DataGrid_GroupSortFilter#114](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#114)]

<span data-ttu-id="f1da4-138">當專案在中分組時 <xref:System.Windows.Controls.DataGrid> ，您可以定義，以 <xref:System.Windows.Controls.GroupStyle> 指定每個群組的外觀。</span><span class="sxs-lookup"><span data-stu-id="f1da4-138">When items are grouped in the <xref:System.Windows.Controls.DataGrid>, you can define a <xref:System.Windows.Controls.GroupStyle> that specifies the appearance of each group.</span></span> <span data-ttu-id="f1da4-139">您可以將 <xref:System.Windows.Controls.GroupStyle> 它新增至 DataGrid 的 <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> 集合來套用。</span><span class="sxs-lookup"><span data-stu-id="f1da4-139">You apply the <xref:System.Windows.Controls.GroupStyle> by adding it to the <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> collection of the DataGrid.</span></span> <span data-ttu-id="f1da4-140">如果您有多個層級的群組，您可以將不同的樣式套用至每個群組層級。</span><span class="sxs-lookup"><span data-stu-id="f1da4-140">If you have multiple levels of grouping, you can apply different styles to each group level.</span></span> <span data-ttu-id="f1da4-141">樣式會依照其定義的順序套用。</span><span class="sxs-lookup"><span data-stu-id="f1da4-141">Styles are applied in the order in which they are defined.</span></span> <span data-ttu-id="f1da4-142">例如，如果您定義兩個樣式，第一個會套用至最上層的資料列群組。</span><span class="sxs-lookup"><span data-stu-id="f1da4-142">For example, if you define two styles, the first will be applied to top level row groups.</span></span> <span data-ttu-id="f1da4-143">第二種樣式會套用到第二層級的所有資料列群組，並在較低的位置套用。</span><span class="sxs-lookup"><span data-stu-id="f1da4-143">The second style will be applied to all row groups at the second level and lower.</span></span> <span data-ttu-id="f1da4-144">的 <xref:System.Windows.FrameworkElement.DataContext%2A> <xref:System.Windows.Controls.GroupStyle> 是 <xref:System.Windows.Data.CollectionViewGroup> 群組代表的。</span><span class="sxs-lookup"><span data-stu-id="f1da4-144">The <xref:System.Windows.FrameworkElement.DataContext%2A> of the <xref:System.Windows.Controls.GroupStyle> is the <xref:System.Windows.Data.CollectionViewGroup> that the group represents.</span></span>

### <a name="to-change-the-appearance-of-row-group-headers"></a><span data-ttu-id="f1da4-145">若要變更資料列群組標頭的外觀</span><span class="sxs-lookup"><span data-stu-id="f1da4-145">To change the appearance of row group headers</span></span>

1. <span data-ttu-id="f1da4-146">建立 <xref:System.Windows.Controls.GroupStyle> 定義資料列群組外觀的。</span><span class="sxs-lookup"><span data-stu-id="f1da4-146">Create a <xref:System.Windows.Controls.GroupStyle> that defines the appearance of the row group.</span></span>

2. <span data-ttu-id="f1da4-147">將放在 <xref:System.Windows.Controls.GroupStyle> `<DataGrid.GroupStyle>` 標記內。</span><span class="sxs-lookup"><span data-stu-id="f1da4-147">Put the <xref:System.Windows.Controls.GroupStyle> inside the `<DataGrid.GroupStyle>` tags.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#003](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#003)]

## <a name="sorting-items-in-a-datagrid"></a><span data-ttu-id="f1da4-148">排序 DataGrid 中的專案</span><span class="sxs-lookup"><span data-stu-id="f1da4-148">Sorting items in a DataGrid</span></span>

<span data-ttu-id="f1da4-149">若要指定專案在中的排序方式 <xref:System.Windows.Controls.DataGrid> ，您可以使用 <xref:System.ComponentModel.SortDescription> 類型來排序來源視圖中的專案。</span><span class="sxs-lookup"><span data-stu-id="f1da4-149">To specify how items are sorted in a <xref:System.Windows.Controls.DataGrid>, you use the <xref:System.ComponentModel.SortDescription> type to sort the items in the source view.</span></span>

### <a name="to-sort-items-in-a-datagrid"></a><span data-ttu-id="f1da4-150">排序 DataGrid 中的專案</span><span class="sxs-lookup"><span data-stu-id="f1da4-150">To sort items in a DataGrid</span></span>

1. <span data-ttu-id="f1da4-151">建立 <xref:System.ComponentModel.SortDescription> ，指定要排序的屬性。</span><span class="sxs-lookup"><span data-stu-id="f1da4-151">Create a <xref:System.ComponentModel.SortDescription> that specifies the property to sort by.</span></span> <span data-ttu-id="f1da4-152">您可以在 XAML 或程式碼中指定屬性。</span><span class="sxs-lookup"><span data-stu-id="f1da4-152">You can specify the property in XAML or in code.</span></span>

    1. <span data-ttu-id="f1da4-153">在 XAML 中，將設定 <xref:System.ComponentModel.SortDescription.PropertyName%2A> 為要排序的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="f1da4-153">In XAML, set the <xref:System.ComponentModel.SortDescription.PropertyName%2A> to the name of the property to sort by.</span></span>

    2. <span data-ttu-id="f1da4-154">在程式碼中，將屬性的名稱傳遞給排序依據，並將 <xref:System.ComponentModel.ListSortDirection> 設為。</span><span class="sxs-lookup"><span data-stu-id="f1da4-154">In code, pass the name of the property to sort by and the <xref:System.ComponentModel.ListSortDirection> to the constructor.</span></span>

2. <span data-ttu-id="f1da4-155">將加入 <xref:System.ComponentModel.SortDescription> 至 <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A?displayProperty=nameWithType> 集合。</span><span class="sxs-lookup"><span data-stu-id="f1da4-155">Add the <xref:System.ComponentModel.SortDescription> to the <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A?displayProperty=nameWithType> collection.</span></span>

3. <span data-ttu-id="f1da4-156">將的其他實例新增 <xref:System.ComponentModel.SortDescription> 至 <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A> 集合，以依其他屬性排序。</span><span class="sxs-lookup"><span data-stu-id="f1da4-156">Add additional instances of <xref:System.ComponentModel.SortDescription> to the <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A> collection to sort by additional properties.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#011](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#011)]
    [!code-csharp[DataGrid_GroupSortFilter#211](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml.cs#211)]
    [!code-vb[DataGrid_GroupSortFilter#211](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#211)]

## <a name="filtering-items-in-a-datagrid"></a><span data-ttu-id="f1da4-157">篩選 DataGrid 中的專案</span><span class="sxs-lookup"><span data-stu-id="f1da4-157">Filtering items in a DataGrid</span></span>

<span data-ttu-id="f1da4-158">若要使用來篩選中的專案 <xref:System.Windows.Controls.DataGrid> <xref:System.Windows.Data.CollectionViewSource> ，您可以在事件的處理常式中提供篩選邏輯 <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="f1da4-158">To filter items in a <xref:System.Windows.Controls.DataGrid> using a <xref:System.Windows.Data.CollectionViewSource>, you provide the filtering logic in the handler for the <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> event.</span></span>

### <a name="to-filter-items-in-a-datagrid"></a><span data-ttu-id="f1da4-159">若要篩選 DataGrid 中的專案</span><span class="sxs-lookup"><span data-stu-id="f1da4-159">To filter items in a DataGrid</span></span>

1. <span data-ttu-id="f1da4-160">加入事件的處理常式 <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="f1da4-160">Add a handler for the <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> event.</span></span>

2. <span data-ttu-id="f1da4-161">在 <xref:System.Windows.Data.CollectionViewSource.Filter> 事件處理常式中，定義篩選邏輯。</span><span class="sxs-lookup"><span data-stu-id="f1da4-161">In the <xref:System.Windows.Data.CollectionViewSource.Filter> event handler, define the filtering logic.</span></span>

    <span data-ttu-id="f1da4-162">每次重新整理視圖時，就會套用此篩選。</span><span class="sxs-lookup"><span data-stu-id="f1da4-162">The filter will be applied every time the view is refreshed.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#013](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#013)]
    [!code-csharp[DataGrid_GroupSortFilter#113](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#113)]
    [!code-vb[DataGrid_GroupSortFilter#113](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#113)]

<span data-ttu-id="f1da4-163">或者，您可以藉 <xref:System.Windows.Controls.DataGrid> 由建立提供篩選邏輯的方法，並設定要套用篩選的屬性，來篩選中的專案 <xref:System.Windows.Data.CollectionView.Filter%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="f1da4-163">Alternatively, you can filter items in a <xref:System.Windows.Controls.DataGrid> by creating a method that provides the filtering logic and setting the <xref:System.Windows.Data.CollectionView.Filter%2A?displayProperty=nameWithType> property to apply the filter.</span></span> <span data-ttu-id="f1da4-164">若要查看此方法的範例，請參閱[在視圖中篩選資料](../data/how-to-filter-data-in-a-view.md)。</span><span class="sxs-lookup"><span data-stu-id="f1da4-164">To see an example of this method, see [Filter Data in a View](../data/how-to-filter-data-in-a-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="f1da4-165">範例</span><span class="sxs-lookup"><span data-stu-id="f1da4-165">Example</span></span>

<span data-ttu-id="f1da4-166">下列範例示範如何在中分組、排序和篩選 `Task` 資料， <xref:System.Windows.Data.CollectionViewSource> 並在中顯示已分組、已排序和已篩選的 `Task` 資料 <xref:System.Windows.Controls.DataGrid> 。</span><span class="sxs-lookup"><span data-stu-id="f1da4-166">The following example demonstrates grouping, sorting, and filtering `Task` data in a <xref:System.Windows.Data.CollectionViewSource> and displaying the grouped, sorted, and filtered `Task` data in a <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="f1da4-167"><xref:System.Windows.Data.CollectionViewSource>是用來做 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 為的 <xref:System.Windows.Controls.DataGrid> 。</span><span class="sxs-lookup"><span data-stu-id="f1da4-167">The <xref:System.Windows.Data.CollectionViewSource> is used as the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> for the <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="f1da4-168">群組、排序和篩選會在上執行， <xref:System.Windows.Data.CollectionViewSource> 並顯示在 UI 中 <xref:System.Windows.Controls.DataGrid> 。</span><span class="sxs-lookup"><span data-stu-id="f1da4-168">Grouping, sorting, and filtering are performed on the <xref:System.Windows.Data.CollectionViewSource> and are displayed in the <xref:System.Windows.Controls.DataGrid> UI.</span></span>

<span data-ttu-id="f1da4-169">若要測試此範例，您必須調整 DGGroupSortFilterExample 名稱以符合您的專案名稱。</span><span class="sxs-lookup"><span data-stu-id="f1da4-169">To test this example, you will need to adjust the DGGroupSortFilterExample name to match your project name.</span></span> <span data-ttu-id="f1da4-170">如果您使用 Visual Basic，則必須將的類別名稱變更為 <xref:System.Windows.Window> 下列。</span><span class="sxs-lookup"><span data-stu-id="f1da4-170">If you are using Visual Basic, you will need to change the class name for <xref:System.Windows.Window> to the following.</span></span>

`<Window x:Class="MainWindow"`

[!code-xaml[DataGrid_GroupSortFilter#000](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#000)]
[!code-csharp[DataGrid_GroupSortFilter#100](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#100)]
[!code-vb[DataGrid_GroupSortFilter#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#100)]

## <a name="see-also"></a><span data-ttu-id="f1da4-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1da4-171">See also</span></span>

- [<span data-ttu-id="f1da4-172">資料系結總覽</span><span class="sxs-lookup"><span data-stu-id="f1da4-172">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="f1da4-173">建立並系結至 ObservableCollection</span><span class="sxs-lookup"><span data-stu-id="f1da4-173">Create and Bind to an ObservableCollection</span></span>](../data/how-to-create-and-bind-to-an-observablecollection.md)
- [<span data-ttu-id="f1da4-174">篩選視圖中的資料</span><span class="sxs-lookup"><span data-stu-id="f1da4-174">Filter Data in a View</span></span>](../data/how-to-filter-data-in-a-view.md)
- [<span data-ttu-id="f1da4-175">排序視圖中的資料</span><span class="sxs-lookup"><span data-stu-id="f1da4-175">Sort Data in a View</span></span>](../data/how-to-sort-data-in-a-view.md)
- [<span data-ttu-id="f1da4-176">使用 XAML 中的視圖排序和分組資料</span><span class="sxs-lookup"><span data-stu-id="f1da4-176">Sort and Group Data Using a View in XAML</span></span>](../data/how-to-sort-and-group-data-using-a-view-in-xaml.md)

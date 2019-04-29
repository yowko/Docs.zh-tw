---
title: HOW TO：群組、 排序和篩選 DataGrid 控制項中的資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], sort
- DataGrid [WPF], group
- DataGrid [WPF], filter
ms.assetid: 03345e85-89e3-4aec-9ed0-3b80759df770
ms.openlocfilehash: 81fdb0a6d5602f612c55d7e790ca9a0fe56c144e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61771084"
---
# <a name="how-to-group-sort-and-filter-data-in-the-datagrid-control"></a><span data-ttu-id="6d9df-102">HOW TO：群組、 排序和 DataGrid 控制項中的篩選資料</span><span class="sxs-lookup"><span data-stu-id="6d9df-102">How to: Group, sort, and filter data in the DataGrid control</span></span>

<span data-ttu-id="6d9df-103">通常很有用，檢視中的資料<xref:System.Windows.Controls.DataGrid>以不同的方式，藉由將分組、 排序和篩選資料。</span><span class="sxs-lookup"><span data-stu-id="6d9df-103">It is often useful to view data in a <xref:System.Windows.Controls.DataGrid> in different ways by grouping, sorting, and filtering the data.</span></span> <span data-ttu-id="6d9df-104">群組、 排序和篩選中的資料<xref:System.Windows.Controls.DataGrid>，將它繫結<xref:System.Windows.Data.CollectionView>支援這些函式。</span><span class="sxs-lookup"><span data-stu-id="6d9df-104">To group, sort, and filter the data in a <xref:System.Windows.Controls.DataGrid>, you bind it to a <xref:System.Windows.Data.CollectionView> that supports these functions.</span></span> <span data-ttu-id="6d9df-105">您可以使用中的資料<xref:System.Windows.Data.CollectionView>而不會影響基礎來源資料。</span><span class="sxs-lookup"><span data-stu-id="6d9df-105">You can then work with the data in the <xref:System.Windows.Data.CollectionView> without affecting the underlying source data.</span></span> <span data-ttu-id="6d9df-106">集合檢視中的變更會反映在<xref:System.Windows.Controls.DataGrid>使用者介面 (UI)。</span><span class="sxs-lookup"><span data-stu-id="6d9df-106">The changes in the collection view are reflected in the <xref:System.Windows.Controls.DataGrid> user interface (UI).</span></span>

<span data-ttu-id="6d9df-107"><xref:System.Windows.Data.CollectionView>類別會提供群組和排序的資料來源會實作功能<xref:System.Collections.IEnumerable>介面。</span><span class="sxs-lookup"><span data-stu-id="6d9df-107">The <xref:System.Windows.Data.CollectionView> class provides grouping and sorting functionality for a data source that implements the <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="6d9df-108"><xref:System.Windows.Data.CollectionViewSource>類別可讓您設定的屬性<xref:System.Windows.Data.CollectionView>從 XAML。</span><span class="sxs-lookup"><span data-stu-id="6d9df-108">The <xref:System.Windows.Data.CollectionViewSource> class enables you to set the properties of a <xref:System.Windows.Data.CollectionView> from XAML.</span></span>

<span data-ttu-id="6d9df-109">在此範例中，一堆`Task`物件的繫結至<xref:System.Windows.Data.CollectionViewSource>。</span><span class="sxs-lookup"><span data-stu-id="6d9df-109">In this example, a collection of `Task` objects is bound to a <xref:System.Windows.Data.CollectionViewSource>.</span></span> <span data-ttu-id="6d9df-110"><xref:System.Windows.Data.CollectionViewSource>做為<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>如<xref:System.Windows.Controls.DataGrid>。</span><span class="sxs-lookup"><span data-stu-id="6d9df-110">The <xref:System.Windows.Data.CollectionViewSource> is used as the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> for the <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="6d9df-111">分組、 排序和篩選會對<xref:System.Windows.Data.CollectionViewSource>而且會顯示在<xref:System.Windows.Controls.DataGrid>UI。</span><span class="sxs-lookup"><span data-stu-id="6d9df-111">Grouping, sorting, and filtering are performed on the <xref:System.Windows.Data.CollectionViewSource> and are displayed in the <xref:System.Windows.Controls.DataGrid> UI.</span></span>

<span data-ttu-id="6d9df-112">![分組資料格中](././media/wpf-datagridgroups.png "WPF_DataGridGroups") DataGrid 中的群組資料</span><span class="sxs-lookup"><span data-stu-id="6d9df-112">![Grouped data in a DataGrid](././media/wpf-datagridgroups.png "WPF_DataGridGroups") Grouped data in a DataGrid</span></span>

## <a name="using-a-collectionviewsource-as-an-itemssource"></a><span data-ttu-id="6d9df-113">使用 CollectionViewSource ItemsSource</span><span class="sxs-lookup"><span data-stu-id="6d9df-113">Using a CollectionViewSource as an ItemsSource</span></span>

<span data-ttu-id="6d9df-114">要分組、 排序和篩選中的資料<xref:System.Windows.Controls.DataGrid>控制項，您將繫結<xref:System.Windows.Controls.DataGrid>到<xref:System.Windows.Data.CollectionView>支援這些函式。</span><span class="sxs-lookup"><span data-stu-id="6d9df-114">To group, sort, and filter data in a <xref:System.Windows.Controls.DataGrid> control, you bind the <xref:System.Windows.Controls.DataGrid> to a <xref:System.Windows.Data.CollectionView> that supports these functions.</span></span> <span data-ttu-id="6d9df-115">在此範例中，<xref:System.Windows.Controls.DataGrid>繫結至<xref:System.Windows.Data.CollectionViewSource>提供的這些函式<xref:System.Collections.Generic.List%601>的`Task`物件。</span><span class="sxs-lookup"><span data-stu-id="6d9df-115">In this example, the <xref:System.Windows.Controls.DataGrid> is bound to a <xref:System.Windows.Data.CollectionViewSource> that provides these functions for a <xref:System.Collections.Generic.List%601> of `Task` objects.</span></span>

### <a name="to-bind-a-datagrid-to-a-collectionviewsource"></a><span data-ttu-id="6d9df-116">若要將 DataGrid 繫結至 CollectionViewSource</span><span class="sxs-lookup"><span data-stu-id="6d9df-116">To bind a DataGrid to a CollectionViewSource</span></span>

1. <span data-ttu-id="6d9df-117">建立資料集合，實作<xref:System.Collections.IEnumerable>介面。</span><span class="sxs-lookup"><span data-stu-id="6d9df-117">Create a data collection that implements the <xref:System.Collections.IEnumerable> interface.</span></span>

    <span data-ttu-id="6d9df-118">如果您使用<xref:System.Collections.Generic.List%601>若要建立您的集合，您應該建立新的類別繼承自<xref:System.Collections.Generic.List%601>而不是具現化的執行個體<xref:System.Collections.Generic.List%601>。</span><span class="sxs-lookup"><span data-stu-id="6d9df-118">If you use <xref:System.Collections.Generic.List%601> to create your collection, you should create a new class that inherits from <xref:System.Collections.Generic.List%601> instead of instantiating an instance of <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="6d9df-119">這可讓您為資料繫結至 XAML 中的集合。</span><span class="sxs-lookup"><span data-stu-id="6d9df-119">This enables you to data bind to the collection in XAML.</span></span>

    > [!NOTE]
    > <span data-ttu-id="6d9df-120">集合中的物件必須實作<xref:System.ComponentModel.INotifyPropertyChanged>已變更的介面和<xref:System.ComponentModel.IEditableObject>為了讓介面<xref:System.Windows.Controls.DataGrid>來正確回應屬性變更及編輯。</span><span class="sxs-lookup"><span data-stu-id="6d9df-120">The objects in the collection must implement the <xref:System.ComponentModel.INotifyPropertyChanged> changed interface and the <xref:System.ComponentModel.IEditableObject> interface in order for the <xref:System.Windows.Controls.DataGrid> to respond correctly to property changes and edits.</span></span> <span data-ttu-id="6d9df-121">如需詳細資訊，請參閱[實作屬性變更通知](../data/how-to-implement-property-change-notification.md)。</span><span class="sxs-lookup"><span data-stu-id="6d9df-121">For more information, see [Implement Property Change Notification](../data/how-to-implement-property-change-notification.md).</span></span>

    [!code-csharp[DataGrid_GroupSortFilter#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#101)]
    [!code-vb[DataGrid_GroupSortFilter#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#101)]

2. <span data-ttu-id="6d9df-122">在 XAML，請在建立集合類別的執行個體，並設定[X:key 指示詞](../../xaml-services/x-key-directive.md)。</span><span class="sxs-lookup"><span data-stu-id="6d9df-122">In XAML, create an instance of the collection class and set the [x:Key Directive](../../xaml-services/x-key-directive.md).</span></span>

3. <span data-ttu-id="6d9df-123">在 XAML 中，建立的執行個體<xref:System.Windows.Data.CollectionViewSource>類別中，將[X:key 指示詞](../../xaml-services/x-key-directive.md)，並設定您的集合類別做為執行個體<xref:System.Windows.Data.CollectionViewSource.Source%2A>。</span><span class="sxs-lookup"><span data-stu-id="6d9df-123">In XAML, create an instance of the <xref:System.Windows.Data.CollectionViewSource> class, set the [x:Key Directive](../../xaml-services/x-key-directive.md), and set the instance of your collection class as the <xref:System.Windows.Data.CollectionViewSource.Source%2A>.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#201](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml#201)]

4. <span data-ttu-id="6d9df-124">建立的執行個體<xref:System.Windows.Controls.DataGrid>類別，並設定<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>屬性設<xref:System.Windows.Data.CollectionViewSource>。</span><span class="sxs-lookup"><span data-stu-id="6d9df-124">Create an instance of the <xref:System.Windows.Controls.DataGrid> class, and set the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property to the <xref:System.Windows.Data.CollectionViewSource>.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#002](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#002)]

5. <span data-ttu-id="6d9df-125">若要存取<xref:System.Windows.Data.CollectionViewSource>從您的程式碼中，使用<xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A>方法來取得參考<xref:System.Windows.Data.CollectionViewSource>。</span><span class="sxs-lookup"><span data-stu-id="6d9df-125">To access the <xref:System.Windows.Data.CollectionViewSource> from your code, use the <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> method to get a reference to the <xref:System.Windows.Data.CollectionViewSource>.</span></span>

    [!code-csharp[DataGrid_GroupSortFilter#102](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#102)]
    [!code-vb[DataGrid_GroupSortFilter#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#102)]

## <a name="grouping-items-in-a-datagrid"></a><span data-ttu-id="6d9df-126">DataGrid 中分組項目</span><span class="sxs-lookup"><span data-stu-id="6d9df-126">Grouping items in a DataGrid</span></span>

<span data-ttu-id="6d9df-127">若要指定如何在分組項目<xref:System.Windows.Controls.DataGrid>，您使用<xref:System.Windows.Data.PropertyGroupDescription>類型來分組來源檢視中的項目。</span><span class="sxs-lookup"><span data-stu-id="6d9df-127">To specify how items are grouped in a <xref:System.Windows.Controls.DataGrid>, you use the <xref:System.Windows.Data.PropertyGroupDescription> type to group the items in the source view.</span></span>

### <a name="to-group-items-in-a-datagrid-using-xaml"></a><span data-ttu-id="6d9df-128">使用 XAML 的 DataGrid 中的群組項目</span><span class="sxs-lookup"><span data-stu-id="6d9df-128">To group items in a DataGrid using XAML</span></span>

1. <span data-ttu-id="6d9df-129">建立<xref:System.Windows.Data.PropertyGroupDescription>，指定要依群組的屬性。</span><span class="sxs-lookup"><span data-stu-id="6d9df-129">Create a <xref:System.Windows.Data.PropertyGroupDescription> that specifies the property to group by.</span></span> <span data-ttu-id="6d9df-130">在 XAML 或程式碼中，您可以指定屬性。</span><span class="sxs-lookup"><span data-stu-id="6d9df-130">You can specify the property in XAML or in code.</span></span>

   1. <span data-ttu-id="6d9df-131">在 XAML 中，設定<xref:System.Windows.Data.PropertyGroupDescription.PropertyName%2A>可依群組屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="6d9df-131">In XAML, set the <xref:System.Windows.Data.PropertyGroupDescription.PropertyName%2A> to the name of the property to group by.</span></span>

   2. <span data-ttu-id="6d9df-132">程式碼中，將屬性的名稱傳遞至建構函式的群組。</span><span class="sxs-lookup"><span data-stu-id="6d9df-132">In code, pass the name of the property to group by to the constructor.</span></span>

2. <span data-ttu-id="6d9df-133">新增<xref:System.Windows.Data.PropertyGroupDescription>至<xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A?displayProperty=nameWithType>集合。</span><span class="sxs-lookup"><span data-stu-id="6d9df-133">Add the <xref:System.Windows.Data.PropertyGroupDescription> to the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A?displayProperty=nameWithType> collection.</span></span>

3. <span data-ttu-id="6d9df-134">新增的其他執行個體<xref:System.Windows.Data.PropertyGroupDescription>至<xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A>来加入多個層級的群組集合。</span><span class="sxs-lookup"><span data-stu-id="6d9df-134">Add additional instances of <xref:System.Windows.Data.PropertyGroupDescription> to the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> collection to add more levels of grouping.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#012](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#012)]
    [!code-csharp[DataGrid_GroupSortFilter#112](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#112)]
    [!code-vb[DataGrid_GroupSortFilter#112](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#112)]

4. <span data-ttu-id="6d9df-135">若要移除群組，請移除<xref:System.Windows.Data.PropertyGroupDescription>從<xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A>集合。</span><span class="sxs-lookup"><span data-stu-id="6d9df-135">To remove a group, remove the <xref:System.Windows.Data.PropertyGroupDescription> from the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> collection.</span></span>

5. <span data-ttu-id="6d9df-136">若要移除所有群組，請呼叫<xref:System.Collections.ObjectModel.Collection%601.Clear%2A>方法的<xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A>集合。</span><span class="sxs-lookup"><span data-stu-id="6d9df-136">To remove all groups, call the <xref:System.Collections.ObjectModel.Collection%601.Clear%2A> method of the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> collection.</span></span>

    [!code-csharp[DataGrid_GroupSortFilter#114](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#114)]
    [!code-vb[DataGrid_GroupSortFilter#114](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#114)]

<span data-ttu-id="6d9df-137">當項目會分組放入<xref:System.Windows.Controls.DataGrid>，您可以定義<xref:System.Windows.Controls.GroupStyle>指定每個群組的外觀。</span><span class="sxs-lookup"><span data-stu-id="6d9df-137">When items are grouped in the <xref:System.Windows.Controls.DataGrid>, you can define a <xref:System.Windows.Controls.GroupStyle> that specifies the appearance of each group.</span></span> <span data-ttu-id="6d9df-138">您套用<xref:System.Windows.Controls.GroupStyle>將它加入至<xref:System.Windows.Controls.ItemsControl.GroupStyle%2A>DataGrid 的集合。</span><span class="sxs-lookup"><span data-stu-id="6d9df-138">You apply the <xref:System.Windows.Controls.GroupStyle> by adding it to the <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> collection of the DataGrid.</span></span> <span data-ttu-id="6d9df-139">如果您有多個層級的群組，您可以套用到每個群組層級的不同的樣式。</span><span class="sxs-lookup"><span data-stu-id="6d9df-139">If you have multiple levels of grouping, you can apply different styles to each group level.</span></span> <span data-ttu-id="6d9df-140">樣式定義所在的順序套用。</span><span class="sxs-lookup"><span data-stu-id="6d9df-140">Styles are applied in the order in which they are defined.</span></span> <span data-ttu-id="6d9df-141">比方說，如果您定義兩種樣式，第一個會套用到上方的層級資料列群組。</span><span class="sxs-lookup"><span data-stu-id="6d9df-141">For example, if you define two styles, the first will be applied to top level row groups.</span></span> <span data-ttu-id="6d9df-142">第二個的樣式會套用至第二個層級的所有資料列群組和較低。</span><span class="sxs-lookup"><span data-stu-id="6d9df-142">The second style will be applied to all row groups at the second level and lower.</span></span> <span data-ttu-id="6d9df-143"><xref:System.Windows.FrameworkElement.DataContext%2A>的<xref:System.Windows.Controls.GroupStyle>是<xref:System.Windows.Data.CollectionViewGroup>群組代表。</span><span class="sxs-lookup"><span data-stu-id="6d9df-143">The <xref:System.Windows.FrameworkElement.DataContext%2A> of the <xref:System.Windows.Controls.GroupStyle> is the <xref:System.Windows.Data.CollectionViewGroup> that the group represents.</span></span>

### <a name="to-change-the-appearance-of-row-group-headers"></a><span data-ttu-id="6d9df-144">若要變更資料列群組標頭的外觀</span><span class="sxs-lookup"><span data-stu-id="6d9df-144">To change the appearance of row group headers</span></span>

1. <span data-ttu-id="6d9df-145">建立<xref:System.Windows.Controls.GroupStyle>，定義資料列群組的外觀。</span><span class="sxs-lookup"><span data-stu-id="6d9df-145">Create a <xref:System.Windows.Controls.GroupStyle> that defines the appearance of the row group.</span></span>

2. <span data-ttu-id="6d9df-146">放<xref:System.Windows.Controls.GroupStyle>內`<DataGrid.GroupStyle>`標記。</span><span class="sxs-lookup"><span data-stu-id="6d9df-146">Put the <xref:System.Windows.Controls.GroupStyle> inside the `<DataGrid.GroupStyle>` tags.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#003](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#003)]

## <a name="sorting-items-in-a-datagrid"></a><span data-ttu-id="6d9df-147">排序 DataGrid 中的項目</span><span class="sxs-lookup"><span data-stu-id="6d9df-147">Sorting items in a DataGrid</span></span>

<span data-ttu-id="6d9df-148">若要指定項目會按照<xref:System.Windows.Controls.DataGrid>，您使用<xref:System.ComponentModel.SortDescription>要排序的來源檢視中的項目型別。</span><span class="sxs-lookup"><span data-stu-id="6d9df-148">To specify how items are sorted in a <xref:System.Windows.Controls.DataGrid>, you use the <xref:System.ComponentModel.SortDescription> type to sort the items in the source view.</span></span>

### <a name="to-sort-items-in-a-datagrid"></a><span data-ttu-id="6d9df-149">若要排序 DataGrid 中的項目</span><span class="sxs-lookup"><span data-stu-id="6d9df-149">To sort items in a DataGrid</span></span>

1. <span data-ttu-id="6d9df-150">建立<xref:System.ComponentModel.SortDescription>，指定排序所依據的屬性。</span><span class="sxs-lookup"><span data-stu-id="6d9df-150">Create a <xref:System.ComponentModel.SortDescription> that specifies the property to sort by.</span></span> <span data-ttu-id="6d9df-151">在 XAML 或程式碼中，您可以指定屬性。</span><span class="sxs-lookup"><span data-stu-id="6d9df-151">You can specify the property in XAML or in code.</span></span>

    1. <span data-ttu-id="6d9df-152">在 XAML 中，設定<xref:System.ComponentModel.SortDescription.PropertyName%2A>排序所依據之屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="6d9df-152">In XAML, set the <xref:System.ComponentModel.SortDescription.PropertyName%2A> to the name of the property to sort by.</span></span>

    2. <span data-ttu-id="6d9df-153">在程式碼中，會傳遞要排序之屬性的名稱和<xref:System.ComponentModel.ListSortDirection>建構函式。</span><span class="sxs-lookup"><span data-stu-id="6d9df-153">In code, pass the name of the property to sort by and the <xref:System.ComponentModel.ListSortDirection> to the constructor.</span></span>

2. <span data-ttu-id="6d9df-154">新增<xref:System.ComponentModel.SortDescription>至<xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A?displayProperty=nameWithType>集合。</span><span class="sxs-lookup"><span data-stu-id="6d9df-154">Add the <xref:System.ComponentModel.SortDescription> to the <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A?displayProperty=nameWithType> collection.</span></span>

3. <span data-ttu-id="6d9df-155">新增的其他執行個體<xref:System.ComponentModel.SortDescription>至<xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A>依其他屬性排序的集合。</span><span class="sxs-lookup"><span data-stu-id="6d9df-155">Add additional instances of <xref:System.ComponentModel.SortDescription> to the <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A> collection to sort by additional properties.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#011](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#011)]
    [!code-csharp[DataGrid_GroupSortFilter#211](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml.cs#211)]
    [!code-vb[DataGrid_GroupSortFilter#211](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#211)]

## <a name="filtering-items-in-a-datagrid"></a><span data-ttu-id="6d9df-156">篩選 DataGrid 中的項目</span><span class="sxs-lookup"><span data-stu-id="6d9df-156">Filtering items in a DataGrid</span></span>

<span data-ttu-id="6d9df-157">中的篩選器項目<xref:System.Windows.Controls.DataGrid>使用<xref:System.Windows.Data.CollectionViewSource>，您提供的處理常式中的篩選邏輯<xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType>事件。</span><span class="sxs-lookup"><span data-stu-id="6d9df-157">To filter items in a <xref:System.Windows.Controls.DataGrid> using a <xref:System.Windows.Data.CollectionViewSource>, you provide the filtering logic in the handler for the <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> event.</span></span>

### <a name="to-filter-items-in-a-datagrid"></a><span data-ttu-id="6d9df-158">若要篩選的 DataGrid 中的項目</span><span class="sxs-lookup"><span data-stu-id="6d9df-158">To filter items in a DataGrid</span></span>

1. <span data-ttu-id="6d9df-159">加入的處理常式<xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType>事件。</span><span class="sxs-lookup"><span data-stu-id="6d9df-159">Add a handler for the <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> event.</span></span>

2. <span data-ttu-id="6d9df-160">在 <xref:System.Windows.Data.CollectionViewSource.Filter>事件處理常式，定義篩選的邏輯。</span><span class="sxs-lookup"><span data-stu-id="6d9df-160">In the <xref:System.Windows.Data.CollectionViewSource.Filter> event handler, define the filtering logic.</span></span>

    <span data-ttu-id="6d9df-161">每次重新整理檢視，將會套用篩選條件。</span><span class="sxs-lookup"><span data-stu-id="6d9df-161">The filter will be applied every time the view is refreshed.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#013](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#013)]
    [!code-csharp[DataGrid_GroupSortFilter#113](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#113)]
    [!code-vb[DataGrid_GroupSortFilter#113](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#113)]

<span data-ttu-id="6d9df-162">或者，您可以在此篩選中的項目<xref:System.Windows.Controls.DataGrid>藉由建立方法，提供篩選邏輯和設定<xref:System.Windows.Data.CollectionView.Filter%2A?displayProperty=nameWithType>將篩選套用到的屬性。</span><span class="sxs-lookup"><span data-stu-id="6d9df-162">Alternatively, you can filter items in a <xref:System.Windows.Controls.DataGrid> by creating a method that provides the filtering logic and setting the <xref:System.Windows.Data.CollectionView.Filter%2A?displayProperty=nameWithType> property to apply the filter.</span></span> <span data-ttu-id="6d9df-163">若要查看這個方法的範例，請參閱[檢視中的篩選資料](../data/how-to-filter-data-in-a-view.md)。</span><span class="sxs-lookup"><span data-stu-id="6d9df-163">To see an example of this method, see [Filter Data in a View](../data/how-to-filter-data-in-a-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="6d9df-164">範例</span><span class="sxs-lookup"><span data-stu-id="6d9df-164">Example</span></span>

<span data-ttu-id="6d9df-165">下列範例示範如何分組、 排序和篩選`Task`中的資料<xref:System.Windows.Data.CollectionViewSource>和顯示分組、 排序和篩選`Task`中的資料<xref:System.Windows.Controls.DataGrid>。</span><span class="sxs-lookup"><span data-stu-id="6d9df-165">The following example demonstrates grouping, sorting, and filtering `Task` data in a <xref:System.Windows.Data.CollectionViewSource> and displaying the grouped, sorted, and filtered `Task` data in a <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="6d9df-166"><xref:System.Windows.Data.CollectionViewSource>做為<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>如<xref:System.Windows.Controls.DataGrid>。</span><span class="sxs-lookup"><span data-stu-id="6d9df-166">The <xref:System.Windows.Data.CollectionViewSource> is used as the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> for the <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="6d9df-167">分組、 排序和篩選會對<xref:System.Windows.Data.CollectionViewSource>而且會顯示在<xref:System.Windows.Controls.DataGrid>UI。</span><span class="sxs-lookup"><span data-stu-id="6d9df-167">Grouping, sorting, and filtering are performed on the <xref:System.Windows.Data.CollectionViewSource> and are displayed in the <xref:System.Windows.Controls.DataGrid> UI.</span></span>

<span data-ttu-id="6d9df-168">若要測試此範例中，您必須調整 DGGroupSortFilterExample 名稱以符合您的專案名稱。</span><span class="sxs-lookup"><span data-stu-id="6d9df-168">To test this example, you will need to adjust the DGGroupSortFilterExample name to match your project name.</span></span> <span data-ttu-id="6d9df-169">如果您使用 Visual Basic，您必須變更類別名稱<xref:System.Windows.Window>如下。</span><span class="sxs-lookup"><span data-stu-id="6d9df-169">If you are using Visual Basic, you will need to change the class name for <xref:System.Windows.Window> to the following.</span></span>

`<Window x:Class="MainWindow"`

[!code-xaml[DataGrid_GroupSortFilter#000](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#000)]
[!code-csharp[DataGrid_GroupSortFilter#100](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#100)]
[!code-vb[DataGrid_GroupSortFilter#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#100)]

## <a name="see-also"></a><span data-ttu-id="6d9df-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6d9df-170">See also</span></span>

- [<span data-ttu-id="6d9df-171">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="6d9df-171">Data Binding Overview</span></span>](../data/data-binding-overview.md)
- [<span data-ttu-id="6d9df-172">建立和繫結至 ObservableCollection</span><span class="sxs-lookup"><span data-stu-id="6d9df-172">Create and Bind to an ObservableCollection</span></span>](../data/how-to-create-and-bind-to-an-observablecollection.md)
- [<span data-ttu-id="6d9df-173">篩選檢視中的資料</span><span class="sxs-lookup"><span data-stu-id="6d9df-173">Filter Data in a View</span></span>](../data/how-to-filter-data-in-a-view.md)
- [<span data-ttu-id="6d9df-174">排序檢視中的資料</span><span class="sxs-lookup"><span data-stu-id="6d9df-174">Sort Data in a View</span></span>](../data/how-to-sort-data-in-a-view.md)
- [<span data-ttu-id="6d9df-175">使用 XAML 中的檢視排序和群組資料</span><span class="sxs-lookup"><span data-stu-id="6d9df-175">Sort and Group Data Using a View in XAML</span></span>](../data/how-to-sort-and-group-data-using-a-view-in-xaml.md)

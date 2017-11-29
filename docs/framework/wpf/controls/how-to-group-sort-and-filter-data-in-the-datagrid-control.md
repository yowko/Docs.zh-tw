---
title: "如何：在 DataGrid 控制項中分組、排序和篩選資料"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], sort
- DataGrid [WPF], group
- DataGrid [WPF], filter
ms.assetid: 03345e85-89e3-4aec-9ed0-3b80759df770
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b3c8afacfafbe14794bf17a4e9a4df7c175a3668
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-group-sort-and-filter-data-in-the-datagrid-control"></a><span data-ttu-id="fec0a-102">如何：在 DataGrid 控制項中分組、排序和篩選資料</span><span class="sxs-lookup"><span data-stu-id="fec0a-102">How to: Group, Sort, and Filter Data in the DataGrid Control</span></span>
<span data-ttu-id="fec0a-103">通常會很有用，檢視中的資料<xref:System.Windows.Controls.DataGrid>透過分組、 排序和篩選的資料不同的方式。</span><span class="sxs-lookup"><span data-stu-id="fec0a-103">It is often useful to view data in a <xref:System.Windows.Controls.DataGrid> in different ways by grouping, sorting, and filtering the data.</span></span> <span data-ttu-id="fec0a-104">群組、 排序和篩選中的資料<xref:System.Windows.Controls.DataGrid>，您將它繫結<xref:System.Windows.Data.CollectionView>支援這些函式。</span><span class="sxs-lookup"><span data-stu-id="fec0a-104">To group, sort, and filter the data in a <xref:System.Windows.Controls.DataGrid>, you bind it to a <xref:System.Windows.Data.CollectionView> that supports these functions.</span></span> <span data-ttu-id="fec0a-105">您可以使用中的資料<xref:System.Windows.Data.CollectionView>而不會影響基礎來源資料。</span><span class="sxs-lookup"><span data-stu-id="fec0a-105">You can then work with the data in the <xref:System.Windows.Data.CollectionView> without affecting the underlying source data.</span></span> <span data-ttu-id="fec0a-106">集合檢視中的變更會反映在<xref:System.Windows.Controls.DataGrid>使用者介面 (UI)。</span><span class="sxs-lookup"><span data-stu-id="fec0a-106">The changes in the collection view are reflected in the <xref:System.Windows.Controls.DataGrid> user interface (UI).</span></span>  
  
 <span data-ttu-id="fec0a-107"><xref:System.Windows.Data.CollectionView>類別會提供群組和排序的資料來源所實作的功能<xref:System.Collections.IEnumerable>介面。</span><span class="sxs-lookup"><span data-stu-id="fec0a-107">The <xref:System.Windows.Data.CollectionView> class provides grouping and sorting functionality for a data source that implements the <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="fec0a-108"><xref:System.Windows.Data.CollectionViewSource>類別可讓您設定的屬性<xref:System.Windows.Data.CollectionView>從 XAML。</span><span class="sxs-lookup"><span data-stu-id="fec0a-108">The <xref:System.Windows.Data.CollectionViewSource> class enables you to set the properties of a <xref:System.Windows.Data.CollectionView> from XAML.</span></span>  
  
 <span data-ttu-id="fec0a-109">在此範例中，集合`Task`物件繫結至<xref:System.Windows.Data.CollectionViewSource>。</span><span class="sxs-lookup"><span data-stu-id="fec0a-109">In this example, a collection of `Task` objects is bound to a <xref:System.Windows.Data.CollectionViewSource>.</span></span> <span data-ttu-id="fec0a-110"><xref:System.Windows.Data.CollectionViewSource>做<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>如<xref:System.Windows.Controls.DataGrid>。</span><span class="sxs-lookup"><span data-stu-id="fec0a-110">The <xref:System.Windows.Data.CollectionViewSource> is used as the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> for the <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="fec0a-111">分組、 排序和篩選會對<xref:System.Windows.Data.CollectionViewSource>而且會顯示在<xref:System.Windows.Controls.DataGrid>UI。</span><span class="sxs-lookup"><span data-stu-id="fec0a-111">Grouping, sorting, and filtering are performed on the <xref:System.Windows.Data.CollectionViewSource> and are displayed in the <xref:System.Windows.Controls.DataGrid> UI.</span></span>  
  
 <span data-ttu-id="fec0a-112">![分組資料格中](../../../../docs/framework/wpf/controls/media/wpf-datagridgroups.png "WPF_DataGridGroups")</span><span class="sxs-lookup"><span data-stu-id="fec0a-112">![Grouped data in a DataGrid](../../../../docs/framework/wpf/controls/media/wpf-datagridgroups.png "WPF_DataGridGroups")</span></span>  
<span data-ttu-id="fec0a-113">DataGrid 中分組的資料</span><span class="sxs-lookup"><span data-stu-id="fec0a-113">Grouped Data in a DataGrid</span></span>  
  
## <a name="using-a-collectionviewsource-as-an-itemssource"></a><span data-ttu-id="fec0a-114">使用 ItemsSource CollectionViewSource</span><span class="sxs-lookup"><span data-stu-id="fec0a-114">Using a CollectionViewSource as an ItemsSource</span></span>  
 <span data-ttu-id="fec0a-115">群組、 排序和篩選中的資料來<xref:System.Windows.Controls.DataGrid>控制項，您將繫結<xref:System.Windows.Controls.DataGrid>至<xref:System.Windows.Data.CollectionView>支援這些函式。</span><span class="sxs-lookup"><span data-stu-id="fec0a-115">To group, sort, and filter data in a <xref:System.Windows.Controls.DataGrid> control, you bind the <xref:System.Windows.Controls.DataGrid> to a <xref:System.Windows.Data.CollectionView> that supports these functions.</span></span> <span data-ttu-id="fec0a-116">在此範例中，<xref:System.Windows.Controls.DataGrid>繫結至<xref:System.Windows.Data.CollectionViewSource>提供這些函式的<xref:System.Collections.Generic.List%601>的`Task`物件。</span><span class="sxs-lookup"><span data-stu-id="fec0a-116">In this example, the <xref:System.Windows.Controls.DataGrid> is bound to a <xref:System.Windows.Data.CollectionViewSource> that provides these functions for a <xref:System.Collections.Generic.List%601> of `Task` objects.</span></span>  
  
#### <a name="to-bind-a-datagrid-to-a-collectionviewsource"></a><span data-ttu-id="fec0a-117">若要將 DataGrid 繫結至 CollectionViewSource</span><span class="sxs-lookup"><span data-stu-id="fec0a-117">To bind a DataGrid to a CollectionViewSource</span></span>  
  
1.  <span data-ttu-id="fec0a-118">建立資料集合中實作<xref:System.Collections.IEnumerable>介面。</span><span class="sxs-lookup"><span data-stu-id="fec0a-118">Create a data collection that implements the <xref:System.Collections.IEnumerable> interface.</span></span>  
  
     <span data-ttu-id="fec0a-119">如果您使用<xref:System.Collections.Generic.List%601>若要建立您的集合，您應該建立新的類別繼承自<xref:System.Collections.Generic.List%601>而不是具現化的執行個體<xref:System.Collections.Generic.List%601>。</span><span class="sxs-lookup"><span data-stu-id="fec0a-119">If you use <xref:System.Collections.Generic.List%601> to create your collection, you should create a new class that inherits from <xref:System.Collections.Generic.List%601> instead of instantiating an instance of <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="fec0a-120">這可讓您為資料繫結至 XAML 的集合。</span><span class="sxs-lookup"><span data-stu-id="fec0a-120">This enables you to data bind to the collection in XAML.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fec0a-121">集合中的物件必須實作<xref:System.ComponentModel.INotifyPropertyChanged>已變更的介面和<xref:System.ComponentModel.IEditableObject>介面讓<xref:System.Windows.Controls.DataGrid>來正確回應屬性變更及編輯。</span><span class="sxs-lookup"><span data-stu-id="fec0a-121">The objects in the collection must implement the <xref:System.ComponentModel.INotifyPropertyChanged> changed interface and the <xref:System.ComponentModel.IEditableObject> interface in order for the <xref:System.Windows.Controls.DataGrid> to respond correctly to property changes and edits.</span></span> <span data-ttu-id="fec0a-122">如需詳細資訊，請參閱[實作屬性變更通知](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md)。</span><span class="sxs-lookup"><span data-stu-id="fec0a-122">For more information, see [Implement Property Change Notification](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md).</span></span>  
  
     [!code-csharp[DataGrid_GroupSortFilter#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#101)]
     [!code-vb[DataGrid_GroupSortFilter#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#101)]  
  
2.  <span data-ttu-id="fec0a-123">在 XAML 中，建立集合類別的執行個體，並設定[X:key 指示詞](../../../../docs/framework/xaml-services/x-key-directive.md)。</span><span class="sxs-lookup"><span data-stu-id="fec0a-123">In XAML, create an instance of the collection class and set the [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md).</span></span>  
  
3.  <span data-ttu-id="fec0a-124">在 XAML 中，建立的執行個體<xref:System.Windows.Data.CollectionViewSource>類別中，設定[X:key 指示詞](../../../../docs/framework/xaml-services/x-key-directive.md)，並設定您的集合類別做為執行個體<xref:System.Windows.Data.CollectionViewSource.Source%2A>。</span><span class="sxs-lookup"><span data-stu-id="fec0a-124">In XAML, create an instance of the <xref:System.Windows.Data.CollectionViewSource> class, set the [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md), and set the instance of your collection class as the <xref:System.Windows.Data.CollectionViewSource.Source%2A>.</span></span>  
  
     [!code-xaml[DataGrid_GroupSortFilter#201](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml#201)]  
  
4.  <span data-ttu-id="fec0a-125">建立的執行個體<xref:System.Windows.Controls.DataGrid>類別，並設定<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>屬性<xref:System.Windows.Data.CollectionViewSource>。</span><span class="sxs-lookup"><span data-stu-id="fec0a-125">Create an instance of the <xref:System.Windows.Controls.DataGrid> class, and set the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property to the <xref:System.Windows.Data.CollectionViewSource>.</span></span>  
  
     [!code-xaml[DataGrid_GroupSortFilter#002](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#002)]  
  
5.  <span data-ttu-id="fec0a-126">若要存取<xref:System.Windows.Data.CollectionViewSource>從您的程式碼使用<xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A>方法來取得參考<xref:System.Windows.Data.CollectionViewSource>。</span><span class="sxs-lookup"><span data-stu-id="fec0a-126">To access the <xref:System.Windows.Data.CollectionViewSource> from your code, use the <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> method to get a reference to the <xref:System.Windows.Data.CollectionViewSource>.</span></span>  
  
     [!code-csharp[DataGrid_GroupSortFilter#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#102)]
     [!code-vb[DataGrid_GroupSortFilter#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#102)]  
  
## <a name="grouping-items-in-a-datagrid"></a><span data-ttu-id="fec0a-127">將 DataGrid 中的項目分組</span><span class="sxs-lookup"><span data-stu-id="fec0a-127">Grouping items in a DataGrid</span></span>  
 <span data-ttu-id="fec0a-128">若要指定如何在分組項目<xref:System.Windows.Controls.DataGrid>，您使用<xref:System.Windows.Data.PropertyGroupDescription>類型來分組來源檢視中的項目。</span><span class="sxs-lookup"><span data-stu-id="fec0a-128">To specify how items are grouped in a <xref:System.Windows.Controls.DataGrid>, you use the <xref:System.Windows.Data.PropertyGroupDescription> type to group the items in the source view.</span></span>  
  
#### <a name="to-group-items-in-a-datagrid-using-xaml"></a><span data-ttu-id="fec0a-129">使用 XAML 的 DataGrid 中的群組項目</span><span class="sxs-lookup"><span data-stu-id="fec0a-129">To group items in a DataGrid using XAML</span></span>  
  
1.  <span data-ttu-id="fec0a-130">建立<xref:System.Windows.Data.PropertyGroupDescription>，指定要依群組的屬性。</span><span class="sxs-lookup"><span data-stu-id="fec0a-130">Create a <xref:System.Windows.Data.PropertyGroupDescription> that specifies the property to group by.</span></span> <span data-ttu-id="fec0a-131">XAML 或程式碼，您可以指定屬性。</span><span class="sxs-lookup"><span data-stu-id="fec0a-131">You can specify the property in XAML or in code.</span></span>  
  
    1.  <span data-ttu-id="fec0a-132">在 XAML 中，設定<xref:System.Windows.Data.PropertyGroupDescription.PropertyName%2A>至要分組的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="fec0a-132">In XAML, set the <xref:System.Windows.Data.PropertyGroupDescription.PropertyName%2A> to the name of the property to group by.</span></span>  
  
    2.  <span data-ttu-id="fec0a-133">程式碼中，將傳遞至建構函式的分組方式的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="fec0a-133">In code, pass the name of the property to group by to the constructor.</span></span>  
  
2.  <span data-ttu-id="fec0a-134">新增<xref:System.Windows.Data.PropertyGroupDescription>至<xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A?displayProperty=nameWithType>集合。</span><span class="sxs-lookup"><span data-stu-id="fec0a-134">Add the <xref:System.Windows.Data.PropertyGroupDescription> to the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A?displayProperty=nameWithType> collection.</span></span>  
  
3.  <span data-ttu-id="fec0a-135">加入其他執行個體<xref:System.Windows.Data.PropertyGroupDescription>至<xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A>来加入多個層級的群組集合。</span><span class="sxs-lookup"><span data-stu-id="fec0a-135">Add additional instances of <xref:System.Windows.Data.PropertyGroupDescription> to the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> collection to add more levels of grouping.</span></span>  
  
     [!code-xaml[DataGrid_GroupSortFilter#012](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#012)]  
  
     [!code-csharp[DataGrid_GroupSortFilter#112](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#112)]
     [!code-vb[DataGrid_GroupSortFilter#112](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#112)]  
  
4.  <span data-ttu-id="fec0a-136">若要移除群組，移除<xref:System.Windows.Data.PropertyGroupDescription>從<xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A>集合。</span><span class="sxs-lookup"><span data-stu-id="fec0a-136">To remove a group, remove the <xref:System.Windows.Data.PropertyGroupDescription> from the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> collection.</span></span>  
  
5.  <span data-ttu-id="fec0a-137">若要移除所有群組，請呼叫<xref:System.Collections.ObjectModel.Collection%601.Clear%2A>方法<xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A>集合。</span><span class="sxs-lookup"><span data-stu-id="fec0a-137">To remove all groups, call the <xref:System.Collections.ObjectModel.Collection%601.Clear%2A> method of the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> collection.</span></span>  
  
     [!code-csharp[DataGrid_GroupSortFilter#114](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#114)]
     [!code-vb[DataGrid_GroupSortFilter#114](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#114)]  
  
 <span data-ttu-id="fec0a-138">當中分組項目<xref:System.Windows.Controls.DataGrid>，您可以定義<xref:System.Windows.Controls.GroupStyle>，指定每個群組的外觀。</span><span class="sxs-lookup"><span data-stu-id="fec0a-138">When items are grouped in the <xref:System.Windows.Controls.DataGrid>, you can define a <xref:System.Windows.Controls.GroupStyle> that specifies the appearance of each group.</span></span> <span data-ttu-id="fec0a-139">您套用<xref:System.Windows.Controls.GroupStyle>將它加入至<xref:System.Windows.Controls.ItemsControl.GroupStyle%2A>DataGrid 的集合。</span><span class="sxs-lookup"><span data-stu-id="fec0a-139">You apply the <xref:System.Windows.Controls.GroupStyle> by adding it to the <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> collection of the DataGrid.</span></span> <span data-ttu-id="fec0a-140">如果您有多個層級的群組，您可以將不同的樣式套用到每個群組層級。</span><span class="sxs-lookup"><span data-stu-id="fec0a-140">If you have multiple levels of grouping, you can apply different styles to each group level.</span></span> <span data-ttu-id="fec0a-141">樣式中所定義的順序套用。</span><span class="sxs-lookup"><span data-stu-id="fec0a-141">Styles are applied in the order in which they are defined.</span></span> <span data-ttu-id="fec0a-142">例如，如果您定義兩種樣式，第一個將套用至上方層級的資料列群組。</span><span class="sxs-lookup"><span data-stu-id="fec0a-142">For example, if you define two styles, the first will be applied to top level row groups.</span></span> <span data-ttu-id="fec0a-143">第二個樣式會套用至第二個層級的所有資料列群組和較低。</span><span class="sxs-lookup"><span data-stu-id="fec0a-143">The second style will be applied to all row groups at the second level and lower.</span></span> <span data-ttu-id="fec0a-144"><xref:System.Windows.FrameworkElement.DataContext%2A>的<xref:System.Windows.Controls.GroupStyle>是<xref:System.Windows.Data.CollectionViewGroup>群組代表。</span><span class="sxs-lookup"><span data-stu-id="fec0a-144">The <xref:System.Windows.FrameworkElement.DataContext%2A> of the <xref:System.Windows.Controls.GroupStyle> is the <xref:System.Windows.Data.CollectionViewGroup> that the group represents.</span></span>  
  
#### <a name="to-change-the-appearance-of-row-group-headers"></a><span data-ttu-id="fec0a-145">若要變更資料列群組頁首的外觀</span><span class="sxs-lookup"><span data-stu-id="fec0a-145">To change the appearance of row group headers</span></span>  
  
1.  <span data-ttu-id="fec0a-146">建立<xref:System.Windows.Controls.GroupStyle>，定義資料列群組的外觀。</span><span class="sxs-lookup"><span data-stu-id="fec0a-146">Create a <xref:System.Windows.Controls.GroupStyle> that defines the appearance of the row group.</span></span>  
  
2.  <span data-ttu-id="fec0a-147">Put<xref:System.Windows.Controls.GroupStyle>內`<DataGrid.GroupStyle>`標記。</span><span class="sxs-lookup"><span data-stu-id="fec0a-147">Put the <xref:System.Windows.Controls.GroupStyle> inside the `<DataGrid.GroupStyle>` tags.</span></span>  
  
     [!code-xaml[DataGrid_GroupSortFilter#003](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#003)]  
  
## <a name="sorting-items-in-a-datagrid"></a><span data-ttu-id="fec0a-148">排序 DataGrid 中的項目</span><span class="sxs-lookup"><span data-stu-id="fec0a-148">Sorting items in a DataGrid</span></span>  
 <span data-ttu-id="fec0a-149">若要指定項目會按照<xref:System.Windows.Controls.DataGrid>，您使用<xref:System.ComponentModel.SortDescription>要排序的來源檢視中的項目類型。</span><span class="sxs-lookup"><span data-stu-id="fec0a-149">To specify how items are sorted in a <xref:System.Windows.Controls.DataGrid>, you use the <xref:System.ComponentModel.SortDescription> type to sort the items in the source view.</span></span>  
  
#### <a name="to-sort-items-in-a-datagrid"></a><span data-ttu-id="fec0a-150">若要排序的 DataGrid 中的項目</span><span class="sxs-lookup"><span data-stu-id="fec0a-150">To sort items in a DataGrid</span></span>  
  
1.  <span data-ttu-id="fec0a-151">建立<xref:System.ComponentModel.SortDescription>，指定要排序的屬性。</span><span class="sxs-lookup"><span data-stu-id="fec0a-151">Create a <xref:System.ComponentModel.SortDescription> that specifies the property to sort by.</span></span> <span data-ttu-id="fec0a-152">XAML 或程式碼，您可以指定屬性。</span><span class="sxs-lookup"><span data-stu-id="fec0a-152">You can specify the property in XAML or in code.</span></span>  
  
    1.  <span data-ttu-id="fec0a-153">在 XAML 中，設定<xref:System.ComponentModel.SortDescription.PropertyName%2A>排序所依據之屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="fec0a-153">In XAML, set the <xref:System.ComponentModel.SortDescription.PropertyName%2A> to the name of the property to sort by.</span></span>  
  
    2.  <span data-ttu-id="fec0a-154">程式碼中，傳遞要排序之屬性的名稱和<xref:System.ComponentModel.ListSortDirection>建構函式。</span><span class="sxs-lookup"><span data-stu-id="fec0a-154">In code, pass the name of the property to sort by and the <xref:System.ComponentModel.ListSortDirection> to the constructor.</span></span>  
  
2.  <span data-ttu-id="fec0a-155">新增<xref:System.ComponentModel.SortDescription>至<xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A?displayProperty=nameWithType>集合。</span><span class="sxs-lookup"><span data-stu-id="fec0a-155">Add the <xref:System.ComponentModel.SortDescription> to the <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A?displayProperty=nameWithType> collection.</span></span>  
  
3.  <span data-ttu-id="fec0a-156">加入其他執行個體<xref:System.ComponentModel.SortDescription>至<xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A>來排序其他屬性的集合。</span><span class="sxs-lookup"><span data-stu-id="fec0a-156">Add additional instances of <xref:System.ComponentModel.SortDescription> to the <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A> collection to sort by additional properties.</span></span>  
  
     [!code-xaml[DataGrid_GroupSortFilter#011](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#011)]  
  
     [!code-csharp[DataGrid_GroupSortFilter#211](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml.cs#211)]
     [!code-vb[DataGrid_GroupSortFilter#211](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#211)]  
  
## <a name="filtering-items-in-a-datagrid"></a><span data-ttu-id="fec0a-157">DataGrid 中的篩選項目</span><span class="sxs-lookup"><span data-stu-id="fec0a-157">Filtering items in a DataGrid</span></span>  
 <span data-ttu-id="fec0a-158">以篩選項目中<xref:System.Windows.Controls.DataGrid>使用<xref:System.Windows.Data.CollectionViewSource>，提供篩選的邏輯處理常式中<xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType>事件。</span><span class="sxs-lookup"><span data-stu-id="fec0a-158">To filter items in a <xref:System.Windows.Controls.DataGrid> using a <xref:System.Windows.Data.CollectionViewSource>, you provide the filtering logic in the handler for the <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> event.</span></span>  
  
#### <a name="to-filter-items-in-a-datagrid"></a><span data-ttu-id="fec0a-159">若要篩選的 DataGrid 中的項目</span><span class="sxs-lookup"><span data-stu-id="fec0a-159">To filter items in a DataGrid</span></span>  
  
1.  <span data-ttu-id="fec0a-160">加入的處理常式<xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType>事件。</span><span class="sxs-lookup"><span data-stu-id="fec0a-160">Add a handler for the <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> event.</span></span>  
  
2.  <span data-ttu-id="fec0a-161">在<xref:System.Windows.Data.CollectionViewSource.Filter>事件處理常式，定義篩選邏輯。</span><span class="sxs-lookup"><span data-stu-id="fec0a-161">In the <xref:System.Windows.Data.CollectionViewSource.Filter> event handler, define the filtering logic.</span></span>  
  
     <span data-ttu-id="fec0a-162">每次重新整理檢視，將會套用篩選。</span><span class="sxs-lookup"><span data-stu-id="fec0a-162">The filter will be applied every time the view is refreshed.</span></span>  
  
     [!code-xaml[DataGrid_GroupSortFilter#013](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#013)]  
  
     [!code-csharp[DataGrid_GroupSortFilter#113](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#113)]
     [!code-vb[DataGrid_GroupSortFilter#113](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#113)]  
  
 <span data-ttu-id="fec0a-163">或者，您可以篩選中的項目<xref:System.Windows.Controls.DataGrid>藉由建立提供篩選的邏輯和設定的方法<xref:System.Windows.Data.CollectionView.Filter%2A?displayProperty=nameWithType>將篩選套用到屬性。</span><span class="sxs-lookup"><span data-stu-id="fec0a-163">Alternatively, you can filter items in a <xref:System.Windows.Controls.DataGrid> by creating a method that provides the filtering logic and setting the <xref:System.Windows.Data.CollectionView.Filter%2A?displayProperty=nameWithType> property to apply the filter.</span></span> <span data-ttu-id="fec0a-164">若要查看此方法的範例，請參閱[檢視中的篩選資料](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)。</span><span class="sxs-lookup"><span data-stu-id="fec0a-164">To see an example of this method, see [Filter Data in a View](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fec0a-165">範例</span><span class="sxs-lookup"><span data-stu-id="fec0a-165">Example</span></span>  
 <span data-ttu-id="fec0a-166">下列範例示範如何分組、 排序和篩選`Task`中的資料<xref:System.Windows.Data.CollectionViewSource>和排序，並篩選顯示群組`Task`中的資料<xref:System.Windows.Controls.DataGrid>。</span><span class="sxs-lookup"><span data-stu-id="fec0a-166">The following example demonstrates grouping, sorting, and filtering `Task` data in a <xref:System.Windows.Data.CollectionViewSource> and displaying the grouped, sorted, and filtered `Task` data in a <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="fec0a-167"><xref:System.Windows.Data.CollectionViewSource>做<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>如<xref:System.Windows.Controls.DataGrid>。</span><span class="sxs-lookup"><span data-stu-id="fec0a-167">The <xref:System.Windows.Data.CollectionViewSource> is used as the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> for the <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="fec0a-168">分組、 排序和篩選會對<xref:System.Windows.Data.CollectionViewSource>而且會顯示在<xref:System.Windows.Controls.DataGrid>UI。</span><span class="sxs-lookup"><span data-stu-id="fec0a-168">Grouping, sorting, and filtering are performed on the <xref:System.Windows.Data.CollectionViewSource> and are displayed in the <xref:System.Windows.Controls.DataGrid> UI.</span></span>  
  
 <span data-ttu-id="fec0a-169">若要測試此範例中，您必須調整 DGGroupSortFilterExample 名稱以符合您的專案名稱。</span><span class="sxs-lookup"><span data-stu-id="fec0a-169">To test this example, you will need to adjust the DGGroupSortFilterExample name to match your project name.</span></span> <span data-ttu-id="fec0a-170">如果您使用 Visual Basic，您必須變更的類別名稱<xref:System.Windows.Window>下。</span><span class="sxs-lookup"><span data-stu-id="fec0a-170">If you are using Visual Basic, you will need to change the class name for <xref:System.Windows.Window> to the following.</span></span>  
  
 `<Window x:Class="MainWindow"`  
  
 [!code-xaml[DataGrid_GroupSortFilter#000](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#000)]  
  
 [!code-csharp[DataGrid_GroupSortFilter#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#100)]
 [!code-vb[DataGrid_GroupSortFilter#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#100)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fec0a-171">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="fec0a-171">Compiling the Code</span></span>  
  
-  
  
## <a name="robust-programming"></a><span data-ttu-id="fec0a-172">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="fec0a-172">Robust Programming</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="fec0a-173">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="fec0a-173">.NET Framework Security</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fec0a-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fec0a-174">See Also</span></span>  
 [<span data-ttu-id="fec0a-175">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="fec0a-175">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="fec0a-176">建立和繫結至 ObservableCollection</span><span class="sxs-lookup"><span data-stu-id="fec0a-176">Create and Bind to an ObservableCollection</span></span>](../../../../docs/framework/wpf/data/how-to-create-and-bind-to-an-observablecollection.md)  
 [<span data-ttu-id="fec0a-177">篩選檢視中的資料</span><span class="sxs-lookup"><span data-stu-id="fec0a-177">Filter Data in a View</span></span>](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)  
 [<span data-ttu-id="fec0a-178">排序檢視中的資料</span><span class="sxs-lookup"><span data-stu-id="fec0a-178">Sort Data in a View</span></span>](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)  
 [<span data-ttu-id="fec0a-179">使用 XAML 中的檢視排序和群組資料</span><span class="sxs-lookup"><span data-stu-id="fec0a-179">Sort and Group Data Using a View in XAML</span></span>](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)

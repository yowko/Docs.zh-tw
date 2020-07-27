---
title: ListView 概觀
description: 瞭解 Windows Presentation Foundation ListView 控制項，其可提供基礎結構，以在不同的版面配置或視圖中顯示資料項目。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], ListView
- ListView controls [WPF], about ListView control
ms.assetid: 989e12b0-260e-4570-95c6-489284003ce2
ms.openlocfilehash: 419c6216f0af696ec71e7607c79c2db637caa785
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164555"
---
# <a name="listview-overview"></a><span data-ttu-id="a6016-103">ListView 概觀</span><span class="sxs-lookup"><span data-stu-id="a6016-103">ListView Overview</span></span>
<span data-ttu-id="a6016-104"><xref:System.Windows.Controls.ListView>控制項會提供基礎結構，以在不同的版面配置或視圖中顯示一組資料項目。</span><span class="sxs-lookup"><span data-stu-id="a6016-104">The <xref:System.Windows.Controls.ListView> control provides the infrastructure to display a set of data items in different layouts or views.</span></span> <span data-ttu-id="a6016-105">例如，使用者可能會想要以表格顯示資料項目，還要排序其資料行。</span><span class="sxs-lookup"><span data-stu-id="a6016-105">For example, a user may want to display data items in a table and also to sort its columns.</span></span>  

<a name="WhatisaListView"></a>
## <a name="what-is-a-listview"></a><span data-ttu-id="a6016-106">什麼是 ListView？</span><span class="sxs-lookup"><span data-stu-id="a6016-106">What Is a ListView?</span></span>  
 <span data-ttu-id="a6016-107"><xref:System.Windows.Controls.ListView>控制項是 <xref:System.Windows.Controls.ItemsControl> 衍生自的 <xref:System.Windows.Controls.ListBox> 。</span><span class="sxs-lookup"><span data-stu-id="a6016-107">The <xref:System.Windows.Controls.ListView> control is an <xref:System.Windows.Controls.ItemsControl> that is derived from <xref:System.Windows.Controls.ListBox>.</span></span> <span data-ttu-id="a6016-108">通常，其專案為資料集合的成員，並以物件表示 <xref:System.Windows.Controls.ListViewItem> 。</span><span class="sxs-lookup"><span data-stu-id="a6016-108">Typically, its items are members of a data collection and are represented as <xref:System.Windows.Controls.ListViewItem> objects.</span></span> <span data-ttu-id="a6016-109"><xref:System.Windows.Controls.ListViewItem>是 <xref:System.Windows.Controls.ContentControl> ，而且只能包含單一子項目。</span><span class="sxs-lookup"><span data-stu-id="a6016-109">A <xref:System.Windows.Controls.ListViewItem> is a <xref:System.Windows.Controls.ContentControl> and can contain only a single child element.</span></span> <span data-ttu-id="a6016-110">不過，該子元素可以是任何視覺元素。</span><span class="sxs-lookup"><span data-stu-id="a6016-110">However, that child element can be any visual element.</span></span>  
  
<a name="DefiningaListViewView"></a>
## <a name="defining-a-view-mode-for-a-listview"></a><span data-ttu-id="a6016-111">定義 ListView 的檢視模式</span><span class="sxs-lookup"><span data-stu-id="a6016-111">Defining a View Mode for a ListView</span></span>  
 <span data-ttu-id="a6016-112">若要指定控制項內容的視圖模式 <xref:System.Windows.Controls.ListView> ，請設定 <xref:System.Windows.Controls.ListView.View%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="a6016-112">To specify a view mode for the content of a <xref:System.Windows.Controls.ListView> control, you set the <xref:System.Windows.Controls.ListView.View%2A> property.</span></span> <span data-ttu-id="a6016-113">提供的一個 view 模式 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 是 <xref:System.Windows.Controls.GridView> ，它會在具有可自訂資料行的資料表中顯示資料項目的集合。</span><span class="sxs-lookup"><span data-stu-id="a6016-113">One view mode that [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] provides is <xref:System.Windows.Controls.GridView>, which displays a collection of data items in a table that has customizable columns.</span></span>  
  
 <span data-ttu-id="a6016-114">下列範例示範如何為 <xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.ListView> 顯示員工資訊的控制項定義。</span><span class="sxs-lookup"><span data-stu-id="a6016-114">The following example shows how to define a <xref:System.Windows.Controls.GridView> for a <xref:System.Windows.Controls.ListView> control that displays employee information.</span></span>  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 <span data-ttu-id="a6016-115">下圖顯示上一個範例的資料顯示方式。</span><span class="sxs-lookup"><span data-stu-id="a6016-115">The following illustration shows how the data appears for the previous example.</span></span>  
  
 ![顯示具有 GridView 輸出之 ListView 的螢幕擷取畫面。](./media/gridview-overview/listview-gridview-output.jpg)  
  
 <span data-ttu-id="a6016-117">您可以藉由定義繼承自類別的類別來建立自訂視圖模式 <xref:System.Windows.Controls.ViewBase> 。</span><span class="sxs-lookup"><span data-stu-id="a6016-117">You can create a custom view mode by defining a class that inherits from the <xref:System.Windows.Controls.ViewBase> class.</span></span> <span data-ttu-id="a6016-118"><xref:System.Windows.Controls.ViewBase>類別會提供建立自訂視圖所需的基礎結構。</span><span class="sxs-lookup"><span data-stu-id="a6016-118">The <xref:System.Windows.Controls.ViewBase> class provides the infrastructure that you need to create a custom view.</span></span> <span data-ttu-id="a6016-119">如需有關如何建立自訂檢視的詳細資訊，請參閱[建立 ListView 的自訂檢視模式](how-to-create-a-custom-view-mode-for-a-listview.md)。</span><span class="sxs-lookup"><span data-stu-id="a6016-119">For more information about how to create a custom view, see [Create a Custom View Mode for a ListView](how-to-create-a-custom-view-mode-for-a-listview.md).</span></span>  
  
<a name="BindingDatatoaListView"></a>
## <a name="binding-data-to-a-listview"></a><span data-ttu-id="a6016-120">將資料繫結至 ListView</span><span class="sxs-lookup"><span data-stu-id="a6016-120">Binding Data to a ListView</span></span>  
 <span data-ttu-id="a6016-121">您 <xref:System.Windows.Controls.ItemsControl.Items%2A> 可以使用和 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 屬性來指定控制項的專案 <xref:System.Windows.Controls.ListView> 。</span><span class="sxs-lookup"><span data-stu-id="a6016-121">Use the <xref:System.Windows.Controls.ItemsControl.Items%2A> and <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> properties to specify items for a <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="a6016-122">下列範例 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 會將屬性設定為所呼叫的資料集合 `EmployeeInfoDataSource` 。</span><span class="sxs-lookup"><span data-stu-id="a6016-122">The following example sets the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property to a data collection that is called `EmployeeInfoDataSource`.</span></span>  
  
 [!code-xaml[ListViewCode#ItemsSource](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#itemssource)]  
  
 <span data-ttu-id="a6016-123">在中 <xref:System.Windows.Controls.GridView> ，物件會系結 <xref:System.Windows.Controls.GridViewColumn> 至指定的資料欄位。</span><span class="sxs-lookup"><span data-stu-id="a6016-123">In a <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridViewColumn> objects bind to specified data fields.</span></span> <span data-ttu-id="a6016-124">下列範例會藉由指定屬性的來將物件系結 <xref:System.Windows.Controls.GridViewColumn> 至資料欄位 <xref:System.Windows.Data.Binding> <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> 。</span><span class="sxs-lookup"><span data-stu-id="a6016-124">The following example binds a <xref:System.Windows.Controls.GridViewColumn> object to a data field by specifying a <xref:System.Windows.Data.Binding> for the <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> property.</span></span>  
  
 [!code-csharp[ListViewCode#GridViewColumnProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml.cs#gridviewcolumnproperties)]
 [!code-vb[ListViewCode#GridViewColumnProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCode/visualbasic/window1.xaml.vb#gridviewcolumnproperties)]
 [!code-xaml[ListViewCode#GridViewColumnProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#gridviewcolumnproperties)]  
  
 <span data-ttu-id="a6016-125">您也可以將指定 <xref:System.Windows.Data.Binding> 為 <xref:System.Windows.DataTemplate> 定義的一部分，以用來將資料行中的儲存格樣式。</span><span class="sxs-lookup"><span data-stu-id="a6016-125">You can also specify a <xref:System.Windows.Data.Binding> as part of a <xref:System.Windows.DataTemplate> definition that you use to style the cells in a column.</span></span> <span data-ttu-id="a6016-126">在下列範例中， <xref:System.Windows.DataTemplate> 使用所識別的會設定的 <xref:System.Windows.ResourceKey> <xref:System.Windows.Data.Binding> <xref:System.Windows.Controls.GridViewColumn> 。</span><span class="sxs-lookup"><span data-stu-id="a6016-126">In the following example, the <xref:System.Windows.DataTemplate> that is identified with a <xref:System.Windows.ResourceKey> sets the <xref:System.Windows.Data.Binding> for a <xref:System.Windows.Controls.GridViewColumn>.</span></span> <span data-ttu-id="a6016-127">請注意，此範例不會定義， <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> 因為這樣做會覆寫所指定的系結 <xref:System.Windows.DataTemplate> 。</span><span class="sxs-lookup"><span data-stu-id="a6016-127">Note that this example does not define the <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> because doing so overrides the binding that is specified by <xref:System.Windows.DataTemplate>.</span></span>  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
<a name="StylingaListView"></a>
## <a name="styling-a-listview-that-implements-a-gridview"></a><span data-ttu-id="a6016-128">為實作 GridView 的 ListView 設定樣式</span><span class="sxs-lookup"><span data-stu-id="a6016-128">Styling a ListView That Implements a GridView</span></span>  
 <span data-ttu-id="a6016-129"><xref:System.Windows.Controls.ListView>控制項包含 <xref:System.Windows.Controls.ListViewItem> 物件，代表顯示的資料項目。</span><span class="sxs-lookup"><span data-stu-id="a6016-129">The <xref:System.Windows.Controls.ListView> control contains <xref:System.Windows.Controls.ListViewItem> objects, which represent the data items that are displayed.</span></span> <span data-ttu-id="a6016-130">您可以使用下列屬性來定義資料項目的內容和樣式：</span><span class="sxs-lookup"><span data-stu-id="a6016-130">You can use the following properties to define the content and style of data items:</span></span>  
  
- <span data-ttu-id="a6016-131">在 <xref:System.Windows.Controls.ListView> 控制項上，使用 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> 、 <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A> 和 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="a6016-131">On the <xref:System.Windows.Controls.ListView> control, use the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>, <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>, and <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> properties.</span></span>  
  
- <span data-ttu-id="a6016-132">在 <xref:System.Windows.Controls.ListViewItem> 控制項上，使用 <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> 和 <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="a6016-132">On the <xref:System.Windows.Controls.ListViewItem> control, use the <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> and <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A> properties.</span></span>  
  
 <span data-ttu-id="a6016-133">若要避免在中的資料格之間對齊問題 <xref:System.Windows.Controls.GridView> ，請勿使用 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> 來設定屬性，或加入會影響中專案寬度的內容 <xref:System.Windows.Controls.ListView> 。</span><span class="sxs-lookup"><span data-stu-id="a6016-133">To avoid alignment issues between cells in a <xref:System.Windows.Controls.GridView>, do not use the <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> to set properties or add content that affects the width of an item in a <xref:System.Windows.Controls.ListView>.</span></span> <span data-ttu-id="a6016-134">例如，當您在中設定屬性時，可能會發生對齊問題 <xref:System.Windows.FrameworkElement.Margin%2A> <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> 。</span><span class="sxs-lookup"><span data-stu-id="a6016-134">For example, an alignment issue can occur when you set the <xref:System.Windows.FrameworkElement.Margin%2A> property in the <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>.</span></span> <span data-ttu-id="a6016-135">若要指定屬性或定義會影響中專案寬度的內容 <xref:System.Windows.Controls.GridView> ，請使用類別的屬性 <xref:System.Windows.Controls.GridView> 及其相關類別，例如 <xref:System.Windows.Controls.GridViewColumn> 。</span><span class="sxs-lookup"><span data-stu-id="a6016-135">To specify properties or define content that affects the width of items in a <xref:System.Windows.Controls.GridView>, use the properties of the <xref:System.Windows.Controls.GridView> class and its related classes, such as <xref:System.Windows.Controls.GridViewColumn>.</span></span>  
  
 <span data-ttu-id="a6016-136">如需如何使用 <xref:System.Windows.Controls.GridView> 及其支援類別的詳細資訊，請參閱[GridView 總覽](gridview-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="a6016-136">For more information about how to use <xref:System.Windows.Controls.GridView> and its supporting classes, see [GridView Overview](gridview-overview.md).</span></span>  
  
 <span data-ttu-id="a6016-137">如果您 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> 為 <xref:System.Windows.Controls.ListView> 控制項定義，並同時定義 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> ，則必須在樣式中包含，才能 <xref:System.Windows.Controls.ContentPresenter> 讓正常 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> 運作。</span><span class="sxs-lookup"><span data-stu-id="a6016-137">If you define an <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> for a <xref:System.Windows.Controls.ListView> control and also define an <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>, you must include a <xref:System.Windows.Controls.ContentPresenter> in the style in order for the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> to work correctly.</span></span>  
  
 <span data-ttu-id="a6016-138">請不要 <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> 針對使用所顯示的內容使用和屬性 <xref:System.Windows.Controls.ListView> <xref:System.Windows.Controls.GridView> 。</span><span class="sxs-lookup"><span data-stu-id="a6016-138">Do not use the <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> and <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> properties for <xref:System.Windows.Controls.ListView> content that is displayed by using a <xref:System.Windows.Controls.GridView>.</span></span> <span data-ttu-id="a6016-139">若要指定資料行中內容的對齊方式 <xref:System.Windows.Controls.GridView> ，請定義 <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> 。</span><span class="sxs-lookup"><span data-stu-id="a6016-139">To specify the alignment of content in a column of a <xref:System.Windows.Controls.GridView>, define a <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>.</span></span>  
  
<a name="UsingtheSameViewMoreThanOnce"></a>
## <a name="sharing-the-same-view-mode"></a><span data-ttu-id="a6016-140">共用相同的檢視模式</span><span class="sxs-lookup"><span data-stu-id="a6016-140">Sharing the Same View Mode</span></span>  
 <span data-ttu-id="a6016-141">兩個 <xref:System.Windows.Controls.ListView> 控制項不能同時共用相同的視圖模式。</span><span class="sxs-lookup"><span data-stu-id="a6016-141">Two <xref:System.Windows.Controls.ListView> controls cannot share the same view mode at the same time.</span></span> <span data-ttu-id="a6016-142">如果您嘗試使用與多個控制項相同的 view 模式 <xref:System.Windows.Controls.ListView> ，就會發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a6016-142">If you try to use the same view mode with more than one <xref:System.Windows.Controls.ListView> control, an exception occurs.</span></span>  
  
 <span data-ttu-id="a6016-143">若要指定可同時由多個使用的視圖模式 <xref:System.Windows.Controls.ListView> ，請使用範本或樣式。</span><span class="sxs-lookup"><span data-stu-id="a6016-143">To specify a view mode that can be simultaneously used by more than one <xref:System.Windows.Controls.ListView>, use templates or styles.</span></span>
  
<a name="CreatingaCustomView"></a>
## <a name="creating-a-custom-view-mode"></a><span data-ttu-id="a6016-144">建立自訂檢視模式</span><span class="sxs-lookup"><span data-stu-id="a6016-144">Creating a Custom View Mode</span></span>  
 <span data-ttu-id="a6016-145">之類的自訂視圖 <xref:System.Windows.Controls.GridView> 衍生自 <xref:System.Windows.Controls.ViewBase> 抽象類別，它提供工具來顯示以物件表示的資料項目 <xref:System.Windows.Controls.ListViewItem> 。</span><span class="sxs-lookup"><span data-stu-id="a6016-145">Customized views like <xref:System.Windows.Controls.GridView> are derived from the <xref:System.Windows.Controls.ViewBase> abstract class, which provides the tools to display data items that are represented as <xref:System.Windows.Controls.ListViewItem> objects.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a6016-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6016-146">See also</span></span>

- <xref:System.Windows.Controls.GridView>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.ListViewItem>
- <xref:System.Windows.Data.Binding>
- [<span data-ttu-id="a6016-147">GridView 概觀</span><span class="sxs-lookup"><span data-stu-id="a6016-147">GridView Overview</span></span>](gridview-overview.md)
- [<span data-ttu-id="a6016-148">操作說明主題</span><span class="sxs-lookup"><span data-stu-id="a6016-148">How-to Topics</span></span>](listview-how-to-topics.md)
- [<span data-ttu-id="a6016-149">控制項</span><span class="sxs-lookup"><span data-stu-id="a6016-149">Controls</span></span>](../advanced/optimizing-performance-controls.md)

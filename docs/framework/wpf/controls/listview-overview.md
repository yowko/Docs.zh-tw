---
title: ListView 概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], ListView
- ListView controls [WPF], about ListView control
ms.assetid: 989e12b0-260e-4570-95c6-489284003ce2
ms.openlocfilehash: 2f336d1eb8dcdfec3c3c8059ba865147c6b6c825
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187511"
---
# <a name="listview-overview"></a><span data-ttu-id="8b954-102">ListView 概觀</span><span class="sxs-lookup"><span data-stu-id="8b954-102">ListView Overview</span></span>
<span data-ttu-id="8b954-103">該<xref:System.Windows.Controls.ListView>控制項提供基礎結構以在不同的佈局或視圖中顯示一組資料項目。</span><span class="sxs-lookup"><span data-stu-id="8b954-103">The <xref:System.Windows.Controls.ListView> control provides the infrastructure to display a set of data items in different layouts or views.</span></span> <span data-ttu-id="8b954-104">例如，使用者可能會想要以表格顯示資料項目，還要排序其資料行。</span><span class="sxs-lookup"><span data-stu-id="8b954-104">For example, a user may want to display data items in a table and also to sort its columns.</span></span>  

<a name="WhatisaListView"></a>
## <a name="what-is-a-listview"></a><span data-ttu-id="8b954-105">什麼是 ListView？</span><span class="sxs-lookup"><span data-stu-id="8b954-105">What Is a ListView?</span></span>  
 <span data-ttu-id="8b954-106">控制項<xref:System.Windows.Controls.ListView>是從<xref:System.Windows.Controls.ItemsControl>派生的<xref:System.Windows.Controls.ListBox>。</span><span class="sxs-lookup"><span data-stu-id="8b954-106">The <xref:System.Windows.Controls.ListView> control is an <xref:System.Windows.Controls.ItemsControl> that is derived from <xref:System.Windows.Controls.ListBox>.</span></span> <span data-ttu-id="8b954-107">通常，其項是資料收集的成員，並表示為<xref:System.Windows.Controls.ListViewItem>物件。</span><span class="sxs-lookup"><span data-stu-id="8b954-107">Typically, its items are members of a data collection and are represented as <xref:System.Windows.Controls.ListViewItem> objects.</span></span> <span data-ttu-id="8b954-108">a<xref:System.Windows.Controls.ListViewItem>是<xref:System.Windows.Controls.ContentControl>，只能包含單個子項目。</span><span class="sxs-lookup"><span data-stu-id="8b954-108">A <xref:System.Windows.Controls.ListViewItem> is a <xref:System.Windows.Controls.ContentControl> and can contain only a single child element.</span></span> <span data-ttu-id="8b954-109">不過，該子元素可以是任何視覺元素。</span><span class="sxs-lookup"><span data-stu-id="8b954-109">However, that child element can be any visual element.</span></span>  
  
<a name="DefiningaListViewView"></a>
## <a name="defining-a-view-mode-for-a-listview"></a><span data-ttu-id="8b954-110">定義 ListView 的檢視模式</span><span class="sxs-lookup"><span data-stu-id="8b954-110">Defining a View Mode for a ListView</span></span>  
 <span data-ttu-id="8b954-111">要為<xref:System.Windows.Controls.ListView>控制項的內容指定視圖模式，請設置 屬性<xref:System.Windows.Controls.ListView.View%2A>。</span><span class="sxs-lookup"><span data-stu-id="8b954-111">To specify a view mode for the content of a <xref:System.Windows.Controls.ListView> control, you set the <xref:System.Windows.Controls.ListView.View%2A> property.</span></span> <span data-ttu-id="8b954-112">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]提供的一種視圖模式是<xref:System.Windows.Controls.GridView>，它顯示具有可自訂列的表中的資料項目的集合。</span><span class="sxs-lookup"><span data-stu-id="8b954-112">One view mode that [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] provides is <xref:System.Windows.Controls.GridView>, which displays a collection of data items in a table that has customizable columns.</span></span>  
  
 <span data-ttu-id="8b954-113">下面的示例演示如何為顯示員工資訊的<xref:System.Windows.Controls.GridView><xref:System.Windows.Controls.ListView>控制項定義 。</span><span class="sxs-lookup"><span data-stu-id="8b954-113">The following example shows how to define a <xref:System.Windows.Controls.GridView> for a <xref:System.Windows.Controls.ListView> control that displays employee information.</span></span>  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 <span data-ttu-id="8b954-114">下圖顯示上一個範例的資料顯示方式。</span><span class="sxs-lookup"><span data-stu-id="8b954-114">The following illustration shows how the data appears for the previous example.</span></span>  
  
 ![顯示帶有 GridView 輸出的 ListView 的螢幕截圖。](./media/gridview-overview/listview-gridview-output.jpg)  
  
 <span data-ttu-id="8b954-116">可以通過定義從類繼承的<xref:System.Windows.Controls.ViewBase>類來創建自訂視圖模式。</span><span class="sxs-lookup"><span data-stu-id="8b954-116">You can create a custom view mode by defining a class that inherits from the <xref:System.Windows.Controls.ViewBase> class.</span></span> <span data-ttu-id="8b954-117">類<xref:System.Windows.Controls.ViewBase>提供創建自訂視圖所需的基礎結構。</span><span class="sxs-lookup"><span data-stu-id="8b954-117">The <xref:System.Windows.Controls.ViewBase> class provides the infrastructure that you need to create a custom view.</span></span> <span data-ttu-id="8b954-118">如需有關如何建立自訂檢視的詳細資訊，請參閱[建立 ListView 的自訂檢視模式](how-to-create-a-custom-view-mode-for-a-listview.md)。</span><span class="sxs-lookup"><span data-stu-id="8b954-118">For more information about how to create a custom view, see [Create a Custom View Mode for a ListView](how-to-create-a-custom-view-mode-for-a-listview.md).</span></span>  
  
<a name="BindingDatatoaListView"></a>
## <a name="binding-data-to-a-listview"></a><span data-ttu-id="8b954-119">將資料繫結至 ListView</span><span class="sxs-lookup"><span data-stu-id="8b954-119">Binding Data to a ListView</span></span>  
 <span data-ttu-id="8b954-120">使用<xref:System.Windows.Controls.ItemsControl.Items%2A>和<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>屬性為控制項指定項<xref:System.Windows.Controls.ListView>。</span><span class="sxs-lookup"><span data-stu-id="8b954-120">Use the <xref:System.Windows.Controls.ItemsControl.Items%2A> and <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> properties to specify items for a <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="8b954-121">下面的示例將<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>屬性設置到稱為`EmployeeInfoDataSource`的資料收集。</span><span class="sxs-lookup"><span data-stu-id="8b954-121">The following example sets the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property to a data collection that is called `EmployeeInfoDataSource`.</span></span>  
  
 [!code-xaml[ListViewCode#ItemsSource](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#itemssource)]  
  
 <span data-ttu-id="8b954-122">在<xref:System.Windows.Controls.GridView>中<xref:System.Windows.Controls.GridViewColumn>，物件綁定到指定的資料欄位。</span><span class="sxs-lookup"><span data-stu-id="8b954-122">In a <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridViewColumn> objects bind to specified data fields.</span></span> <span data-ttu-id="8b954-123">下面的示例通過為<xref:System.Windows.Controls.GridViewColumn><xref:System.Windows.Data.Binding><xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>屬性指定 的 將物件綁定到資料欄位。</span><span class="sxs-lookup"><span data-stu-id="8b954-123">The following example binds a <xref:System.Windows.Controls.GridViewColumn> object to a data field by specifying a <xref:System.Windows.Data.Binding> for the <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> property.</span></span>  
  
 [!code-csharp[ListViewCode#GridViewColumnProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml.cs#gridviewcolumnproperties)]
 [!code-vb[ListViewCode#GridViewColumnProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCode/visualbasic/window1.xaml.vb#gridviewcolumnproperties)]
 [!code-xaml[ListViewCode#GridViewColumnProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#gridviewcolumnproperties)]  
  
 <span data-ttu-id="8b954-124">還可以指定 作為<xref:System.Windows.Data.Binding>用於設置列儲存格樣式<xref:System.Windows.DataTemplate>的定義的一部分。</span><span class="sxs-lookup"><span data-stu-id="8b954-124">You can also specify a <xref:System.Windows.Data.Binding> as part of a <xref:System.Windows.DataTemplate> definition that you use to style the cells in a column.</span></span> <span data-ttu-id="8b954-125">在下面的<xref:System.Windows.DataTemplate>示例中，使用<xref:System.Windows.ResourceKey>集<xref:System.Windows.Data.Binding>標識 的 。 <xref:System.Windows.Controls.GridViewColumn></span><span class="sxs-lookup"><span data-stu-id="8b954-125">In the following example, the <xref:System.Windows.DataTemplate> that is identified with a <xref:System.Windows.ResourceKey> sets the <xref:System.Windows.Data.Binding> for a <xref:System.Windows.Controls.GridViewColumn>.</span></span> <span data-ttu-id="8b954-126">請注意，此示例不定義，<xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>因為這樣做會覆蓋 由<xref:System.Windows.DataTemplate>指定的綁定。</span><span class="sxs-lookup"><span data-stu-id="8b954-126">Note that this example does not define the <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> because doing so overrides the binding that is specified by <xref:System.Windows.DataTemplate>.</span></span>  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
<a name="StylingaListView"></a>
## <a name="styling-a-listview-that-implements-a-gridview"></a><span data-ttu-id="8b954-127">為實作 GridView 的 ListView 設定樣式</span><span class="sxs-lookup"><span data-stu-id="8b954-127">Styling a ListView That Implements a GridView</span></span>  
 <span data-ttu-id="8b954-128">控制項<xref:System.Windows.Controls.ListView>包含<xref:System.Windows.Controls.ListViewItem>表示顯示的資料項目的物件。</span><span class="sxs-lookup"><span data-stu-id="8b954-128">The <xref:System.Windows.Controls.ListView> control contains <xref:System.Windows.Controls.ListViewItem> objects, which represent the data items that are displayed.</span></span> <span data-ttu-id="8b954-129">您可以使用下列屬性來定義資料項目的內容和樣式：</span><span class="sxs-lookup"><span data-stu-id="8b954-129">You can use the following properties to define the content and style of data items:</span></span>  
  
- <span data-ttu-id="8b954-130">在控制項<xref:System.Windows.Controls.ListView>上，使用<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>、<xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>和<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="8b954-130">On the <xref:System.Windows.Controls.ListView> control, use the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>, <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>, and <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> properties.</span></span>  
  
- <span data-ttu-id="8b954-131">在控制項<xref:System.Windows.Controls.ListViewItem>上，使用<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>和<xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="8b954-131">On the <xref:System.Windows.Controls.ListViewItem> control, use the <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> and <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A> properties.</span></span>  
  
 <span data-ttu-id="8b954-132">為了避免 在<xref:System.Windows.Controls.GridView>的儲存格之間對齊問題，請勿使用<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>來設置 屬性或添加影響 中項寬度的內容<xref:System.Windows.Controls.ListView>。</span><span class="sxs-lookup"><span data-stu-id="8b954-132">To avoid alignment issues between cells in a <xref:System.Windows.Controls.GridView>, do not use the <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> to set properties or add content that affects the width of an item in a <xref:System.Windows.Controls.ListView>.</span></span> <span data-ttu-id="8b954-133">例如，在 中設置<xref:System.Windows.FrameworkElement.Margin%2A>屬性時，可能會出現對齊問題。 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A></span><span class="sxs-lookup"><span data-stu-id="8b954-133">For example, an alignment issue can occur when you set the <xref:System.Windows.FrameworkElement.Margin%2A> property in the <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>.</span></span> <span data-ttu-id="8b954-134">要指定影響 中項寬度的屬性或定義內容<xref:System.Windows.Controls.GridView>，請使用<xref:System.Windows.Controls.GridView>類及其相關類的屬性，如<xref:System.Windows.Controls.GridViewColumn>。</span><span class="sxs-lookup"><span data-stu-id="8b954-134">To specify properties or define content that affects the width of items in a <xref:System.Windows.Controls.GridView>, use the properties of the <xref:System.Windows.Controls.GridView> class and its related classes, such as <xref:System.Windows.Controls.GridViewColumn>.</span></span>  
  
 <span data-ttu-id="8b954-135">有關如何使用<xref:System.Windows.Controls.GridView>及其支援類的詳細資訊，請參閱[GridView 概述](gridview-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="8b954-135">For more information about how to use <xref:System.Windows.Controls.GridView> and its supporting classes, see [GridView Overview](gridview-overview.md).</span></span>  
  
 <span data-ttu-id="8b954-136">如果<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>為<xref:System.Windows.Controls.ListView>控制項定義 。 ，並且還定義了<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>， 必須在樣式<xref:System.Windows.Controls.ContentPresenter><xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>中包括 。</span><span class="sxs-lookup"><span data-stu-id="8b954-136">If you define an <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> for a <xref:System.Windows.Controls.ListView> control and also define an <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>, you must include a <xref:System.Windows.Controls.ContentPresenter> in the style in order for the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> to work correctly.</span></span>  
  
 <span data-ttu-id="8b954-137">不要對使用<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>顯示<xref:System.Windows.Controls.Control.VerticalContentAlignment%2A><xref:System.Windows.Controls.ListView>的內容使用 和 屬性<xref:System.Windows.Controls.GridView>。</span><span class="sxs-lookup"><span data-stu-id="8b954-137">Do not use the <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> and <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> properties for <xref:System.Windows.Controls.ListView> content that is displayed by using a <xref:System.Windows.Controls.GridView>.</span></span> <span data-ttu-id="8b954-138">要指定 內容在 的列中的對齊方式<xref:System.Windows.Controls.GridView>，請定義<xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>。</span><span class="sxs-lookup"><span data-stu-id="8b954-138">To specify the alignment of content in a column of a <xref:System.Windows.Controls.GridView>, define a <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>.</span></span>  
  
<a name="UsingtheSameViewMoreThanOnce"></a>
## <a name="sharing-the-same-view-mode"></a><span data-ttu-id="8b954-139">共用相同的檢視模式</span><span class="sxs-lookup"><span data-stu-id="8b954-139">Sharing the Same View Mode</span></span>  
 <span data-ttu-id="8b954-140">兩<xref:System.Windows.Controls.ListView>個控制項不能同時共用同一視圖模式。</span><span class="sxs-lookup"><span data-stu-id="8b954-140">Two <xref:System.Windows.Controls.ListView> controls cannot share the same view mode at the same time.</span></span> <span data-ttu-id="8b954-141">如果嘗試對多個<xref:System.Windows.Controls.ListView>控制項使用相同的視圖模式，則會發生異常。</span><span class="sxs-lookup"><span data-stu-id="8b954-141">If you try to use the same view mode with more than one <xref:System.Windows.Controls.ListView> control, an exception occurs.</span></span>  
  
 <span data-ttu-id="8b954-142">要指定可以由多個<xref:System.Windows.Controls.ListView>多個同時使用的視圖模式，請使用範本或樣式。</span><span class="sxs-lookup"><span data-stu-id="8b954-142">To specify a view mode that can be simultaneously used by more than one <xref:System.Windows.Controls.ListView>, use templates or styles.</span></span>
  
<a name="CreatingaCustomView"></a>
## <a name="creating-a-custom-view-mode"></a><span data-ttu-id="8b954-143">建立自訂檢視模式</span><span class="sxs-lookup"><span data-stu-id="8b954-143">Creating a Custom View Mode</span></span>  
 <span data-ttu-id="8b954-144">自訂視圖如<xref:System.Windows.Controls.GridView>從<xref:System.Windows.Controls.ViewBase>抽象類別派生，它提供了顯示表示為<xref:System.Windows.Controls.ListViewItem>物件的資料項目的工具。</span><span class="sxs-lookup"><span data-stu-id="8b954-144">Customized views like <xref:System.Windows.Controls.GridView> are derived from the <xref:System.Windows.Controls.ViewBase> abstract class, which provides the tools to display data items that are represented as <xref:System.Windows.Controls.ListViewItem> objects.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="8b954-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b954-145">See also</span></span>

- <xref:System.Windows.Controls.GridView>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.ListViewItem>
- <xref:System.Windows.Data.Binding>
- [<span data-ttu-id="8b954-146">GridView 概觀</span><span class="sxs-lookup"><span data-stu-id="8b954-146">GridView Overview</span></span>](gridview-overview.md)
- [<span data-ttu-id="8b954-147">如何使用主題</span><span class="sxs-lookup"><span data-stu-id="8b954-147">How-to Topics</span></span>](listview-how-to-topics.md)
- [<span data-ttu-id="8b954-148">控制</span><span class="sxs-lookup"><span data-stu-id="8b954-148">Controls</span></span>](../advanced/optimizing-performance-controls.md)

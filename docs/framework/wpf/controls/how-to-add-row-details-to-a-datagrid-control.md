---
title: HOW TO：將資料列詳細資料新增至 DataGrid 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataTemplate [WPF], DataGrid
- row details [WPF], DataGrid
- DataGrid [WPF], row details
ms.assetid: 0bdc6f50-9b4c-483f-9df6-a47a1fde998b
ms.openlocfilehash: d5b6539f3d379088528b9654861267988b6fc69b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61911379"
---
# <a name="how-to-add-row-details-to-a-datagrid-control"></a><span data-ttu-id="1fd5a-102">HOW TO：將資料列詳細資料新增至 DataGrid 控制項</span><span class="sxs-lookup"><span data-stu-id="1fd5a-102">How to: Add Row Details to a DataGrid Control</span></span>
<span data-ttu-id="1fd5a-103">當使用<xref:System.Windows.Controls.DataGrid>控制項，您可以藉由新增資料列的詳細資料 區段中自訂資料呈現方式。</span><span class="sxs-lookup"><span data-stu-id="1fd5a-103">When using the <xref:System.Windows.Controls.DataGrid> control, you can customize the data presentation by adding a row details section.</span></span> <span data-ttu-id="1fd5a-104">新增資料列詳細資料 區段可讓您將可選擇性地看見或是已摺疊的範本中的部分資料。</span><span class="sxs-lookup"><span data-stu-id="1fd5a-104">Adding a row details section enables you to group some data in a template that is optionally visible or collapsed.</span></span> <span data-ttu-id="1fd5a-105">例如，您可以在其中新增資料列詳細資料，以<xref:System.Windows.Controls.DataGrid>其中會提供每個資料列的資料摘要<xref:System.Windows.Controls.DataGrid>，但是當使用者選取一個資料列會顯示更多資料欄位。</span><span class="sxs-lookup"><span data-stu-id="1fd5a-105">For example, you can add row details to a <xref:System.Windows.Controls.DataGrid> that presents only a summary of the data for each row in the <xref:System.Windows.Controls.DataGrid>, but presents more data fields when the user selects a row.</span></span> <span data-ttu-id="1fd5a-106">您定義的範本中的資料列詳細資料 區段<xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="1fd5a-106">You define the template for the row details section in the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property.</span></span> <span data-ttu-id="1fd5a-107">下圖顯示資料列詳細資料區段的範例。</span><span class="sxs-lookup"><span data-stu-id="1fd5a-107">The following illustration shows an example of a row details section.</span></span>  
  
 <span data-ttu-id="1fd5a-108">![顯示資料列詳細資料的 DataGrid](./media/ndp-rowdetails.png "NDP_RowDetails")</span><span class="sxs-lookup"><span data-stu-id="1fd5a-108">![DataGrid shown with row details](./media/ndp-rowdetails.png "NDP_RowDetails")</span></span>  
  
 <span data-ttu-id="1fd5a-109">為內嵌 XAML 或資源，您會定義資料列詳細資料範本。</span><span class="sxs-lookup"><span data-stu-id="1fd5a-109">You define the row details template as either inline XAML or as a resource.</span></span> <span data-ttu-id="1fd5a-110">下列程序中會展示這兩個方法。</span><span class="sxs-lookup"><span data-stu-id="1fd5a-110">Both approaches are shown in the following procedures.</span></span> <span data-ttu-id="1fd5a-111">資料範本新增為資源可以使用在整個專案，而不需要重新建立範本。</span><span class="sxs-lookup"><span data-stu-id="1fd5a-111">A data template that is added as a resource can be used throughout the project without re-creating the template.</span></span> <span data-ttu-id="1fd5a-112">資料範本新增為內嵌 XAML 就只能存取從控制項定義的位置。</span><span class="sxs-lookup"><span data-stu-id="1fd5a-112">A data template that is added as inline XAML is only accessible from the control where it is defined.</span></span>  
  
### <a name="to-display-row-details-by-using-inline-xaml"></a><span data-ttu-id="1fd5a-113">若要使用內嵌 XAML 顯示資料列詳細資料</span><span class="sxs-lookup"><span data-stu-id="1fd5a-113">To display row details by using inline XAML</span></span>  
  
1. <span data-ttu-id="1fd5a-114">建立<xref:System.Windows.Controls.DataGrid>顯示來自資料來源的資料。</span><span class="sxs-lookup"><span data-stu-id="1fd5a-114">Create a <xref:System.Windows.Controls.DataGrid> that displays data from a data source.</span></span>  
  
2. <span data-ttu-id="1fd5a-115">在 <xref:System.Windows.Controls.DataGrid> 項目中，加入 <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> 項目。</span><span class="sxs-lookup"><span data-stu-id="1fd5a-115">In the <xref:System.Windows.Controls.DataGrid> element, add a <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> element.</span></span>  
  
3. <span data-ttu-id="1fd5a-116">建立<xref:System.Windows.DataTemplate>，定義資料列的 [詳細資料] 區段的外觀。</span><span class="sxs-lookup"><span data-stu-id="1fd5a-116">Create a <xref:System.Windows.DataTemplate> that defines the appearance of the row details section.</span></span>  
  
     <span data-ttu-id="1fd5a-117">下列 XAML 示範<xref:System.Windows.Controls.DataGrid>以及如何定義<xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A>內嵌。</span><span class="sxs-lookup"><span data-stu-id="1fd5a-117">The following XAML shows the <xref:System.Windows.Controls.DataGrid> and how to define the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> inline.</span></span> <span data-ttu-id="1fd5a-118"><xref:System.Windows.Controls.DataGrid>顯示三個值在每個資料列和三個多個值時選取的資料列。</span><span class="sxs-lookup"><span data-stu-id="1fd5a-118">The <xref:System.Windows.Controls.DataGrid> displays three values in each row and three more values when the row is selected.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#1](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml#1)]  
  
     <span data-ttu-id="1fd5a-119">下列程式碼顯示用來選取的資料，會顯示在查詢<xref:System.Windows.Controls.DataGrid>。</span><span class="sxs-lookup"><span data-stu-id="1fd5a-119">The following code shows the query that is used to select the data that is displayed in the <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="1fd5a-120">在此範例中，查詢會從包含客戶資訊的實體選取資料。</span><span class="sxs-lookup"><span data-stu-id="1fd5a-120">In this example, the query selects data from an entity that contains customer information.</span></span>  
  
     [!code-csharp[DataGrid_RowDetails#2](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml.cs#2)]
     [!code-vb[DataGrid_RowDetails#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_rowdetails/vb/mainwindow.xaml.vb#2)]  
  
### <a name="to-display-row-details-by-using-a-resource"></a><span data-ttu-id="1fd5a-121">若要使用的資源來顯示資料列詳細資料</span><span class="sxs-lookup"><span data-stu-id="1fd5a-121">To display row details by using a resource</span></span>  
  
1. <span data-ttu-id="1fd5a-122">建立<xref:System.Windows.Controls.DataGrid>顯示來自資料來源的資料。</span><span class="sxs-lookup"><span data-stu-id="1fd5a-122">Create a <xref:System.Windows.Controls.DataGrid> that displays data from a data source.</span></span>  
  
2. <span data-ttu-id="1fd5a-123">新增<xref:System.Windows.FrameworkElement.Resources%2A>元素的根項目，例如<xref:System.Windows.Window>控制或<xref:System.Windows.Controls.Page>控制項，或是將<xref:System.Windows.Application.Resources%2A>項目<xref:System.Windows.Application>App.xaml （或 Application.xaml） 檔案中的類別。</span><span class="sxs-lookup"><span data-stu-id="1fd5a-123">Add a <xref:System.Windows.FrameworkElement.Resources%2A> element to the root element, such as a <xref:System.Windows.Window> control or a <xref:System.Windows.Controls.Page> control, or add a <xref:System.Windows.Application.Resources%2A> element to the <xref:System.Windows.Application> class in the App.xaml (or Application.xaml) file.</span></span>  
  
3. <span data-ttu-id="1fd5a-124">在資源項目中，建立<xref:System.Windows.DataTemplate>，定義資料列的 [詳細資料] 區段的外觀。</span><span class="sxs-lookup"><span data-stu-id="1fd5a-124">In the resources element, create a <xref:System.Windows.DataTemplate> that defines the appearance of the row details section.</span></span>  
  
     <span data-ttu-id="1fd5a-125">下列 XAML 示範<xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A>中所定義<xref:System.Windows.Application>類別。</span><span class="sxs-lookup"><span data-stu-id="1fd5a-125">The following XAML shows the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> defined in the <xref:System.Windows.Application> class.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#3](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/app.xaml#3)]  
  
4. <span data-ttu-id="1fd5a-126">在  <xref:System.Windows.DataTemplate>，將[X:key 指示詞](../../xaml-services/x-key-directive.md)唯一識別資料範本的值。</span><span class="sxs-lookup"><span data-stu-id="1fd5a-126">On the <xref:System.Windows.DataTemplate>, set the [x:Key Directive](../../xaml-services/x-key-directive.md) to a value that uniquely identifies the data template.</span></span>  
  
5. <span data-ttu-id="1fd5a-127">在 <xref:System.Windows.Controls.DataGrid>項目，設定<xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A>屬性，以在先前步驟中定義的資源。</span><span class="sxs-lookup"><span data-stu-id="1fd5a-127">In the <xref:System.Windows.Controls.DataGrid> element, set the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property to the resource defined in the previous steps.</span></span> <span data-ttu-id="1fd5a-128">將資源指派為靜態資源。</span><span class="sxs-lookup"><span data-stu-id="1fd5a-128">Assign the resource as a static resource.</span></span>  
  
     <span data-ttu-id="1fd5a-129">下列 XAML 顯示<xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A>屬性設定為 資源從先前的範例。</span><span class="sxs-lookup"><span data-stu-id="1fd5a-129">The following XAML shows the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property set to the resource from the previous example.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#4](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/window2.xaml#4)]  
  
### <a name="to-set-visibility-and-prevent-horizontal-scrolling-for-row-details"></a><span data-ttu-id="1fd5a-130">若要設定可見性，並避免水平捲動的資料列詳細資料</span><span class="sxs-lookup"><span data-stu-id="1fd5a-130">To set visibility and prevent horizontal scrolling for row details</span></span>  
  
1. <span data-ttu-id="1fd5a-131">如有需要設定<xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A>屬性設<xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode>值。</span><span class="sxs-lookup"><span data-stu-id="1fd5a-131">If needed, set the <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> property to a <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> value.</span></span>  
  
     <span data-ttu-id="1fd5a-132">根據預設，此值設為<xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected>。</span><span class="sxs-lookup"><span data-stu-id="1fd5a-132">By default, the value is set to <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected>.</span></span> <span data-ttu-id="1fd5a-133">您可以將它設定為<xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible>以顯示所有資料列的詳細資料或<xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed>隱藏所有資料列的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="1fd5a-133">You can set it to <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible> to show the details for all of the rows or <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed> to hide the details for all rows.</span></span>  
  
2. <span data-ttu-id="1fd5a-134">如有需要設定<xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A>屬性設`true`以避免資料列詳細資料從水平捲動的區段。</span><span class="sxs-lookup"><span data-stu-id="1fd5a-134">If needed, set the <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> property to `true` to prevent the row details section from scrolling horizontally.</span></span>

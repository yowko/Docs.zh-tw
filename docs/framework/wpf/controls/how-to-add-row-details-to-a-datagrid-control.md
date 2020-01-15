---
title: 如何：將資料列詳細資料加入至 DataGrid 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataTemplate [WPF], DataGrid
- row details [WPF], DataGrid
- DataGrid [WPF], row details
ms.assetid: 0bdc6f50-9b4c-483f-9df6-a47a1fde998b
ms.openlocfilehash: 4db414e1907d42071f7251c390077d4020fa577c
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559673"
---
# <a name="how-to-add-row-details-to-a-datagrid-control"></a><span data-ttu-id="8ac53-102">如何：將資料列詳細資料加入至 DataGrid 控制項</span><span class="sxs-lookup"><span data-stu-id="8ac53-102">How to: Add Row Details to a DataGrid Control</span></span>
<span data-ttu-id="8ac53-103">使用 <xref:System.Windows.Controls.DataGrid> 控制項時，您可以藉由加入資料列詳細資料區段來自訂資料呈現方式。</span><span class="sxs-lookup"><span data-stu-id="8ac53-103">When using the <xref:System.Windows.Controls.DataGrid> control, you can customize the data presentation by adding a row details section.</span></span> <span data-ttu-id="8ac53-104">加入 [資料列詳細資料] 區段可讓您在範本中，將可選擇性地顯示或折迭的某些資料群組起來。</span><span class="sxs-lookup"><span data-stu-id="8ac53-104">Adding a row details section enables you to group some data in a template that is optionally visible or collapsed.</span></span> <span data-ttu-id="8ac53-105">例如，您可以將資料列詳細資料加入至僅顯示 <xref:System.Windows.Controls.DataGrid>中每個資料列之資料摘要的 <xref:System.Windows.Controls.DataGrid>，但當使用者選取資料列時，會顯示更多的資料欄位。</span><span class="sxs-lookup"><span data-stu-id="8ac53-105">For example, you can add row details to a <xref:System.Windows.Controls.DataGrid> that presents only a summary of the data for each row in the <xref:System.Windows.Controls.DataGrid>, but presents more data fields when the user selects a row.</span></span> <span data-ttu-id="8ac53-106">您可以在 [<xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A>] 屬性中定義 [資料列詳細資料] 區段的範本。</span><span class="sxs-lookup"><span data-stu-id="8ac53-106">You define the template for the row details section in the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property.</span></span> <span data-ttu-id="8ac53-107">下圖顯示資料列詳細資料區段的範例。</span><span class="sxs-lookup"><span data-stu-id="8ac53-107">The following illustration shows an example of a row details section.</span></span>  
  
 <span data-ttu-id="8ac53-108">![以資料列詳細資料顯示的 DataGrid](./media/ndp-rowdetails.png "NDP_RowDetails")</span><span class="sxs-lookup"><span data-stu-id="8ac53-108">![DataGrid shown with row details](./media/ndp-rowdetails.png "NDP_RowDetails")</span></span>  
  
 <span data-ttu-id="8ac53-109">您可以將資料列詳細資料範本定義為內嵌 XAML 或資源。</span><span class="sxs-lookup"><span data-stu-id="8ac53-109">You define the row details template as either inline XAML or as a resource.</span></span> <span data-ttu-id="8ac53-110">下列程式會顯示這兩種方法。</span><span class="sxs-lookup"><span data-stu-id="8ac53-110">Both approaches are shown in the following procedures.</span></span> <span data-ttu-id="8ac53-111">新增為資源的資料範本可以在整個專案中使用，而不需要重新建立範本。</span><span class="sxs-lookup"><span data-stu-id="8ac53-111">A data template that is added as a resource can be used throughout the project without re-creating the template.</span></span> <span data-ttu-id="8ac53-112">加入為內嵌 XAML 的資料範本只能從其定義所在的控制項存取。</span><span class="sxs-lookup"><span data-stu-id="8ac53-112">A data template that is added as inline XAML is only accessible from the control where it is defined.</span></span>  
  
### <a name="to-display-row-details-by-using-inline-xaml"></a><span data-ttu-id="8ac53-113">若要使用內嵌 XAML 顯示資料列詳細資料</span><span class="sxs-lookup"><span data-stu-id="8ac53-113">To display row details by using inline XAML</span></span>  
  
1. <span data-ttu-id="8ac53-114">建立顯示資料來源資料的 <xref:System.Windows.Controls.DataGrid>。</span><span class="sxs-lookup"><span data-stu-id="8ac53-114">Create a <xref:System.Windows.Controls.DataGrid> that displays data from a data source.</span></span>  
  
2. <span data-ttu-id="8ac53-115">在 <xref:System.Windows.Controls.DataGrid> 項目中，加入 <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> 項目。</span><span class="sxs-lookup"><span data-stu-id="8ac53-115">In the <xref:System.Windows.Controls.DataGrid> element, add a <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> element.</span></span>  
  
3. <span data-ttu-id="8ac53-116">建立定義 [資料列詳細資料] 區段外觀的 <xref:System.Windows.DataTemplate>。</span><span class="sxs-lookup"><span data-stu-id="8ac53-116">Create a <xref:System.Windows.DataTemplate> that defines the appearance of the row details section.</span></span>  
  
     <span data-ttu-id="8ac53-117">下列 XAML 會顯示 <xref:System.Windows.Controls.DataGrid> 以及如何定義內嵌 <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A>。</span><span class="sxs-lookup"><span data-stu-id="8ac53-117">The following XAML shows the <xref:System.Windows.Controls.DataGrid> and how to define the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> inline.</span></span> <span data-ttu-id="8ac53-118">當選取資料列時，<xref:System.Windows.Controls.DataGrid> 會在每個資料列中顯示三個值，以及三個更多的值。</span><span class="sxs-lookup"><span data-stu-id="8ac53-118">The <xref:System.Windows.Controls.DataGrid> displays three values in each row and three more values when the row is selected.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#1](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml#1)]  
  
     <span data-ttu-id="8ac53-119">下列程式碼顯示用來選取 <xref:System.Windows.Controls.DataGrid>中所顯示之資料的查詢。</span><span class="sxs-lookup"><span data-stu-id="8ac53-119">The following code shows the query that is used to select the data that is displayed in the <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="8ac53-120">在此範例中，查詢會從包含客戶資訊的實體選取資料。</span><span class="sxs-lookup"><span data-stu-id="8ac53-120">In this example, the query selects data from an entity that contains customer information.</span></span>  
  
     [!code-csharp[DataGrid_RowDetails#2](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml.cs#2)]
     [!code-vb[DataGrid_RowDetails#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_rowdetails/vb/mainwindow.xaml.vb#2)]  
  
### <a name="to-display-row-details-by-using-a-resource"></a><span data-ttu-id="8ac53-121">使用資源顯示資料列詳細資料</span><span class="sxs-lookup"><span data-stu-id="8ac53-121">To display row details by using a resource</span></span>  
  
1. <span data-ttu-id="8ac53-122">建立顯示資料來源資料的 <xref:System.Windows.Controls.DataGrid>。</span><span class="sxs-lookup"><span data-stu-id="8ac53-122">Create a <xref:System.Windows.Controls.DataGrid> that displays data from a data source.</span></span>  
  
2. <span data-ttu-id="8ac53-123">將 <xref:System.Windows.FrameworkElement.Resources%2A> 元素新增至根項目（例如 <xref:System.Windows.Window> 控制項或 <xref:System.Windows.Controls.Page> 控制項），或將 <xref:System.Windows.Application.Resources%2A> 專案加入至 app.xaml （或 app.xaml）檔案中的 <xref:System.Windows.Application> 類別。</span><span class="sxs-lookup"><span data-stu-id="8ac53-123">Add a <xref:System.Windows.FrameworkElement.Resources%2A> element to the root element, such as a <xref:System.Windows.Window> control or a <xref:System.Windows.Controls.Page> control, or add a <xref:System.Windows.Application.Resources%2A> element to the <xref:System.Windows.Application> class in the App.xaml (or Application.xaml) file.</span></span>  
  
3. <span data-ttu-id="8ac53-124">在 resources 元素中，建立定義 [資料列詳細資料] 區段外觀的 <xref:System.Windows.DataTemplate>。</span><span class="sxs-lookup"><span data-stu-id="8ac53-124">In the resources element, create a <xref:System.Windows.DataTemplate> that defines the appearance of the row details section.</span></span>  
  
     <span data-ttu-id="8ac53-125">下列 XAML 會顯示 <xref:System.Windows.Application> 類別中定義的 <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A>。</span><span class="sxs-lookup"><span data-stu-id="8ac53-125">The following XAML shows the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> defined in the <xref:System.Windows.Application> class.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#3](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/app.xaml#3)]  
  
4. <span data-ttu-id="8ac53-126">在 <xref:System.Windows.DataTemplate>上，將  [x：Key](../../../desktop-wpf/xaml-services/xkey-directive.md)  指示詞設定為可唯一識別資料範本的值。</span><span class="sxs-lookup"><span data-stu-id="8ac53-126">On the <xref:System.Windows.DataTemplate>, set the [x:Key Directive](../../../desktop-wpf/xaml-services/xkey-directive.md) to a value that uniquely identifies the data template.</span></span>  
  
5. <span data-ttu-id="8ac53-127">在 <xref:System.Windows.Controls.DataGrid> 元素中，將 <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> 屬性設定為先前步驟中定義的資源。</span><span class="sxs-lookup"><span data-stu-id="8ac53-127">In the <xref:System.Windows.Controls.DataGrid> element, set the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property to the resource defined in the previous steps.</span></span> <span data-ttu-id="8ac53-128">將資源指派為靜態資源。</span><span class="sxs-lookup"><span data-stu-id="8ac53-128">Assign the resource as a static resource.</span></span>  
  
     <span data-ttu-id="8ac53-129">下列 XAML 顯示 <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> 屬性設定為上一個範例中的資源。</span><span class="sxs-lookup"><span data-stu-id="8ac53-129">The following XAML shows the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property set to the resource from the previous example.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#4](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/window2.xaml#4)]  
  
### <a name="to-set-visibility-and-prevent-horizontal-scrolling-for-row-details"></a><span data-ttu-id="8ac53-130">若要設定可見度並防止水準滾動列詳細資料</span><span class="sxs-lookup"><span data-stu-id="8ac53-130">To set visibility and prevent horizontal scrolling for row details</span></span>  
  
1. <span data-ttu-id="8ac53-131">如有需要，請將 <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> 屬性設定為 <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> 值。</span><span class="sxs-lookup"><span data-stu-id="8ac53-131">If needed, set the <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> property to a <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> value.</span></span>  
  
     <span data-ttu-id="8ac53-132">依預設，此值設定為 <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected>。</span><span class="sxs-lookup"><span data-stu-id="8ac53-132">By default, the value is set to <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected>.</span></span> <span data-ttu-id="8ac53-133">您可以將它設定為 <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible>，以顯示所有資料列的詳細資料，或 <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed> 隱藏所有資料列的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="8ac53-133">You can set it to <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible> to show the details for all of the rows or <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed> to hide the details for all rows.</span></span>  
  
2. <span data-ttu-id="8ac53-134">如有需要，請將 <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> 屬性設定為 [`true`]，以防止資料列詳細資料區段水準滾動。</span><span class="sxs-lookup"><span data-stu-id="8ac53-134">If needed, set the <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> property to `true` to prevent the row details section from scrolling horizontally.</span></span>

---
title: "GridView 概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GridView view mode [WPF]
- ListView controls [WPF], GridView view mode
- controls [WPF], ListView
ms.assetid: b2d02267-32b3-40ce-8e9f-06972d8749d9
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 44574b5737873371f9a7bc9be2d851a8ae1e101b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="gridview-overview"></a><span data-ttu-id="ff250-102">GridView 概觀</span><span class="sxs-lookup"><span data-stu-id="ff250-102">GridView Overview</span></span>
<span data-ttu-id="ff250-103"><xref:System.Windows.Controls.GridView>檢視模式是一種檢視模式的<xref:System.Windows.Controls.ListView>控制項。</span><span class="sxs-lookup"><span data-stu-id="ff250-103"><xref:System.Windows.Controls.GridView> view mode is one of the view modes for a <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="ff250-104"><xref:System.Windows.Controls.GridView>類別和其支援的類別可讓您和您的使用者通常使用按鈕為互動式的資料行標頭的資料表中檢視項目集合。</span><span class="sxs-lookup"><span data-stu-id="ff250-104">The <xref:System.Windows.Controls.GridView> class and its supporting classes enable you and your users to view item collections in a table that typically uses buttons as interactive column headers.</span></span> <span data-ttu-id="ff250-105">本主題將介紹<xref:System.Windows.Controls.GridView>類別，並且摘要說明其用途。</span><span class="sxs-lookup"><span data-stu-id="ff250-105">This topic introduces the <xref:System.Windows.Controls.GridView> class and outlines its use.</span></span>  
  
  
  
<a name="DefiningaListViewthatusesGridViewView"></a>   
## <a name="what-is-a-gridview-view"></a><span data-ttu-id="ff250-106">什麼是 GridView 檢視？</span><span class="sxs-lookup"><span data-stu-id="ff250-106">What Is a GridView View?</span></span>  
 <span data-ttu-id="ff250-107"><xref:System.Windows.Controls.GridView>檢視模式顯示項目清單，由繫結至資料行的資料欄位和顯示資料行標頭，識別欄位。</span><span class="sxs-lookup"><span data-stu-id="ff250-107">The <xref:System.Windows.Controls.GridView> view mode displays a list of data items by binding data fields to columns and by displaying a column header to identify the field.</span></span> <span data-ttu-id="ff250-108">預設值<xref:System.Windows.Controls.GridView>樣式實作作為資料行標頭的按鈕。</span><span class="sxs-lookup"><span data-stu-id="ff250-108">The default <xref:System.Windows.Controls.GridView> style implements buttons as column headers.</span></span> <span data-ttu-id="ff250-109">藉由使用資料行標頭的按鈕，您可以實作重要的使用者互動功能。例如，使用者可以按一下資料行標頭來排序<xref:System.Windows.Controls.GridView>根據特定資料行的內容資料。</span><span class="sxs-lookup"><span data-stu-id="ff250-109">By using buttons for column headers, you can implement important user interaction capabilities; for example, users can click the column header to sort <xref:System.Windows.Controls.GridView> data according to the contents of a specific column.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ff250-110">按鈕控制項<xref:System.Windows.Controls.GridView>資料行標頭的用法衍生自<xref:System.Windows.Controls.Primitives.ButtonBase>。</span><span class="sxs-lookup"><span data-stu-id="ff250-110">The button controls that <xref:System.Windows.Controls.GridView> uses for column headers are derived from <xref:System.Windows.Controls.Primitives.ButtonBase>.</span></span>  
  
 <span data-ttu-id="ff250-111">下圖顯示<xref:System.Windows.Controls.GridView>檢視<xref:System.Windows.Controls.ListView>內容。</span><span class="sxs-lookup"><span data-stu-id="ff250-111">The following illustration shows a <xref:System.Windows.Controls.GridView> view of <xref:System.Windows.Controls.ListView> content.</span></span>  
  
 <span data-ttu-id="ff250-112">**ListView 內容的 GridView 檢視**</span><span class="sxs-lookup"><span data-stu-id="ff250-112">**GridView view of ListView content**</span></span>  
  
 <span data-ttu-id="ff250-113">![已設定樣式的 ListView](../../../../docs/framework/wpf/controls/media/styledlistview.PNG "StyledListView")</span><span class="sxs-lookup"><span data-stu-id="ff250-113">![Styled ListView](../../../../docs/framework/wpf/controls/media/styledlistview.PNG "StyledListView")</span></span>  
  
 <span data-ttu-id="ff250-114"><xref:System.Windows.Controls.GridView>資料行都由<xref:System.Windows.Controls.GridViewColumn>物件，其內容可以自動調整大小。</span><span class="sxs-lookup"><span data-stu-id="ff250-114"><xref:System.Windows.Controls.GridView> columns are represented by <xref:System.Windows.Controls.GridViewColumn> objects, which can automatically size to their content.</span></span> <span data-ttu-id="ff250-115">（選擇性） 您可以明確設定<xref:System.Windows.Controls.GridViewColumn>寬度。</span><span class="sxs-lookup"><span data-stu-id="ff250-115">Optionally, you can explicitly set a <xref:System.Windows.Controls.GridViewColumn> to a specific width.</span></span> <span data-ttu-id="ff250-116">您可以藉由拖曳資料行標頭間的移駐夾來調整資料行大小。</span><span class="sxs-lookup"><span data-stu-id="ff250-116">You can resize columns by dragging the gripper between column headers.</span></span> <span data-ttu-id="ff250-117">您可以也會動態地新增、 移除、 取代和重新排列資料行，因為這項功能已內建在<xref:System.Windows.Controls.GridView>。</span><span class="sxs-lookup"><span data-stu-id="ff250-117">You can also dynamically add, remove, replace, and reorder columns because this functionality is built into <xref:System.Windows.Controls.GridView>.</span></span> <span data-ttu-id="ff250-118">不過，<xref:System.Windows.Controls.GridView>無法直接更新它所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="ff250-118">However, <xref:System.Windows.Controls.GridView> cannot directly update the data that it displays.</span></span>  
  
 <span data-ttu-id="ff250-119">下列範例示範如何定義<xref:System.Windows.Controls.GridView>，會顯示員工資料。</span><span class="sxs-lookup"><span data-stu-id="ff250-119">The following example shows how to define a <xref:System.Windows.Controls.GridView> that displays employee data.</span></span> <span data-ttu-id="ff250-120">在此範例中，<xref:System.Windows.Controls.ListView>定義`EmployeeInfoDataSource`為<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>。</span><span class="sxs-lookup"><span data-stu-id="ff250-120">In this example, <xref:System.Windows.Controls.ListView> defines the `EmployeeInfoDataSource` as the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>.</span></span> <span data-ttu-id="ff250-121">屬性定義的<xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>繫結<xref:System.Windows.Controls.GridViewColumn>內容`EmployeeInfoDataSource`資料類別。</span><span class="sxs-lookup"><span data-stu-id="ff250-121">The property definitions of <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> bind <xref:System.Windows.Controls.GridViewColumn> content to `EmployeeInfoDataSource` data categories.</span></span>  
  
 [!code-xaml[ListViewCode#ListViewEmployee](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 <span data-ttu-id="ff250-122">下圖顯示上一個範例所建立的表格。</span><span class="sxs-lookup"><span data-stu-id="ff250-122">The following illustration shows the table that the previous example creates.</span></span>  
  
 <span data-ttu-id="ff250-123">**顯示來自 ItemsSource 之資料的 GridView**</span><span class="sxs-lookup"><span data-stu-id="ff250-123">**GridView that displays data from an ItemsSource**</span></span>  
  
 <span data-ttu-id="ff250-124">![含有 GridView 輸出的 ListView](../../../../docs/framework/wpf/controls/media/listviewgridview.JPG "ListViewGridView")</span><span class="sxs-lookup"><span data-stu-id="ff250-124">![ListView with GridView output](../../../../docs/framework/wpf/controls/media/listviewgridview.JPG "ListViewGridView")</span></span>  
  
<a name="GridViewLayoutandStyle"></a>   
## <a name="gridview-layout-and-style"></a><span data-ttu-id="ff250-125">GridView 版面配置和樣式</span><span class="sxs-lookup"><span data-stu-id="ff250-125">GridView Layout and Style</span></span>  
 <span data-ttu-id="ff250-126">資料行儲存格和資料行標頭的<xref:System.Windows.Controls.GridViewColumn>具有相同寬度。</span><span class="sxs-lookup"><span data-stu-id="ff250-126">The column cells and the column header of a <xref:System.Windows.Controls.GridViewColumn> have the same width.</span></span> <span data-ttu-id="ff250-127">根據預設，每個資料行會依據其內容來調整其寬度。</span><span class="sxs-lookup"><span data-stu-id="ff250-127">By default, each column sizes its width to fit its content.</span></span> <span data-ttu-id="ff250-128">您也可以選擇將資料行設定成固定寬度。</span><span class="sxs-lookup"><span data-stu-id="ff250-128">Optionally, you can set a column to a fixed width.</span></span>  
  
 <span data-ttu-id="ff250-129">相關資料內容會顯示在水平資料列中。</span><span class="sxs-lookup"><span data-stu-id="ff250-129">Related data content displays in horizontal rows.</span></span> <span data-ttu-id="ff250-130">例如，在上圖中，是將每個員工的姓氏、名字及識別碼都顯示成一組，因為它們是出現在水平資料列中。</span><span class="sxs-lookup"><span data-stu-id="ff250-130">For example, in the previous illustration, each employee's last name, first name, and ID number are displayed as a set because they appear in a horizontal row.</span></span>  
  
<a name="DefiningandStylingColumnsinaGridView"></a>   
### <a name="defining-and-styling-columns-in-a-gridview"></a><span data-ttu-id="ff250-131">定義及設定 GridView 中的資料行樣式</span><span class="sxs-lookup"><span data-stu-id="ff250-131">Defining and Styling Columns in a GridView</span></span>  
 <span data-ttu-id="ff250-132">定義要顯示的資料欄位時<xref:System.Windows.Controls.GridViewColumn>，使用<xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>， <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>，或<xref:System.Windows.Controls.GridViewColumn.CellTemplateSelector%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="ff250-132">When defining the data field to display in a <xref:System.Windows.Controls.GridViewColumn>, use the <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>, <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>, or <xref:System.Windows.Controls.GridViewColumn.CellTemplateSelector%2A> properties.</span></span> <span data-ttu-id="ff250-133"><xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>屬性會優先於其中一個範本內容。</span><span class="sxs-lookup"><span data-stu-id="ff250-133">The <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> property takes precedence over either of the template properties.</span></span>  
  
 <span data-ttu-id="ff250-134">若要指定內容的對齊方式的資料行中<xref:System.Windows.Controls.GridView>，定義<xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>。</span><span class="sxs-lookup"><span data-stu-id="ff250-134">To specify the alignment of content in a column of a <xref:System.Windows.Controls.GridView>, define a <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>.</span></span> <span data-ttu-id="ff250-135">請勿使用<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>和<xref:System.Windows.Controls.Control.VerticalContentAlignment%2A>屬性<xref:System.Windows.Controls.ListView>使用所顯示的內容<xref:System.Windows.Controls.GridView>。</span><span class="sxs-lookup"><span data-stu-id="ff250-135">Do not use the <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> and <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> properties for <xref:System.Windows.Controls.ListView> content that is displayed by using a <xref:System.Windows.Controls.GridView>.</span></span>  
  
 <span data-ttu-id="ff250-136">若要指定資料行標頭的範本和樣式屬性，請使用<xref:System.Windows.Controls.GridView>， <xref:System.Windows.Controls.GridViewColumn>，和<xref:System.Windows.Controls.GridViewColumnHeader>類別。</span><span class="sxs-lookup"><span data-stu-id="ff250-136">To specify template and style properties for column headers, use the <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridViewColumn>, and <xref:System.Windows.Controls.GridViewColumnHeader> classes.</span></span> <span data-ttu-id="ff250-137">如需詳細資訊，請參閱 [GridView 資料行標頭樣式和範本概觀](../../../../docs/framework/wpf/controls/gridview-column-header-styles-and-templates-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="ff250-137">For more information, see [GridView Column Header Styles and Templates Overview](../../../../docs/framework/wpf/controls/gridview-column-header-styles-and-templates-overview.md).</span></span>  
  
<a name="AddingVisualElementstoaGridViewView"></a>   
### <a name="adding-visual-elements-to-a-gridview"></a><span data-ttu-id="ff250-138">將視覺元素新增到 GridView</span><span class="sxs-lookup"><span data-stu-id="ff250-138">Adding Visual Elements to a GridView</span></span>  
 <span data-ttu-id="ff250-139">若要加入視覺項目，例如<xref:System.Windows.Controls.CheckBox>和<xref:System.Windows.Controls.Button>控制項，為<xref:System.Windows.Controls.GridView>檢視模式，請使用範本或樣式。</span><span class="sxs-lookup"><span data-stu-id="ff250-139">To add visual elements, such as <xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.Button> controls, to a <xref:System.Windows.Controls.GridView> view mode, use templates or styles.</span></span>  
  
 <span data-ttu-id="ff250-140">如果您明確地定義視覺項目，做為資料項目，它可以出現一次只能在<xref:System.Windows.Controls.GridView>。</span><span class="sxs-lookup"><span data-stu-id="ff250-140">If you explicitly define a visual element as a data item, it can appear only one time in a <xref:System.Windows.Controls.GridView>.</span></span> <span data-ttu-id="ff250-141">之所以會有這項限制，是因為一個元素只能有一個父代，因此在視覺化樹狀結構中只能出現一次。</span><span class="sxs-lookup"><span data-stu-id="ff250-141">This limitation exists because an element can have only one parent and therefore, can appear only one time in the visual tree.</span></span>  
  
<a name="StylingRowsinaGridViewView"></a>   
### <a name="styling-rows-in-a-gridview"></a><span data-ttu-id="ff250-142">設定 GridView 中資料列的樣式</span><span class="sxs-lookup"><span data-stu-id="ff250-142">Styling Rows in a GridView</span></span>  
 <span data-ttu-id="ff250-143">使用<xref:System.Windows.Controls.GridViewRowPresenter>和<xref:System.Windows.Controls.GridViewHeaderRowPresenter>格式化及顯示的資料列類別<xref:System.Windows.Controls.GridView>。</span><span class="sxs-lookup"><span data-stu-id="ff250-143">Use the <xref:System.Windows.Controls.GridViewRowPresenter> and <xref:System.Windows.Controls.GridViewHeaderRowPresenter> classes to format and display the rows of a <xref:System.Windows.Controls.GridView>.</span></span> <span data-ttu-id="ff250-144">如需如何樣式中的資料列<xref:System.Windows.Controls.GridView>檢視模式，請參閱[GridView 樣式 ListView 的實作中的資料列](../../../../docs/framework/wpf/controls/how-to-style-a-row-in-a-listview-that-implements-a-gridview.md)。</span><span class="sxs-lookup"><span data-stu-id="ff250-144">For an example of how to style rows in a <xref:System.Windows.Controls.GridView> view mode, see [Style a Row in a ListView That Implements a GridView](../../../../docs/framework/wpf/controls/how-to-style-a-row-in-a-listview-that-implements-a-gridview.md).</span></span>  
  
<a name="AlignmentIssuesWhenUsingItemContainerStyle"></a>   
### <a name="alignment-issues-when-you-use-itemcontainerstyle"></a><span data-ttu-id="ff250-145">使用 ItemContainerStyle 時的對齊問題</span><span class="sxs-lookup"><span data-stu-id="ff250-145">Alignment Issues When You Use ItemContainerStyle</span></span>  
 <span data-ttu-id="ff250-146">若要避免資料行標頭之間的資料格的對齊問題，請勿設定屬性，或指定的範本，會影響中項目的寬度<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>。</span><span class="sxs-lookup"><span data-stu-id="ff250-146">To prevent alignment issues between column headers and cells, do not set a property or specify a template that affects the width of an item in an <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>.</span></span> <span data-ttu-id="ff250-147">例如，請勿設定<xref:System.Windows.FrameworkElement.Margin%2A>屬性，或指定<xref:System.Windows.Controls.ControlTemplate>，將加上<xref:System.Windows.Controls.CheckBox>至<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>上定義的<xref:System.Windows.Controls.ListView>控制項。</span><span class="sxs-lookup"><span data-stu-id="ff250-147">For example, do not set the <xref:System.Windows.FrameworkElement.Margin%2A> property or specify a <xref:System.Windows.Controls.ControlTemplate> that adds a <xref:System.Windows.Controls.CheckBox> to an <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> that is defined on a <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="ff250-148">請改為指定的屬性和會影響直接上定義的類別資料行寬度的範本<xref:System.Windows.Controls.GridView>檢視模式。</span><span class="sxs-lookup"><span data-stu-id="ff250-148">Instead, specify the properties and templates that affect column width directly on classes that define a <xref:System.Windows.Controls.GridView> view mode.</span></span>  
  
 <span data-ttu-id="ff250-149">例如，若要新增<xref:System.Windows.Controls.CheckBox>中的資料列<xref:System.Windows.Controls.GridView>檢視模式中，加入<xref:System.Windows.Controls.CheckBox>至<xref:System.Windows.DataTemplate>，然後設定<xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>屬性的<xref:System.Windows.DataTemplate>。</span><span class="sxs-lookup"><span data-stu-id="ff250-149">For example, to add a <xref:System.Windows.Controls.CheckBox> to the rows in <xref:System.Windows.Controls.GridView> view mode, add the <xref:System.Windows.Controls.CheckBox> to a <xref:System.Windows.DataTemplate>, and then set the <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> property to that <xref:System.Windows.DataTemplate>.</span></span>  
  
<a name="InteractingwithaGridViewControl"></a>   
## <a name="user-interactions-with-a-gridview"></a><span data-ttu-id="ff250-150">使用者與 GridView 的互動</span><span class="sxs-lookup"><span data-stu-id="ff250-150">User Interactions with a GridView</span></span>  
 <span data-ttu-id="ff250-151">當您使用<xref:System.Windows.Controls.GridView>應用程式中，使用者可以互動和修改的格式設定<xref:System.Windows.Controls.GridView>。</span><span class="sxs-lookup"><span data-stu-id="ff250-151">When you use a <xref:System.Windows.Controls.GridView> in your application, users can interact with and modify the formatting of the <xref:System.Windows.Controls.GridView>.</span></span> <span data-ttu-id="ff250-152">例如，使用者可以重新排列資料行、調整資料行大小、選取表格中的項目，以及捲動內容。</span><span class="sxs-lookup"><span data-stu-id="ff250-152">For example, users can reorder columns, resize a column, select items in a table, and scroll through content.</span></span> <span data-ttu-id="ff250-153">您也可以定義會在使用者按一下資料行標頭按鈕時回應的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="ff250-153">You can also define an event handler that responds when a user clicks the column header button.</span></span> <span data-ttu-id="ff250-154">此事件處理常式可以執行作業，例如排序的資料，會顯示在<xref:System.Windows.Controls.GridView>根據資料行的內容。</span><span class="sxs-lookup"><span data-stu-id="ff250-154">The event handler can perform operations like sorting the data that is displayed in the <xref:System.Windows.Controls.GridView> according to the contents of a column.</span></span>  
  
 <span data-ttu-id="ff250-155">下列清單詳細的功能使用討論<xref:System.Windows.Controls.GridView>與使用者互動：</span><span class="sxs-lookup"><span data-stu-id="ff250-155">The following list discusses in more detail the capabilities of using <xref:System.Windows.Controls.GridView> for user interaction:</span></span>  
  
-   <span data-ttu-id="ff250-156">**使用拖放方法來重新排列資料行。**</span><span class="sxs-lookup"><span data-stu-id="ff250-156">**Reorder columns by using the drag-and-drop method.**</span></span>  
  
     <span data-ttu-id="ff250-157">使用者可以重新排列中的資料行<xref:System.Windows.Controls.GridView>資料行標頭上方時，按滑鼠左鍵，然後將該資料行拖曳至新位置。</span><span class="sxs-lookup"><span data-stu-id="ff250-157">Users can reorder columns in a <xref:System.Windows.Controls.GridView> by pressing the left mouse button while it is over a column header and then dragging that column to a new position.</span></span> <span data-ttu-id="ff250-158">當使用者拖曳資料行標頭時，除了會顯示一條指出資料行插入位置的實心黑線之外，也會顯示該標頭的浮動版本。</span><span class="sxs-lookup"><span data-stu-id="ff250-158">While the user drags the column header, a floating version of the header is displayed as well as a solid black line that shows where to insert the column.</span></span>  
  
     <span data-ttu-id="ff250-159">如果您想要修改預設樣式浮點版本的標頭，指定<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.GridViewColumnHeader>類型，它是觸發時<xref:System.Windows.Controls.GridViewColumnHeader.Role%2A>屬性設定為<xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>。</span><span class="sxs-lookup"><span data-stu-id="ff250-159">If you want to modify the default style for the floating version of a header, specify a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.GridViewColumnHeader> type that is triggered when the <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> property is set to <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>.</span></span> <span data-ttu-id="ff250-160">如需詳細資訊，請參閱[為已拖曳的 GridView 資料行標頭建立樣式](../../../../docs/framework/wpf/controls/how-to-create-a-style-for-a-dragged-gridview-column-header.md)。</span><span class="sxs-lookup"><span data-stu-id="ff250-160">For more information, see [Create a Style for a Dragged GridView Column Header](../../../../docs/framework/wpf/controls/how-to-create-a-style-for-a-dragged-gridview-column-header.md).</span></span>  
  
-   <span data-ttu-id="ff250-161">**依資料行內容調整資料行大小。**</span><span class="sxs-lookup"><span data-stu-id="ff250-161">**Resize a column to its content.**</span></span>  
  
     <span data-ttu-id="ff250-162">使用者可以按兩下資料行標頭右邊的移駐夾，來依資料行內容調整資料行大小。</span><span class="sxs-lookup"><span data-stu-id="ff250-162">Users can double-click the gripper to the right of a column header in order to resize a column to fit its content.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ff250-163">您可以設定<xref:System.Windows.Controls.GridViewColumn.Width%2A>屬性`Double.NaN`產生相同的效果。</span><span class="sxs-lookup"><span data-stu-id="ff250-163">You can set the <xref:System.Windows.Controls.GridViewColumn.Width%2A> property to `Double.NaN` to produce the same effect.</span></span>  
  
-   <span data-ttu-id="ff250-164">**選取資料列項目。**</span><span class="sxs-lookup"><span data-stu-id="ff250-164">**Select row items.**</span></span>  
  
     <span data-ttu-id="ff250-165">使用者可以選取一個或多個項目中的<xref:System.Windows.Controls.GridView>。</span><span class="sxs-lookup"><span data-stu-id="ff250-165">Users can select one or more items in a <xref:System.Windows.Controls.GridView>.</span></span>  
  
     <span data-ttu-id="ff250-166">如果您想要變更<xref:System.Windows.Style>的選取項目，請參閱[使用觸發程序至樣式 ListView 中選取項目的](../../../../docs/framework/wpf/controls/how-to-use-triggers-to-style-selected-items-in-a-listview.md)。</span><span class="sxs-lookup"><span data-stu-id="ff250-166">If you want to change the <xref:System.Windows.Style> of a selected item, see [Use Triggers to Style Selected Items in a ListView](../../../../docs/framework/wpf/controls/how-to-use-triggers-to-style-selected-items-in-a-listview.md).</span></span>  
  
-   <span data-ttu-id="ff250-167">**捲動以檢視一開始在畫面上看不到的內容。**</span><span class="sxs-lookup"><span data-stu-id="ff250-167">**Scroll to view content that is not initially visible on the screen.**</span></span>  
  
     <span data-ttu-id="ff250-168">如果大小<xref:System.Windows.Controls.GridView>不是大到足以顯示所有項目，使用者可以捲動水平或垂直藉由使用捲軸，這由提供<xref:System.Windows.Controls.ScrollViewer>控制項。</span><span class="sxs-lookup"><span data-stu-id="ff250-168">If the size of the <xref:System.Windows.Controls.GridView> is not large enough to display all the items, users can scroll horizontally or vertically by using scrollbars, which are provided by a <xref:System.Windows.Controls.ScrollViewer> control.</span></span> <span data-ttu-id="ff250-169">A<xref:System.Windows.Controls.Primitives.ScrollBar>如果特定方向中顯示所有內容，都則都會隱藏。</span><span class="sxs-lookup"><span data-stu-id="ff250-169">A <xref:System.Windows.Controls.Primitives.ScrollBar> is hidden if all the content is visible in a specific direction.</span></span> <span data-ttu-id="ff250-170">資料行標頭不會以垂直捲軸捲動，但是會以水平方式捲動。</span><span class="sxs-lookup"><span data-stu-id="ff250-170">Column headers do not scroll with a vertical scroll bar, but do scroll horizontally.</span></span>  
  
-   <span data-ttu-id="ff250-171">**按一下資料行標頭按鈕來與資料行進行互動。**</span><span class="sxs-lookup"><span data-stu-id="ff250-171">**Interact with columns by clicking the column header buttons.**</span></span>  
  
     <span data-ttu-id="ff250-172">如果您已提供排序演算法，則當使用者按一下資料行標頭按鈕時，將可排序該資料行中顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="ff250-172">When users click a column header button, they can sort the data that is displayed in the column if you have provided a sorting algorithm.</span></span>  
  
     <span data-ttu-id="ff250-173">您可以處理<xref:System.Windows.Controls.Primitives.ButtonBase.Click>資料行行首按鈕，以提供排序演算法等功能的事件。</span><span class="sxs-lookup"><span data-stu-id="ff250-173">You can handle the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event for column header buttons in order to provide functionality like a sorting algorithm.</span></span> <span data-ttu-id="ff250-174">若要處理<xref:System.Windows.Controls.Primitives.ButtonBase.Click>單一的資料行標頭，事件上設定的事件處理常式<xref:System.Windows.Controls.GridViewColumnHeader>。</span><span class="sxs-lookup"><span data-stu-id="ff250-174">To handle the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event for a single column header, set an event handler on the <xref:System.Windows.Controls.GridViewColumnHeader>.</span></span> <span data-ttu-id="ff250-175">若要設定事件處理常式處理<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件的所有資料行標頭，在設定處理常式<xref:System.Windows.Controls.ListView>控制項。</span><span class="sxs-lookup"><span data-stu-id="ff250-175">To set an event handler that handles the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event for all column headers, set the handler on the <xref:System.Windows.Controls.ListView> control.</span></span>  
  
<a name="Obtaining_Other_Custom_Views"></a>   
## <a name="obtaining-other-custom-views"></a><span data-ttu-id="ff250-176">取得其他自訂檢視</span><span class="sxs-lookup"><span data-stu-id="ff250-176">Obtaining Other Custom Views</span></span>  
 <span data-ttu-id="ff250-177"><xref:System.Windows.Controls.GridView>類別，衍生自<xref:System.Windows.Controls.ViewBase>抽象類別，只是其中一個可能的檢視模式的<xref:System.Windows.Controls.ListView>類別。</span><span class="sxs-lookup"><span data-stu-id="ff250-177">The <xref:System.Windows.Controls.GridView> class, which is derived from the <xref:System.Windows.Controls.ViewBase> abstract class, is just one of the possible view modes for the <xref:System.Windows.Controls.ListView> class.</span></span> <span data-ttu-id="ff250-178">您可以建立其他自訂檢視<xref:System.Windows.Controls.ListView>由衍生自<xref:System.Windows.Controls.ViewBase>類別。</span><span class="sxs-lookup"><span data-stu-id="ff250-178">You can create other custom views for <xref:System.Windows.Controls.ListView> by deriving from the <xref:System.Windows.Controls.ViewBase> class.</span></span> <span data-ttu-id="ff250-179">如需自訂檢視模式的範例，請參閱[建立 ListView 的自訂檢視模式](../../../../docs/framework/wpf/controls/how-to-create-a-custom-view-mode-for-a-listview.md)。</span><span class="sxs-lookup"><span data-stu-id="ff250-179">For an example of a custom view mode, see [Create a Custom View Mode for a ListView](../../../../docs/framework/wpf/controls/how-to-create-a-custom-view-mode-for-a-listview.md).</span></span>  
  
<a name="GridViewSupportingClasses"></a>   
## <a name="gridview-supporting-classes"></a><span data-ttu-id="ff250-180">支援 GridView 的類別</span><span class="sxs-lookup"><span data-stu-id="ff250-180">GridView Supporting Classes</span></span>  
 <span data-ttu-id="ff250-181">下列類別會支援<xref:System.Windows.Controls.GridView>檢視模式。</span><span class="sxs-lookup"><span data-stu-id="ff250-181">The following classes support the <xref:System.Windows.Controls.GridView> view mode.</span></span>  
  
-   <xref:System.Windows.Controls.GridViewColumn>  
  
-   <xref:System.Windows.Controls.GridViewColumnHeader>  
  
-   <xref:System.Windows.Controls.GridViewRowPresenter>  
  
-   <xref:System.Windows.Controls.GridViewHeaderRowPresenter>  
  
-   <xref:System.Windows.Controls.GridViewColumnCollection>  
  
-   <xref:System.Windows.Controls.GridViewColumnHeaderRole>  
  
## <a name="see-also"></a><span data-ttu-id="ff250-182">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff250-182">See Also</span></span>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.ListViewItem>  
 <xref:System.Windows.Controls.GridViewColumn>  
 <xref:System.Windows.Controls.GridViewColumnHeader>  
 <xref:System.Windows.Controls.GridViewRowPresenter>  
 <xref:System.Windows.Controls.GridViewHeaderRowPresenter>  
 <xref:System.Windows.Controls.ViewBase>  
 [<span data-ttu-id="ff250-183">ListView 概觀</span><span class="sxs-lookup"><span data-stu-id="ff250-183">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [<span data-ttu-id="ff250-184">在按一下標頭時排序 GridView 資料行</span><span class="sxs-lookup"><span data-stu-id="ff250-184">Sort a GridView Column When a Header Is Clicked</span></span>](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)  
 [<span data-ttu-id="ff250-185">操作說明主題</span><span class="sxs-lookup"><span data-stu-id="ff250-185">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)

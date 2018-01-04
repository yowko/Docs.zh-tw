---
title: "如何：格式化 Windows Form DataGrid 控制項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- columns [Windows Forms], DataGrid control
- colors [Windows Forms], applying to DataGrid controls
- DataGrid control [Windows Forms], formatting
- columns [Windows Forms], formatting in DataGrid control
- DataGrid control [Windows Forms], default styles
- tables [Windows Forms], formatting in DataGrid control
- formatting [Windows Forms]
ms.assetid: a50fcc3b-8abf-47ec-9029-7f268af4ddb1
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6f03f65c878e72a8ec4b7f8bb447a1d6cf820690
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-format-the-windows-forms-datagrid-control"></a><span data-ttu-id="b88f4-102">如何：格式化 Windows Form DataGrid 控制項</span><span class="sxs-lookup"><span data-stu-id="b88f4-102">How to: Format the Windows Forms DataGrid Control</span></span>
> [!NOTE]
>  <span data-ttu-id="b88f4-103"><xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="b88f4-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="b88f4-104">如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="b88f4-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="b88f4-105">將不同的色彩套用至各個部分<xref:System.Windows.Forms.DataGrid>控制項可以協助讓您更輕鬆地閱讀及解譯中的資訊。</span><span class="sxs-lookup"><span data-stu-id="b88f4-105">Applying different colors to various parts of a <xref:System.Windows.Forms.DataGrid> control can help to make the information in it easier to read and interpret.</span></span> <span data-ttu-id="b88f4-106">色彩可以套用至資料列和資料行中。</span><span class="sxs-lookup"><span data-stu-id="b88f4-106">Color can be applied to rows and columns.</span></span> <span data-ttu-id="b88f4-107">資料列和資料行也可以隱藏或顯示自行斟酌。</span><span class="sxs-lookup"><span data-stu-id="b88f4-107">Rows and columns can also be hidden or shown at your discretion.</span></span>  
  
 <span data-ttu-id="b88f4-108">有三個基本層面等的格式化<xref:System.Windows.Forms.DataGrid>控制項。</span><span class="sxs-lookup"><span data-stu-id="b88f4-108">There are three basic aspects of formatting the <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="b88f4-109">您可以設定屬性，以建立資料會顯示為預設樣式。</span><span class="sxs-lookup"><span data-stu-id="b88f4-109">You can set properties to establish a default style in which data is displayed.</span></span> <span data-ttu-id="b88f4-110">從該基底，您可以自訂某些資料表顯示在執行階段的方式。</span><span class="sxs-lookup"><span data-stu-id="b88f4-110">From that base, you can then customize the way certain tables are displayed at run time.</span></span> <span data-ttu-id="b88f4-111">最後，您可以修改哪些資料行中的資料格，以及色彩顯示，並顯示的其他格式設定。</span><span class="sxs-lookup"><span data-stu-id="b88f4-111">Finally, you can modify which columns are displayed in the data grid as well as the colors and other formatting that is shown.</span></span>  
  
 <span data-ttu-id="b88f4-112">格式化資料格在初始步驟，您可以設定的屬性<xref:System.Windows.Forms.DataGrid>本身。</span><span class="sxs-lookup"><span data-stu-id="b88f4-112">As an initial step in formatting a data grid, you can set the properties of the <xref:System.Windows.Forms.DataGrid> itself.</span></span> <span data-ttu-id="b88f4-113">這些色彩和格式的選擇會形成從中您可以再進行變更，取決於資料的資料表和顯示的資料行的基底。</span><span class="sxs-lookup"><span data-stu-id="b88f4-113">These color and format choices form a base from which you can then make changes depending on the data tables and columns displayed.</span></span>  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a><span data-ttu-id="b88f4-114">若要建立之預設樣式的 DataGrid 控制項</span><span class="sxs-lookup"><span data-stu-id="b88f4-114">To establish a default style for the DataGrid control</span></span>  
  
1.  <span data-ttu-id="b88f4-115">視需要設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="b88f4-115">Set the following properties as appropriate:</span></span>  
  
    |<span data-ttu-id="b88f4-116">屬性</span><span class="sxs-lookup"><span data-stu-id="b88f4-116">Property</span></span>|<span data-ttu-id="b88f4-117">描述</span><span class="sxs-lookup"><span data-stu-id="b88f4-117">Description</span></span>|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|<span data-ttu-id="b88f4-118"><xref:System.Windows.Forms.DataGrid.BackColor%2A>屬性定義的方格其偶數資料列的色彩。</span><span class="sxs-lookup"><span data-stu-id="b88f4-118">The <xref:System.Windows.Forms.DataGrid.BackColor%2A> property defines the color of the even-numbered rows of the grid.</span></span> <span data-ttu-id="b88f4-119">當您將<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>為不同的色彩屬性，每個資料列設定為這個新的色彩 （1、 3、 5 和等等的資料列）。</span><span class="sxs-lookup"><span data-stu-id="b88f4-119">When you set the <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> property to a different color, every other row is set to this new color (rows 1, 3, 5, and so on).</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|<span data-ttu-id="b88f4-120">方格其偶數資料列的背景色彩 （0、 2、 4、 6 和等等的資料列）。</span><span class="sxs-lookup"><span data-stu-id="b88f4-120">The background color of the even-numbered rows of the grid (rows 0, 2, 4, 6, and so on).</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|<span data-ttu-id="b88f4-121">而<xref:System.Windows.Forms.DataGrid.BackColor%2A>和<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>屬性決定在方格中，資料列的色彩<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>屬性決定 nonrow 區域中，才看得見，由上至下，捲動方格時，或者如果只有少數資料列中所包含的色彩在方格中。</span><span class="sxs-lookup"><span data-stu-id="b88f4-121">Whereas the <xref:System.Windows.Forms.DataGrid.BackColor%2A> and <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> properties determines the color of rows in the grid, the <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> property determines the color of the nonrow area, which is only visible when the grid is scrolled to the bottom, or if only a few rows are contained in the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|<span data-ttu-id="b88f4-122">方格的框線樣式，其中<xref:System.Windows.Forms.BorderStyle>列舉值。</span><span class="sxs-lookup"><span data-stu-id="b88f4-122">The grid's border style, one of the <xref:System.Windows.Forms.BorderStyle> enumeration values.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|<span data-ttu-id="b88f4-123">就會立即顯示方格上方的方格視窗標題的背景色彩。</span><span class="sxs-lookup"><span data-stu-id="b88f4-123">The background color of the grid's window caption which appears immediately above the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|<span data-ttu-id="b88f4-124">頂端的方格標題的字型。</span><span class="sxs-lookup"><span data-stu-id="b88f4-124">The font of the caption at the top of the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|<span data-ttu-id="b88f4-125">方格的視窗標題的背景色彩。</span><span class="sxs-lookup"><span data-stu-id="b88f4-125">The background color of the grid's window caption.</span></span>|  
    |<xref:System.Windows.Forms.Control.Font%2A>|<span data-ttu-id="b88f4-126">用來在方格中顯示文字的字型。</span><span class="sxs-lookup"><span data-stu-id="b88f4-126">The font used to display the text in the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|<span data-ttu-id="b88f4-127">資料格的資料列中的資料顯示的字型色彩。</span><span class="sxs-lookup"><span data-stu-id="b88f4-127">The color of the font displayed by the data in the rows of the data grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|<span data-ttu-id="b88f4-128">資料格的格線色彩。</span><span class="sxs-lookup"><span data-stu-id="b88f4-128">The color of the grid lines of the data grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|<span data-ttu-id="b88f4-129">分隔資料格方格，其中線條的樣式<xref:System.Windows.Forms.DataGridLineStyle>列舉值。</span><span class="sxs-lookup"><span data-stu-id="b88f4-129">The style of the lines separating the cells of the grid, one of the <xref:System.Windows.Forms.DataGridLineStyle> enumeration values.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|<span data-ttu-id="b88f4-130">資料列和資料行的標頭的背景色彩。</span><span class="sxs-lookup"><span data-stu-id="b88f4-130">The background color of row and column headers.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|<span data-ttu-id="b88f4-131">資料行標頭所使用的字型。</span><span class="sxs-lookup"><span data-stu-id="b88f4-131">The font used for the column headers.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|<span data-ttu-id="b88f4-132">方格的資料行標頭，包括資料行標頭文字和加號/減號圖像 （glyph） （若要顯示多個相關的資料表時，請展開資料列） 的前景色彩。</span><span class="sxs-lookup"><span data-stu-id="b88f4-132">The foreground color of the grid's column headers, including the column header text and the plus/minus glyphs (to expand rows when multiple related tables are displayed).</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|<span data-ttu-id="b88f4-133">資料格，其中包含子資料表、 關聯性名稱和等等的連結中的所有連結的文字色彩。</span><span class="sxs-lookup"><span data-stu-id="b88f4-133">The color of text of all the links in the data grid, including links to child tables, the relation name, and so on.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|<span data-ttu-id="b88f4-134">在子資料表中，這會是父資料列的背景色彩。</span><span class="sxs-lookup"><span data-stu-id="b88f4-134">In a child table, this is the background color of the parent rows.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|<span data-ttu-id="b88f4-135">在子資料表中，這會是父資料列的前景色彩。</span><span class="sxs-lookup"><span data-stu-id="b88f4-135">In a child table, this is the foreground color of the parent rows.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|<span data-ttu-id="b88f4-136">判斷資料表和資料行名稱是否會顯示在父資料列，藉由<xref:System.Windows.Forms.DataGridParentRowsLabelStyle>列舉型別。</span><span class="sxs-lookup"><span data-stu-id="b88f4-136">Determines whether the table and column names are displayed in the parent row, by means of the <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> enumeration.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|<span data-ttu-id="b88f4-137">方格中資料行的預設寬度 (單位為像素)。</span><span class="sxs-lookup"><span data-stu-id="b88f4-137">The default width (in pixels) of columns in the grid.</span></span> <span data-ttu-id="b88f4-138">重設之前設定此屬性<xref:System.Windows.Forms.DataGrid.DataSource%2A>和<xref:System.Windows.Forms.DataGrid.DataMember%2A>屬性 (可能是分開，或是透過<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>方法)，或屬性會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="b88f4-138">Set this property before resetting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties (either separately, or through the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method), or the property will have no effect.</span></span><br /><br /> <span data-ttu-id="b88f4-139">屬性無法設為小於 0。</span><span class="sxs-lookup"><span data-stu-id="b88f4-139">The property cannot be set to a value less than 0.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|<span data-ttu-id="b88f4-140">在方格中的資料列的資料列高度 （以像素為單位）。</span><span class="sxs-lookup"><span data-stu-id="b88f4-140">The row height (in pixels) of rows in the grid.</span></span> <span data-ttu-id="b88f4-141">重設之前設定此屬性<xref:System.Windows.Forms.DataGrid.DataSource%2A>和<xref:System.Windows.Forms.DataGrid.DataMember%2A>屬性 (可能是分開，或是透過<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>方法)，或屬性會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="b88f4-141">Set this property before resetting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties (either separately, or through the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method), or the property will have no effect.</span></span><br /><br /> <span data-ttu-id="b88f4-142">屬性無法設為小於 0。</span><span class="sxs-lookup"><span data-stu-id="b88f4-142">The property cannot be set to a value less than 0.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|<span data-ttu-id="b88f4-143">方格的資料列行首的寬度。</span><span class="sxs-lookup"><span data-stu-id="b88f4-143">The width of the row headers of the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|<span data-ttu-id="b88f4-144">選取的資料列或資料格時，這是背景色彩。</span><span class="sxs-lookup"><span data-stu-id="b88f4-144">When a row or cell is selected, this is the background color.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|<span data-ttu-id="b88f4-145">選取的資料列或資料格時，這是前景色彩。</span><span class="sxs-lookup"><span data-stu-id="b88f4-145">When a row or cell is selected, this is the foreground color.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="b88f4-146">請記住，當自訂控制項，便可將控制項設為無法存取，因為不佳的色彩選擇 （例如，紅色和綠色） 的色彩。</span><span class="sxs-lookup"><span data-stu-id="b88f4-146">Keep in mind, when customizing the colors of controls, that it is possible to make the control inaccessible, due to poor color choice (for example, red and green).</span></span> <span data-ttu-id="b88f4-147">使用上可用的色彩**系統色彩**調色盤，若要避免這個問題。</span><span class="sxs-lookup"><span data-stu-id="b88f4-147">Use the colors available on the **System Colors** palette to avoid this issue.</span></span>  
  
     <span data-ttu-id="b88f4-148">下列程序假設您的表單具有<xref:System.Windows.Forms.DataGrid>控制項繫結至資料表。</span><span class="sxs-lookup"><span data-stu-id="b88f4-148">The following procedures assume your form has a <xref:System.Windows.Forms.DataGrid> control bound to a data table.</span></span> <span data-ttu-id="b88f4-149">如需詳細資訊，請參閱[繫結至資料來源的 Windows Form DataGrid 控制項](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)。</span><span class="sxs-lookup"><span data-stu-id="b88f4-149">For more information, see [Binding the Windows Forms DataGrid Control to a Data Source](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span></span>  
  
### <a name="to-set-the-table-and-column-style-of-a-data-table-programmatically"></a><span data-ttu-id="b88f4-150">以程式設計方式設定資料表的資料的資料表和資料行樣式</span><span class="sxs-lookup"><span data-stu-id="b88f4-150">To set the table and column style of a data table programmatically</span></span>  
  
1.  <span data-ttu-id="b88f4-151">建立新的資料表樣式，並設定其屬性。</span><span class="sxs-lookup"><span data-stu-id="b88f4-151">Create a new table style and set its properties.</span></span>  
  
2.  <span data-ttu-id="b88f4-152">建立資料行樣式，並設定其屬性。</span><span class="sxs-lookup"><span data-stu-id="b88f4-152">Create a column style and set its properties.</span></span>  
  
3.  <span data-ttu-id="b88f4-153">加入資料表樣式的資料行樣式集合中的資料行樣式。</span><span class="sxs-lookup"><span data-stu-id="b88f4-153">Add the column style to the table style's column styles collection.</span></span>  
  
4.  <span data-ttu-id="b88f4-154">將資料表樣式加入至資料格資料表樣式集合中。</span><span class="sxs-lookup"><span data-stu-id="b88f4-154">Add the table style to the data grid's table styles collection.</span></span>  
  
5.  <span data-ttu-id="b88f4-155">在下列範例中，建立新的執行個體<xref:System.Windows.Forms.DataGridTableStyle>並設定其<xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="b88f4-155">In the example below, create an instance of a new <xref:System.Windows.Forms.DataGridTableStyle> and set its <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> property.</span></span>  
  
6.  <span data-ttu-id="b88f4-156">建立的新執行個體**GridColumnStyle**並設定其**MappingName** （和其他配置和顯示屬性）。</span><span class="sxs-lookup"><span data-stu-id="b88f4-156">Create a new instance of a **GridColumnStyle** and set its **MappingName** (and some other layout and display properties).</span></span>  
  
7.  <span data-ttu-id="b88f4-157">針對您想要建立每個資料行樣式重複步驟 2 到 6。</span><span class="sxs-lookup"><span data-stu-id="b88f4-157">Repeat steps 2 through 6 for each column style you want to create.</span></span>  
  
     <span data-ttu-id="b88f4-158">下列範例說明如何<xref:System.Windows.Forms.DataGridTextBoxColumn>建立，因為資料行中顯示的名稱。</span><span class="sxs-lookup"><span data-stu-id="b88f4-158">The following example illustrates how a <xref:System.Windows.Forms.DataGridTextBoxColumn> is created, because a name is to be displayed in the column.</span></span> <span data-ttu-id="b88f4-159">此外，您將資料行樣式<xref:System.Windows.Forms.GridColumnStylesCollection>的資料表樣式，並加入資料表樣式<xref:System.Windows.Forms.GridTableStylesCollection>資料格。</span><span class="sxs-lookup"><span data-stu-id="b88f4-159">Additionally, you add the column style to the <xref:System.Windows.Forms.GridColumnStylesCollection> of the table style, and you add the table style to the <xref:System.Windows.Forms.GridTableStylesCollection> of the data grid.</span></span>  
  
    ```vb  
    Private Sub CreateAuthorFirstNameColumn()  
       ' Add a GridTableStyle and set the MappingName   
       ' to the name of the DataTable.  
       Dim TSAuthors As New DataGridTableStyle()  
       TSAuthors.MappingName = "Authors"  
  
       ' Add a GridColumnStyle and set the MappingName   
       ' to the name of a DataColumn in the DataTable.   
       ' Set the HeaderText and Width properties.   
       Dim TCFirstName As New DataGridTextBoxColumn()  
       TCFirstName.MappingName = "AV_FName"  
       TCFirstName.HeaderText = "First Name"  
       TCFirstName.Width = 75  
       TSAuthors.GridColumnStyles.Add(TCFirstName)  
  
       ' Add the DataGridTableStyle instance to   
       ' the GridTableStylesCollection.   
       myDataGrid.TableStyles.Add(TSAuthors)  
    End Sub  
    ```  
  
    ```csharp  
    private void addCustomDataTableStyle()  
    {  
       // Add a GridTableStyle and set the MappingName   
       // to the name of the DataTable.  
       DataGridTableStyle TSAuthors = new DataGridTableStyle();  
       TSAuthors.MappingName = "Authors";  
  
       // Add a GridColumnStyle and set the MappingName   
       // to the name of a DataColumn in the DataTable.   
       // Set the HeaderText and Width properties.   
       DataGridColumnStyle TCFirstName = new DataGridTextBoxColumn();  
       TCFirstName.MappingName = " AV_FName";  
       TCFirstName.HeaderText = "First Name";  
       TCFirstName.Width = 75;  
       TSAuthors.GridColumnStyles.Add(TCFirstName);  
  
       // Add the DataGridTableStyle instance to   
       // the GridTableStylesCollection.   
       dataGrid1.TableStyles.Add(TSAuthors);  
    }  
    ```  
  
    ```cpp  
    private:  
       void addCustomDataTableStyle()  
       {  
          // Add a GridTableStyle and set the MappingName   
          // to the name of the DataTable.  
          DataGridTableStyle^ TSAuthors = new DataGridTableStyle();  
          TSAuthors->MappingName = "Authors";  
  
          // Add a GridColumnStyle and set the MappingName   
          // to the name of a DataColumn in the DataTable.   
          // Set the HeaderText and Width properties.   
          DataGridColumnStyle^ TCFirstName = gcnew DataGridTextBoxColumn();  
          TCFirstName->MappingName = "AV_FName";  
          TCFirstName->HeaderText = "First Name";  
          TCFirstName->Width = 75;  
          TSAuthors->GridColumnStyles->Add(TCFirstName);  
  
          // Add the DataGridTableStyle instance to   
          // the GridTableStylesCollection.   
          dataGrid1->TableStyles->Add(TSAuthors);  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b88f4-160">請參閱</span><span class="sxs-lookup"><span data-stu-id="b88f4-160">See Also</span></span>  
 <xref:System.Windows.Forms.GridTableStylesCollection>  
 <xref:System.Windows.Forms.GridColumnStylesCollection>  
 <xref:System.Windows.Forms.DataGrid>  
 [<span data-ttu-id="b88f4-161">操作說明：刪除或隱藏 Windows Forms DataGrid 控制項中的資料行</span><span class="sxs-lookup"><span data-stu-id="b88f4-161">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)  
 [<span data-ttu-id="b88f4-162">DataGrid 控制項</span><span class="sxs-lookup"><span data-stu-id="b88f4-162">DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)

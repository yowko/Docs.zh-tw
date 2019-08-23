---
title: 作法：格式化 Windows Forms DataGrid 控制項
ms.date: 03/30/2017
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
ms.openlocfilehash: 99acef0a7b29228ddf0406352ff5a88b77294b00
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966663"
---
# <a name="how-to-format-the-windows-forms-datagrid-control"></a><span data-ttu-id="f3d95-102">作法：格式化 Windows Forms DataGrid 控制項</span><span class="sxs-lookup"><span data-stu-id="f3d95-102">How to: Format the Windows Forms DataGrid Control</span></span>
> [!NOTE]
> <span data-ttu-id="f3d95-103"><xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="f3d95-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="f3d95-104">如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="f3d95-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="f3d95-105">將不同的色彩套用至<xref:System.Windows.Forms.DataGrid>控制項的各個部分, 可協助您更輕鬆地讀取和解讀中的資訊。</span><span class="sxs-lookup"><span data-stu-id="f3d95-105">Applying different colors to various parts of a <xref:System.Windows.Forms.DataGrid> control can help to make the information in it easier to read and interpret.</span></span> <span data-ttu-id="f3d95-106">色彩可以套用至資料列和資料行。</span><span class="sxs-lookup"><span data-stu-id="f3d95-106">Color can be applied to rows and columns.</span></span> <span data-ttu-id="f3d95-107">您也可以自行隱藏或顯示資料列和資料行。</span><span class="sxs-lookup"><span data-stu-id="f3d95-107">Rows and columns can also be hidden or shown at your discretion.</span></span>  
  
 <span data-ttu-id="f3d95-108"><xref:System.Windows.Forms.DataGrid>控制項的格式有三個基本層面。</span><span class="sxs-lookup"><span data-stu-id="f3d95-108">There are three basic aspects of formatting the <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="f3d95-109">您可以設定屬性, 以建立顯示資料的預設樣式。</span><span class="sxs-lookup"><span data-stu-id="f3d95-109">You can set properties to establish a default style in which data is displayed.</span></span> <span data-ttu-id="f3d95-110">接著, 您可以從該基底中, 自訂在執行時間顯示特定資料表的方式。</span><span class="sxs-lookup"><span data-stu-id="f3d95-110">From that base, you can then customize the way certain tables are displayed at run time.</span></span> <span data-ttu-id="f3d95-111">最後, 您可以修改資料方格中所顯示的資料行, 以及所顯示的色彩和其他格式。</span><span class="sxs-lookup"><span data-stu-id="f3d95-111">Finally, you can modify which columns are displayed in the data grid as well as the colors and other formatting that is shown.</span></span>  
  
 <span data-ttu-id="f3d95-112">在格式化資料方格的初始步驟中, 您可以設定<xref:System.Windows.Forms.DataGrid>本身的屬性。</span><span class="sxs-lookup"><span data-stu-id="f3d95-112">As an initial step in formatting a data grid, you can set the properties of the <xref:System.Windows.Forms.DataGrid> itself.</span></span> <span data-ttu-id="f3d95-113">這些色彩和格式選擇會形成一個基底, 您可以根據顯示的資料表和資料行進行變更。</span><span class="sxs-lookup"><span data-stu-id="f3d95-113">These color and format choices form a base from which you can then make changes depending on the data tables and columns displayed.</span></span>  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a><span data-ttu-id="f3d95-114">若要建立 DataGrid 控制項的預設樣式</span><span class="sxs-lookup"><span data-stu-id="f3d95-114">To establish a default style for the DataGrid control</span></span>  
  
1. <span data-ttu-id="f3d95-115">適當地設定下列屬性:</span><span class="sxs-lookup"><span data-stu-id="f3d95-115">Set the following properties as appropriate:</span></span>  
  
    |<span data-ttu-id="f3d95-116">屬性</span><span class="sxs-lookup"><span data-stu-id="f3d95-116">Property</span></span>|<span data-ttu-id="f3d95-117">描述</span><span class="sxs-lookup"><span data-stu-id="f3d95-117">Description</span></span>|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|<span data-ttu-id="f3d95-118"><xref:System.Windows.Forms.DataGrid.BackColor%2A>屬性會定義方格中偶數資料列的色彩。</span><span class="sxs-lookup"><span data-stu-id="f3d95-118">The <xref:System.Windows.Forms.DataGrid.BackColor%2A> property defines the color of the even-numbered rows of the grid.</span></span> <span data-ttu-id="f3d95-119">當您將<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>屬性設定為不同的色彩時, 每個其他資料列都會設定為這個新的色彩 (資料列1、3、5等等)。</span><span class="sxs-lookup"><span data-stu-id="f3d95-119">When you set the <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> property to a different color, every other row is set to this new color (rows 1, 3, 5, and so on).</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|<span data-ttu-id="f3d95-120">方格中偶數資料列的背景色彩 (資料列0、2、4、6等等)。</span><span class="sxs-lookup"><span data-stu-id="f3d95-120">The background color of the even-numbered rows of the grid (rows 0, 2, 4, 6, and so on).</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|<span data-ttu-id="f3d95-121">和屬性會決定方格<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>中的資料列色彩, 而屬性會決定 nonrow 區域的色彩, 只有在格線滾動到底部, 或是只有少數資料列包含在其中時, 才會顯示此顏色。 <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> <xref:System.Windows.Forms.DataGrid.BackColor%2A>方格。</span><span class="sxs-lookup"><span data-stu-id="f3d95-121">Whereas the <xref:System.Windows.Forms.DataGrid.BackColor%2A> and <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> properties determines the color of rows in the grid, the <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> property determines the color of the nonrow area, which is only visible when the grid is scrolled to the bottom, or if only a few rows are contained in the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|<span data-ttu-id="f3d95-122">方格的框線樣式, 其中一個<xref:System.Windows.Forms.BorderStyle>列舉值。</span><span class="sxs-lookup"><span data-stu-id="f3d95-122">The grid's border style, one of the <xref:System.Windows.Forms.BorderStyle> enumeration values.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|<span data-ttu-id="f3d95-123">方格視窗標題的背景色彩, 出現在方格的正上方。</span><span class="sxs-lookup"><span data-stu-id="f3d95-123">The background color of the grid's window caption which appears immediately above the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|<span data-ttu-id="f3d95-124">方格頂端標題的字型。</span><span class="sxs-lookup"><span data-stu-id="f3d95-124">The font of the caption at the top of the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|<span data-ttu-id="f3d95-125">方格視窗標題的背景色彩。</span><span class="sxs-lookup"><span data-stu-id="f3d95-125">The background color of the grid's window caption.</span></span>|  
    |<xref:System.Windows.Forms.Control.Font%2A>|<span data-ttu-id="f3d95-126">用來在方格中顯示文字的字型。</span><span class="sxs-lookup"><span data-stu-id="f3d95-126">The font used to display the text in the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|<span data-ttu-id="f3d95-127">資料方格的資料列中所顯示的字型色彩。</span><span class="sxs-lookup"><span data-stu-id="f3d95-127">The color of the font displayed by the data in the rows of the data grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|<span data-ttu-id="f3d95-128">資料格的格線色彩。</span><span class="sxs-lookup"><span data-stu-id="f3d95-128">The color of the grid lines of the data grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|<span data-ttu-id="f3d95-129">分隔方格儲存格的線條樣式, 這是其中一個<xref:System.Windows.Forms.DataGridLineStyle>列舉值。</span><span class="sxs-lookup"><span data-stu-id="f3d95-129">The style of the lines separating the cells of the grid, one of the <xref:System.Windows.Forms.DataGridLineStyle> enumeration values.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|<span data-ttu-id="f3d95-130">資料列和資料行標頭的背景色彩。</span><span class="sxs-lookup"><span data-stu-id="f3d95-130">The background color of row and column headers.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|<span data-ttu-id="f3d95-131">資料行標頭所使用的字型。</span><span class="sxs-lookup"><span data-stu-id="f3d95-131">The font used for the column headers.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|<span data-ttu-id="f3d95-132">方格之資料行標頭的前景色彩, 包括資料行標題文字和加號/減號字元 (在顯示多個相關資料表時, 要展開資料列)。</span><span class="sxs-lookup"><span data-stu-id="f3d95-132">The foreground color of the grid's column headers, including the column header text and the plus/minus glyphs (to expand rows when multiple related tables are displayed).</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|<span data-ttu-id="f3d95-133">資料方格中所有連結的文字色彩, 包括子資料工作表的連結、關聯名稱等等。</span><span class="sxs-lookup"><span data-stu-id="f3d95-133">The color of text of all the links in the data grid, including links to child tables, the relation name, and so on.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|<span data-ttu-id="f3d95-134">在子資料工作表中, 這是父資料列的背景色彩。</span><span class="sxs-lookup"><span data-stu-id="f3d95-134">In a child table, this is the background color of the parent rows.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|<span data-ttu-id="f3d95-135">在子資料工作表中, 這是父資料列的前景色彩。</span><span class="sxs-lookup"><span data-stu-id="f3d95-135">In a child table, this is the foreground color of the parent rows.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|<span data-ttu-id="f3d95-136">藉由<xref:System.Windows.Forms.DataGridParentRowsLabelStyle>列舉, 判斷資料表和資料行名稱是否顯示在父資料列中。</span><span class="sxs-lookup"><span data-stu-id="f3d95-136">Determines whether the table and column names are displayed in the parent row, by means of the <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> enumeration.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|<span data-ttu-id="f3d95-137">方格中資料行的預設寬度 (單位為像素)。</span><span class="sxs-lookup"><span data-stu-id="f3d95-137">The default width (in pixels) of columns in the grid.</span></span> <span data-ttu-id="f3d95-138">請先設定此屬性, <xref:System.Windows.Forms.DataGrid.DataSource%2A>再<xref:System.Windows.Forms.DataGrid.DataMember%2A>重設和屬性 (個別或透過<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>方法), 否則屬性不會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="f3d95-138">Set this property before resetting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties (either separately, or through the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method), or the property will have no effect.</span></span><br /><br /> <span data-ttu-id="f3d95-139">屬性不能設定為小於0的值。</span><span class="sxs-lookup"><span data-stu-id="f3d95-139">The property cannot be set to a value less than 0.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|<span data-ttu-id="f3d95-140">方格中資料列的資料列高度 (以圖元為單位)。</span><span class="sxs-lookup"><span data-stu-id="f3d95-140">The row height (in pixels) of rows in the grid.</span></span> <span data-ttu-id="f3d95-141">請先設定此屬性, <xref:System.Windows.Forms.DataGrid.DataSource%2A>再<xref:System.Windows.Forms.DataGrid.DataMember%2A>重設和屬性 (個別或透過<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>方法), 否則屬性不會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="f3d95-141">Set this property before resetting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties (either separately, or through the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method), or the property will have no effect.</span></span><br /><br /> <span data-ttu-id="f3d95-142">屬性不能設定為小於0的值。</span><span class="sxs-lookup"><span data-stu-id="f3d95-142">The property cannot be set to a value less than 0.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|<span data-ttu-id="f3d95-143">方格的資料列標頭寬度。</span><span class="sxs-lookup"><span data-stu-id="f3d95-143">The width of the row headers of the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|<span data-ttu-id="f3d95-144">選取資料列或儲存格時, 這就是背景色彩。</span><span class="sxs-lookup"><span data-stu-id="f3d95-144">When a row or cell is selected, this is the background color.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|<span data-ttu-id="f3d95-145">選取資料列或儲存格時, 這就是前景色彩。</span><span class="sxs-lookup"><span data-stu-id="f3d95-145">When a row or cell is selected, this is the foreground color.</span></span>|  
  
    > [!NOTE]
    > <span data-ttu-id="f3d95-146">請記住, 自訂控制項的色彩時, 可能會因為色彩選擇不佳 (例如, 紅色和綠色) 而使控制項無法存取。</span><span class="sxs-lookup"><span data-stu-id="f3d95-146">Keep in mind, when customizing the colors of controls, that it is possible to make the control inaccessible, due to poor color choice (for example, red and green).</span></span> <span data-ttu-id="f3d95-147">使用 [**系統色彩**] 調色板上可用的色彩來避免此問題。</span><span class="sxs-lookup"><span data-stu-id="f3d95-147">Use the colors available on the **System Colors** palette to avoid this issue.</span></span>  
  
     <span data-ttu-id="f3d95-148">下列程式假設您的<xref:System.Windows.Forms.DataGrid>表單有系結至資料表的控制項。</span><span class="sxs-lookup"><span data-stu-id="f3d95-148">The following procedures assume your form has a <xref:System.Windows.Forms.DataGrid> control bound to a data table.</span></span> <span data-ttu-id="f3d95-149">如需詳細資訊, 請參閱將[Windows Forms DataGrid 控制項系結至資料來源](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)。</span><span class="sxs-lookup"><span data-stu-id="f3d95-149">For more information, see [Binding the Windows Forms DataGrid Control to a Data Source](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span></span>  
  
### <a name="to-set-the-table-and-column-style-of-a-data-table-programmatically"></a><span data-ttu-id="f3d95-150">以程式設計方式設定資料表的資料表和資料行樣式</span><span class="sxs-lookup"><span data-stu-id="f3d95-150">To set the table and column style of a data table programmatically</span></span>  
  
1. <span data-ttu-id="f3d95-151">建立新的資料表樣式, 並設定其屬性。</span><span class="sxs-lookup"><span data-stu-id="f3d95-151">Create a new table style and set its properties.</span></span>  
  
2. <span data-ttu-id="f3d95-152">建立資料行樣式, 並設定其屬性。</span><span class="sxs-lookup"><span data-stu-id="f3d95-152">Create a column style and set its properties.</span></span>  
  
3. <span data-ttu-id="f3d95-153">將資料行樣式加入至資料表樣式的資料行樣式集合。</span><span class="sxs-lookup"><span data-stu-id="f3d95-153">Add the column style to the table style's column styles collection.</span></span>  
  
4. <span data-ttu-id="f3d95-154">將資料表樣式加入至資料方格的資料表樣式集合。</span><span class="sxs-lookup"><span data-stu-id="f3d95-154">Add the table style to the data grid's table styles collection.</span></span>  
  
5. <span data-ttu-id="f3d95-155">在下列範例中, 建立新<xref:System.Windows.Forms.DataGridTableStyle>的實例, 並設定其<xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="f3d95-155">In the example below, create an instance of a new <xref:System.Windows.Forms.DataGridTableStyle> and set its <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> property.</span></span>  
  
6. <span data-ttu-id="f3d95-156">建立**GridColumnStyle**的新實例, 並設定其**MappingName** (以及一些其他的版面配置和顯示內容)。</span><span class="sxs-lookup"><span data-stu-id="f3d95-156">Create a new instance of a **GridColumnStyle** and set its **MappingName** (and some other layout and display properties).</span></span>  
  
7. <span data-ttu-id="f3d95-157">針對您想要建立的每個資料行樣式, 重複步驟2到6。</span><span class="sxs-lookup"><span data-stu-id="f3d95-157">Repeat steps 2 through 6 for each column style you want to create.</span></span>  
  
     <span data-ttu-id="f3d95-158">下列範例說明如何<xref:System.Windows.Forms.DataGridTextBoxColumn>建立, 因為名稱會顯示在資料行中。</span><span class="sxs-lookup"><span data-stu-id="f3d95-158">The following example illustrates how a <xref:System.Windows.Forms.DataGridTextBoxColumn> is created, because a name is to be displayed in the column.</span></span> <span data-ttu-id="f3d95-159">此外, 您可以將資料行樣式加入<xref:System.Windows.Forms.GridColumnStylesCollection>至資料表樣式的, 並將資料表樣式加入<xref:System.Windows.Forms.GridTableStylesCollection>至資料方格的。</span><span class="sxs-lookup"><span data-stu-id="f3d95-159">Additionally, you add the column style to the <xref:System.Windows.Forms.GridColumnStylesCollection> of the table style, and you add the table style to the <xref:System.Windows.Forms.GridTableStylesCollection> of the data grid.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f3d95-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3d95-160">See also</span></span>

- <xref:System.Windows.Forms.GridTableStylesCollection>
- <xref:System.Windows.Forms.GridColumnStylesCollection>
- <xref:System.Windows.Forms.DataGrid>
- [<span data-ttu-id="f3d95-161">如何：刪除或隱藏 Windows Forms DataGrid 控制項中的資料行</span><span class="sxs-lookup"><span data-stu-id="f3d95-161">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="f3d95-162">DataGrid 控制項</span><span class="sxs-lookup"><span data-stu-id="f3d95-162">DataGrid Control</span></span>](datagrid-control-windows-forms.md)

---
title: HOW TO：格式化 Windows Forms DataGrid 控制項
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
ms.openlocfilehash: 8e5c41d6f146e6abef8d7670e6191b587ac86c92
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941358"
---
# <a name="how-to-format-the-windows-forms-datagrid-control"></a><span data-ttu-id="93f13-102">HOW TO：格式化 Windows Forms DataGrid 控制項</span><span class="sxs-lookup"><span data-stu-id="93f13-102">How to: Format the Windows Forms DataGrid Control</span></span>
> [!NOTE]
>  <span data-ttu-id="93f13-103"><xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="93f13-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="93f13-104">如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="93f13-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="93f13-105">將不同的色彩套用至各個部分<xref:System.Windows.Forms.DataGrid>控制項可以協助讓您更輕鬆地閱讀及解譯中的資訊。</span><span class="sxs-lookup"><span data-stu-id="93f13-105">Applying different colors to various parts of a <xref:System.Windows.Forms.DataGrid> control can help to make the information in it easier to read and interpret.</span></span> <span data-ttu-id="93f13-106">色彩可以套用至資料列和資料行中。</span><span class="sxs-lookup"><span data-stu-id="93f13-106">Color can be applied to rows and columns.</span></span> <span data-ttu-id="93f13-107">資料列和資料行也可以隱藏或顯示您自行斟酌。</span><span class="sxs-lookup"><span data-stu-id="93f13-107">Rows and columns can also be hidden or shown at your discretion.</span></span>  
  
 <span data-ttu-id="93f13-108">有三個基本的格式化層面<xref:System.Windows.Forms.DataGrid>控制項。</span><span class="sxs-lookup"><span data-stu-id="93f13-108">There are three basic aspects of formatting the <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="93f13-109">您可以設定屬性，以建立資料會顯示為預設樣式。</span><span class="sxs-lookup"><span data-stu-id="93f13-109">You can set properties to establish a default style in which data is displayed.</span></span> <span data-ttu-id="93f13-110">從該基底，您可以自訂某些資料表顯示在執行階段的方式。</span><span class="sxs-lookup"><span data-stu-id="93f13-110">From that base, you can then customize the way certain tables are displayed at run time.</span></span> <span data-ttu-id="93f13-111">最後，您可以修改哪些資料行資料格，以及色彩顯示，而且其他格式設定，會顯示。</span><span class="sxs-lookup"><span data-stu-id="93f13-111">Finally, you can modify which columns are displayed in the data grid as well as the colors and other formatting that is shown.</span></span>  
  
 <span data-ttu-id="93f13-112">格式化資料格初始步驟中，您可以設定的屬性<xref:System.Windows.Forms.DataGrid>本身。</span><span class="sxs-lookup"><span data-stu-id="93f13-112">As an initial step in formatting a data grid, you can set the properties of the <xref:System.Windows.Forms.DataGrid> itself.</span></span> <span data-ttu-id="93f13-113">這些色彩和格式的選擇會形成您接著可以從該處進行變更資料表和資料行顯示根據基底。</span><span class="sxs-lookup"><span data-stu-id="93f13-113">These color and format choices form a base from which you can then make changes depending on the data tables and columns displayed.</span></span>  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a><span data-ttu-id="93f13-114">若要建立的預設樣式的 DataGrid 控制項</span><span class="sxs-lookup"><span data-stu-id="93f13-114">To establish a default style for the DataGrid control</span></span>  
  
1. <span data-ttu-id="93f13-115">視需要設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="93f13-115">Set the following properties as appropriate:</span></span>  
  
    |<span data-ttu-id="93f13-116">屬性</span><span class="sxs-lookup"><span data-stu-id="93f13-116">Property</span></span>|<span data-ttu-id="93f13-117">描述</span><span class="sxs-lookup"><span data-stu-id="93f13-117">Description</span></span>|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|<span data-ttu-id="93f13-118"><xref:System.Windows.Forms.DataGrid.BackColor%2A>屬性定義的方格其偶數資料列的色彩。</span><span class="sxs-lookup"><span data-stu-id="93f13-118">The <xref:System.Windows.Forms.DataGrid.BackColor%2A> property defines the color of the even-numbered rows of the grid.</span></span> <span data-ttu-id="93f13-119">當您將設定<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>不同的色彩，每個資料列設定為這個新的色彩 （1、 3、 5 和等等的資料列）。</span><span class="sxs-lookup"><span data-stu-id="93f13-119">When you set the <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> property to a different color, every other row is set to this new color (rows 1, 3, 5, and so on).</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|<span data-ttu-id="93f13-120">方格其偶數資料列的背景色彩 （0、 2、 4、 6 和等等的資料列）。</span><span class="sxs-lookup"><span data-stu-id="93f13-120">The background color of the even-numbered rows of the grid (rows 0, 2, 4, 6, and so on).</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|<span data-ttu-id="93f13-121">而<xref:System.Windows.Forms.DataGrid.BackColor%2A>並<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>屬性會決定在方格中，資料列的色彩<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>屬性會決定 nonrow 區域中，才看得到，捲動到底部，格線時，或者如果只有少數資料列中所包含的色彩方格中。</span><span class="sxs-lookup"><span data-stu-id="93f13-121">Whereas the <xref:System.Windows.Forms.DataGrid.BackColor%2A> and <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> properties determines the color of rows in the grid, the <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> property determines the color of the nonrow area, which is only visible when the grid is scrolled to the bottom, or if only a few rows are contained in the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|<span data-ttu-id="93f13-122">方格的框線樣式，其中<xref:System.Windows.Forms.BorderStyle>列舉值。</span><span class="sxs-lookup"><span data-stu-id="93f13-122">The grid's border style, one of the <xref:System.Windows.Forms.BorderStyle> enumeration values.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|<span data-ttu-id="93f13-123">這會立即顯示方格上方的方格視窗標題背景色彩。</span><span class="sxs-lookup"><span data-stu-id="93f13-123">The background color of the grid's window caption which appears immediately above the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|<span data-ttu-id="93f13-124">在方格頂端之標題的字型。</span><span class="sxs-lookup"><span data-stu-id="93f13-124">The font of the caption at the top of the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|<span data-ttu-id="93f13-125">方格視窗標題的背景色彩。</span><span class="sxs-lookup"><span data-stu-id="93f13-125">The background color of the grid's window caption.</span></span>|  
    |<xref:System.Windows.Forms.Control.Font%2A>|<span data-ttu-id="93f13-126">用來在方格中顯示文字的字型。</span><span class="sxs-lookup"><span data-stu-id="93f13-126">The font used to display the text in the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|<span data-ttu-id="93f13-127">資料的資料格的資料列所顯示的字型色彩。</span><span class="sxs-lookup"><span data-stu-id="93f13-127">The color of the font displayed by the data in the rows of the data grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|<span data-ttu-id="93f13-128">資料格的格線色彩。</span><span class="sxs-lookup"><span data-stu-id="93f13-128">The color of the grid lines of the data grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|<span data-ttu-id="93f13-129">分隔資料格方格，其中線條的樣式<xref:System.Windows.Forms.DataGridLineStyle>列舉值。</span><span class="sxs-lookup"><span data-stu-id="93f13-129">The style of the lines separating the cells of the grid, one of the <xref:System.Windows.Forms.DataGridLineStyle> enumeration values.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|<span data-ttu-id="93f13-130">資料列和資料行的標頭的背景色彩。</span><span class="sxs-lookup"><span data-stu-id="93f13-130">The background color of row and column headers.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|<span data-ttu-id="93f13-131">資料行行首所使用的字型。</span><span class="sxs-lookup"><span data-stu-id="93f13-131">The font used for the column headers.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|<span data-ttu-id="93f13-132">方格的資料行標頭，包括資料行頁首文字和加號/減號圖像 （glyph） （若要顯示多個相關的資料表時，請展開資料列） 的前景色彩。</span><span class="sxs-lookup"><span data-stu-id="93f13-132">The foreground color of the grid's column headers, including the column header text and the plus/minus glyphs (to expand rows when multiple related tables are displayed).</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|<span data-ttu-id="93f13-133">在資料方格中，包括連結到子資料表、 關聯性名稱等等的所有連結的文字色彩。</span><span class="sxs-lookup"><span data-stu-id="93f13-133">The color of text of all the links in the data grid, including links to child tables, the relation name, and so on.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|<span data-ttu-id="93f13-134">在子資料表中，這會是父資料列的背景色彩。</span><span class="sxs-lookup"><span data-stu-id="93f13-134">In a child table, this is the background color of the parent rows.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|<span data-ttu-id="93f13-135">在子資料表中，這會是父資料列的前景色彩。</span><span class="sxs-lookup"><span data-stu-id="93f13-135">In a child table, this is the foreground color of the parent rows.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|<span data-ttu-id="93f13-136">判斷資料表和資料行名稱是否會顯示在父資料列中，藉由<xref:System.Windows.Forms.DataGridParentRowsLabelStyle>列舉型別。</span><span class="sxs-lookup"><span data-stu-id="93f13-136">Determines whether the table and column names are displayed in the parent row, by means of the <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> enumeration.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|<span data-ttu-id="93f13-137">方格中資料行的預設寬度 (單位為像素)。</span><span class="sxs-lookup"><span data-stu-id="93f13-137">The default width (in pixels) of columns in the grid.</span></span> <span data-ttu-id="93f13-138">重設之前設定這個屬性<xref:System.Windows.Forms.DataGrid.DataSource%2A>並<xref:System.Windows.Forms.DataGrid.DataMember%2A>屬性 (可能是分開，或透過<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>方法)，或屬性會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="93f13-138">Set this property before resetting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties (either separately, or through the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method), or the property will have no effect.</span></span><br /><br /> <span data-ttu-id="93f13-139">屬性無法設定為小於 0 的值。</span><span class="sxs-lookup"><span data-stu-id="93f13-139">The property cannot be set to a value less than 0.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|<span data-ttu-id="93f13-140">在方格中的資料列資料列高度 （以像素為單位）。</span><span class="sxs-lookup"><span data-stu-id="93f13-140">The row height (in pixels) of rows in the grid.</span></span> <span data-ttu-id="93f13-141">重設之前設定這個屬性<xref:System.Windows.Forms.DataGrid.DataSource%2A>並<xref:System.Windows.Forms.DataGrid.DataMember%2A>屬性 (可能是分開，或透過<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>方法)，或屬性會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="93f13-141">Set this property before resetting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties (either separately, or through the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method), or the property will have no effect.</span></span><br /><br /> <span data-ttu-id="93f13-142">屬性無法設定為小於 0 的值。</span><span class="sxs-lookup"><span data-stu-id="93f13-142">The property cannot be set to a value less than 0.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|<span data-ttu-id="93f13-143">方格的資料列行首的寬度。</span><span class="sxs-lookup"><span data-stu-id="93f13-143">The width of the row headers of the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|<span data-ttu-id="93f13-144">選取的資料列或資料格時，這是背景色彩。</span><span class="sxs-lookup"><span data-stu-id="93f13-144">When a row or cell is selected, this is the background color.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|<span data-ttu-id="93f13-145">選取的資料列或資料格時，這會是前景色彩。</span><span class="sxs-lookup"><span data-stu-id="93f13-145">When a row or cell is selected, this is the foreground color.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="93f13-146">請記住，當自訂控制項，就可以將控制項設為無法存取，因為不佳的色彩選擇 （例如，紅色和綠色） 的色彩。</span><span class="sxs-lookup"><span data-stu-id="93f13-146">Keep in mind, when customizing the colors of controls, that it is possible to make the control inaccessible, due to poor color choice (for example, red and green).</span></span> <span data-ttu-id="93f13-147">使用上可用的色彩**系統色彩**調色盤，若要避免這個問題。</span><span class="sxs-lookup"><span data-stu-id="93f13-147">Use the colors available on the **System Colors** palette to avoid this issue.</span></span>  
  
     <span data-ttu-id="93f13-148">下列程序假設您的表單具有<xref:System.Windows.Forms.DataGrid>控制項繫結至資料表。</span><span class="sxs-lookup"><span data-stu-id="93f13-148">The following procedures assume your form has a <xref:System.Windows.Forms.DataGrid> control bound to a data table.</span></span> <span data-ttu-id="93f13-149">如需詳細資訊，請參閱 <<c0> [ 繫結至資料來源的 Windows Forms DataGrid 控制項](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)。</span><span class="sxs-lookup"><span data-stu-id="93f13-149">For more information, see [Binding the Windows Forms DataGrid Control to a Data Source](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span></span>  
  
### <a name="to-set-the-table-and-column-style-of-a-data-table-programmatically"></a><span data-ttu-id="93f13-150">以程式設計方式設定資料表的資料表和資料行樣式</span><span class="sxs-lookup"><span data-stu-id="93f13-150">To set the table and column style of a data table programmatically</span></span>  
  
1. <span data-ttu-id="93f13-151">建立新的表格樣式，並設定其屬性。</span><span class="sxs-lookup"><span data-stu-id="93f13-151">Create a new table style and set its properties.</span></span>  
  
2. <span data-ttu-id="93f13-152">建立資料行樣式，並設定其屬性。</span><span class="sxs-lookup"><span data-stu-id="93f13-152">Create a column style and set its properties.</span></span>  
  
3. <span data-ttu-id="93f13-153">加入資料表樣式的資料行樣式集合中的資料行樣式。</span><span class="sxs-lookup"><span data-stu-id="93f13-153">Add the column style to the table style's column styles collection.</span></span>  
  
4. <span data-ttu-id="93f13-154">加入資料格的資料表樣式集合中的表格樣式。</span><span class="sxs-lookup"><span data-stu-id="93f13-154">Add the table style to the data grid's table styles collection.</span></span>  
  
5. <span data-ttu-id="93f13-155">在下列範例中，建立新的執行個體<xref:System.Windows.Forms.DataGridTableStyle>並設定其<xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="93f13-155">In the example below, create an instance of a new <xref:System.Windows.Forms.DataGridTableStyle> and set its <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> property.</span></span>  
  
6. <span data-ttu-id="93f13-156">建立的新執行個體**GridColumnStyle**並設定其**MappingName** （和一些其他版面配置和顯示屬性）。</span><span class="sxs-lookup"><span data-stu-id="93f13-156">Create a new instance of a **GridColumnStyle** and set its **MappingName** (and some other layout and display properties).</span></span>  
  
7. <span data-ttu-id="93f13-157">針對您想要建立每個資料行樣式重複步驟 2 到 6。</span><span class="sxs-lookup"><span data-stu-id="93f13-157">Repeat steps 2 through 6 for each column style you want to create.</span></span>  
  
     <span data-ttu-id="93f13-158">下列範例說明如何<xref:System.Windows.Forms.DataGridTextBoxColumn>建立，因為資料行中顯示的名稱。</span><span class="sxs-lookup"><span data-stu-id="93f13-158">The following example illustrates how a <xref:System.Windows.Forms.DataGridTextBoxColumn> is created, because a name is to be displayed in the column.</span></span> <span data-ttu-id="93f13-159">此外，您可以新增資料行樣式<xref:System.Windows.Forms.GridColumnStylesCollection>的表格樣式，而且您新增的表格樣式<xref:System.Windows.Forms.GridTableStylesCollection>資料格。</span><span class="sxs-lookup"><span data-stu-id="93f13-159">Additionally, you add the column style to the <xref:System.Windows.Forms.GridColumnStylesCollection> of the table style, and you add the table style to the <xref:System.Windows.Forms.GridTableStylesCollection> of the data grid.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="93f13-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93f13-160">See also</span></span>

- <xref:System.Windows.Forms.GridTableStylesCollection>
- <xref:System.Windows.Forms.GridColumnStylesCollection>
- <xref:System.Windows.Forms.DataGrid>
- [<span data-ttu-id="93f13-161">如何：刪除或隱藏 Windows Forms DataGrid 控制項中的資料行</span><span class="sxs-lookup"><span data-stu-id="93f13-161">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="93f13-162">DataGrid 控制項</span><span class="sxs-lookup"><span data-stu-id="93f13-162">DataGrid Control</span></span>](datagrid-control-windows-forms.md)

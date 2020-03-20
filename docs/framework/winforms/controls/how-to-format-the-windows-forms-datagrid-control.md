---
title: 格式化資料網格控制
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
ms.openlocfilehash: 180f837c7d60f49af880faefc05da262be061d12
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182140"
---
# <a name="how-to-format-the-windows-forms-datagrid-control"></a><span data-ttu-id="f4bd2-102">如何：格式化 Windows Form DataGrid 控制項</span><span class="sxs-lookup"><span data-stu-id="f4bd2-102">How to: Format the Windows Forms DataGrid Control</span></span>
> [!NOTE]
> <span data-ttu-id="f4bd2-103"><xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="f4bd2-104">如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="f4bd2-105">將不同顏色應用於<xref:System.Windows.Forms.DataGrid>控制項的各個部分有助於使其中的資訊更易於閱讀和解釋。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-105">Applying different colors to various parts of a <xref:System.Windows.Forms.DataGrid> control can help to make the information in it easier to read and interpret.</span></span> <span data-ttu-id="f4bd2-106">顏色可以應用於行和列。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-106">Color can be applied to rows and columns.</span></span> <span data-ttu-id="f4bd2-107">行和列也可以隱藏或顯示由您自行決定。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-107">Rows and columns can also be hidden or shown at your discretion.</span></span>  
  
 <span data-ttu-id="f4bd2-108">設置<xref:System.Windows.Forms.DataGrid>控制項的格式有三個基本方面。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-108">There are three basic aspects of formatting the <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="f4bd2-109">您可以設置屬性以建立顯示資料的預設樣式。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-109">You can set properties to establish a default style in which data is displayed.</span></span> <span data-ttu-id="f4bd2-110">然後，您可以自訂運行時顯示某些表的方式。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-110">From that base, you can then customize the way certain tables are displayed at run time.</span></span> <span data-ttu-id="f4bd2-111">最後，您可以修改資料網格中顯示的列以及顯示的顏色和其他格式。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-111">Finally, you can modify which columns are displayed in the data grid as well as the colors and other formatting that is shown.</span></span>  
  
 <span data-ttu-id="f4bd2-112">作為設置資料網格格式的第一步，可以設置<xref:System.Windows.Forms.DataGrid>自身的屬性。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-112">As an initial step in formatting a data grid, you can set the properties of the <xref:System.Windows.Forms.DataGrid> itself.</span></span> <span data-ttu-id="f4bd2-113">這些顏色和格式選項構成了一個基礎，然後根據顯示的資料表和列進行更改。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-113">These color and format choices form a base from which you can then make changes depending on the data tables and columns displayed.</span></span>  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a><span data-ttu-id="f4bd2-114">為 DataGrid 控制項建立預設樣式</span><span class="sxs-lookup"><span data-stu-id="f4bd2-114">To establish a default style for the DataGrid control</span></span>  
  
1. <span data-ttu-id="f4bd2-115">根據需要設置以下屬性：</span><span class="sxs-lookup"><span data-stu-id="f4bd2-115">Set the following properties as appropriate:</span></span>  
  
    |<span data-ttu-id="f4bd2-116">屬性</span><span class="sxs-lookup"><span data-stu-id="f4bd2-116">Property</span></span>|<span data-ttu-id="f4bd2-117">描述</span><span class="sxs-lookup"><span data-stu-id="f4bd2-117">Description</span></span>|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|<span data-ttu-id="f4bd2-118">屬性<xref:System.Windows.Forms.DataGrid.BackColor%2A>定義網格偶數行的顏色。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-118">The <xref:System.Windows.Forms.DataGrid.BackColor%2A> property defines the color of the even-numbered rows of the grid.</span></span> <span data-ttu-id="f4bd2-119">將<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>屬性設置為其他顏色時，其他行將設置為此新顏色（行 1、3、5 等）。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-119">When you set the <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> property to a different color, every other row is set to this new color (rows 1, 3, 5, and so on).</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|<span data-ttu-id="f4bd2-120">網格偶數行的背景顏色（行 0、2、4、6 等）。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-120">The background color of the even-numbered rows of the grid (rows 0, 2, 4, 6, and so on).</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|<span data-ttu-id="f4bd2-121"><xref:System.Windows.Forms.DataGrid.BackColor%2A>和<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>屬性確定網格中的行顏色，<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>而屬性確定非列區域的顏色，僅當網格滾動到底部時，或者如果網格中僅包含幾行，則該區域可見。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-121">Whereas the <xref:System.Windows.Forms.DataGrid.BackColor%2A> and <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> properties determines the color of rows in the grid, the <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> property determines the color of the nonrow area, which is only visible when the grid is scrolled to the bottom, or if only a few rows are contained in the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|<span data-ttu-id="f4bd2-122">網格的邊框樣式，枚舉值之<xref:System.Windows.Forms.BorderStyle>一。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-122">The grid's border style, one of the <xref:System.Windows.Forms.BorderStyle> enumeration values.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|<span data-ttu-id="f4bd2-123">網格視窗標題的背景顏色，該顏色顯示在網格的緊要上方。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-123">The background color of the grid's window caption which appears immediately above the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|<span data-ttu-id="f4bd2-124">網格頂部的標題字體。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-124">The font of the caption at the top of the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|<span data-ttu-id="f4bd2-125">網格視窗標題的背景顏色。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-125">The background color of the grid's window caption.</span></span>|  
    |<xref:System.Windows.Forms.Control.Font%2A>|<span data-ttu-id="f4bd2-126">用於在網格中顯示文本的字體。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-126">The font used to display the text in the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|<span data-ttu-id="f4bd2-127">資料網格行中顯示的字體顏色。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-127">The color of the font displayed by the data in the rows of the data grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|<span data-ttu-id="f4bd2-128">資料網格的格線的顏色。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-128">The color of the grid lines of the data grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|<span data-ttu-id="f4bd2-129">分隔網格儲存格的行的樣式，即枚舉值之<xref:System.Windows.Forms.DataGridLineStyle>一。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-129">The style of the lines separating the cells of the grid, one of the <xref:System.Windows.Forms.DataGridLineStyle> enumeration values.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|<span data-ttu-id="f4bd2-130">行標題和列標題的背景顏色。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-130">The background color of row and column headers.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|<span data-ttu-id="f4bd2-131">用於列標題的字體。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-131">The font used for the column headers.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|<span data-ttu-id="f4bd2-132">網格的列標題的前景顏色，包括列標題文本和加/減字形（在顯示多個相關表時展開行）。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-132">The foreground color of the grid's column headers, including the column header text and the plus/minus glyphs (to expand rows when multiple related tables are displayed).</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|<span data-ttu-id="f4bd2-133">資料網格中所有連結的文本顏色，包括指向子表的連結、關係名稱等。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-133">The color of text of all the links in the data grid, including links to child tables, the relation name, and so on.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|<span data-ttu-id="f4bd2-134">在子表中，這是父行的背景顏色。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-134">In a child table, this is the background color of the parent rows.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|<span data-ttu-id="f4bd2-135">在子表中，這是父行的前景顏色。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-135">In a child table, this is the foreground color of the parent rows.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|<span data-ttu-id="f4bd2-136">通過枚<xref:System.Windows.Forms.DataGridParentRowsLabelStyle>舉確定表和列名稱是否顯示在父行中。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-136">Determines whether the table and column names are displayed in the parent row, by means of the <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> enumeration.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|<span data-ttu-id="f4bd2-137">方格中資料行的預設寬度 (單位為像素)。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-137">The default width (in pixels) of columns in the grid.</span></span> <span data-ttu-id="f4bd2-138">在重置<xref:System.Windows.Forms.DataGrid.DataSource%2A>和<xref:System.Windows.Forms.DataGrid.DataMember%2A>屬性之前設置此屬性（單獨或通過<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>方法），否則該屬性將不起作用。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-138">Set this property before resetting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties (either separately, or through the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method), or the property will have no effect.</span></span><br /><br /> <span data-ttu-id="f4bd2-139">屬性不能設置為小於 0 的值。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-139">The property cannot be set to a value less than 0.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|<span data-ttu-id="f4bd2-140">網格中行的行高度（以圖元為單位）。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-140">The row height (in pixels) of rows in the grid.</span></span> <span data-ttu-id="f4bd2-141">在重置<xref:System.Windows.Forms.DataGrid.DataSource%2A>和<xref:System.Windows.Forms.DataGrid.DataMember%2A>屬性之前設置此屬性（單獨或通過<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>方法），否則該屬性將不起作用。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-141">Set this property before resetting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties (either separately, or through the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method), or the property will have no effect.</span></span><br /><br /> <span data-ttu-id="f4bd2-142">屬性不能設置為小於 0 的值。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-142">The property cannot be set to a value less than 0.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|<span data-ttu-id="f4bd2-143">網格的行標題的寬度。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-143">The width of the row headers of the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|<span data-ttu-id="f4bd2-144">選擇行或儲存格時，這是背景顏色。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-144">When a row or cell is selected, this is the background color.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|<span data-ttu-id="f4bd2-145">選擇行或儲存格時，這是前景顏色。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-145">When a row or cell is selected, this is the foreground color.</span></span>|  
  
    > [!NOTE]
    > <span data-ttu-id="f4bd2-146">請記住，在自訂控制項的顏色時，由於顏色選擇不佳（例如紅色和綠色），因此可以使控制項無法訪問。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-146">Keep in mind, when customizing the colors of controls, that it is possible to make the control inaccessible, due to poor color choice (for example, red and green).</span></span> <span data-ttu-id="f4bd2-147">使用 **"系統色彩**"調色板上可用的顏色以避免此問題。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-147">Use the colors available on the **System Colors** palette to avoid this issue.</span></span>  
  
     <span data-ttu-id="f4bd2-148">以下過程假定表單具有綁定到資料<xref:System.Windows.Forms.DataGrid>表的控制項。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-148">The following procedures assume your form has a <xref:System.Windows.Forms.DataGrid> control bound to a data table.</span></span> <span data-ttu-id="f4bd2-149">有關詳細資訊，請參閱將[Windows 表單資料網格控制項綁定到資料來源](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-149">For more information, see [Binding the Windows Forms DataGrid Control to a Data Source](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span></span>  
  
### <a name="to-set-the-table-and-column-style-of-a-data-table-programmatically"></a><span data-ttu-id="f4bd2-150">以程式設計方式設置資料表的表和列樣式</span><span class="sxs-lookup"><span data-stu-id="f4bd2-150">To set the table and column style of a data table programmatically</span></span>  
  
1. <span data-ttu-id="f4bd2-151">創建新的表樣式並設置其屬性。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-151">Create a new table style and set its properties.</span></span>  
  
2. <span data-ttu-id="f4bd2-152">創建列樣式並設置其屬性。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-152">Create a column style and set its properties.</span></span>  
  
3. <span data-ttu-id="f4bd2-153">將列樣式添加到表樣式的列樣式集合中。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-153">Add the column style to the table style's column styles collection.</span></span>  
  
4. <span data-ttu-id="f4bd2-154">將表樣式添加到資料網格的表樣式集合中。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-154">Add the table style to the data grid's table styles collection.</span></span>  
  
5. <span data-ttu-id="f4bd2-155">在下面的示例中，創建 new<xref:System.Windows.Forms.DataGridTableStyle>的實例並設置其<xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-155">In the example below, create an instance of a new <xref:System.Windows.Forms.DataGridTableStyle> and set its <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> property.</span></span>  
  
6. <span data-ttu-id="f4bd2-156">創建**GridColumnStyle**的新實例並設置其**映射名稱**（以及一些其他佈局和顯示內容）。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-156">Create a new instance of a **GridColumnStyle** and set its **MappingName** (and some other layout and display properties).</span></span>  
  
7. <span data-ttu-id="f4bd2-157">對於要創建的每個列樣式，重複步驟 2 到 6。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-157">Repeat steps 2 through 6 for each column style you want to create.</span></span>  
  
     <span data-ttu-id="f4bd2-158">下面的示例說明了如何創建<xref:System.Windows.Forms.DataGridTextBoxColumn>， 因為名稱將在列中顯示。</span><span class="sxs-lookup"><span data-stu-id="f4bd2-158">The following example illustrates how a <xref:System.Windows.Forms.DataGridTextBoxColumn> is created, because a name is to be displayed in the column.</span></span> <span data-ttu-id="f4bd2-159">此外，您將列樣式添加到<xref:System.Windows.Forms.GridColumnStylesCollection>表樣式，並將表樣式添加到資料網格的。 <xref:System.Windows.Forms.GridTableStylesCollection></span><span class="sxs-lookup"><span data-stu-id="f4bd2-159">Additionally, you add the column style to the <xref:System.Windows.Forms.GridColumnStylesCollection> of the table style, and you add the table style to the <xref:System.Windows.Forms.GridTableStylesCollection> of the data grid.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f4bd2-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4bd2-160">See also</span></span>

- <xref:System.Windows.Forms.GridTableStylesCollection>
- <xref:System.Windows.Forms.GridColumnStylesCollection>
- <xref:System.Windows.Forms.DataGrid>
- [<span data-ttu-id="f4bd2-161">如何：刪除或隱藏 Windows Form DataGrid 控制項中的資料行</span><span class="sxs-lookup"><span data-stu-id="f4bd2-161">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="f4bd2-162">DataGrid 控制項</span><span class="sxs-lookup"><span data-stu-id="f4bd2-162">DataGrid Control</span></span>](datagrid-control-windows-forms.md)

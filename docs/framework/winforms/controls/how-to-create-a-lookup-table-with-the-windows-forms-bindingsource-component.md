---
title: "如何：使用 Windows Forms BindingSource 元件建立查閱資料表"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- lookup tables
- tables [Windows Forms], creating lookup tables
- BindingSource component [Windows Forms], creating a lookup table
- BindingSource component [Windows Forms], examples
ms.assetid: 622fce80-879d-44be-abbf-8350ec22ca2b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 27c1c6cd0e617c0940a734e7e16a3ec5d12f920d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-lookup-table-with-the-windows-forms-bindingsource-component"></a><span data-ttu-id="a455b-102">如何：使用 Windows Forms BindingSource 元件建立查閱資料表</span><span class="sxs-lookup"><span data-stu-id="a455b-102">How to: Create a Lookup Table with the Windows Forms BindingSource Component</span></span>
<span data-ttu-id="a455b-103">查閱資料表是具有資料行的資料表，而此資料行會從相關資料表的記錄中顯示資料。</span><span class="sxs-lookup"><span data-stu-id="a455b-103">A lookup table is a table of data that has a column that displays data from records in a related table.</span></span> <span data-ttu-id="a455b-104">在下列程序中，會使用 <xref:System.Windows.Forms.ComboBox> 控制項顯示從父資料表到子資料表具有外部索引鍵關聯性的欄位。</span><span class="sxs-lookup"><span data-stu-id="a455b-104">In the following procedures, a <xref:System.Windows.Forms.ComboBox> control is used to display the field with the foreign-key relationship from the parent to the child table.</span></span>  
  
 <span data-ttu-id="a455b-105">為了協助您設想這兩個資料表與此種關聯性，以下是父資料表和子資料表的範例：</span><span class="sxs-lookup"><span data-stu-id="a455b-105">To help visualize these two tables and this relationship, here is an example of a parent and child table:</span></span>  
  
 <span data-ttu-id="a455b-106">CustomersTable (父資料表)</span><span class="sxs-lookup"><span data-stu-id="a455b-106">CustomersTable (parent table)</span></span>  
  
|<span data-ttu-id="a455b-107">CustomerID</span><span class="sxs-lookup"><span data-stu-id="a455b-107">CustomerID</span></span>|<span data-ttu-id="a455b-108">CustomerName</span><span class="sxs-lookup"><span data-stu-id="a455b-108">CustomerName</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="a455b-109">712</span><span class="sxs-lookup"><span data-stu-id="a455b-109">712</span></span>|<span data-ttu-id="a455b-110">Paul Koch</span><span class="sxs-lookup"><span data-stu-id="a455b-110">Paul Koch</span></span>|  
|<span data-ttu-id="a455b-111">713</span><span class="sxs-lookup"><span data-stu-id="a455b-111">713</span></span>|<span data-ttu-id="a455b-112">Tamara Johnston</span><span class="sxs-lookup"><span data-stu-id="a455b-112">Tamara Johnston</span></span>|  
  
 <span data-ttu-id="a455b-113">OrdersTable (子資料表)</span><span class="sxs-lookup"><span data-stu-id="a455b-113">OrdersTable (child table)</span></span>  
  
|<span data-ttu-id="a455b-114">OrderID</span><span class="sxs-lookup"><span data-stu-id="a455b-114">OrderID</span></span>|<span data-ttu-id="a455b-115">OrderDate</span><span class="sxs-lookup"><span data-stu-id="a455b-115">OrderDate</span></span>|<span data-ttu-id="a455b-116">CustomerID</span><span class="sxs-lookup"><span data-stu-id="a455b-116">CustomerID</span></span>|  
|-------------|---------------|----------------|  
|<span data-ttu-id="a455b-117">903</span><span class="sxs-lookup"><span data-stu-id="a455b-117">903</span></span>|<span data-ttu-id="a455b-118">2004 年 2 月 12 日</span><span class="sxs-lookup"><span data-stu-id="a455b-118">February 12, 2004</span></span>|<span data-ttu-id="a455b-119">712</span><span class="sxs-lookup"><span data-stu-id="a455b-119">712</span></span>|  
|<span data-ttu-id="a455b-120">904</span><span class="sxs-lookup"><span data-stu-id="a455b-120">904</span></span>|<span data-ttu-id="a455b-121">2004 年 2 月 13 日</span><span class="sxs-lookup"><span data-stu-id="a455b-121">February 13, 2004</span></span>|<span data-ttu-id="a455b-122">713</span><span class="sxs-lookup"><span data-stu-id="a455b-122">713</span></span>|  
  
 <span data-ttu-id="a455b-123">在此案例中，有一個資料表 CustomersTable 儲存了您想要顯示及儲存的資訊。</span><span class="sxs-lookup"><span data-stu-id="a455b-123">In this scenario, one table, CustomersTable, stores the actual information you want to display and save.</span></span> <span data-ttu-id="a455b-124">但為了節省空間，資料表省去了可增加明確性的資料。</span><span class="sxs-lookup"><span data-stu-id="a455b-124">But to save space, the table leaves out data that adds clarity.</span></span> <span data-ttu-id="a455b-125">另一個資料表 OrdersTable 只包含看似相關的資訊，關於哪個客戶 ID 號碼對應至哪個訂單日期和訂單 ID。</span><span class="sxs-lookup"><span data-stu-id="a455b-125">The other table, OrdersTable, contains only appearance-related information about which customer ID number is equivalent to which order date and order ID.</span></span> <span data-ttu-id="a455b-126">沒有提到客戶的任何姓名。</span><span class="sxs-lookup"><span data-stu-id="a455b-126">There is no mention of the customers' names.</span></span>  
  
 <span data-ttu-id="a455b-127">[ComboBox 控制項](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md)上設定了四個重要的屬性，以供建立查閱資料表。</span><span class="sxs-lookup"><span data-stu-id="a455b-127">Four important properties are set on the [ComboBox Control](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md) control to create the lookup table.</span></span>  
  
-   <span data-ttu-id="a455b-128"><xref:System.Windows.Forms.ComboBox.DataSource%2A> 屬性包含資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="a455b-128">The <xref:System.Windows.Forms.ComboBox.DataSource%2A> property contains the name of the table.</span></span>  
  
-   <span data-ttu-id="a455b-129"><xref:System.Windows.Forms.ListControl.DisplayMember%2A> 屬性包含該資料表中您想要為控制項文字 (客戶姓名) 顯示的資料行。</span><span class="sxs-lookup"><span data-stu-id="a455b-129">The <xref:System.Windows.Forms.ListControl.DisplayMember%2A> property contains the data column of that table that you want to display for the control text (the customer's name).</span></span>  
  
-   <span data-ttu-id="a455b-130"><xref:System.Windows.Forms.ListControl.ValueMember%2A> 屬性包含該資料表中具有儲存之資訊 (父資料表中的 ID 編號) 的資料行。</span><span class="sxs-lookup"><span data-stu-id="a455b-130">The <xref:System.Windows.Forms.ListControl.ValueMember%2A> property contains the data column of that table with the stored information (the ID number in the parent table).</span></span>  
  
-   <span data-ttu-id="a455b-131"><xref:System.Windows.Forms.ListControl.SelectedValue%2A> 屬性提供子資料表的查閱值 (根據 <xref:System.Windows.Forms.ListControl.ValueMember%2A>)。</span><span class="sxs-lookup"><span data-stu-id="a455b-131">The <xref:System.Windows.Forms.ListControl.SelectedValue%2A> property provides the lookup value for the child table, based on the <xref:System.Windows.Forms.ListControl.ValueMember%2A>.</span></span>  
  
 <span data-ttu-id="a455b-132">以下程序向您示範如何將表單配置為查閱資料表，並將資料繫結至其控制項。</span><span class="sxs-lookup"><span data-stu-id="a455b-132">The procedures below show you how to lay out your form as a lookup table and bind data to the controls on it.</span></span> <span data-ttu-id="a455b-133">為了成功完成此這些程序，您必須要有具有外部索引鍵關聯性之父資料表和子資料表的資料來源 (如上所述)。</span><span class="sxs-lookup"><span data-stu-id="a455b-133">To successfully complete the procedures, you must have a data source with parent and child tables that have a foreign-key relationship, as mentioned previously.</span></span>  
  
### <a name="to-create-the-user-interface"></a><span data-ttu-id="a455b-134">若要建立使用者介面</span><span class="sxs-lookup"><span data-stu-id="a455b-134">To create the user interface</span></span>  
  
1.  <span data-ttu-id="a455b-135">從**工具箱**，拖曳<xref:System.Windows.Forms.ComboBox>控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="a455b-135">From the **ToolBox**, drag a <xref:System.Windows.Forms.ComboBox> control onto the form.</span></span>  
  
     <span data-ttu-id="a455b-136">此控制項會從父資料表顯示資料行。</span><span class="sxs-lookup"><span data-stu-id="a455b-136">This control will display the column from parent table.</span></span>  
  
2.  <span data-ttu-id="a455b-137">拖曳其他控制項以從子資料表顯示詳細資料。</span><span class="sxs-lookup"><span data-stu-id="a455b-137">Drag other controls to display details from the child table.</span></span> <span data-ttu-id="a455b-138">資料表中的資料格式會決定您要選擇哪些控制項。</span><span class="sxs-lookup"><span data-stu-id="a455b-138">The format of the data in the table should determine which controls you choose.</span></span> <span data-ttu-id="a455b-139">如需詳細資訊，請參閱[依功能區分的 Windows Forms 控制項](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)。</span><span class="sxs-lookup"><span data-stu-id="a455b-139">For more information, see [Windows Forms Controls by Function](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md).</span></span>  
  
3.  <span data-ttu-id="a455b-140">將 <xref:System.Windows.Forms.BindingNavigator> 控制項拖曳至表單上，這可讓您巡覽子資料表中的資料。</span><span class="sxs-lookup"><span data-stu-id="a455b-140">Drag a <xref:System.Windows.Forms.BindingNavigator> control onto the form; this will allow you to navigate the data in the child table.</span></span>  
  
### <a name="to-connect-to-the-data-and-bind-it-to-controls"></a><span data-ttu-id="a455b-141">連接至資料並將資料繫節至控制項</span><span class="sxs-lookup"><span data-stu-id="a455b-141">To connect to the data and bind it to controls</span></span>  
  
1.  <span data-ttu-id="a455b-142">選取 <xref:System.Windows.Forms.ComboBox>，然後按一下 [智慧工作提示] 圖像，以顯示 [智慧工作提示] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a455b-142">Select the <xref:System.Windows.Forms.ComboBox> and click the Smart Task glyph to display the Smart Task dialog box.</span></span>  
  
2.  <span data-ttu-id="a455b-143">選取 [使用資料繫結項目]。</span><span class="sxs-lookup"><span data-stu-id="a455b-143">Select **Use data bound items**.</span></span>  
  
3.  <span data-ttu-id="a455b-144">按一下 [資料來源] 下拉式方塊旁邊的箭頭。</span><span class="sxs-lookup"><span data-stu-id="a455b-144">Click the arrow next to the **Data Source** drop-down box.</span></span> <span data-ttu-id="a455b-145">若之前已為專案或表單設定過資料來源，則會顯示；若無設定，請完成下列步驟 (此範例使用 Northwind 範例資料庫的 Customers 及 Orders 資料表，並在引用時使用括號)。</span><span class="sxs-lookup"><span data-stu-id="a455b-145">If a data source has previously been configured for the project or form, it will appear; otherwise, complete the following steps (This example uses the Customers and Orders tables of the Northwind sample database and refers to them in parentheses).</span></span>  
  
    1.  <span data-ttu-id="a455b-146">按一下 [新增專案資料來源] 以連接至資料，並建立資料來源。</span><span class="sxs-lookup"><span data-stu-id="a455b-146">Click **Add Project Data Source** to connect to data and create a data source.</span></span>  
  
    2.  <span data-ttu-id="a455b-147">在 [資料來源組態精靈] 歡迎頁面上，按 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="a455b-147">On the **Data Source Configuration Wizard** welcome page, click **Next**.</span></span>  
  
    3.  <span data-ttu-id="a455b-148">選取 [選擇資料來源類型] 頁面中的 [資料庫]。</span><span class="sxs-lookup"><span data-stu-id="a455b-148">Select **Database** on the **Choose a Data Source Type** page.</span></span>  
  
    4.  <span data-ttu-id="a455b-149">從 [選擇資料連接] 頁面中的可用連接清單，選取資料連接。</span><span class="sxs-lookup"><span data-stu-id="a455b-149">Select a data connection from the list of available connections on the **Choose Your Data Connection** page.</span></span> <span data-ttu-id="a455b-150">若您想要的資料連接無法使用，請選取 [新增連接] 以建立新資料連接。</span><span class="sxs-lookup"><span data-stu-id="a455b-150">If your desired data connection is not available, select **New Connection** to create a new data connection.</span></span>  
  
    5.  <span data-ttu-id="a455b-151">按一下 [是，將連接儲存為]，將連接字串儲存至應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="a455b-151">Click **Yes, save the connection** to save the connection string in the application configuration file.</span></span>  
  
    6.  <span data-ttu-id="a455b-152">選取要帶入應用程式中的資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="a455b-152">Select the database objects to bring into your application.</span></span> <span data-ttu-id="a455b-153">在此情況中，請選取具有外部索引鍵關聯性的父資料表和子資料表 (例如 Customers 和 Orders)。</span><span class="sxs-lookup"><span data-stu-id="a455b-153">In this case, select a parent table and child table (for example, Customers and Orders) with a foreign key relationship.</span></span>  
  
    7.  <span data-ttu-id="a455b-154">您可以視需要更換預設資料集名稱。</span><span class="sxs-lookup"><span data-stu-id="a455b-154">Replace the default dataset name if you want.</span></span>  
  
    8.  <span data-ttu-id="a455b-155">按一下 [ **完成**]。</span><span class="sxs-lookup"><span data-stu-id="a455b-155">Click **Finish**.</span></span>  
  
4.  <span data-ttu-id="a455b-156">在 [顯示成員] 下拉式方塊中，選取要顯示在下拉式方塊中的資料行名稱 (例如 ContactName)。</span><span class="sxs-lookup"><span data-stu-id="a455b-156">In the **Display Member** drop-down box, select the column name (for example, ContactName) to be displayed in the combo box.</span></span>  
  
5.  <span data-ttu-id="a455b-157">在 [值成員] 下拉式方塊中，選取要在子資料表中執行查詢作業的資料行名稱 (例如 CustomerID)。</span><span class="sxs-lookup"><span data-stu-id="a455b-157">In the **Value Member** drop-down box, select the column (for example, CustomerID) to perform the lookup operation in the child table.</span></span>  
  
6.  <span data-ttu-id="a455b-158">在 [選取的值] 下拉式方塊中，巡覽至 [專案資料來源]，以及您剛剛建立包含父資料表及子資料表的資料集。</span><span class="sxs-lookup"><span data-stu-id="a455b-158">In the **Selected Value** drop-down box, navigate to **Project Data Sources** and the dataset you just created that contains the parent and child tables.</span></span> <span data-ttu-id="a455b-159">選取與父資料表的值成員相同的子資料表屬性 (例如 Orders.CustomerID)。</span><span class="sxs-lookup"><span data-stu-id="a455b-159">Select the same property of the child table that is the Value Member of the parent table (for example, Orders.CustomerID).</span></span> <span data-ttu-id="a455b-160">將會建立適當的 <xref:System.Windows.Forms.BindingSource>、資料集和資料表配接器元件，並加入至表單中。</span><span class="sxs-lookup"><span data-stu-id="a455b-160">The appropriate <xref:System.Windows.Forms.BindingSource> , data set, and table adapter components will be created and added to the form.</span></span>  
  
7.  <span data-ttu-id="a455b-161">將 <xref:System.Windows.Forms.BindingNavigator> 控制項繫結至子資料表的 <xref:System.Windows.Forms.BindingSource> (例如 `OrdersBindingSource`)。</span><span class="sxs-lookup"><span data-stu-id="a455b-161">Bind the <xref:System.Windows.Forms.BindingNavigator> control to the <xref:System.Windows.Forms.BindingSource> of the child table (for example, `OrdersBindingSource`).</span></span>  
  
8.  <span data-ttu-id="a455b-162">從子資料表的 <xref:System.Windows.Forms.ComboBox> (例如 <xref:System.Windows.Forms.BindingNavigator>)，將 <xref:System.Windows.Forms.BindingSource> 和 `OrdersBindingSource` 以外的控制項繫結至您想要顯示的詳細資料欄位。</span><span class="sxs-lookup"><span data-stu-id="a455b-162">Bind the controls other than the <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.BindingNavigator> control to the details fields from the child table's <xref:System.Windows.Forms.BindingSource> (for example, `OrdersBindingSource`) that you want to display.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a455b-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a455b-163">See Also</span></span>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="a455b-164">BindingSource 元件</span><span class="sxs-lookup"><span data-stu-id="a455b-164">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="a455b-165">ComboBox 控制項</span><span class="sxs-lookup"><span data-stu-id="a455b-165">ComboBox Control</span></span>](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md)  
 [<span data-ttu-id="a455b-166">將控制項繫結至 Visual Studio 中的資料</span><span class="sxs-lookup"><span data-stu-id="a455b-166">Bind controls to data in Visual Studio</span></span>](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)

---
title: 為 ComboBox、ListBox 或 CheckedListBox 控制項建立查閱資料表
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CheckedListBox control [Windows Forms], creating lookup tables
- lookup tables
- list boxes [Windows Forms], lookup tables
- ListBox control [Windows Forms], lookup tables
- ComboBox control [Windows Forms], lookup table
- lookup tables [Windows Forms], creating for controls
- combo boxes [Windows Forms], lookup tables
- ListBox control [Windows Forms], creating lookup tables
ms.assetid: 4ce35f12-1f4e-4317-92d1-af8686a8cfaa
ms.openlocfilehash: 4bbbc66a56c7ce269c2dabd593db88f96907d755
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737364"
---
# <a name="how-to-create-a-lookup-table-for-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a><span data-ttu-id="27555-102">如何：為 Windows Form 的 ComboBox、ListBox 或 CheckedListBox 控制項建立查閱資料表</span><span class="sxs-lookup"><span data-stu-id="27555-102">How to: Create a Lookup Table for a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>
<span data-ttu-id="27555-103">在 Windows Form 上以方便使用的格式來顯示資料，但以對程式更有意義的格式來存放資料，這樣的做法有時候相當實用。</span><span class="sxs-lookup"><span data-stu-id="27555-103">Sometimes it is useful to display data in a user-friendly format on a Windows Form, but store the data in a format that is more meaningful to your program.</span></span> <span data-ttu-id="27555-104">例如，食品的訂單表單可能會在清單方塊中依名稱來顯示功能表項目。</span><span class="sxs-lookup"><span data-stu-id="27555-104">For example, an order form for food might display the menu items by name in a list box.</span></span> <span data-ttu-id="27555-105">但是，記錄訂單的資料表則會包含代表食品的唯一 ID 編號。</span><span class="sxs-lookup"><span data-stu-id="27555-105">However, the data table recording the order would contain the unique ID numbers representing the food.</span></span> <span data-ttu-id="27555-106">下表將顯示如何存放並顯示食品訂單表單資料的範例。</span><span class="sxs-lookup"><span data-stu-id="27555-106">The following tables show an example of how to store and display order-form data for food.</span></span>  
  
### <a name="orderdetailstable"></a><span data-ttu-id="27555-107">OrderDetailsTable</span><span class="sxs-lookup"><span data-stu-id="27555-107">OrderDetailsTable</span></span>  
  
|<span data-ttu-id="27555-108">OrderID</span><span class="sxs-lookup"><span data-stu-id="27555-108">OrderID</span></span>|<span data-ttu-id="27555-109">ItemID</span><span class="sxs-lookup"><span data-stu-id="27555-109">ItemID</span></span>|<span data-ttu-id="27555-110">Quantity</span><span class="sxs-lookup"><span data-stu-id="27555-110">Quantity</span></span>|  
|-------------|------------|--------------|  
|<span data-ttu-id="27555-111">4085</span><span class="sxs-lookup"><span data-stu-id="27555-111">4085</span></span>|<span data-ttu-id="27555-112">12</span><span class="sxs-lookup"><span data-stu-id="27555-112">12</span></span>|<span data-ttu-id="27555-113">1</span><span class="sxs-lookup"><span data-stu-id="27555-113">1</span></span>|  
|<span data-ttu-id="27555-114">4086</span><span class="sxs-lookup"><span data-stu-id="27555-114">4086</span></span>|<span data-ttu-id="27555-115">13</span><span class="sxs-lookup"><span data-stu-id="27555-115">13</span></span>|<span data-ttu-id="27555-116">3</span><span class="sxs-lookup"><span data-stu-id="27555-116">3</span></span>|  
  
### <a name="itemtable"></a><span data-ttu-id="27555-117">ItemTable</span><span class="sxs-lookup"><span data-stu-id="27555-117">ItemTable</span></span>  
  
|<span data-ttu-id="27555-118">識別碼</span><span class="sxs-lookup"><span data-stu-id="27555-118">ID</span></span>|<span data-ttu-id="27555-119">Name</span><span class="sxs-lookup"><span data-stu-id="27555-119">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="27555-120">12</span><span class="sxs-lookup"><span data-stu-id="27555-120">12</span></span>|<span data-ttu-id="27555-121">馬鈴薯</span><span class="sxs-lookup"><span data-stu-id="27555-121">Potato</span></span>|  
|<span data-ttu-id="27555-122">13</span><span class="sxs-lookup"><span data-stu-id="27555-122">13</span></span>|<span data-ttu-id="27555-123">雞肉</span><span class="sxs-lookup"><span data-stu-id="27555-123">Chicken</span></span>|  
  
 <span data-ttu-id="27555-124">在此案例中，一個資料表**OrderDetailsTable**會儲存您關心顯示和儲存的實際資訊。</span><span class="sxs-lookup"><span data-stu-id="27555-124">In this scenario, one table, **OrderDetailsTable**, stores the actual information you are concerned with displaying and saving.</span></span> <span data-ttu-id="27555-125">但為節省空間，它是以隱晦的方式來設計的。</span><span class="sxs-lookup"><span data-stu-id="27555-125">But to save space, it does so in a fairly cryptic fashion.</span></span> <span data-ttu-id="27555-126">另一個資料表**ItemTable**只包含與外觀相關的資訊，其識別碼等於哪個食物名稱，而不是實際食物訂單的任何值。</span><span class="sxs-lookup"><span data-stu-id="27555-126">The other table, **ItemTable**, contains only appearance-related information about which ID number is equivalent to which food name, and nothing about the actual food orders.</span></span>  
  
 <span data-ttu-id="27555-127">**ItemTable**會透過三個屬性連接到 <xref:System.Windows.Forms.ComboBox>、<xref:System.Windows.Forms.ListBox>或 <xref:System.Windows.Forms.CheckedListBox> 控制項。</span><span class="sxs-lookup"><span data-stu-id="27555-127">The **ItemTable** is connected to the <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, or <xref:System.Windows.Forms.CheckedListBox> control through three properties.</span></span> <span data-ttu-id="27555-128">`DataSource` 屬性包含此資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="27555-128">The `DataSource` property contains the name of this table.</span></span> <span data-ttu-id="27555-129">`DisplayMember` 屬性包含您想要在控制項中顯示之資料表的資料行（食物名稱）。</span><span class="sxs-lookup"><span data-stu-id="27555-129">The `DisplayMember` property contains the data column of that table that you want to display in the control (the food name).</span></span> <span data-ttu-id="27555-130">`ValueMember` 屬性包含該資料表的資料行，其中含有儲存的資訊（ID 編號）。</span><span class="sxs-lookup"><span data-stu-id="27555-130">The `ValueMember` property contains the data column of that table with the stored information (the ID number).</span></span>  
  
 <span data-ttu-id="27555-131">**OrderDetailsTable**是由其系結集合（透過 <xref:System.Windows.Forms.Control.DataBindings%2A> 屬性來存取）連接到控制項。</span><span class="sxs-lookup"><span data-stu-id="27555-131">The **OrderDetailsTable** is connected to the control by its bindings collection, accessed through the <xref:System.Windows.Forms.Control.DataBindings%2A> property.</span></span> <span data-ttu-id="27555-132">當您將系結物件新增至集合時，您會將控制項屬性連接至資料來源（ **OrderDetailsTable**）中的特定資料成員（識別碼數位資料行）。</span><span class="sxs-lookup"><span data-stu-id="27555-132">When you add a binding object to the collection, you connect a control property to a specific data member (the column of ID numbers) in a data source (the **OrderDetailsTable**).</span></span> <span data-ttu-id="27555-133">當在控制項中進行選取時，這個資料表就是表單輸入儲存之處。</span><span class="sxs-lookup"><span data-stu-id="27555-133">When a selection is made in the control, this table is where the form input is saved.</span></span>  
  
### <a name="to-create-a-lookup-table"></a><span data-ttu-id="27555-134">若要建立查閱資料表</span><span class="sxs-lookup"><span data-stu-id="27555-134">To create a lookup table</span></span>  
  
1. <span data-ttu-id="27555-135">將 <xref:System.Windows.Forms.ComboBox>、<xref:System.Windows.Forms.ListBox> 或 <xref:System.Windows.Forms.CheckedListBox> 控制項加入表單。</span><span class="sxs-lookup"><span data-stu-id="27555-135">Add a <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, or <xref:System.Windows.Forms.CheckedListBox> control to the form.</span></span>  
  
2. <span data-ttu-id="27555-136">連接到您的資料來源。</span><span class="sxs-lookup"><span data-stu-id="27555-136">Connect to your data source.</span></span>  
  
3. <span data-ttu-id="27555-137">在兩個資料表之間建立資料關聯。</span><span class="sxs-lookup"><span data-stu-id="27555-137">Establish a data relation between the two tables.</span></span> <span data-ttu-id="27555-138">請參閱[DataRelation 物件簡介](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0k21zcyx(v=vs.120))。</span><span class="sxs-lookup"><span data-stu-id="27555-138">See [Introduction to DataRelation Objects](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0k21zcyx(v=vs.120)).</span></span>  
  
4. <span data-ttu-id="27555-139">設定下列屬性。</span><span class="sxs-lookup"><span data-stu-id="27555-139">Set the following properties.</span></span> <span data-ttu-id="27555-140">您可以在程式碼或設計工具中設定這些屬性。</span><span class="sxs-lookup"><span data-stu-id="27555-140">They can be set in code or in the designer.</span></span>  
  
    |<span data-ttu-id="27555-141">屬性</span><span class="sxs-lookup"><span data-stu-id="27555-141">Property</span></span>|<span data-ttu-id="27555-142">設定</span><span class="sxs-lookup"><span data-stu-id="27555-142">Setting</span></span>|  
    |--------------|-------------|  
    |<xref:System.Windows.Forms.ListControl.DataSource%2A>|<span data-ttu-id="27555-143">資料表，其中包含哪個 ID 編號對應於哪個項目的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="27555-143">The table that contains information about which ID number is equivalent to which item.</span></span> <span data-ttu-id="27555-144">在先前的案例中，這是 `ItemTable`。</span><span class="sxs-lookup"><span data-stu-id="27555-144">In the previous scenario, this is `ItemTable`.</span></span>|  
    |<xref:System.Windows.Forms.ListControl.DisplayMember%2A>|<span data-ttu-id="27555-145">想要在控制項中顯示的資料來源資料表之資料行。</span><span class="sxs-lookup"><span data-stu-id="27555-145">The column of the data source table that you want to display in the control.</span></span> <span data-ttu-id="27555-146">在先前的案例中，這是 `"Name"` （在程式碼中設定，請使用引號）。</span><span class="sxs-lookup"><span data-stu-id="27555-146">In the previous scenario, this is `"Name"` (to set in code, use quotation marks).</span></span>|  
    |<xref:System.Windows.Forms.ListControl.ValueMember%2A>|<span data-ttu-id="27555-147">包含儲存資訊的資料來源資料表之資料行。</span><span class="sxs-lookup"><span data-stu-id="27555-147">The column of the data source table that contains the stored information.</span></span> <span data-ttu-id="27555-148">在先前的案例中，這是 `"ID"` （在程式碼中設定，請使用引號）。</span><span class="sxs-lookup"><span data-stu-id="27555-148">In the previous scenario, this is `"ID"` (to set in code, use quotation marks).</span></span>|  
  
5. <span data-ttu-id="27555-149">在程序中，呼叫 <xref:System.Windows.Forms.ControlBindingsCollection> 類別的 <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> 方法，藉此將控制項的 <xref:System.Windows.Forms.ListControl.SelectedValue%2A> 屬性繫結至記錄表單輸入的資料表。</span><span class="sxs-lookup"><span data-stu-id="27555-149">In a procedure, call the <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> method of the <xref:System.Windows.Forms.ControlBindingsCollection> class to bind the control's <xref:System.Windows.Forms.ListControl.SelectedValue%2A> property to the table recording the form input.</span></span> <span data-ttu-id="27555-150">您也可以在設計工具中執行這項操作，而不是在程式碼中，存取 [**屬性**] 視窗中的控制項的 [<xref:System.Windows.Forms.Control.DataBindings%2A>] 屬性。</span><span class="sxs-lookup"><span data-stu-id="27555-150">You can also do this in the Designer instead of in code, by accessing the control's <xref:System.Windows.Forms.Control.DataBindings%2A> property in the **Properties** window.</span></span> <span data-ttu-id="27555-151">在前一個案例中，這是 `OrderDetailsTable`，而資料行是 `"ItemID"`。</span><span class="sxs-lookup"><span data-stu-id="27555-151">In the previous scenario, this is `OrderDetailsTable`, and the column is `"ItemID"`.</span></span>  
  
    ```vb  
    ListBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID")  
    ```  
  
    ```csharp  
    listBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="27555-152">請參閱</span><span class="sxs-lookup"><span data-stu-id="27555-152">See also</span></span>

- [<span data-ttu-id="27555-153">資料繫結和 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="27555-153">Data Binding and Windows Forms</span></span>](../data-binding-and-windows-forms.md)
- [<span data-ttu-id="27555-154">ListBox 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="27555-154">ListBox Control Overview</span></span>](listbox-control-overview-windows-forms.md)
- [<span data-ttu-id="27555-155">ComboBox 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="27555-155">ComboBox Control Overview</span></span>](combobox-control-overview-windows-forms.md)
- [<span data-ttu-id="27555-156">CheckedListBox 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="27555-156">CheckedListBox Control Overview</span></span>](checkedlistbox-control-overview-windows-forms.md)
- [<span data-ttu-id="27555-157">用來列出選項的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="27555-157">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)

---
title: "如何：為 Windows Form 的 ComboBox、ListBox 或 CheckedListBox 控制項建立查閱資料表"
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cb7ffb8a7f20c1e53b24a1db8bda326d73743a93
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-lookup-table-for-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a><span data-ttu-id="26a92-102">如何：為 Windows Form 的 ComboBox、ListBox 或 CheckedListBox 控制項建立查閱資料表</span><span class="sxs-lookup"><span data-stu-id="26a92-102">How to: Create a Lookup Table for a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>
<span data-ttu-id="26a92-103">在 Windows Form 上以方便使用的格式來顯示資料，但以對程式更有意義的格式來存放資料，這樣的做法有時候相當實用。</span><span class="sxs-lookup"><span data-stu-id="26a92-103">Sometimes it is useful to display data in a user-friendly format on a Windows Form, but store the data in a format that is more meaningful to your program.</span></span> <span data-ttu-id="26a92-104">例如，食品的訂單表單可能會在清單方塊中依名稱來顯示功能表項目。</span><span class="sxs-lookup"><span data-stu-id="26a92-104">For example, an order form for food might display the menu items by name in a list box.</span></span> <span data-ttu-id="26a92-105">但是，記錄訂單的資料表則會包含代表食品的唯一 ID 編號。</span><span class="sxs-lookup"><span data-stu-id="26a92-105">However, the data table recording the order would contain the unique ID numbers representing the food.</span></span> <span data-ttu-id="26a92-106">下表將顯示如何存放並顯示食品訂單表單資料的範例。</span><span class="sxs-lookup"><span data-stu-id="26a92-106">The following tables show an example of how to store and display order-form data for food.</span></span>  
  
### <a name="orderdetailstable"></a><span data-ttu-id="26a92-107">OrderDetailsTable</span><span class="sxs-lookup"><span data-stu-id="26a92-107">OrderDetailsTable</span></span>  
  
|<span data-ttu-id="26a92-108">OrderID</span><span class="sxs-lookup"><span data-stu-id="26a92-108">OrderID</span></span>|<span data-ttu-id="26a92-109">ItemID</span><span class="sxs-lookup"><span data-stu-id="26a92-109">ItemID</span></span>|<span data-ttu-id="26a92-110">Quantity</span><span class="sxs-lookup"><span data-stu-id="26a92-110">Quantity</span></span>|  
|-------------|------------|--------------|  
|<span data-ttu-id="26a92-111">4085</span><span class="sxs-lookup"><span data-stu-id="26a92-111">4085</span></span>|<span data-ttu-id="26a92-112">12</span><span class="sxs-lookup"><span data-stu-id="26a92-112">12</span></span>|<span data-ttu-id="26a92-113">1</span><span class="sxs-lookup"><span data-stu-id="26a92-113">1</span></span>|  
|<span data-ttu-id="26a92-114">4086</span><span class="sxs-lookup"><span data-stu-id="26a92-114">4086</span></span>|<span data-ttu-id="26a92-115">13</span><span class="sxs-lookup"><span data-stu-id="26a92-115">13</span></span>|<span data-ttu-id="26a92-116">3</span><span class="sxs-lookup"><span data-stu-id="26a92-116">3</span></span>|  
  
### <a name="itemtable"></a><span data-ttu-id="26a92-117">ItemTable</span><span class="sxs-lookup"><span data-stu-id="26a92-117">ItemTable</span></span>  
  
|<span data-ttu-id="26a92-118">ID</span><span class="sxs-lookup"><span data-stu-id="26a92-118">ID</span></span>|<span data-ttu-id="26a92-119">名稱</span><span class="sxs-lookup"><span data-stu-id="26a92-119">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="26a92-120">12</span><span class="sxs-lookup"><span data-stu-id="26a92-120">12</span></span>|<span data-ttu-id="26a92-121">馬鈴薯</span><span class="sxs-lookup"><span data-stu-id="26a92-121">Potato</span></span>|  
|<span data-ttu-id="26a92-122">13</span><span class="sxs-lookup"><span data-stu-id="26a92-122">13</span></span>|<span data-ttu-id="26a92-123">雞肉</span><span class="sxs-lookup"><span data-stu-id="26a92-123">Chicken</span></span>|  
  
 <span data-ttu-id="26a92-124">在此案例中，一個資料表中， **OrderDetailsTable**，儲存的實際的資訊，您可能會與顯示和儲存。</span><span class="sxs-lookup"><span data-stu-id="26a92-124">In this scenario, one table, **OrderDetailsTable**, stores the actual information you are concerned with displaying and saving.</span></span> <span data-ttu-id="26a92-125">但為節省空間，它是以隱晦的方式來設計的。</span><span class="sxs-lookup"><span data-stu-id="26a92-125">But to save space, it does so in a fairly cryptic fashion.</span></span> <span data-ttu-id="26a92-126">另一個資料表， **ItemTable**，只包含與外觀相關的資訊有關哪個 ID 編號相當哪個食物名稱，與實質食品訂單相關的所有項目。</span><span class="sxs-lookup"><span data-stu-id="26a92-126">The other table, **ItemTable**, contains only appearance-related information about which ID number is equivalent to which food name, and nothing about the actual food orders.</span></span>  
  
 <span data-ttu-id="26a92-127">**ItemTable**連線到<xref:System.Windows.Forms.ComboBox>， <xref:System.Windows.Forms.ListBox>，或<xref:System.Windows.Forms.CheckedListBox>透過三個屬性的控制項。</span><span class="sxs-lookup"><span data-stu-id="26a92-127">The **ItemTable** is connected to the <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, or <xref:System.Windows.Forms.CheckedListBox> control through three properties.</span></span> <span data-ttu-id="26a92-128">`DataSource`屬性包含此資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="26a92-128">The `DataSource` property contains the name of this table.</span></span> <span data-ttu-id="26a92-129">`DisplayMember`屬性包含您想要在控制項 （食品名稱） 中顯示該資料表的資料行。</span><span class="sxs-lookup"><span data-stu-id="26a92-129">The `DisplayMember` property contains the data column of that table that you want to display in the control (the food name).</span></span> <span data-ttu-id="26a92-130">`ValueMember`屬性包含該資料表中具有儲存的資訊 （ID 編號） 的資料行。</span><span class="sxs-lookup"><span data-stu-id="26a92-130">The `ValueMember` property contains the data column of that table with the stored information (the ID number).</span></span>  
  
 <span data-ttu-id="26a92-131">**OrderDetailsTable**由其繫結的集合，透過連接到控制項<xref:System.Windows.Forms.Control.DataBindings%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="26a92-131">The **OrderDetailsTable** is connected to the control by its bindings collection, accessed through the <xref:System.Windows.Forms.Control.DataBindings%2A> property.</span></span> <span data-ttu-id="26a92-132">當您將繫結物件加入集合時，便控制項屬性連接到資料來源中的特定資料成員 （ID 編號的資料行） ( **OrderDetailsTable**)。</span><span class="sxs-lookup"><span data-stu-id="26a92-132">When you add a binding object to the collection, you connect a control property to a specific data member (the column of ID numbers) in a data source (the **OrderDetailsTable**).</span></span> <span data-ttu-id="26a92-133">當在控制項中進行選取時，這個資料表就是表單輸入儲存之處。</span><span class="sxs-lookup"><span data-stu-id="26a92-133">When a selection is made in the control, this table is where the form input is saved.</span></span>  
  
### <a name="to-create-a-lookup-table"></a><span data-ttu-id="26a92-134">若要建立查閱資料表</span><span class="sxs-lookup"><span data-stu-id="26a92-134">To create a lookup table</span></span>  
  
1.  <span data-ttu-id="26a92-135">將 <xref:System.Windows.Forms.ComboBox>、<xref:System.Windows.Forms.ListBox> 或 <xref:System.Windows.Forms.CheckedListBox> 控制項加入表單。</span><span class="sxs-lookup"><span data-stu-id="26a92-135">Add a <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, or <xref:System.Windows.Forms.CheckedListBox> control to the form.</span></span>  
  
2.  <span data-ttu-id="26a92-136">連接到您的資料來源。</span><span class="sxs-lookup"><span data-stu-id="26a92-136">Connect to your data source.</span></span>  
  
3.  <span data-ttu-id="26a92-137">在兩個資料表之間建立資料關聯。</span><span class="sxs-lookup"><span data-stu-id="26a92-137">Establish a data relation between the two tables.</span></span> <span data-ttu-id="26a92-138">請參閱[DataRelation 物件簡介](http://msdn.microsoft.com/library/89d8a881-8265-41f2-a88b-61311ab06192)。</span><span class="sxs-lookup"><span data-stu-id="26a92-138">See [Introduction to DataRelation Objects](http://msdn.microsoft.com/library/89d8a881-8265-41f2-a88b-61311ab06192).</span></span>  
  
4.  <span data-ttu-id="26a92-139">設定下列屬性。</span><span class="sxs-lookup"><span data-stu-id="26a92-139">Set the following properties.</span></span> <span data-ttu-id="26a92-140">您可以在程式碼或設計工具中設定這些屬性。</span><span class="sxs-lookup"><span data-stu-id="26a92-140">They can be set in code or in the designer.</span></span>  
  
    |<span data-ttu-id="26a92-141">屬性</span><span class="sxs-lookup"><span data-stu-id="26a92-141">Property</span></span>|<span data-ttu-id="26a92-142">設定</span><span class="sxs-lookup"><span data-stu-id="26a92-142">Setting</span></span>|  
    |--------------|-------------|  
    |<xref:System.Windows.Forms.ListControl.DataSource%2A>|<span data-ttu-id="26a92-143">資料表，其中包含哪個 ID 編號對應於哪個項目的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="26a92-143">The table that contains information about which ID number is equivalent to which item.</span></span> <span data-ttu-id="26a92-144">在前述案例中，這是`ItemTable`。</span><span class="sxs-lookup"><span data-stu-id="26a92-144">In the previous scenario, this is `ItemTable`.</span></span>|  
    |<xref:System.Windows.Forms.ListControl.DisplayMember%2A>|<span data-ttu-id="26a92-145">想要在控制項中顯示的資料來源資料表之資料行。</span><span class="sxs-lookup"><span data-stu-id="26a92-145">The column of the data source table that you want to display in the control.</span></span> <span data-ttu-id="26a92-146">在前述案例中，這是`"Name"`（程式碼中設定，請使用引號）。</span><span class="sxs-lookup"><span data-stu-id="26a92-146">In the previous scenario, this is `"Name"` (to set in code, use quotation marks).</span></span>|  
    |<xref:System.Windows.Forms.ListControl.ValueMember%2A>|<span data-ttu-id="26a92-147">包含儲存資訊的資料來源資料表之資料行。</span><span class="sxs-lookup"><span data-stu-id="26a92-147">The column of the data source table that contains the stored information.</span></span> <span data-ttu-id="26a92-148">在前述案例中，這是`"ID"`（程式碼中設定，請使用引號）。</span><span class="sxs-lookup"><span data-stu-id="26a92-148">In the previous scenario, this is `"ID"` (to set in code, use quotation marks).</span></span>|  
  
5.  <span data-ttu-id="26a92-149">在程序中，呼叫 <xref:System.Windows.Forms.ControlBindingsCollection> 類別的 <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> 方法，藉此將控制項的 <xref:System.Windows.Forms.ListControl.SelectedValue%2A> 屬性繫結至記錄表單輸入的資料表。</span><span class="sxs-lookup"><span data-stu-id="26a92-149">In a procedure, call the <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> method of the <xref:System.Windows.Forms.ControlBindingsCollection> class to bind the control's <xref:System.Windows.Forms.ListControl.SelectedValue%2A> property to the table recording the form input.</span></span> <span data-ttu-id="26a92-150">您也這樣可以在程式碼，而不是在設計工具中存取控制項的<xref:System.Windows.Forms.Control.DataBindings%2A>屬性**屬性**視窗。</span><span class="sxs-lookup"><span data-stu-id="26a92-150">You can also do this in the Designer instead of in code, by accessing the control's <xref:System.Windows.Forms.Control.DataBindings%2A> property in the **Properties** window.</span></span> <span data-ttu-id="26a92-151">在前述案例中，這是`OrderDetailsTable`，與資料行是`"ItemID"`。</span><span class="sxs-lookup"><span data-stu-id="26a92-151">In the previous scenario, this is `OrderDetailsTable`, and the column is `"ItemID"`.</span></span>  
  
    ```vb  
    ListBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID")  
    ```  
  
    ```csharp  
    listBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="26a92-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26a92-152">See Also</span></span>  
 [<span data-ttu-id="26a92-153">資料繫結和 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="26a92-153">Data Binding and Windows Forms</span></span>](../../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [<span data-ttu-id="26a92-154">ListBox 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="26a92-154">ListBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/listbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="26a92-155">ComboBox 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="26a92-155">ComboBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/combobox-control-overview-windows-forms.md)  
 [<span data-ttu-id="26a92-156">CheckedListBox 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="26a92-156">CheckedListBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/checkedlistbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="26a92-157">用來列出選項的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="26a92-157">Windows Forms Controls Used to List Options</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)

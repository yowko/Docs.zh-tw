---
title: "如何：存取 Windows Form DataGridViewComboBoxCell 下拉式清單中的物件"
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
- DataGridView control [Windows Forms], accessing objects in combo box cells
- combo boxes [Windows Forms], in DataGridView control
- combo boxes [Windows Forms], accessing objects in DataGridViewComboBoxCell drop-down lists
ms.assetid: bcbe794a-d1fa-47f8-b5a3-5f085b32097d
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a0fac2e73e76ad49a5b1ce6942f3ae2b4c0584e3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-objects-in-a-windows-forms-datagridviewcomboboxcell-drop-down-list"></a><span data-ttu-id="9f3ef-102">如何：存取 Windows Form DataGridViewComboBoxCell 下拉式清單中的物件</span><span class="sxs-lookup"><span data-stu-id="9f3ef-102">How to: Access Objects in a Windows Forms DataGridViewComboBoxCell Drop-Down List</span></span>
<span data-ttu-id="9f3ef-103">像<xref:System.Windows.Forms.ComboBox>控制項，<xref:System.Windows.Forms.DataGridViewComboBoxColumn>和<xref:System.Windows.Forms.DataGridViewComboBoxCell>類型可讓您將任意的物件加入至他們的下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="9f3ef-103">Like the <xref:System.Windows.Forms.ComboBox> control, the <xref:System.Windows.Forms.DataGridViewComboBoxColumn> and <xref:System.Windows.Forms.DataGridViewComboBoxCell> types enable you to add arbitrary objects to their drop-down lists.</span></span> <span data-ttu-id="9f3ef-104">利用此功能，您可以表示複雜下拉式清單中的狀態而不需要對應的物件儲存在不同的集合。</span><span class="sxs-lookup"><span data-stu-id="9f3ef-104">With this feature, you can represent complex states in a drop-down list without having to store corresponding objects in a separate collection.</span></span>  
  
 <span data-ttu-id="9f3ef-105">不同於<xref:System.Windows.Forms.ComboBox>控制項，<xref:System.Windows.Forms.DataGridView>型別沒有<xref:System.Windows.Forms.ComboBox.SelectedItem%2A>來擷取目前所選的物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="9f3ef-105">Unlike the <xref:System.Windows.Forms.ComboBox> control, the <xref:System.Windows.Forms.DataGridView> types do not have a <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> property for retrieving the currently selected object.</span></span> <span data-ttu-id="9f3ef-106">相反地，您必須設定<xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType>或<xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType>屬性設為您的商務物件上的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="9f3ef-106">Instead, you must set the <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType> or <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType> property to the name of a property on your business object.</span></span> <span data-ttu-id="9f3ef-107">當使用者進行選取時，商務物件的指定的屬性設定的儲存格<xref:System.Windows.Forms.DataGridViewCell.Value%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="9f3ef-107">When the user makes a selection, the indicated property of the business object sets the cell <xref:System.Windows.Forms.DataGridViewCell.Value%2A> property.</span></span>  
  
 <span data-ttu-id="9f3ef-108">若要擷取商務物件，用來儲存格的值，`ValueMember`屬性必須指定此屬性，傳回本身的商務物件的參考。</span><span class="sxs-lookup"><span data-stu-id="9f3ef-108">To retrieve the business object through the cell value, the `ValueMember` property must indicate a property that returns a reference to the business object itself.</span></span> <span data-ttu-id="9f3ef-109">因此，如果商務物件的類型不是在您的控制，您必須新增這類屬性擴充透過繼承型別。</span><span class="sxs-lookup"><span data-stu-id="9f3ef-109">Therefore, if the type of the business object is not under your control, you must add such a property by extending the type through inheritance.</span></span>  
  
 <span data-ttu-id="9f3ef-110">下列程序示範如何填入下拉式清單使用商務物件，並擷取物件的儲存格<xref:System.Windows.Forms.DataGridViewCell.Value%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="9f3ef-110">The following procedures demonstrate how to populate a drop-down list with business objects and retrieve the objects through the cell <xref:System.Windows.Forms.DataGridViewCell.Value%2A> property.</span></span>  
  
### <a name="to-add-business-objects-to-the-drop-down-list"></a><span data-ttu-id="9f3ef-111">將商務物件新增到下拉式清單</span><span class="sxs-lookup"><span data-stu-id="9f3ef-111">To add business objects to the drop-down list</span></span>  
  
1.  <span data-ttu-id="9f3ef-112">建立新<xref:System.Windows.Forms.DataGridViewComboBoxColumn>並擴展其<xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A>集合。</span><span class="sxs-lookup"><span data-stu-id="9f3ef-112">Create a new <xref:System.Windows.Forms.DataGridViewComboBoxColumn> and populate its <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> collection.</span></span> <span data-ttu-id="9f3ef-113">或者，您可以設定資料行<xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A>商務物件的集合的屬性。</span><span class="sxs-lookup"><span data-stu-id="9f3ef-113">Alternatively, you can set the column <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> property to the collection of business objects.</span></span> <span data-ttu-id="9f3ef-114">在此情況下，不過，您無法將 「 未指派 」 加入下拉式清單而不需要建立對應的商務物件集合中。</span><span class="sxs-lookup"><span data-stu-id="9f3ef-114">In that case, however, you cannot add "unassigned" to the drop-down list without creating a corresponding business object in your collection.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#110)]  
  
2.  <span data-ttu-id="9f3ef-115">設定 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> 和 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="9f3ef-115">Set the <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> and <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> properties.</span></span> <span data-ttu-id="9f3ef-116"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A>表示要顯示在下拉式清單中的商務物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="9f3ef-116"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> indicates the property of the business object to display in the drop-down list.</span></span> <span data-ttu-id="9f3ef-117"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A>表示傳回的商務物件的參考的屬性。</span><span class="sxs-lookup"><span data-stu-id="9f3ef-117"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> indicates the property that returns a reference to the business object.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#115)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#115)]  
  
3.  <span data-ttu-id="9f3ef-118">請確定您的商務物件型別包含將參考傳回給目前的執行個體的屬性。</span><span class="sxs-lookup"><span data-stu-id="9f3ef-118">Make sure that your business object type contains a property that returns a reference to the current instance.</span></span> <span data-ttu-id="9f3ef-119">這個屬性必須與指派給的值為<xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A>上一個步驟中。</span><span class="sxs-lookup"><span data-stu-id="9f3ef-119">This property must be named with the value assigned to <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> in the previous step.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#310)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#310)]  
  
### <a name="to-retrieve-the-currently-selected-business-object"></a><span data-ttu-id="9f3ef-120">若要擷取目前選取的商務物件</span><span class="sxs-lookup"><span data-stu-id="9f3ef-120">To retrieve the currently selected business object</span></span>  
  
-   <span data-ttu-id="9f3ef-121">取得儲存格<xref:System.Windows.Forms.DataGridViewCell.Value%2A>屬性並將它轉換成商務物件類型。</span><span class="sxs-lookup"><span data-stu-id="9f3ef-121">Get the cell <xref:System.Windows.Forms.DataGridViewCell.Value%2A> property and cast it to the business object type.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#120)]  
  
## <a name="example"></a><span data-ttu-id="9f3ef-122">範例</span><span class="sxs-lookup"><span data-stu-id="9f3ef-122">Example</span></span>  
 <span data-ttu-id="9f3ef-123">完整的範例將示範使用下拉式清單中的商務物件。</span><span class="sxs-lookup"><span data-stu-id="9f3ef-123">The complete example demonstrates the use of business objects in a drop-down list.</span></span> <span data-ttu-id="9f3ef-124">在範例中，<xref:System.Windows.Forms.DataGridView>控制項所繫結的集合`Task`物件。</span><span class="sxs-lookup"><span data-stu-id="9f3ef-124">In the example, a <xref:System.Windows.Forms.DataGridView> control is bound to a collection of `Task` objects.</span></span> <span data-ttu-id="9f3ef-125">每個`Task`物件具有`AssignedTo`屬性，指出`Employee`物件目前指派給該工作。</span><span class="sxs-lookup"><span data-stu-id="9f3ef-125">Each `Task` object has an `AssignedTo` property that indicates the `Employee` object currently assigned to that task.</span></span> <span data-ttu-id="9f3ef-126">`Assigned To`資料行會顯示`Name`每個屬性值指派給員工或 「 未指派 」`Task.AssignedTo`屬性值是`null`。</span><span class="sxs-lookup"><span data-stu-id="9f3ef-126">The `Assigned To` column displays the `Name` property value for each assigned employee, or "unassigned" if the `Task.AssignedTo` property value is `null`.</span></span>  
  
 <span data-ttu-id="9f3ef-127">若要檢視此範例的行為，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="9f3ef-127">To view the behavior of this example, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="9f3ef-128">變更中的指派`Assigned To`從下拉式清單中選取不同的值，或按 CTRL + 0 下拉式方塊儲存格中的資料行。</span><span class="sxs-lookup"><span data-stu-id="9f3ef-128">Change assignments in the `Assigned To` column by selecting different values from the drop-down lists or pressing CTRL+0 in a combo-box cell.</span></span>  
  
2.  <span data-ttu-id="9f3ef-129">按一下`Generate Report`顯示目前的指派。</span><span class="sxs-lookup"><span data-stu-id="9f3ef-129">Click `Generate Report` to display the current assignments.</span></span> <span data-ttu-id="9f3ef-130">此示範中的變更`Assigned To`會自動更新資料行`tasks`集合。</span><span class="sxs-lookup"><span data-stu-id="9f3ef-130">This demonstrates that a change in the `Assigned To` column automatically updates the `tasks` collection.</span></span>  
  
3.  <span data-ttu-id="9f3ef-131">按一下`Request Status`按鈕呼叫`RequestStatus`方法目前`Employee`物件，該資料列。</span><span class="sxs-lookup"><span data-stu-id="9f3ef-131">Click a `Request Status` button to call the `RequestStatus` method of the current `Employee` object for that row.</span></span> <span data-ttu-id="9f3ef-132">這會顯示已順利擷取選取的物件。</span><span class="sxs-lookup"><span data-stu-id="9f3ef-132">This demonstrates that the selected object has been successfully retrieved.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9f3ef-133">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="9f3ef-133">Compiling the Code</span></span>  
 <span data-ttu-id="9f3ef-134">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="9f3ef-134">This example requires:</span></span>  
  
-   <span data-ttu-id="9f3ef-135">System 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="9f3ef-135">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f3ef-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9f3ef-136">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxCell>  
 <xref:System.Windows.Forms.DataGridViewComboBoxCell.Items%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxCell.DataSource%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCell.Value%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ComboBox>  
 [<span data-ttu-id="9f3ef-137">在 Windows Forms DataGridView 控制項中顯示資料</span><span class="sxs-lookup"><span data-stu-id="9f3ef-137">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)

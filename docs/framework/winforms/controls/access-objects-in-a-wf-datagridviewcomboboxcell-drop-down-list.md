---
title: 在 DataGridViewComboBoxCell 中存取物件下拉式清單
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], accessing objects in combo box cells
- combo boxes [Windows Forms], in DataGridView control
- combo boxes [Windows Forms], accessing objects in DataGridViewComboBoxCell drop-down lists
ms.assetid: bcbe794a-d1fa-47f8-b5a3-5f085b32097d
ms.openlocfilehash: 7e76ab1ac9089778e4371f4ee65b06d5ebc570bf
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746318"
---
# <a name="how-to-access-objects-in-a-windows-forms-datagridviewcomboboxcell-drop-down-list"></a><span data-ttu-id="85fd7-102">如何：存取 Windows Form DataGridViewComboBoxCell 下拉式清單中的物件</span><span class="sxs-lookup"><span data-stu-id="85fd7-102">How to: Access Objects in a Windows Forms DataGridViewComboBoxCell Drop-Down List</span></span>
<span data-ttu-id="85fd7-103">如同 <xref:System.Windows.Forms.ComboBox> 控制項，<xref:System.Windows.Forms.DataGridViewComboBoxColumn> 和 <xref:System.Windows.Forms.DataGridViewComboBoxCell> 類型可讓您將任意物件加入其下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="85fd7-103">Like the <xref:System.Windows.Forms.ComboBox> control, the <xref:System.Windows.Forms.DataGridViewComboBoxColumn> and <xref:System.Windows.Forms.DataGridViewComboBoxCell> types enable you to add arbitrary objects to their drop-down lists.</span></span> <span data-ttu-id="85fd7-104">使用這項功能，您可以在下拉式清單中代表複雜的狀態，而不需要將對應的物件儲存在不同的集合中。</span><span class="sxs-lookup"><span data-stu-id="85fd7-104">With this feature, you can represent complex states in a drop-down list without having to store corresponding objects in a separate collection.</span></span>  
  
 <span data-ttu-id="85fd7-105">不同于 <xref:System.Windows.Forms.ComboBox> 控制項，<xref:System.Windows.Forms.DataGridView> 類型沒有 <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> 屬性可用於抓取目前選取的物件。</span><span class="sxs-lookup"><span data-stu-id="85fd7-105">Unlike the <xref:System.Windows.Forms.ComboBox> control, the <xref:System.Windows.Forms.DataGridView> types do not have a <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> property for retrieving the currently selected object.</span></span> <span data-ttu-id="85fd7-106">相反地，您必須將 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType> 或 <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType> 屬性設定為商務物件上的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="85fd7-106">Instead, you must set the <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType> or <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType> property to the name of a property on your business object.</span></span> <span data-ttu-id="85fd7-107">當使用者進行選取時，商務物件的指定屬性會將資料格設定 <xref:System.Windows.Forms.DataGridViewCell.Value%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="85fd7-107">When the user makes a selection, the indicated property of the business object sets the cell <xref:System.Windows.Forms.DataGridViewCell.Value%2A> property.</span></span>  
  
 <span data-ttu-id="85fd7-108">若要透過資料格值抓取商務物件，`ValueMember` 屬性必須指出傳回商務物件本身參考的屬性。</span><span class="sxs-lookup"><span data-stu-id="85fd7-108">To retrieve the business object through the cell value, the `ValueMember` property must indicate a property that returns a reference to the business object itself.</span></span> <span data-ttu-id="85fd7-109">因此，如果商務物件的型別不在您的控制之下，您就必須透過繼承擴充型別來加入這類屬性。</span><span class="sxs-lookup"><span data-stu-id="85fd7-109">Therefore, if the type of the business object is not under your control, you must add such a property by extending the type through inheritance.</span></span>  
  
 <span data-ttu-id="85fd7-110">下列程式示範如何在下拉式清單中填入商務物件，並透過資料格 <xref:System.Windows.Forms.DataGridViewCell.Value%2A> 屬性來抓取物件。</span><span class="sxs-lookup"><span data-stu-id="85fd7-110">The following procedures demonstrate how to populate a drop-down list with business objects and retrieve the objects through the cell <xref:System.Windows.Forms.DataGridViewCell.Value%2A> property.</span></span>  
  
### <a name="to-add-business-objects-to-the-drop-down-list"></a><span data-ttu-id="85fd7-111">若要在下拉式清單中加入商務物件</span><span class="sxs-lookup"><span data-stu-id="85fd7-111">To add business objects to the drop-down list</span></span>  
  
1. <span data-ttu-id="85fd7-112">建立新的 <xref:System.Windows.Forms.DataGridViewComboBoxColumn> 並填入其 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> 集合。</span><span class="sxs-lookup"><span data-stu-id="85fd7-112">Create a new <xref:System.Windows.Forms.DataGridViewComboBoxColumn> and populate its <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> collection.</span></span> <span data-ttu-id="85fd7-113">或者，您也可以將資料行 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> 屬性設定為商務物件的集合。</span><span class="sxs-lookup"><span data-stu-id="85fd7-113">Alternatively, you can set the column <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> property to the collection of business objects.</span></span> <span data-ttu-id="85fd7-114">不過，在這種情況下，您不能在下拉式清單中加入「未指派」，而不需要在您的集合中建立對應的商務物件。</span><span class="sxs-lookup"><span data-stu-id="85fd7-114">In that case, however, you cannot add "unassigned" to the drop-down list without creating a corresponding business object in your collection.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#110)]  
  
2. <span data-ttu-id="85fd7-115">請設定 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> 和 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="85fd7-115">Set the <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> and <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> properties.</span></span> <span data-ttu-id="85fd7-116"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> 表示要顯示在下拉式清單中之商務物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="85fd7-116"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> indicates the property of the business object to display in the drop-down list.</span></span> <span data-ttu-id="85fd7-117"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> 表示傳回商務物件參考的屬性。</span><span class="sxs-lookup"><span data-stu-id="85fd7-117"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> indicates the property that returns a reference to the business object.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#115)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#115)]  
  
3. <span data-ttu-id="85fd7-118">請確定您的商業物件類型包含會傳回目前實例之參考的屬性。</span><span class="sxs-lookup"><span data-stu-id="85fd7-118">Make sure that your business object type contains a property that returns a reference to the current instance.</span></span> <span data-ttu-id="85fd7-119">這個屬性必須以在上一個步驟中指派給 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> 的值命名。</span><span class="sxs-lookup"><span data-stu-id="85fd7-119">This property must be named with the value assigned to <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> in the previous step.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#310)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#310)]  
  
### <a name="to-retrieve-the-currently-selected-business-object"></a><span data-ttu-id="85fd7-120">若要取出目前選取的商務物件</span><span class="sxs-lookup"><span data-stu-id="85fd7-120">To retrieve the currently selected business object</span></span>  
  
- <span data-ttu-id="85fd7-121">取得 <xref:System.Windows.Forms.DataGridViewCell.Value%2A> 屬性的資料格，並將它轉換成商業物件類型。</span><span class="sxs-lookup"><span data-stu-id="85fd7-121">Get the cell <xref:System.Windows.Forms.DataGridViewCell.Value%2A> property and cast it to the business object type.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#120)]  
  
## <a name="example"></a><span data-ttu-id="85fd7-122">範例</span><span class="sxs-lookup"><span data-stu-id="85fd7-122">Example</span></span>  
 <span data-ttu-id="85fd7-123">完整的範例會示範如何在下拉式清單中使用商務物件。</span><span class="sxs-lookup"><span data-stu-id="85fd7-123">The complete example demonstrates the use of business objects in a drop-down list.</span></span> <span data-ttu-id="85fd7-124">在此範例中，<xref:System.Windows.Forms.DataGridView> 控制項系結至 `Task` 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="85fd7-124">In the example, a <xref:System.Windows.Forms.DataGridView> control is bound to a collection of `Task` objects.</span></span> <span data-ttu-id="85fd7-125">每個 `Task` 物件都有 `AssignedTo` 屬性，指出目前指派給該工作的 `Employee` 物件。</span><span class="sxs-lookup"><span data-stu-id="85fd7-125">Each `Task` object has an `AssignedTo` property that indicates the `Employee` object currently assigned to that task.</span></span> <span data-ttu-id="85fd7-126">[`Assigned To`] 資料行會顯示每個指派員工的 `Name` 屬性值，如果 `null``Task.AssignedTo` 屬性值，則為「未指派」。</span><span class="sxs-lookup"><span data-stu-id="85fd7-126">The `Assigned To` column displays the `Name` property value for each assigned employee, or "unassigned" if the `Task.AssignedTo` property value is `null`.</span></span>  
  
 <span data-ttu-id="85fd7-127">若要查看此範例的行為，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="85fd7-127">To view the behavior of this example, perform the following steps:</span></span>  
  
1. <span data-ttu-id="85fd7-128">在 [`Assigned To`] 資料行中變更指派，方法是從下拉式清單中選取不同的值，或在下拉式列示方塊儲存格中按 CTRL + 0。</span><span class="sxs-lookup"><span data-stu-id="85fd7-128">Change assignments in the `Assigned To` column by selecting different values from the drop-down lists or pressing CTRL+0 in a combo-box cell.</span></span>  
  
2. <span data-ttu-id="85fd7-129">按一下 [`Generate Report`] 以顯示目前的指派。</span><span class="sxs-lookup"><span data-stu-id="85fd7-129">Click `Generate Report` to display the current assignments.</span></span> <span data-ttu-id="85fd7-130">這會示範 `Assigned To` 資料行中的變更會自動更新 `tasks` 集合。</span><span class="sxs-lookup"><span data-stu-id="85fd7-130">This demonstrates that a change in the `Assigned To` column automatically updates the `tasks` collection.</span></span>  
  
3. <span data-ttu-id="85fd7-131">按一下 [`Request Status`] 按鈕，為該資料列呼叫目前 `Employee` 物件的 `RequestStatus` 方法。</span><span class="sxs-lookup"><span data-stu-id="85fd7-131">Click a `Request Status` button to call the `RequestStatus` method of the current `Employee` object for that row.</span></span> <span data-ttu-id="85fd7-132">這會示範已成功抓取選取的物件。</span><span class="sxs-lookup"><span data-stu-id="85fd7-132">This demonstrates that the selected object has been successfully retrieved.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="85fd7-133">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="85fd7-133">Compiling the Code</span></span>  
 <span data-ttu-id="85fd7-134">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="85fd7-134">This example requires:</span></span>  
  
- <span data-ttu-id="85fd7-135">System 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="85fd7-135">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85fd7-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85fd7-136">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxCell>
- <xref:System.Windows.Forms.DataGridViewComboBoxCell.Items%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxCell.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCell.Value%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ComboBox>
- [<span data-ttu-id="85fd7-137">在 Windows Forms DataGridView 控制項中顯示資料</span><span class="sxs-lookup"><span data-stu-id="85fd7-137">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)

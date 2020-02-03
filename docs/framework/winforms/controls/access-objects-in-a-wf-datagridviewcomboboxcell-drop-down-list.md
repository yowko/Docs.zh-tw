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
# <a name="how-to-access-objects-in-a-windows-forms-datagridviewcomboboxcell-drop-down-list"></a>如何：存取 Windows Form DataGridViewComboBoxCell 下拉式清單中的物件
如同 <xref:System.Windows.Forms.ComboBox> 控制項，<xref:System.Windows.Forms.DataGridViewComboBoxColumn> 和 <xref:System.Windows.Forms.DataGridViewComboBoxCell> 類型可讓您將任意物件加入其下拉式清單中。 使用這項功能，您可以在下拉式清單中代表複雜的狀態，而不需要將對應的物件儲存在不同的集合中。  
  
 不同于 <xref:System.Windows.Forms.ComboBox> 控制項，<xref:System.Windows.Forms.DataGridView> 類型沒有 <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> 屬性可用於抓取目前選取的物件。 相反地，您必須將 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType> 或 <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType> 屬性設定為商務物件上的屬性名稱。 當使用者進行選取時，商務物件的指定屬性會將資料格設定 <xref:System.Windows.Forms.DataGridViewCell.Value%2A> 屬性。  
  
 若要透過資料格值抓取商務物件，`ValueMember` 屬性必須指出傳回商務物件本身參考的屬性。 因此，如果商務物件的型別不在您的控制之下，您就必須透過繼承擴充型別來加入這類屬性。  
  
 下列程式示範如何在下拉式清單中填入商務物件，並透過資料格 <xref:System.Windows.Forms.DataGridViewCell.Value%2A> 屬性來抓取物件。  
  
### <a name="to-add-business-objects-to-the-drop-down-list"></a>若要在下拉式清單中加入商務物件  
  
1. 建立新的 <xref:System.Windows.Forms.DataGridViewComboBoxColumn> 並填入其 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> 集合。 或者，您也可以將資料行 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> 屬性設定為商務物件的集合。 不過，在這種情況下，您不能在下拉式清單中加入「未指派」，而不需要在您的集合中建立對應的商務物件。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#110)]  
  
2. 請設定 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> 和 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> 屬性。 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> 表示要顯示在下拉式清單中之商務物件的屬性。 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> 表示傳回商務物件參考的屬性。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#115)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#115)]  
  
3. 請確定您的商業物件類型包含會傳回目前實例之參考的屬性。 這個屬性必須以在上一個步驟中指派給 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> 的值命名。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#310)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#310)]  
  
### <a name="to-retrieve-the-currently-selected-business-object"></a>若要取出目前選取的商務物件  
  
- 取得 <xref:System.Windows.Forms.DataGridViewCell.Value%2A> 屬性的資料格，並將它轉換成商業物件類型。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#120)]  
  
## <a name="example"></a>範例  
 完整的範例會示範如何在下拉式清單中使用商務物件。 在此範例中，<xref:System.Windows.Forms.DataGridView> 控制項系結至 `Task` 物件的集合。 每個 `Task` 物件都有 `AssignedTo` 屬性，指出目前指派給該工作的 `Employee` 物件。 [`Assigned To`] 資料行會顯示每個指派員工的 `Name` 屬性值，如果 `null``Task.AssignedTo` 屬性值，則為「未指派」。  
  
 若要查看此範例的行為，請執行下列步驟：  
  
1. 在 [`Assigned To`] 資料行中變更指派，方法是從下拉式清單中選取不同的值，或在下拉式列示方塊儲存格中按 CTRL + 0。  
  
2. 按一下 [`Generate Report`] 以顯示目前的指派。 這會示範 `Assigned To` 資料行中的變更會自動更新 `tasks` 集合。  
  
3. 按一下 [`Request Status`] 按鈕，為該資料列呼叫目前 `Employee` 物件的 `RequestStatus` 方法。 這會示範已成功抓取選取的物件。  
  
 [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#000)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
- System 和 System.Windows.Forms 組件的參考。  
  
## <a name="see-also"></a>另請參閱

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
- [在 Windows Forms DataGridView 控制項中顯示資料](displaying-data-in-the-windows-forms-datagridview-control.md)

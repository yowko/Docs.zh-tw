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
ms.workload: dotnet
ms.openlocfilehash: d0f4eb14fbb459f6844053507d1eb4f0a46cede3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-access-objects-in-a-windows-forms-datagridviewcomboboxcell-drop-down-list"></a>如何：存取 Windows Form DataGridViewComboBoxCell 下拉式清單中的物件
像<xref:System.Windows.Forms.ComboBox>控制項，<xref:System.Windows.Forms.DataGridViewComboBoxColumn>和<xref:System.Windows.Forms.DataGridViewComboBoxCell>類型可讓您將任意的物件加入至他們的下拉式清單。 利用此功能，您可以表示複雜下拉式清單中的狀態而不需要對應的物件儲存在不同的集合。  
  
 不同於<xref:System.Windows.Forms.ComboBox>控制項，<xref:System.Windows.Forms.DataGridView>型別沒有<xref:System.Windows.Forms.ComboBox.SelectedItem%2A>來擷取目前所選的物件的屬性。 相反地，您必須設定<xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType>或<xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType>屬性設為您的商務物件上的屬性名稱。 當使用者進行選取時，商務物件的指定的屬性設定的儲存格<xref:System.Windows.Forms.DataGridViewCell.Value%2A>屬性。  
  
 若要擷取商務物件，用來儲存格的值，`ValueMember`屬性必須指定此屬性，傳回本身的商務物件的參考。 因此，如果商務物件的類型不是在您的控制，您必須新增這類屬性擴充透過繼承型別。  
  
 下列程序示範如何填入下拉式清單使用商務物件，並擷取物件的儲存格<xref:System.Windows.Forms.DataGridViewCell.Value%2A>屬性。  
  
### <a name="to-add-business-objects-to-the-drop-down-list"></a>將商務物件新增到下拉式清單  
  
1.  建立新<xref:System.Windows.Forms.DataGridViewComboBoxColumn>並擴展其<xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A>集合。 或者，您可以設定資料行<xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A>商務物件的集合的屬性。 在此情況下，不過，您無法將 「 未指派 」 加入下拉式清單而不需要建立對應的商務物件集合中。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#110)]  
  
2.  設定 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> 和 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> 屬性。 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A>表示要顯示在下拉式清單中的商務物件的屬性。 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A>表示傳回的商務物件的參考的屬性。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#115)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#115)]  
  
3.  請確定您的商務物件型別包含將參考傳回給目前的執行個體的屬性。 這個屬性必須與指派給的值為<xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A>上一個步驟中。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#310)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#310)]  
  
### <a name="to-retrieve-the-currently-selected-business-object"></a>若要擷取目前選取的商務物件  
  
-   取得儲存格<xref:System.Windows.Forms.DataGridViewCell.Value%2A>屬性並將它轉換成商務物件類型。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#120)]  
  
## <a name="example"></a>範例  
 完整的範例將示範使用下拉式清單中的商務物件。 在範例中，<xref:System.Windows.Forms.DataGridView>控制項所繫結的集合`Task`物件。 每個`Task`物件具有`AssignedTo`屬性，指出`Employee`物件目前指派給該工作。 `Assigned To`資料行會顯示`Name`每個屬性值指派給員工或 「 未指派 」`Task.AssignedTo`屬性值是`null`。  
  
 若要檢視此範例的行為，請執行下列步驟：  
  
1.  變更中的指派`Assigned To`從下拉式清單中選取不同的值，或按 CTRL + 0 下拉式方塊儲存格中的資料行。  
  
2.  按一下`Generate Report`顯示目前的指派。 此示範中的變更`Assigned To`會自動更新資料行`tasks`集合。  
  
3.  按一下`Request Status`按鈕呼叫`RequestStatus`方法目前`Employee`物件，該資料列。 這會顯示已順利擷取選取的物件。  
  
 [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#000)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   System 和 System.Windows.Forms 組件的參考。  
  
## <a name="see-also"></a>請參閱  
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
 [在 Windows Forms DataGridView 控制項中顯示資料](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)

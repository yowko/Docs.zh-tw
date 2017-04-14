---
title: "如何：存取 Windows Form DataGridViewComboBoxCell 下拉式清單中的物件 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "下拉式方塊, 存取 DataGridViewComboBoxCell 下拉式清單中的物件"
  - "下拉式方塊, 在 DataGridView 控制項中"
  - "DataGridView 控制項 [Windows Form], 存取下拉式方塊儲存格中的物件"
ms.assetid: bcbe794a-d1fa-47f8-b5a3-5f085b32097d
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 如何：存取 Windows Form DataGridViewComboBoxCell 下拉式清單中的物件
如同 <xref:System.Windows.Forms.ComboBox> 控制項，<xref:System.Windows.Forms.DataGridViewComboBoxColumn> 和 <xref:System.Windows.Forms.DataGridViewComboBoxCell> 型別讓您可以將任意物件加入至其下拉式清單。  利用這個功能，您可以在下拉式清單中表示複雜的狀態，而不需要將對應的物件儲存在不同的集合物件 \(Collection\) 中。  
  
 和 <xref:System.Windows.Forms.ComboBox> 控制項不同的是，<xref:System.Windows.Forms.DataGridView> 型別沒有可供擷取目前所選取之物件的 <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> 屬性。  而且，您必須將 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=fullName> 或 <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=fullName> 屬性設定為商務物件 \(Business Object\) 上的屬性名稱。  當使用者進行選取時，指定的商務物件屬性會設定儲存格 <xref:System.Windows.Forms.DataGridViewCell.Value%2A> 屬性。  
  
 若要透過儲存格的值來擷取商務物件，`ValueMember` 屬性必須指定可傳回商務物件本身之參考的屬性。  因此，如果您無法控制商務物件的型別，則必須透過繼承以擴充該型別，藉以加入前述的屬性。  
  
 下列程序將示範如何在下拉式清單中填入商務物件，並透過儲存格 <xref:System.Windows.Forms.DataGridViewCell.Value%2A> 屬性擷取物件。  
  
### 若要將商務物件加入至下拉式清單  
  
1.  建立新的 <xref:System.Windows.Forms.DataGridViewComboBoxColumn>，並填入其 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> 集合物件 \(Collection\)。  或者，您可以將資料行 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> 屬性設定為商務物件的集合。  但是，在這個情況下，您必須在集合中建立對應的商務物件，才能將「未指派」加入至下拉式清單。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#110)]  
  
2.  設定 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> 和 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> 屬性。  <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> 表示在下拉式清單中顯示商務物件的屬性。  <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> 表示傳回商務物件之參考的屬性。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#115)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#115)]  
  
3.  請確定您的商務物件型別是否包含傳回目前執行個體之參考的屬性。  這個屬性必須使用在先前步驟中指派給 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> 的值來命名。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#310)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#310)]  
  
### 若要擷取目前選取的商務物件  
  
-   取得儲存格 <xref:System.Windows.Forms.DataGridViewCell.Value%2A> 屬性，然後將它轉型為商務物件型別。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#120)]  
  
## 範例  
 此完整範例將示範下拉式清單中之商務物件的使用方式。  在此範例中，<xref:System.Windows.Forms.DataGridView> 控制項會繫結至 `Task` 物件的集合。  每一個 `Task` 物件皆具有 `AssignedTo` 屬性，用以表示目前指派給該工作的 `Employee` 物件。  `Assigned To` 資料行會顯示每一個受指派員工的 `Name` 屬性值，如果 `Task.AssignedTo` 屬性值為 `null`，則顯示「未指派」。  
  
 若要檢視此範例的行為，請執行下列步驟：  
  
1.  從下拉式清單中選取不同的值或在下拉式方塊儲存格中按下 CTRL\+0，變更 `Assigned To` 資料行中的指派。  
  
2.  按一下 \[`Generate Report`\]，以顯示目前的指派。  這將示範在 `Assigned To` 資料行中的變更會自動更新 `tasks` 集合物件。  
  
3.  按一下 \[`Request Status`\] 按鈕，以呼叫該資料列之目前 `Employee` 物件的 `RequestStatus` 方法。  這將展示成功擷取所選取的物件。  
  
 [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#000)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   System 和 System.Windows.Forms 組件的參考。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn>   
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewComboBoxCell>   
 <xref:System.Windows.Forms.DataGridViewComboBoxCell.Items%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewComboBoxCell.DataSource%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewCell.Value%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.ComboBox>   
 [在 Windows Form DataGridView 控制項中顯示資料](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)
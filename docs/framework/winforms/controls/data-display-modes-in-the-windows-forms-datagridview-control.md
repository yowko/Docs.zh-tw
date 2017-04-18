---
title: "Windows Form DataGridView 控制項的資料顯示模式 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "資料 [Windows Form], 顯示模式"
  - "資料格, 顯示模式"
  - "DataGridView 控制項 [Windows Form], 顯示模式"
ms.assetid: 9755a030-3f3f-4705-a661-ba5a48a81875
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Windows Form DataGridView 控制項的資料顯示模式
<xref:System.Windows.Forms.DataGridView> 控制項可以使用三種不同的模式來顯示資料：繫結、未繫結和虛擬。  請依您的需要選擇最適合的模式。  
  
## 未繫結  
 如果您想要顯示以程式設計方式進行管理的少量資料，則未繫結模式會相當適用。  與繫結模式不同的是，您並不需要直接將 <xref:System.Windows.Forms.DataGridView> 控制項與資料來源連接。  您所必須做的是自行填入控制項的內容，而這通常是使用 <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=fullName> 方法來完成。  
  
 對於靜態、唯讀資料而言，或者當您想提供與外部資料來源存放區的程式碼時，未繫結模式便會特別有用。  然而，當您希望使用者與外部資料來源互動時，通常會使用繫結模式。  
  
 如需使用唯讀繫結 <xref:System.Windows.Forms.DataGridView> 的範例，請參閱 [如何：建立未繫結的 Windows Form DataGridView 控制項](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md)。  
  
## 繫結  
 繫結模式適合使用與資料存放區的自動互動來管理資料。  您可以經由設定 <xref:System.Windows.Forms.DataGridView.DataSource%2A> 屬性，直接附加 <xref:System.Windows.Forms.DataGridView> 控制項至資料來源。  當控制項為資料繫結時，便會推入和提取資料列，不需要您進行明確管理。  當 <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> 屬性為 `true` 時，在資料來源中的每個資料行都會造成在控制項中產生對應的資料行。  如果偏好建立自己的資料行，您可以將這個屬性設定為 `false`，並在設定時使用 <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A> 屬性來繫結每個資料行。  如果想使用預設所產生的資料行型別以外的型別，這就會非常有用。  如需詳細資訊，請參閱 [Windows Form DataGridView 控制項中的資料行類型](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)。  
  
 如需使用繫結 <xref:System.Windows.Forms.DataGridView> 控制項的範例，請參閱[逐步解說：驗證 Windows Form DataGridView 控制項中的資料](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)。  
  
 您也可以加入未繫結的資料行至繫結模式的 <xref:System.Windows.Forms.DataGridView> 控制項。  當您想顯示按鈕的資料行，或顯示允許使用者在特定資料列上執行動作的連結時，這將會很有用。  對於顯示具有從繫結資料行計算得來的值之資料行，也是很有用。  您可以在 <xref:System.Windows.Forms.DataGridView.CellFormatting> 事件的處理常式中，填入計算資料行的儲存格值。  但是若您使用 <xref:System.Data.DataSet> 或 <xref:System.Data.DataTable> 做為資料來源，您反而會想要使用 <xref:System.Data.DataColumn.Expression%2A?displayProperty=fullName> 屬性建立計算資料行。  在這種情況下，<xref:System.Windows.Forms.DataGridView> 控制項將會把計算資料行視為資料來源中的任何其他資料行。  
  
 在繫結模式中依未繫結的資料行排序不受支援。  如果您在繫結模式中建立未繫結資料行 \(內含使用者可編輯的值\)，則在依繫結資料行排序控制項時，就必須實作虛擬模式以維護這些值。  
  
## 虛擬  
 使用虛擬模式，您可以實作自己的資料管理作業。  當控制項是依繫結資料行排列時，這對於維護在繫結模式中未繫結資料行的值而言，是必須的。  不過虛擬模式的主要用途，是在與大量資料互動時最佳化效能。  
  
 您要將 <xref:System.Windows.Forms.DataGridView> 控制項附加至您管理的快取，而您的程式碼則會控制推入和提取資料列的時機。  若要維持少量的記憶體，快取的大小必須類似目前顯示的資料列數目。  當使用者將新資料列捲動到檢視內時，程式碼會從快取要求新資料，並且選擇性地清除記憶體的舊資料。  
  
 在實作虛擬模式時，需要追蹤資料模式需要新資料列以及需要復原加入新資料列的時機。  此功能的精確實作會依資料模型的實作和交易語意而定，不管認可的範圍是儲存格或資料列層級。  
  
 如需虛擬模式的詳細資訊，請參閱 [Windows Form DataGridView 控制項中的虛擬模式](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)。  如需示範如何使用虛擬模式事件的範例，請參閱[逐步解說：在 Windows Form DataGridView 控制項中實作虛擬模式](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.BindingSource>   
 <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A?displayProperty=fullName>   
 [在 Windows Form DataGridView 控制項中顯示資料](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)   
 [Windows Form DataGridView 控制項中的資料行類型](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)   
 [逐步解說：建立未繫結的 Windows Form DataGridView 控制項](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)   
 [如何：將資料繫結至 Windows Form DataGridView 控制項](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md)   
 [Windows Form DataGridView 控制項中的虛擬模式](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)   
 [逐步解說：在 Windows Form DataGridView 控制項中實作虛擬模式](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)
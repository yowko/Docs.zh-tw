---
title: "逐步解說：建立未繫結的 Windows Form DataGridView 控制項 | Microsoft Docs"
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
  - "資料 [Windows Form], 在不繫結至資料來源的情況下顯示"
  - "資料 [Windows Form], 未繫結"
  - "DataGridView 控制項 [Windows Form], 在不繫結至資料來源的情況下顯示資料"
  - "DataGridView 控制項 [Windows Form], 未繫結資料"
  - "逐步解說 [Windows Form], DataGridView 控制項"
ms.assetid: 5a8d6afa-1b4b-4b24-8db8-501086ffdebe
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# 逐步解說：建立未繫結的 Windows Form DataGridView 控制項
您可能經常想要顯示並非來自資料庫的表格式資料。  例如，您可能想要顯示二維陣列字串的內容。  <xref:System.Windows.Forms.DataGridView> 類別提供簡單且可高度自訂的方式來顯示資料，而不必繫結至資料來源。  這個逐步解說會顯示如何填入 <xref:System.Windows.Forms.DataGridView> 控制項，並在「未繫結」模式中管理資料列的加入和刪除。  根據預設，使用者可以加入新的資料列。  若要防止加入資料列，請將 <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> 屬性設定為 `false`。  
  
 若要將此主題中的程式碼複製為一份清單，請參閱 [如何：建立未繫結的 Windows Form DataGridView 控制項](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md)。  
  
## 建立表單  
  
#### 若要使用未繫結的 DataGridView 控制項  
  
1.  建立衍生自 <xref:System.Windows.Forms.Form> 並包含下列變數宣告和 `Main` 方法的類別。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#01](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#01](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#02](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#02](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#02)]  
  
2.  在表單的類別定義中實作 `SetupLayout` 方法，以設定表單的配置。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#20)]  
  
3.  建立 `SetupDataGridView` 方法，以設定 <xref:System.Windows.Forms.DataGridView> 資料行和屬性。  
  
     這個方法會先將 <xref:System.Windows.Forms.DataGridView> 控制項加入表單的 <xref:System.Windows.Forms.Control.Controls%2A> 集合。  接著，要顯示的資料行數目會使用 <xref:System.Windows.Forms.DataGridView.ColumnCount%2A> 屬性來設定。  資料行行首的預設樣式是經由 <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> 屬性所傳回的 <xref:System.Windows.Forms.DataGridViewCellStyle> 的 <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A>、<xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> 和 <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A> 屬性來設定。  
  
     配置和外觀屬性便會設定，然後也會指派資料行名稱。  當這個方法結束時，<xref:System.Windows.Forms.DataGridView> 控制項便已可供填入。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#30)]  
  
4.  建立 `PopulateDataGridView` 方法，將資料列加入 <xref:System.Windows.Forms.DataGridView> 控制項。  
  
     每個資料列都代表一首歌以及關聯的資訊。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#40](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#40)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#40](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#40)]  
  
5.  透過適當的公用程式方法，您可以附加事件處理常式。  
  
     您將處理 \[**加入**\] 和 \[**刪除**\] 按鈕的 <xref:System.Windows.Forms.Control.Click> 事件、表單的 <xref:System.Windows.Forms.Form.Load> 事件，以及 <xref:System.Windows.Forms.DataGridView> 控制項的 <xref:System.Windows.Forms.DataGridView.CellFormatting> 事件。  
  
     當引發 \[**加入**\] 按鈕的 <xref:System.Windows.Forms.Control.Click> 事件時，一個新的空資料列便會加入至 <xref:System.Windows.Forms.DataGridView>。  
  
     當引發 \[**刪除**\] 按鈕的 <xref:System.Windows.Forms.Control.Click> 事件時，選取的資料列便會刪除，除非它是新資料錄的資料列 \(可以讓使用者加入新資料列\)。  這個資料列一定是 <xref:System.Windows.Forms.DataGridView> 控制項中的最後一個資料列。  
  
     當引發表單的 <xref:System.Windows.Forms.Form.Load> 事件時，便會呼叫 `SetupLayout`、`SetupDataGridView` 和 `PopulateDataGridView` 公用程式方法。  
  
     當引發 <xref:System.Windows.Forms.DataGridView.CellFormatting> 事件時，`Date` 資料行中的每個儲存格都會格式化為完整日期，除非無法剖析儲存格的值。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#10)]  
  
## 測試應用程式  
 您現在可以測試表單以確定它的行為表現如預期般。  
  
#### 若要測試表單  
  
-   按下 F5 執行應用程式。  
  
     您會看到一個 <xref:System.Windows.Forms.DataGridView> 控制項，顯示 `PopulateDataGridView` 中所列出的歌曲。  您可以使用 \[**Add Row**\] 按鈕來加入新的資料列，並且使用 \[**Delete Row**\] 按鈕來刪除選取的資料列。  未繫結的 <xref:System.Windows.Forms.DataGridView> 控制項是資料存放區，而它的資料與任何外部來源 \(例如 <xref:System.Data.DataSet> 或陣列\) 無關。  
  
## 後續步驟  
 這個應用程式讓您對 <xref:System.Windows.Forms.DataGridView> 控制項的功能有了初步的了解。  您可以用許多方式來自訂 <xref:System.Windows.Forms.DataGridView> 控制項的外觀和行為：  
  
-   變更框線和行首樣式。  如需詳細資訊，請參閱 [如何：變更 Windows Form DataGridView 控制項中的框線和格線樣式](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md)。  
  
-   啟用或限制使用者對 <xref:System.Windows.Forms.DataGridView> 控制項的輸入。  如需詳細資訊，請參閱[如何：防止在 Windows Form DataGridView 控制項中新增和刪除資料列](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md)和 [如何：使 Windows Form DataGridView 控制項中的資料行成為唯讀](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)。  
  
-   檢查使用者輸入中的資料庫相關錯誤。  如需詳細資訊，請參閱[逐步解說：處理 Windows Form DataGridView 控制項中的資料輸入期間所發生的錯誤](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md)。  
  
-   在處理大量資料時使用虛擬模式。  如需詳細資訊，請參閱[逐步解說：在 Windows Form DataGridView 控制項中實作虛擬模式](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)。  
  
-   自訂儲存格的外觀。  如需詳細資訊，請參閱 [如何：在 Windows Form DataGridView 控制項中自訂儲存格的外觀](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md) 和 [如何：設定 Windows Form DataGridView 控制項的預設儲存格樣式](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 [在 Windows Form DataGridView 控制項中顯示資料](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)   
 [如何：建立未繫結的 Windows Form DataGridView 控制項](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md)   
 [Windows Form DataGridView 控制項的資料顯示模式](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)
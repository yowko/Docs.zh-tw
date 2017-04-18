---
title: "逐步解說：處理 Windows Form DataGridView 控制項中的資料輸入期間所發生的錯誤 | Microsoft Docs"
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
  - "資料輸入, 錯誤處理"
  - "資料格, 錯誤處理"
  - "DataGridView 控制項 [Windows Form], 錯誤處理"
  - "錯誤處理, 資料輸入"
  - "錯誤處理, DataGridView 控制項"
  - "逐步解說 [Windows Form], DataGridView 控制項"
ms.assetid: 30a68b85-d3af-4946-83c1-1e2d010d0511
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 逐步解說：處理 Windows Form DataGridView 控制項中的資料輸入期間所發生的錯誤
處理來自基礎資料存放區的錯誤是資料輸入應用程式的必要功能。  Windows Form <xref:System.Windows.Forms.DataGridView> 控制項透過公開 <xref:System.Windows.Forms.DataGridView.DataError> 事件 \(它會在資料存放區偵測到違反條件約束或壞的商務規則時引發\)，使這項功能更加容易。  
  
 在這個逐步解說中，您將從 Northwind 範例資料庫的 `Customers` 資料表擷取資料列，並在 <xref:System.Windows.Forms.DataGridView> 控制項中顯示這些資料列。  當在新的資料列或已編輯的現有資料列中偵測到重複的 `CustomerID` 值時，便會發生 <xref:System.Windows.Forms.DataGridView.DataError> 事件，而這個事件將透過顯示一個描述此例外狀況的 <xref:System.Windows.Forms.MessageBox> 來進行處理。  
  
 若要將此主題中的程式碼複製為一份清單，請參閱 [如何：處理 Windows Form DataGridView 控制項中的資料輸入期間所發生的錯誤](../../../../docs/framework/winforms/controls/handle-errors-that-occur-during-data-entry-in-the-datagrid.md)。  
  
## 必要條件  
 若要完成這個逐步解說，您必須要有：  
  
-   存取具有 Northwind SQL Server 範例資料庫的伺服器。  
  
## 建立表單  
  
#### 若要處理 DataGridView 控制項中的資料輸入錯誤  
  
1.  建立一個由 <xref:System.Windows.Forms.Form> 所衍生，而且包含一個 <xref:System.Windows.Forms.DataGridView> 控制項和一個 <xref:System.Windows.Forms.BindingSource> 元件的類別。  
  
     下列的程式碼範例提供基本的初始化，而且包含了一個 `Main` 方法。  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#01](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#01](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridView.DataError#02](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#02](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#02)]  
  
2.  在表單的類別定義中實作一個方法，來處理與資料庫連接的細節。  
  
     這個程式碼範使用一個  `GetData`  方法，此方法會傳回填入 <xref:System.Data.DataTable> 物件。  請確認您已將 `connectionString` 變數設定為適合此資料庫的值。  
  
    > [!IMPORTANT]
    >  在連接字串內儲存機密資訊 \(例如密碼\) 會影響應用程式的安全性。  使用 Windows 驗證 \(也稱為整合式安全性\) 是控制資料庫存取的更安全方式。  如需詳細資訊，請參閱[保護連接資訊](../../../../docs/framework/data/adonet/protecting-connection-information.md)。  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#30)]  
  
3.  為表單中初始化 <xref:System.Windows.Forms.DataGridView> 和 <xref:System.Windows.Forms.BindingSource> 的 <xref:System.Windows.Forms.Form.Load> 事件實作處理常式，並且設定資料繫結。  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#10)]  
  
4.  處理 <xref:System.Windows.Forms.DataGridView> 上的 <xref:System.Windows.Forms.DataGridView.DataError> 事件。  
  
     如果錯誤的內容是一項認可作業，請在 <xref:System.Windows.Forms.MessageBox> 中顯示錯誤。  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#20)]  
  
## 測試應用程式  
 您現在可以測試表單以確定它的行為表現如預期般。  
  
#### 若要測試表單  
  
-   按下 F5 執行應用程式。  
  
     您將看到 <xref:System.Windows.Forms.DataGridView> 控制項中填滿來自 Customers 資料表的資料。  如果您輸入重複的 `CustomerID` 值並認可編輯，儲存格值將會自動還原，而且您將看到顯示資料輸入錯誤的 <xref:System.Windows.Forms.MessageBox>。  
  
## 後續步驟  
 這個應用程式讓您對 <xref:System.Windows.Forms.DataGridView> 控制項的功能有了初步的了解。  您可以用許多方式來自訂 <xref:System.Windows.Forms.DataGridView> 控制項的外觀和行為：  
  
-   變更框線和行首樣式。  如需詳細資訊，請參閱 [如何：變更 Windows Form DataGridView 控制項中的框線和格線樣式](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md)。  
  
-   啟用或限制使用者對 <xref:System.Windows.Forms.DataGridView> 控制項的輸入。  如需詳細資訊，請參閱[如何：防止在 Windows Form DataGridView 控制項中新增和刪除資料列](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md)和 [如何：使 Windows Form DataGridView 控制項中的資料行成為唯讀](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)。  
  
-   驗證使用者在 <xref:System.Windows.Forms.DataGridView> 控制項中輸入的資料。  如需詳細資訊，請參閱[逐步解說：驗證 Windows Form DataGridView 控制項中的資料](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)。  
  
-   在處理大量資料時使用虛擬模式。  如需詳細資訊，請參閱[逐步解說：在 Windows Form DataGridView 控制項中實作虛擬模式](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)。  
  
-   自訂儲存格的外觀。  如需詳細資訊，請參閱 [如何：在 Windows Form DataGridView 控制項中自訂儲存格的外觀](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md) 和 [如何：設定 Windows Form DataGridView 控制項的預設儲存格樣式](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.BindingSource>   
 [Windows Form DataGridView 控制項中的資料輸入](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)   
 [如何：處理 Windows Form DataGridView 控制項中的資料輸入期間所發生的錯誤](../../../../docs/framework/winforms/controls/handle-errors-that-occur-during-data-entry-in-the-datagrid.md)   
 [逐步解說：驗證 Windows Form DataGridView 控制項中的資料](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)   
 [保護連接資訊](../../../../docs/framework/data/adonet/protecting-connection-information.md)
---
title: "逐步解說：驗證 Windows Form DataGridView 控制項中的資料 | Microsoft Docs"
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
  - "資料 [Windows Form], 驗證"
  - "資料格, 驗證資料"
  - "資料驗證, Windows Form"
  - "DataGridView 控制項 [Windows Form], 資料驗證"
  - "驗證資料, Windows Form"
  - "逐步解說 [Windows Form], DataGridView 控制項"
ms.assetid: a4f1d015-2969-430c-8ea2-b612d179c290
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 22
---
# 逐步解說：驗證 Windows Form DataGridView 控制項中的資料
當您提供資料輸入功能給使用者時，通常您必須驗證輸入表單中的資料。  <xref:System.Windows.Forms.DataGridView> 類別提供了一個方便的方法，可以在資料被認可並寫入資料存放區之前進行驗證。  您可以處理 <xref:System.Windows.Forms.DataGridView.CellValidating> 事件來驗證資料，這個事件是在目前的儲存格發生變更時由 <xref:System.Windows.Forms.DataGridView> 所引發。  
  
 在這個逐步解說中，您將從 Northwind 範例資料庫的 `Customers` 資料表擷取資料列，並在 <xref:System.Windows.Forms.DataGridView> 控制項中顯示這些資料列。  當使用者編輯了位於 `CompanyName` 資料行中的儲存格，而且試圖離開該儲存格時，<xref:System.Windows.Forms.DataGridView.CellValidating> 事件處理常式將會檢查新的公司名稱字串以確保其不是空字串；如果新值是一個空字串，<xref:System.Windows.Forms.DataGridView> 會防止使用者的游標離開該儲存格，直到輸入了一個不是非空字串為止。  
  
 若要將此主題中的程式碼複製為一份清單，請參閱 [如何：驗證 Windows Form DataGridView 控制項中的資料](../../../../docs/framework/winforms/controls/how-to-validate-data-in-the-windows-forms-datagridview-control.md)。  
  
## 必要條件  
 若要完成這個逐步解說，您必須要有：  
  
-   存取具有 Northwind SQL Server 範例資料庫的伺服器。  
  
## 建立表單  
  
#### 若要驗證在 DataGridView 中輸入的資料  
  
1.  建立一個由 <xref:System.Windows.Forms.Form> 所衍生，而且包含一個 <xref:System.Windows.Forms.DataGridView> 控制項和一個 <xref:System.Windows.Forms.BindingSource> 元件的類別。  
  
     下列的程式碼範例提供基本的初始化，而且包含了一個 `Main` 方法。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#01](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#01](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#02](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#02](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#02)]  
  
2.  在表單的類別定義中實作一個方法，來處理與資料庫連接的細節。  
  
     這個程式碼範使用一個  `GetData`  方法，此方法會傳回填入 <xref:System.Data.DataTable> 物件。  請確認您已將 `connectionString` 變數設定為適合此資料庫的值。  
  
    > [!IMPORTANT]
    >  在連接字串內儲存機密資訊 \(例如密碼\) 會影響應用程式的安全性。  使用 Windows 驗證 \(也稱為整合式安全性\) 是資料庫存取控制中比較安全的一種做法。  如需詳細資訊，請參閱[保護連接資訊](../../../../docs/framework/data/adonet/protecting-connection-information.md)。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#30)]  
  
3.  為表單中初始化 <xref:System.Windows.Forms.DataGridView> 和 <xref:System.Windows.Forms.BindingSource> 的 <xref:System.Windows.Forms.Form.Load> 事件實作處理常式，並且設定資料繫結。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#10)]  
  
4.  實作 <xref:System.Windows.Forms.DataGridView> 控制項的 <xref:System.Windows.Forms.DataGridView.CellValidating> 和 <xref:System.Windows.Forms.DataGridView.CellEndEdit> 事件之處理常式。  
  
     <xref:System.Windows.Forms.DataGridView.CellValidating> 事件處理常式就是您判斷 `CompanyName` 資料行中的儲存格是否空白的地方。  如果儲存格的值驗證失敗，則將 <xref:System.Windows.Forms.DataGridViewCellValidatingEventArgs?displayProperty=fullName> 類別的 <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> 屬性設定為 `true`。  這會讓 <xref:System.Windows.Forms.DataGridView> 控制項防止游標離開儲存格。  在資料列的 <xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A> 屬性中設定一段說明字串。  這會顯示一個具有錯誤圖示的工具提示，其中包含了錯誤說明文字。  在 <xref:System.Windows.Forms.DataGridView.CellEndEdit> 事件處理常式中，將資料列的 <xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A> 屬性設定至該空字串。  只有當儲存格離開編輯模式時，才會發生 <xref:System.Windows.Forms.DataGridView.CellEndEdit> 事件，但是如果儲存格驗證失敗，就無法離開編輯模式。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#20)]  
  
## 測試應用程式  
 您現在可以測試表單以確定它的行為表現如預期般。  
  
#### 若要測試表單  
  
-   編譯及執行應用程式。  
  
     您將看到一個 <xref:System.Windows.Forms.DataGridView>，其中填入了來自 `Customers` 資料表的資料。  當您在 `CompanyName` 資料行的其中一個儲存格按兩下時，您就可以編輯其值。  如果您刪除了所有字元，並且按 TAB 鍵試圖離開儲存格，<xref:System.Windows.Forms.DataGridView> 會阻止您離開儲存格。  在您於儲存格中輸入了非空字串之後，<xref:System.Windows.Forms.DataGridView> 控制項就會讓您離開儲存格。  
  
## 後續步驟  
 這個應用程式讓您對 <xref:System.Windows.Forms.DataGridView> 控制項的功能有了初步的了解。  您可以用許多方式來自訂 <xref:System.Windows.Forms.DataGridView> 控制項的外觀和行為：  
  
-   變更框線和行首樣式。  如需詳細資訊，請參閱 [如何：變更 Windows Form DataGridView 控制項中的框線和格線樣式](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md)。  
  
-   啟用或限制使用者對 <xref:System.Windows.Forms.DataGridView> 控制項的輸入。  如需詳細資訊，請參閱[如何：防止在 Windows Form DataGridView 控制項中新增和刪除資料列](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md)和 [如何：使 Windows Form DataGridView 控制項中的資料行成為唯讀](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)。  
  
-   檢查使用者輸入中的資料庫相關錯誤。  如需詳細資訊，請參閱[逐步解說：處理 Windows Form DataGridView 控制項中的資料輸入期間所發生的錯誤](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md)。  
  
-   在處理大量資料時使用虛擬模式。  如需詳細資訊，請參閱[逐步解說：在 Windows Form DataGridView 控制項中實作虛擬模式](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)。  
  
-   自訂儲存格的外觀。  如需詳細資訊，請參閱 [如何：在 Windows Form DataGridView 控制項中自訂儲存格的外觀](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)和 [如何：設定 Windows Form DataGridView 控制項的字型和色彩樣式](../../../../docs/framework/winforms/controls/how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.BindingSource>   
 [Windows Form DataGridView 控制項中的資料輸入](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)   
 [如何：驗證 Windows Form DataGridView 控制項中的資料](../../../../docs/framework/winforms/controls/how-to-validate-data-in-the-windows-forms-datagridview-control.md)   
 [逐步解說：處理 Windows Form DataGridView 控制項中的資料輸入期間所發生的錯誤](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md)   
 [保護連接資訊](../../../../docs/framework/data/adonet/protecting-connection-information.md)
---
title: "逐步解說：使用兩個 Windows Form DataGridView 控制項建立主要/詳細表單 | Microsoft Docs"
ms.custom: ""
ms.date: "02/15/2017"
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
  - "DataGridView 控制項 [Windows Form], 主從式表單"
  - "主從式清單, 在 Windows Form 上顯示"
  - "父子資料表, 在 Windows Form 上顯示"
  - "逐步解說 [Windows Form], DataGridView 控制項"
ms.assetid: c5fa29e8-47f7-4691-829b-0e697a691f36
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 逐步解說：使用兩個 Windows Form DataGridView 控制項建立主要/詳細表單
使用 <xref:System.Windows.Forms.DataGridView> 控制項時，最常見的一種案例就是*主要\/詳細*表單，這種表單可顯示出兩個資料庫資料表之間的父\/子關聯。  在主要資料表中選取資料列，會使得詳細資料表更新其相對應的子系資料。  
  
 透過 <xref:System.Windows.Forms.DataGridView> 控制項和 <xref:System.Windows.Forms.BindingSource> 元件之間的互動，實作主要\/詳細表單是一件很容易的事。  在本逐步解說中，您會使用兩個 <xref:System.Windows.Forms.DataGridView> 控制項和兩個 <xref:System.Windows.Forms.BindingSource> 元件來建立表單。  表單將顯示在 Northwind SQL Server 範例資料庫中兩個關聯資料表：`Customers` 和 `Orders`。  當您完成時將會擁有一個表單，其中資料庫的所有客戶會顯示在主要的 <xref:System.Windows.Forms.DataGridView>，而特定客戶的所有訂單則會顯示在詳細的 <xref:System.Windows.Forms.DataGridView> 當中。  
  
 若要將此主題中的程式碼複製為一份清單，請參閱 [如何：使用兩個 Windows Form DataGridView 控制項建立主從式表單](../../../../docs/framework/winforms/controls/create-a-master-detail-form-using-two-datagrids.md)。  
  
## 必要條件  
 若要完成這個逐步解說，您必須要有：  
  
-   存取具有 Northwind SQL Server 範例資料庫的伺服器。  
  
## 建立表單  
  
#### 若要建立主要\/詳細表單  
  
1.  建立一個由 <xref:System.Windows.Forms.Form> 所衍生，而且包含兩個 <xref:System.Windows.Forms.DataGridView> 控制項和兩個 <xref:System.Windows.Forms.BindingSource> 元件的類別。  下列的程式碼提供基本的表單初始化，而且包含了一個 `Main` 方法。  如果您使用 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 設計工具來建立表單，則可以用設計工具產生的程式碼來取代下列程式碼，不過請確認您使用了此處變數宣告中所顯示的名稱。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#01](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#01](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#02](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#02](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#02)]  
  
2.  在表單的類別定義中實作一個方法，來處理與資料庫連接的細節。  這個範例使用一個 `GetData` 方法，它會填入一個 <xref:System.Data.DataSet> 物件、在資料集中加入一個 <xref:System.Data.DataRelation> 物件，以及繫結 <xref:System.Windows.Forms.BindingSource> 元件。  請確認有將 `connectionString` 變數設定為您資料庫的適當值。  
  
    > [!IMPORTANT]
    >  在連接字串內儲存機密資訊 \(例如密碼\) 會影響應用程式的安全性。  使用 Windows 驗證 \(也稱為整合式安全性\) 是控制資料庫存取的更安全方式。  如需詳細資訊，請參閱[保護連接資訊](../../../../docs/framework/data/adonet/protecting-connection-information.md)。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#20)]  
  
3.  為表單中將 <xref:System.Windows.Forms.DataGridView> 控制項繫結至 <xref:System.Windows.Forms.BindingSource> 元件的 <xref:System.Windows.Forms.Form.Load> 事件實作一個處理常式，並且呼叫 `GetData` 方法。  下列範例中包含了根據所顯示的資料調整 <xref:System.Windows.Forms.DataGridView> 資料行大小的程式碼。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#10)]  
  
## 測試應用程式  
 您現在可以測試表單以確定它的行為表現如預期般。  
  
#### 若要測試表單  
  
-   編譯及執行應用程式。  
  
     您將看到兩個重疊的 <xref:System.Windows.Forms.DataGridView> 控制項。  位於上方的是來自 Northwind `Customers` 資料表的客戶名稱，而位於下方的則是與上方所選取客戶對應的 `Orders`。  每當您在上方的 <xref:System.Windows.Forms.DataGridView> 中選取不同的資料列，下方 <xref:System.Windows.Forms.DataGridView> 中的內容就會隨之變更。  
  
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
 [在 Windows Form DataGridView 控制項中顯示資料](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)   
 [如何：使用兩個 Windows Form DataGridView 控制項建立主從式表單](../../../../docs/framework/winforms/controls/create-a-master-detail-form-using-two-datagrids.md)   
 [保護連接資訊](../../../../docs/framework/data/adonet/protecting-connection-information.md)
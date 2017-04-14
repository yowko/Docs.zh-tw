---
title: "在 Windows Form DataGridView 控制項中以 Just-In-Time 資料載入方式實作虛擬模式 | Microsoft Docs"
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
  - "資料 [Windows Form], 管理大型資料集"
  - "DataGridView 控制項 [Windows Form], 大型資料集"
  - "DataGridView 控制項 [Windows Form], 虛擬模式"
  - "範例 [Windows Form], Just-in-Time 資料載入"
  - "Just-in-Time 資料載入"
  - "虛擬模式, Just-in-Time 資料載入"
ms.assetid: c2a052b9-423c-4ff7-91dc-d8c7c79345f6
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 在 Windows Form DataGridView 控制項中以 Just-In-Time 資料載入方式實作虛擬模式
在 <xref:System.Windows.Forms.DataGridView> 控制項中實作虛擬模式的理由，就是只在需要時才擷取資料。  這稱為「*Just\-In\-Time 資料載入*」。  
  
 例如，如果您使用的是位於遠端資料庫中非常大型的資料表，則可能會想藉由只擷取顯示所需的資料，以及只在使用者將新資料列捲動至檢視時才擷取其他資料等方法，防止啟動延遲。  如果執行應用程式的用戶端電腦可用來儲存資料的記憶體有限，您可能也會想在從資料庫擷取新的值時捨棄未使用的資料。  
  
 下列章節描述如何以「Just\-In\-Time」快取來使用 <xref:System.Windows.Forms.DataGridView> 控制項。  
  
 若要將此主題中的程式碼複製為一份清單，請參閱 [如何：在 Windows Form DataGridView 控制項中以 Just\-In\-Time 資料載入方式實作虛擬模式](../../../../docs/framework/winforms/controls/virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)。  
  
## 表單  
 下列程式碼範例會定義包含唯讀 <xref:System.Windows.Forms.DataGridView> 控制項的表單，此控制項會透過 <xref:System.Windows.Forms.DataGridView.CellValueNeeded> 事件處理常式與 `Cache` 物件互動。  `Cache` 物件會管理存放在本機上的值，並使用 `DataRetriever` 物件從範例 Northwind 資料庫的 Orders 資料表中擷取值。  `DataRetriever` 物件會實作 `Cache` 類別需要的 `IDataPageRetriever` 介面，同時也用來初始化 <xref:System.Windows.Forms.DataGridView> 控制項資料列和資料行。  
  
 稍後將在此主題中說明 `IDataPageRetriever`、`DataRetriever` 和 `Cache` 型別。  
  
> [!NOTE]
>  在連接字串內儲存機密資訊 \(例如密碼\) 會影響應用程式的安全性。  使用 Windows 驗證 \(也稱為整合式安全性\) 是控制資料庫存取的更安全方式。  如需詳細資訊，請參閱[保護連接資訊](../../../../docs/framework/data/adonet/protecting-connection-information.md)。  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#100)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#100)]  
  
## IDataPageRetriever 介面  
 下列程式碼範例會定義由 `DataRetriever` 類別實作的 `IDataPageRetriever` 介面。  在這個介面中唯一宣告的方法是 `SupplyPageOfData` 方法，此方法需要初始資料列索引和在單一資料頁面中的資料列計數。  這些值是由實作器用來擷取資料來源的資料子集。  
  
 `Cache` 物件會在建構時使用這個介面的實作，以載入資料的兩個初始頁面。  每當需要未快取的值時，快取會捨棄這些頁面中的其中一頁，並要求包含 `IDataPageRetriever` 值的新頁面。  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#201)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#201)]  
  
## DataRetriever 類別  
 下列程式碼範例會定義 `DataRetriever` 類別，此類別會實作 `IDataPageRetriever` 介面，從伺服器擷取資料頁面。  `DataRetriever` 類別也提供 `Columns` 和 `RowCount` 屬性，<xref:System.Windows.Forms.DataGridView> 控制項使用這些屬性來建立必要的資料行，並加入適當數目的空白資料列至 <xref:System.Windows.Forms.DataGridView.Rows%2A> 集合。  加入空白資料列是必須的，如此控制項才能以彷彿包含資料表中所有資料的方式進行運作。  這表示在捲軸中的捲動方塊將會有適當的大小，而使用者也能夠存取資料表中的任何資料列。  資料列只有在捲動入檢視時，才會由 <xref:System.Windows.Forms.DataGridView.CellValueNeeded> 事件處理常式填滿。  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#200)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#200)]  
  
## Cache 類別  
 下列程式碼範例會定義 `Cache` 類別，此類別管理透過 `IDataPageRetriever` 實作所填入的兩個資料頁面。  `Cache` 類別會定義內部 `DataPage` 結構，這個結構包含 <xref:System.Data.DataTable> 會將值儲存於單一的快取頁面，並會計算代表頁面上方與下方界限的資料列索引。  
  
 `Cache` 類別會在建構階段載入兩個資料頁面。  每當 <xref:System.Windows.Forms.DataGridView.CellValueNeeded> 事件需要值時，`Cache` 物件就會決定值是否可以使用於兩個頁面的其中一個，如果是的話，就會傳回該值。  如果在本機上無法使用該值，`Cache` 物件便會決定兩個頁面中的哪個頁面離目前顯示的資料列最遠，然後使用包含要求值的新頁面加以取代，之後就會傳回該值。  
  
 這個模型假設資料頁面中的資料列數目與可以一次顯示於螢幕的資料列數目相同，可以讓使用者對資料表進行分頁，以便有效率地返回最新檢視過的頁面。  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#300)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#300)]  
  
## 其他考量  
 上一個程式碼範例是提供做為「Just\-In\-Time」資料載入的示範。  您需要根據個人需求修改程式碼，以達到最大的效率。  您至少要為快取中每一個資料頁面的資料列數目選擇適當的值。  這個值會傳遞至 `Cache` 建構函式。  每一頁的資料列數目不應該少於可同時顯示於 <xref:System.Windows.Forms.DataGridView> 控制項的資料列數目。  
  
 要得到最佳結果，您需要執行效能測試和可用性測試，以決定系統和使用者的需求。  您需要考慮的幾個因素包括：執行應用程式的用戶端機器上的記憶體容量，使用的網路連接的可用頻寬，以及使用的伺服器的延遲。  頻寬和延遲應該以尖峰用量為準。  
  
 若要改進應用程式的捲動效能，您可以增加在本機上存放的資料量。  不過，若要加快啟動時間，就必須避免一開始時載入太多的資料。  您可能會想修改 `Cache` 類別以增加可以儲存的資料頁面數量。  使用更多資料頁面可以改善捲動效率，但是您會需要依據可用的頻寬和伺服器延遲，來決定資料頁面中理想的資料列數目。  使用較小的頁面，將會增加存取伺服器的次數，但傳回所要求的資料時花費的時間較少。  若延遲的問題比頻寬嚴重，您可能會想使用較大的資料頁面。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>   
 [Windows Form DataGridView 控制項中的效能微調](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)   
 [縮放 Windows Form DataGridView 控制項的最佳作法](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)   
 [Windows Form DataGridView 控制項中的虛擬模式](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)   
 [逐步解說：在 Windows Form DataGridView 控制項中實作虛擬模式](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)   
 [如何：在 Windows Form DataGridView 控制項中以 Just\-In\-Time 資料載入方式實作虛擬模式](../../../../docs/framework/winforms/controls/virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)
---
title: 使用 DataGridView 控制項中的即時資料載入來執行虛擬模式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], just-in-time data loading
- data [Windows Forms], managing large data sets
- DataGridView control [Windows Forms], virtual mode
- just-in-time data loading
- DataGridView control [Windows Forms], large data sets
- virtual mode [Windows Forms], just-in-time data loading
ms.assetid: c2a052b9-423c-4ff7-91dc-d8c7c79345f6
ms.openlocfilehash: 85c6877a9fc6a92752eb039da9d36e34811f8b77
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745063"
---
# <a name="implementing-virtual-mode-with-just-in-time-data-loading-in-the-windows-forms-datagridview-control"></a>在 Windows Form DataGridView 控制項中以 Just-In-Time 資料載入方式實作虛擬模式
在 <xref:System.Windows.Forms.DataGridView> 控制項中實作為虛擬模式的其中一個原因，就是只視需要取得資料。 這就是所謂的即時*資料載入*。  
  
 例如，如果您在遠端資料庫中使用非常大型的資料表，您可能會想要避免啟動延遲，方法是只抓取在使用者將新資料列轉換成視圖時，只需要顯示並取得其他資料的必要資料。 如果執行您應用程式的用戶端電腦的記憶體數量有限，可用於儲存資料，您可能也會想要在從資料庫中抓取新值時，捨棄未使用的資料。  
  
 下列各節說明如何搭配使用 <xref:System.Windows.Forms.DataGridView> 控制項與即時快取。  
  
 若要將本主題中的程式碼複製成單一清單，請參閱 how [to：在 Windows Forms DataGridView 控制項中使用即時資料載入來執行虛擬模式](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)。  
  
## <a name="the-form"></a>表單  
 下列程式碼範例會定義一個表單，其中包含可透過 <xref:System.Windows.Forms.DataGridView.CellValueNeeded> 事件處理常式與 `Cache` 物件互動的唯讀 <xref:System.Windows.Forms.DataGridView> 控制項。 `Cache` 物件會管理本機儲存的值，並使用 `DataRetriever` 物件，從範例 Northwind 資料庫的 Orders 資料表中取出值。 執行 `Cache` 類別所需之 `IDataPageRetriever` 介面的 `DataRetriever` 物件也會用來初始化 <xref:System.Windows.Forms.DataGridView> 控制項的資料列和資料行。  
  
 本主題稍後將說明 `IDataPageRetriever`、`DataRetriever`和 `Cache` 類型。  
  
> [!NOTE]
> 在連接字串內儲存機密資訊 (例如密碼) 會影響應用程式的安全性。 使用 Windows 驗證 (也稱為整合式安全性) 是控制資料庫存取的更安全方式。 如需詳細資訊，請參閱[保護連線資訊](../../data/adonet/protecting-connection-information.md)。  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#100)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#100)]  
  
## <a name="the-idatapageretriever-interface"></a>IDataPageRetriever 介面  
 下列程式碼範例會定義 `IDataPageRetriever` 介面，這是由 `DataRetriever` 類別所執行。 在此介面中宣告的唯一方法是 `SupplyPageOfData` 方法，這需要初始資料列索引，以及單一頁面中的資料列數目計數。 這些值是由實施者用來從資料來源中取出資料的子集。  
  
 `Cache` 物件會在結構中使用此介面的實作為載入兩個初始頁面的資料。 每當需要無快取的值時，快取就會捨棄其中一個頁面，並要求新的頁面，其中包含來自 `IDataPageRetriever`的值。  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#201)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#201)]  
  
## <a name="the-dataretriever-class"></a>DataRetriever 類別  
 下列程式碼範例會定義 `DataRetriever` 類別，它會執行 `IDataPageRetriever` 介面，以從伺服器抓取資料頁面。 `DataRetriever` 類別也會提供 `Columns` 和 `RowCount` 屬性，<xref:System.Windows.Forms.DataGridView> 控制項會使用這些屬性來建立必要的資料行，並將適當數目的空白資料列加入至 <xref:System.Windows.Forms.DataGridView.Rows%2A> 集合。 您必須加入空白資料列，讓控制項的行為就像它包含資料表中的所有資料一樣。 這表示捲軸中的捲動方塊會有適當的大小，而使用者將能夠存取資料表中的任何資料列。 只有當 <xref:System.Windows.Forms.DataGridView.CellValueNeeded> 事件處理常式滾動到 view 時，才會填入這些資料列。  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#200)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#200)]  
  
## <a name="the-cache-class"></a>Cache 類別  
 下列程式碼範例會定義 `Cache` 類別，它會管理兩個透過 `IDataPageRetriever` 執行所填入的資料頁面。 `Cache` 類別會定義內部 `DataPage` 結構，其中包含將值儲存在單一快取頁面中的 <xref:System.Data.DataTable>，並會計算代表頁面上限和下限的資料列索引。  
  
 `Cache` 類別會在結構的時間載入兩頁的資料。 每當 <xref:System.Windows.Forms.DataGridView.CellValueNeeded> 事件要求一個值時，`Cache` 物件就會判斷值是否可用於其中一頁的其中一個，如果是的話，則會傳回它。 如果在本機無法使用此值，則 `Cache` 物件會判斷其兩個頁面中的哪一個與目前顯示的資料列最遠，並以包含所要求值的新頁面取代該頁面，然後再傳回。  
  
 假設資料頁中的資料列數目與可以同時在螢幕上顯示的資料列數目相同，此模型可讓使用者逐頁查看資料表，以有效率地回到最近看到的頁面。  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#300)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#300)]  
  
## <a name="additional-considerations"></a>其他考量  
 先前的程式碼範例是以即時資料載入的示範形式提供。 您必須針對自己的需求修改程式碼，以達到最高效率。 您至少需要針對快取中的每頁數據列數選擇適當的值。 這個值會傳遞至 `Cache` 的函式。 每頁的資料列數目應該小於可以同時顯示在 <xref:System.Windows.Forms.DataGridView> 控制項中的資料列數目。  
  
 為了獲得最佳結果，您必須執行效能測試和可用性測試，以判斷您的系統和使用者的需求。 您需要考慮的幾個因素包括執行應用程式的用戶端電腦中的記憶體數量、使用的網路連線可用頻寬，以及所使用伺服器的延遲。 頻寬和延遲應該取決於尖峰使用量的時間。  
  
 若要改善應用程式的滾動效能，您可以增加儲存在本機的資料量。 不過，若要改善啟動時間，您必須避免一開始載入太多資料。 您可能想要修改 `Cache` 類別，以增加可儲存的資料頁數目。 使用更多資料頁可以改善滾動效率，但是您必須根據可用的頻寬和伺服器延遲，判斷資料頁中的理想資料列數目。 使用較小的頁面，將會更頻繁地存取伺服器，但會花較少的時間來傳回要求的資料。 如果延遲大於頻寬的問題，您可能會想要使用較大的資料頁。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- [Windows Forms DataGridView 控制項中的效能微調](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [縮放 Windows Forms DataGridView 控制項的最佳作法](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView 控制項中的虛擬模式](virtual-mode-in-the-windows-forms-datagridview-control.md)
- [逐步解說：在 Windows Forms DataGridView 控制項中實作虛擬模式](implementing-virtual-mode-wf-datagridview-control.md)
- [操作說明：在 Windows Forms DataGridView 控制項中以 Just-In-Time 資料載入方式實作虛擬模式](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)

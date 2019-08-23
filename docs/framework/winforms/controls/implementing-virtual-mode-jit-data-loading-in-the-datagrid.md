---
title: 在 Windows Form DataGridView 控制項中以 Just-In-Time 資料載入方式實作虛擬模式
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
ms.openlocfilehash: fa40f1657a433f5f4ade3de25648ca04c37dfa67
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962594"
---
# <a name="implementing-virtual-mode-with-just-in-time-data-loading-in-the-windows-forms-datagridview-control"></a>在 Windows Form DataGridView 控制項中以 Just-In-Time 資料載入方式實作虛擬模式
在<xref:System.Windows.Forms.DataGridView>控制項中實作為虛擬模式的其中一個原因, 就是只視需要取得資料。 這就是所謂的即時*資料載入*。  
  
 例如, 如果您在遠端資料庫中使用非常大型的資料表, 您可能會想要避免啟動延遲, 方法是只抓取在使用者將新資料列轉換成視圖時, 只需要顯示並取得其他資料的必要資料。 如果執行您應用程式的用戶端電腦的記憶體數量有限, 可用於儲存資料, 您可能也會想要在從資料庫中抓取新值時, 捨棄未使用的資料。  
  
 下列各節說明如何<xref:System.Windows.Forms.DataGridView>搭配使用控制項與即時快取。  
  
 若要將此主題中的程式碼複製為單一清單，請參閱[如何：使用 Windows Forms DataGridView 控制項](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)中的即時資料載入來執行虛擬模式。  
  
## <a name="the-form"></a>表單  
 下列程式碼範例會定義一個表單, 其中包含<xref:System.Windows.Forms.DataGridView>的唯讀控制項會透過`Cache` <xref:System.Windows.Forms.DataGridView.CellValueNeeded>事件處理常式與物件互動。 物件會管理本機儲存的值, 並`DataRetriever`使用物件來抓取範例 Northwind 資料庫之 Orders 資料表的值。 `Cache` 物件 (其會`Cache`執行類別`IDataPageRetriever`所需的介面) 也會用來初始化控制項的<xref:System.Windows.Forms.DataGridView>資料列和資料行。 `DataRetriever`  
  
 本主題`DataRetriever`稍後將`Cache`說明、和類型。`IDataPageRetriever`  
  
> [!NOTE]
> 在連接字串內儲存機密資訊 (例如密碼) 會影響應用程式的安全性。 使用 Windows 驗證 (也稱為整合式安全性) 是控制資料庫存取的更安全方式。 如需詳細資訊，請參閱[保護連線資訊](../../data/adonet/protecting-connection-information.md)。  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#100)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#100)]  
  
## <a name="the-idatapageretriever-interface"></a>IDataPageRetriever 介面  
 下列程式碼範例會定義`IDataPageRetriever`介面, 它是`DataRetriever`由類別所實作為。 在此介面中宣告的唯一方法是`SupplyPageOfData`方法, 它需要初始資料列索引, 以及單一頁面中的資料列數目計數。 這些值是由實施者用來從資料來源中取出資料的子集。  
  
 在結構中,物件會使用此介面的實作為載入兩頁的初始資料。`Cache` 每當需要未快取的值時, 快取會捨棄其中一個頁面, 並要求新的頁面, 其中`IDataPageRetriever`包含的值。  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#201)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#201)]  
  
## <a name="the-dataretriever-class"></a>DataRetriever 類別  
 下列程式碼範例會定義`DataRetriever`類別, 它`IDataPageRetriever`會執行介面, 以從伺服器抓取資料頁面。 `Columns` 類別也`RowCount`會提供<xref:System.Windows.Forms.DataGridView>和屬性, 控制項會使用這些屬性來建立必要的資料行<xref:System.Windows.Forms.DataGridView.Rows%2A> , 並將適當數目的空白資料列加入至集合。 `DataRetriever` 您必須加入空白資料列, 讓控制項的行為就像它包含資料表中的所有資料一樣。 這表示捲軸中的捲動方塊會有適當的大小, 而使用者將能夠存取資料表中的任何資料列。 只有當<xref:System.Windows.Forms.DataGridView.CellValueNeeded>事件處理常式滾動到 view 時, 才會填入這些資料列。  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#200)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#200)]  
  
## <a name="the-cache-class"></a>Cache 類別  
 下列程式碼範例會定義`Cache`類別, 它會管理兩個`IDataPageRetriever`透過執行填入的資料頁面。 類別會定義內部`DataPage` <xref:System.Data.DataTable>結構, 其中包含將值儲存在單一快取頁面中的, 並會計算代表頁面上限和下限的資料列索引。 `Cache`  
  
 `Cache`類別會在結構的時間載入兩頁的資料。 每當事件要求一個值時`Cache` , 物件就會判斷值是否可用於其兩頁的其中一個, 如果是的話, 則會傳回它。 <xref:System.Windows.Forms.DataGridView.CellValueNeeded> 如果在本機無法使用此值, `Cache`物件會判斷其兩個頁面的哪一個與目前顯示的資料列最遠, 並以包含所要求值的新頁面取代該頁面, 然後再傳回此值。  
  
 假設資料頁中的資料列數目與可以同時在螢幕上顯示的資料列數目相同, 此模型可讓使用者逐頁查看資料表, 以有效率地回到最近看到的頁面。  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#300)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#300)]  
  
## <a name="additional-considerations"></a>其他考量  
 先前的程式碼範例是以即時資料載入的示範形式提供。 您必須針對自己的需求修改程式碼, 以達到最高效率。 您至少需要針對快取中的每頁數據列數選擇適當的值。 這個值會傳遞至`Cache`函式。 每頁的資料列數目應該小於<xref:System.Windows.Forms.DataGridView>控制項中可以同時顯示的資料列數目。  
  
 為了獲得最佳結果, 您必須執行效能測試和可用性測試, 以判斷您的系統和使用者的需求。 您需要考慮的幾個因素包括執行應用程式的用戶端電腦中的記憶體數量、使用的網路連線可用頻寬, 以及所使用伺服器的延遲。 頻寬和延遲應該取決於尖峰使用量的時間。  
  
 若要改善應用程式的滾動效能, 您可以增加儲存在本機的資料量。 不過, 若要改善啟動時間, 您必須避免一開始載入太多資料。 您可能想要修改`Cache`類別, 以增加可儲存的資料頁數目。 使用更多資料頁可以改善滾動效率, 但是您必須根據可用的頻寬和伺服器延遲, 判斷資料頁中的理想資料列數目。 使用較小的頁面, 將會更頻繁地存取伺服器, 但會花較少的時間來傳回要求的資料。 如果延遲大於頻寬的問題, 您可能會想要使用較大的資料頁。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- [Windows Forms DataGridView 控制項中的效能微調](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [縮放 Windows Forms DataGridView 控制項的最佳作法](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView 控制項中的虛擬模式](virtual-mode-in-the-windows-forms-datagridview-control.md)
- [逐步解說：在 Windows Forms DataGridView 控制項中執行虛擬模式](implementing-virtual-mode-wf-datagridview-control.md)
- [如何：使用 Windows Forms DataGridView 控制項中的即時資料載入來執行虛擬模式](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)

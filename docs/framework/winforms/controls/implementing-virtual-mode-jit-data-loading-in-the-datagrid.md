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
ms.openlocfilehash: 641db19cc6493a20c9f9a34622f466e3623c32ad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973819"
---
# <a name="implementing-virtual-mode-with-just-in-time-data-loading-in-the-windows-forms-datagridview-control"></a>在 Windows Form DataGridView 控制項中以 Just-In-Time 資料載入方式實作虛擬模式
若要實作虛擬模式中的其中一個原因<xref:System.Windows.Forms.DataGridView>控制項是只有在需要時擷取資料。 這就叫做 *-just-in-time 資料載入*。  
  
 如果您正在使用中遠端資料庫的非常大型資料表，比方說，您可以擷取只顯示所需的資料，並擷取其他資料，使用者將新的資料列捲動至檢視時，才避免啟動延遲。 如果執行您的應用程式的用戶端電腦數量有限的記憶體可用來儲存資料，您也可以從資料庫擷取新的值時，捨棄未使用的資料。  
  
 下列各節說明如何使用<xref:System.Windows.Forms.DataGridView>中即時快取的控制項。  
  
 若要將此主題中的程式碼複製為單一清單，請參閱[如何：實作虛擬模式，以在 Just-in-time 資料載入，在 Windows Form DataGridView 控制項](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)。  
  
## <a name="the-form"></a>表單  
 下列程式碼範例會定義包含唯讀的表單<xref:System.Windows.Forms.DataGridView>互動的控制項`Cache`物件傳遞<xref:System.Windows.Forms.DataGridView.CellValueNeeded>事件處理常式。 `Cache`物件管理的本機儲存的值，並且使用`DataRetriever`從 Northwind 範例資料庫的 「 訂單 」 資料表中擷取值的物件。 `DataRetriever`物件，它會實作`IDataPageRetriever`介面所需`Cache`類別中，也會用來初始化<xref:System.Windows.Forms.DataGridView>控制資料列和資料行。  
  
 `IDataPageRetriever`， `DataRetriever`，和`Cache`類型會在本主題稍後所述。  
  
> [!NOTE]
>  在連接字串內儲存機密資訊 (例如密碼) 會影響應用程式的安全性。 使用 Windows 驗證 (也稱為整合式安全性) 是控制資料庫存取的更安全方式。 如需詳細資訊，請參閱[保護連線資訊](../../data/adonet/protecting-connection-information.md)。  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#100)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#100)]  
  
## <a name="the-idatapageretriever-interface"></a>IDataPageRetriever 介面  
 下列程式碼範例會定義`IDataPageRetriever`介面，藉由`DataRetriever`類別。 在此介面中宣告的唯一方法是`SupplyPageOfData`方法，而這需要初始資料列索引和資料的單一頁面中的資料列數目的計數。 實作器會使用這些值，從資料來源擷取資料的子集。  
  
 A`Cache`物件會使用此介面的實作，在建構期間載入的資料的兩個初始頁面。 每當需要取消快取的值時，快取捨棄其中一個頁面，並要求新的頁面包含的值從`IDataPageRetriever`。  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#201)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#201)]  
  
## <a name="the-dataretriever-class"></a>DataRetriever 類別  
 下列程式碼範例會定義`DataRetriever`類別，它會實作`IDataPageRetriever`介面，以從伺服器擷取資料的頁面。 `DataRetriever`類別也會提供`Columns`並`RowCount`屬性，其中<xref:System.Windows.Forms.DataGridView>控制項會用來建立必要的資料行，以及加入空的資料列的適當數目<xref:System.Windows.Forms.DataGridView.Rows%2A>集合。 加入空的資料列是必要的因此，控制項的行為模式，如同它包含在資料表中的所有資料。 這表示捲軸的捲動方塊會有適當的大小，而且使用者將能夠存取資料表中的任何資料列。 資料列，以填滿<xref:System.Windows.Forms.DataGridView.CellValueNeeded>它們捲動檢視時，才的事件處理常式。  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#200)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#200)]  
  
## <a name="the-cache-class"></a>快取類別  
 下列程式碼範例會定義`Cache`類別，用來管理兩個頁面的資料填入透過`IDataPageRetriever`實作。 `Cache`類別會定義內部`DataPage`結構，其中包含<xref:System.Data.DataTable>將值儲存在單一快取頁面，並計算資料列編製索引，表示頁面的上限和下限之間。  
  
 `Cache`類別會在建構階段中載入資料的兩個頁面。 每當<xref:System.Windows.Forms.DataGridView.CellValueNeeded>事件要求的值，`Cache`物件會判斷如果值為用於其兩個的其中一個頁面，如果是的話，就會傳回。 如果值不在本機上，`Cache`物件判斷這兩個頁面的距離最遠的目前顯示的資料列和頁面取代為新的資源，包含要求的值，然後它會傳回。  
  
 假設資料頁面中的資料列數目是可以一次顯示在畫面的資料列數目相同，此模型可讓使用者逐頁查看資料表，以有效率地返回最近檢視的網頁。  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#300)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#300)]  
  
## <a name="additional-considerations"></a>其他考量  
 先前的程式碼範例提供以 just-in-time 資料載入的示範。 您必須修改您自己的需求，以達到最高效率的程式碼。 最小值，您必須選擇快取中的每一頁的資料列數目的適當值。 這個值會傳遞至`Cache`建構函式。 每個頁面的資料列數目應該是不大於或等於可以同時在顯示的資料列數目您<xref:System.Windows.Forms.DataGridView>控制項。  
  
 為了獲得最佳結果，您必須進行效能測試或可用性測試，以判斷您的系統和使用者的需求。 您必須納入考量的幾個因素會包含執行您的應用程式、 網路使用的連接，可用的頻寬和延遲所使用的伺服器的用戶端機器的記憶體數量。 頻寬和延遲應該判斷有時的尖峰使用量。  
  
 若要改善您的應用程式的捲動效能，您可以增加本機儲存的資料的量。 若要改善啟動時間，不過，您必須避免一開始載入太多資料。 您可能想要修改`Cache`類別，以增加它可以儲存的資料頁數。 使用多個資料頁，可以改善捲動的效率，但您必須決定根據可用的頻寬和伺服器延遲而定，資料頁中的資料列的理想數目。 使用較小的頁面中，伺服器將會更頻繁地存取，但需要較少的時間才能傳回要求的資料。 如果延遲是多個比頻寬的問題，您可能想要使用較大的資料頁。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- [Windows Forms DataGridView 控制項中的效能微調](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [縮放 Windows Forms DataGridView 控制項的最佳作法](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView 控制項中的虛擬模式](virtual-mode-in-the-windows-forms-datagridview-control.md)
- [逐步解說：在 Windows Form DataGridView 控制項中實作虛擬模式](implementing-virtual-mode-wf-datagridview-control.md)
- [如何：Windows Form DataGridView 控制項中實作虛擬模式，以在 Just-in-time 資料載入](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)

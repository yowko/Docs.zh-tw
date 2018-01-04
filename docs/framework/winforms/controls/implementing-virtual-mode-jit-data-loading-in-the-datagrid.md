---
title: "在 Windows Form DataGridView 控制項中以 Just-In-Time 資料載入方式實作虛擬模式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2a830c11e8df73b71f16c1b9dfd1007461d910f5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-virtual-mode-with-just-in-time-data-loading-in-the-windows-forms-datagridview-control"></a>在 Windows Form DataGridView 控制項中以 Just-In-Time 資料載入方式實作虛擬模式
若要實作中的虛擬模式的其中一個原因<xref:System.Windows.Forms.DataGridView>控制項是只有在需要時才擷取資料。 這稱為*以 just-in-time 資料載入*。  
  
 如果您正在使用遠端資料庫中的極大型資料表，比方說，您可以擷取顯示所需的資料並擷取其他資料，只有當使用者將新的資料列捲動至檢視時，防止啟動延遲。 如果執行您的應用程式的用戶端電腦具有有限的記憶體可用來儲存資料，您也可以從資料庫擷取新的值時，請捨棄未使用的資料。  
  
 下列章節說明如何使用<xref:System.Windows.Forms.DataGridView>中 just-in-time 快取的控制項。  
  
 若要為單一列出本主題中複製的程式碼，請參閱[How to： 以 Just-In-Time 資料載入 Windows Form DataGridView 控制項中實作虛擬模式](../../../../docs/framework/winforms/controls/virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)。  
  
## <a name="the-form"></a>表單  
 下列程式碼範例定義包含一個唯讀表單<xref:System.Windows.Forms.DataGridView>互動的控制項`Cache`物件透過<xref:System.Windows.Forms.DataGridView.CellValueNeeded>事件處理常式。 `Cache`物件管理的本機儲存的值，並使用`DataRetriever`從 Northwind 範例資料庫的 「 訂單 」 資料表擷取值的物件。 `DataRetriever`物件，它會實作`IDataPageRetriever`所需的介面`Cache`類別，也會用來初始化<xref:System.Windows.Forms.DataGridView>控制資料列和資料行。  
  
 `IDataPageRetriever`， `DataRetriever`，和`Cache`類型在本主題稍後描述。  
  
> [!NOTE]
>  在連接字串內儲存機密資訊 (例如密碼) 會影響應用程式的安全性。 使用 Windows 驗證 (也稱為整合式安全性) 是控制資料庫存取的更安全方式。 如需詳細資訊，請參閱[保護連線資訊](../../../../docs/framework/data/adonet/protecting-connection-information.md)。  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#100)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#100)]  
  
## <a name="the-idatapageretriever-interface"></a>IDataPageRetriever 介面  
 下列程式碼範例會定義`IDataPageRetriever`介面實作的`DataRetriever`類別。 在此介面中宣告的唯一方法是`SupplyPageOfData`方法，需要初始資料列索引，以及在單一頁面中的資料列數。 實作器會使用這些值來從資料來源擷取資料的子集。  
  
 A`Cache`物件會使用此介面的實作，在建構期間載入的資料的兩個初始頁面。 每次需要未快取的值時，快取會捨棄這些網頁的其中一個，並要求新的頁面包含的值從`IDataPageRetriever`。  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#201)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#201)]  
  
## <a name="the-dataretriever-class"></a>DataRetriever 類別  
 下列程式碼範例會定義`DataRetriever`類別，它會實作`IDataPageRetriever`介面，以從伺服器擷取資料的頁面。 `DataRetriever`類別也提供`Columns`和`RowCount`屬性，其中<xref:System.Windows.Forms.DataGridView>控制項使用建立必要的資料行，以及加入空的資料列的適當數目<xref:System.Windows.Forms.DataGridView.Rows%2A>集合。 使控制項的行為模式，就好像它包含資料表中的所有資料，加入空白資料列是必要的。 這表示在捲軸的捲動方塊會有適當的大小，而且使用者將能夠存取資料表中的任何資料列。 資料列，以填滿<xref:System.Windows.Forms.DataGridView.CellValueNeeded>它們捲動檢視時，才的事件處理常式。  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#200)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#200)]  
  
## <a name="the-cache-class"></a>快取類別  
 下列程式碼範例會定義`Cache`類別，可管理的資料填入透過兩個頁面`IDataPageRetriever`實作。 `Cache`類別定義內部`DataPage`結構，其中包含<xref:System.Data.DataTable>將值儲存在單一快取中頁面的計算資料列索引代表頁面的上下邊界。  
  
 `Cache`類別會在建構階段中載入資料的兩個頁面。 每當<xref:System.Windows.Forms.DataGridView.CellValueNeeded>事件要求值，`Cache`物件判斷的值是用於其兩個的其中一個頁面，如果是的話，就會傳回物件。 如果值不在本機上，`Cache`物件可以決定其兩個頁面的距離目前顯示的資料列的最遠以及取代包含要求的值，然後傳回新的頁面。  
  
 假設資料頁面中的資料列數目是可以同時顯示在畫面的資料列數目相同，此模型可讓使用者透過資料表分頁有效率地返回最近檢視過的頁面。  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#300)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#300)]  
  
## <a name="additional-considerations"></a>其他考量  
 先前的程式碼範例會提供以 just-in-time 資料載入的示範。 您必須修改您自己的需求，以達到最大效率的程式碼。 最小值，您必須選擇快取中的每個分頁的資料列數目為適當值。 這個值會傳遞至`Cache`建構函式。 每個分頁的資料列數目應該是不小於可以同時在顯示的資料列數目您<xref:System.Windows.Forms.DataGridView>控制項。  
  
 為獲得最佳結果，您必須執行效能測試和可用性測試，以判斷您的系統和使用者的需求。 必須納入考量的幾個因素會併入執行您的應用程式、 使用的網路連線可用的頻寬和延遲使用之伺服器的用戶端機器中的記憶體數量。 頻寬和延遲應該決定有時候的尖峰使用量。  
  
 若要改善您的應用程式的捲動效能，您可以增加在本機儲存的資料量。 若要改善啟動時間，不過，您必須避免一開始載入太多資料。 您可能想要修改`Cache`類別以增加它可以儲存的資料頁數。 使用更多資料頁面，可以改善捲動效率，但是您必須判斷理想數目，視可用頻寬和伺服器延遲而定，資料頁中的資料列。 與較小的頁面，將更頻繁地存取伺服器，但需要較少的時間才能傳回要求的資料。 如果延遲過高的問題比頻寬，您可能想要使用較大的資料頁。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 [Windows Forms DataGridView 控制項中的效能微調](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 [縮放 Windows Forms DataGridView 控制項的最佳作法](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView 控制項中的虛擬模式](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)  
 [逐步解說：在 Windows Forms DataGridView 控制項中實作虛擬模式](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)  
 [操作說明：在 Windows Forms DataGridView 控制項中以 Just-In-Time 資料載入方式實作虛擬模式](../../../../docs/framework/winforms/controls/virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)

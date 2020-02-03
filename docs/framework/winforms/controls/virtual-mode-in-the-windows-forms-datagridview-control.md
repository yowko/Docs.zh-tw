---
title: DataGridView 控制項中的虛擬模式
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], virtual mode
ms.assetid: feae5d43-2848-4b1a-8ea7-77085dc415b5
ms.openlocfilehash: 0d82f0fc9946e5b61ea171f2f5d2ab5690db0c71
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745440"
---
# <a name="virtual-mode-in-the-windows-forms-datagridview-control"></a>Windows Form DataGridView 控制項中的虛擬模式
使用虛擬模式，您可以管理 <xref:System.Windows.Forms.DataGridView> 控制項與自訂資料快取之間的互動。 若要執行虛擬模式，請將 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> 屬性設定為 `true` 並處理本主題中所述的一或多個事件。 您通常至少會處理 `CellValueNeeded` 事件，讓控制項查閱資料快取中的值。  
  
## <a name="bound-mode-and-virtual-mode"></a>系結模式和虛擬模式  
 只有當您需要補充或取代系結模式時，才需要虛擬模式。 在 [系結] 模式中，您可以設定 [<xref:System.Windows.Forms.DataGridView.DataSource%2A>] 屬性，而控制項會自動從指定的來源載入資料，並將使用者的變更提交給它。 您可以控制要顯示的系結資料行，而資料來源本身通常會處理排序之類的作業。  
  
## <a name="supplementing-bound-mode"></a>補充系結模式  
 您可以顯示未系結的資料行以及系結的資料行，以補充系結模式。 這有時稱為「混合模式」，可用於顯示計算值或使用者介面（UI）控制項這類專案。  
  
 由於未系結的資料行是在資料來源之外，因此資料來源的排序作業會忽略它們。 因此，當您在混合模式中啟用排序時，您必須在本機快取中管理未系結的資料，並執行虛擬模式，讓 <xref:System.Windows.Forms.DataGridView> 控制項與它互動。  
  
 如需使用虛擬模式來維護未系結資料行中之值的詳細資訊，請參閱 <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A?displayProperty=nameWithType> 屬性和 <xref:System.Windows.Forms.DataGridViewComboBoxColumn?displayProperty=nameWithType> 類別參考主題中的範例。  
  
## <a name="replacing-bound-mode"></a>取代系結模式  
 如果系結模式不符合您的效能需求，您可以透過虛擬模式事件處理常式，管理自訂快取中的所有資料。 例如，您可以使用虛擬模式來執行即時資料載入機制，只從網路資料庫中取出最多的資料，以達到最佳效能。 當您透過慢速網路連線來處理大量資料，或使用 RAM 或儲存空間數量有限的用戶端電腦時，此案例特別有用。  
  
 如需在即時案例中使用虛擬模式的詳細資訊，請參閱[在 Windows Forms DataGridView 控制項中，使用即時資料載入來執行虛擬模式](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)。  
  
## <a name="virtual-mode-events"></a>虛擬模式事件  
 如果您的資料是唯讀的，則 `CellValueNeeded` 事件可能是您必須處理的唯一事件。 其他虛擬模式事件可讓您啟用特定功能，例如使用者編輯、資料列新增和刪除，以及資料列層級交易。  
  
 某些標準 <xref:System.Windows.Forms.DataGridView> 事件（例如當使用者加入或刪除資料列時，或是在編輯、剖析、驗證或格式化儲存格值時所發生的事件）也適用于虛擬模式。 您也可以處理事件，讓您維護通常不會儲存在系結資料來源中的值，例如儲存格工具提示文字、儲存格和資料列錯誤文字、資料格和資料列快捷方式功能表資料，以及資料列高度資料。  
  
 如需如何使用資料列層級認可範圍來執行虛擬模式來管理讀取/寫入資料的詳細資訊，請參閱[逐步解說：在 Windows Forms DataGridView 控制項中執行虛擬模式](implementing-virtual-mode-wf-datagridview-control.md)。  
  
 如需使用資料格層級認可範圍來執行虛擬模式的範例，請參閱 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> 屬性參考主題。  
  
 只有當 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> 屬性設定為 `true`時，才會發生下列事件。  
  
|事件|描述|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.DataGridView.CellValueNeeded>|由控制項用來抓取資料快取中的儲存格值，以供顯示。 只有未系結資料行中的儲存格才會發生這個事件。|  
|<xref:System.Windows.Forms.DataGridView.CellValuePushed>|由控制項用來將儲存格的使用者輸入認可至資料快取。 只有未系結資料行中的儲存格才會發生這個事件。<br /><br /> 在 <xref:System.Windows.Forms.DataGridView.CellValuePushed> 事件處理常式之外變更快取的值，以確保目前的值會顯示在控制項中，並套用目前作用中的任何自動調整大小模式時，請呼叫 <xref:System.Windows.Forms.DataGridView.UpdateCellValue%2A> 方法。|  
|<xref:System.Windows.Forms.DataGridView.NewRowNeeded>|由控制項用來表示需要資料快取中的新資料列。|  
|<xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>|由控制項用來判斷資料列是否有任何未認可的變更。|  
|<xref:System.Windows.Forms.DataGridView.CancelRowEdit>|由控制項用來指出資料列應該還原為其快取的值。|  
  
 下列事件在虛擬模式中很有用，但不論 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> 屬性設定為何，都可以使用。  
  
|事件|描述|  
|------------|-----------------|  
|<xref:System.Windows.Forms.DataGridView.UserDeletingRow><br /><br /> <xref:System.Windows.Forms.DataGridView.UserDeletedRow><br /><br /> <xref:System.Windows.Forms.DataGridView.RowsRemoved><br /><br /> <xref:System.Windows.Forms.DataGridView.RowsAdded>|由控制項用來表示刪除或加入資料列的時間，讓您據以更新資料快取。|  
|<xref:System.Windows.Forms.DataGridView.CellFormatting><br /><br /> <xref:System.Windows.Forms.DataGridView.CellParsing><br /><br /> <xref:System.Windows.Forms.DataGridView.CellValidating><br /><br /> <xref:System.Windows.Forms.DataGridView.CellValidated><br /><br /> <xref:System.Windows.Forms.DataGridView.RowValidating><br /><br /> <xref:System.Windows.Forms.DataGridView.RowValidated>|由控制項用來格式化要顯示的資料格值，以及用來剖析和驗證使用者輸入。|  
|<xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded>|當設定 <xref:System.Windows.Forms.DataGridView.DataSource%2A> 屬性或 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> 屬性 `true`時，由控制項用來抓取資料格工具提示文字。<br /><br /> 只有在 `true`<xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> 屬性值時，才會顯示資料格工具提示。|  
|<xref:System.Windows.Forms.DataGridView.CellErrorTextNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowErrorTextNeeded>|當設定 <xref:System.Windows.Forms.DataGridView.DataSource%2A> 屬性或 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> 屬性 `true`時，由控制項用來抓取資料格或資料列錯誤文字。<br /><br /> 當您變更資料格或資料列錯誤文字時，請呼叫 <xref:System.Windows.Forms.DataGridView.UpdateCellErrorText%2A> 方法或 <xref:System.Windows.Forms.DataGridView.UpdateRowErrorText%2A> 方法，以確保目前的值會顯示在控制項中。<br /><br /> `true`[<xref:System.Windows.Forms.DataGridView.ShowCellErrors%2A>] 和 [<xref:System.Windows.Forms.DataGridView.ShowRowErrors%2A>] 屬性值時，會顯示儲存格和資料列錯誤圖像。|  
|<xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowContextMenuStripNeeded>|當控制項 <xref:System.Windows.Forms.DataGridView.DataSource%2A> 屬性已設定，或 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> 屬性 `true`時，由控制項用來抓取儲存格或資料列 <xref:System.Windows.Forms.ContextMenuStrip>。|  
|<xref:System.Windows.Forms.DataGridView.RowHeightInfoNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowHeightInfoPushed>|由控制項用來抓取或儲存資料快取中的資料列高度資訊。 在 <xref:System.Windows.Forms.DataGridView.RowHeightInfoPushed> 事件處理常式之外變更快取的資料列高度資訊時，請呼叫 <xref:System.Windows.Forms.DataGridView.UpdateRowHeightInfo%2A> 方法，以確保在控制項的顯示中使用目前的值。|  
  
## <a name="best-practices-in-virtual-mode"></a>虛擬模式中的最佳作法  
 如果您要執行虛擬模式以有效率地處理大量資料，您也會想要確保您能以 <xref:System.Windows.Forms.DataGridView> 控制項本身有效率地工作。 如需有效率地使用儲存格樣式、自動調整大小、選取和資料列共用的詳細資訊，請參閱[縮放 Windows Forms DataGridView 控制項的最佳做法](best-practices-for-scaling-the-windows-forms-datagridview-control.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- [Windows Forms DataGridView 控制項中的效能微調](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [縮放 Windows Forms DataGridView 控制項的最佳作法](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [逐步解說：在 Windows Forms DataGridView 控制項中實作虛擬模式](implementing-virtual-mode-wf-datagridview-control.md)
- [在 Windows Forms DataGridView 控制項中以 Just-In-Time 資料載入方式實作虛擬模式](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)

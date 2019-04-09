---
title: Windows Form DataGridView 控制項中的虛擬模式
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], virtual mode
ms.assetid: feae5d43-2848-4b1a-8ea7-77085dc415b5
ms.openlocfilehash: f284835578221ad1fe859f260e37bb829cd64b2d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59124718"
---
# <a name="virtual-mode-in-the-windows-forms-datagridview-control"></a>Windows Form DataGridView 控制項中的虛擬模式
虛擬模式中，您可以管理之間的互動<xref:System.Windows.Forms.DataGridView>控制項和自訂資料快取。 若要實作虛擬模式，設定<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>屬性設`true`並處理一或多個本主題中所述的事件。 您通常會處理至少`CellValueNeeded`事件，可讓控制項外觀的資料快取中的值。  
  
## <a name="bound-mode-and-virtual-mode"></a>繫結的模式和虛擬模式  
 只有當您需要以補充或取代繫結的模式時，才必須虛擬模式。 在繫結模式中，您將設定<xref:System.Windows.Forms.DataGridView.DataSource%2A>屬性和控制項自動從指定的來源載入資料，並提交使用者變更傳回給它。 您可以控制顯示哪些的繫結的資料行，以及資料來源本身通常會處理作業，例如排序。  
  
## <a name="supplementing-bound-mode"></a>補充繫結的模式  
 您可以顯示未繫結的資料行，以及繫結的資料行，以補充繫結的模式。 這有時候稱為 「 混合的模式 」，而且是適用於顯示一些作業，例如導出的值或使用者介面 (UI) 控制項。  
  
 未繫結的資料行是外部資料來源，因為它們會忽略資料來源的排序作業。 因此，當您啟用混合模式中的排序，您必須管理在本機快取未繫結的資料，並實作虛擬模式，讓<xref:System.Windows.Forms.DataGridView>控制項與它互動。  
  
 如需使用虛擬模式來維護未繫結的資料行中值的詳細資訊，請參閱中的範例<xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A?displayProperty=nameWithType>屬性和<xref:System.Windows.Forms.DataGridViewComboBoxColumn?displayProperty=nameWithType>類別參考主題。  
  
## <a name="replacing-bound-mode"></a>取代繫結的模式  
 如果繫結的模式不符合您效能需求，您可以管理您透過虛擬模式事件處理常式的自訂快取中的所有資料。 例如，您可以使用虛擬模式來實作以 just-in-time 資料載入機制，只會擷取的資料量從網路上的資料庫，才能獲得最佳效能。 使用大量的資料，透過低速網路連線或使用的 RAM 或儲存體空間數量有限的用戶端電腦時，此案例中會特別有用。  
  
 如需使用虛擬模式中以 just-in-time 案例的詳細資訊，請參閱[以 Just-In-Time 資料載入 Windows Forms DataGridView 控制項中實作虛擬模式](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)。  
  
## <a name="virtual-mode-events"></a>虛擬模式事件  
 如果您的資料是唯讀的`CellValueNeeded`事件可能是您要處理的唯一事件。 其他的虛擬模式事件可讓您啟用特定功能，例如使用者編輯、 資料列新增與刪除，以及資料列層級的交易。  
  
 某些標準<xref:System.Windows.Forms.DataGridView>事件 （例如使用者加入或刪除資料列，或當儲存格的值時，會發生的事件是編輯、 剖析、 驗證，或格式化） 可讓虛擬模式中。 您也可以處理事件，讓您維護通常不會儲存在繫結的資料來源，例如資料格工具提示文字、 資料格和資料列的錯誤文字、 資料格和資料列快顯功能表資料，以及資料列高度的值。  
  
 如需有關如何實作虛擬模式，來管理具有認可資料列層級範圍的讀取/寫入資料的詳細資訊，請參閱[逐步解說：實作虛擬模式中的 Windows Form DataGridView 控制項](implementing-virtual-mode-wf-datagridview-control.md)。  
  
 如需實作虛擬模式，以認可資料格層級範圍的範例，請參閱<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>屬性參考主題。  
  
 只會發生下列事件時<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>屬性設定為`true`。  
  
|Event - 事件|描述|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.DataGridView.CellValueNeeded>|使用控制項來擷取顯示的資料快取中的資料格的值。 僅針對未繫結的資料行中的資料格，就會發生此事件。|  
|<xref:System.Windows.Forms.DataGridView.CellValuePushed>|使用控制項來認可至資料快取的資料格的使用者輸入。 僅針對未繫結的資料行中的資料格，就會發生此事件。<br /><br /> 呼叫<xref:System.Windows.Forms.DataGridView.UpdateCellValue%2A>方法，當變更快取的值之外的<xref:System.Windows.Forms.DataGridView.CellValuePushed>事件處理常式，以確保目前的值會顯示在控制項，並套用任何目前作用中的自動調整大小模式。|  
|<xref:System.Windows.Forms.DataGridView.NewRowNeeded>|使用控制項來表示資料快取中的新資料列的需求。|  
|<xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>|使用控制項來判斷資料列是否有任何未認可的變更。|  
|<xref:System.Windows.Forms.DataGridView.CancelRowEdit>|使用控制項來表示資料列應該還原成其快取的值。|  
  
 下列事件可用於虛擬模式中，但可用不論<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>屬性設定。  
  
|事件|描述|  
|------------|-----------------|  
|<xref:System.Windows.Forms.DataGridView.UserDeletingRow><br /><br /> <xref:System.Windows.Forms.DataGridView.UserDeletedRow><br /><br /> <xref:System.Windows.Forms.DataGridView.RowsRemoved><br /><br /> <xref:System.Windows.Forms.DataGridView.RowsAdded>|使用控制項來指出當資料列遭到刪除，或新增時，讓您據以更新的資料快取。|  
|<xref:System.Windows.Forms.DataGridView.CellFormatting><br /><br /> <xref:System.Windows.Forms.DataGridView.CellParsing><br /><br /> <xref:System.Windows.Forms.DataGridView.CellValidating><br /><br /> <xref:System.Windows.Forms.DataGridView.CellValidated><br /><br /> <xref:System.Windows.Forms.DataGridView.RowValidating><br /><br /> <xref:System.Windows.Forms.DataGridView.RowValidated>|使用格式儲存格的值來控制顯示和剖析及驗證使用者輸入。|  
|<xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded>|控制項用於擷取資料格工具提示文字時<xref:System.Windows.Forms.DataGridView.DataSource%2A>屬性設定為<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>屬性是`true`。<br /><br /> 資料格工具提示會顯示時，才<xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A>屬性值是`true`。|  
|<xref:System.Windows.Forms.DataGridView.CellErrorTextNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowErrorTextNeeded>|控制項用來擷取儲存格或資料列的錯誤文字時<xref:System.Windows.Forms.DataGridView.DataSource%2A>屬性設定或<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>屬性是`true`。<br /><br /> 呼叫<xref:System.Windows.Forms.DataGridView.UpdateCellErrorText%2A>方法或<xref:System.Windows.Forms.DataGridView.UpdateRowErrorText%2A>當您變更資料列的錯誤文字以確保目前的值會顯示在控制項中的方法。<br /><br /> 儲存格和資料列錯誤圖像 （glyph） 會顯示當<xref:System.Windows.Forms.DataGridView.ShowCellErrors%2A>並<xref:System.Windows.Forms.DataGridView.ShowRowErrors%2A>屬性的值為`true`。|  
|<xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowContextMenuStripNeeded>|控制項用來擷取儲存格或資料列<xref:System.Windows.Forms.ContextMenuStrip>時控制項<xref:System.Windows.Forms.DataGridView.DataSource%2A>屬性設定為<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>屬性是`true`。|  
|<xref:System.Windows.Forms.DataGridView.RowHeightInfoNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowHeightInfoPushed>|使用控制項來擷取或儲存在資料快取中的資料列高度資訊。 呼叫<xref:System.Windows.Forms.DataGridView.UpdateRowHeightInfo%2A>方法，當變更快取的資料列高度資訊之外<xref:System.Windows.Forms.DataGridView.RowHeightInfoPushed>事件處理常式，以確保目前的值會在控制項的顯示。|  
  
## <a name="best-practices-in-virtual-mode"></a>處於虛擬模式的最佳作法  
 如果您要實作虛擬模式下，若要有效率地處理大量資料，您也會想要確保您正在有效率地使用<xref:System.Windows.Forms.DataGridView>控制項本身。 如需使用有效率的儲存格樣式、 自動調整大小、 選取項目，和共用資料列，請參閱[縮放 Windows Form DataGridView 控制項的最佳作法](best-practices-for-scaling-the-windows-forms-datagridview-control.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- [Windows Form DataGridView 控制項中的效能微調](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [縮放 Windows Form DataGridView 控制項的最佳作法](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [逐步解說：在 Windows Forms DataGridView 控制項中實作虛擬模式](implementing-virtual-mode-wf-datagridview-control.md)
- [在 Windows Form DataGridView 控制項中以 Just-In-Time 資料載入方式實作虛擬模式](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)

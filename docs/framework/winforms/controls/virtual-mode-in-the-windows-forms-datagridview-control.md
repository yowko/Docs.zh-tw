---
title: "Windows Form DataGridView 控制項中的虛擬模式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], virtual mode
ms.assetid: feae5d43-2848-4b1a-8ea7-77085dc415b5
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 06c5bb1d4a36d51bb07d59b48c730f722af23f8c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="virtual-mode-in-the-windows-forms-datagridview-control"></a>Windows Form DataGridView 控制項中的虛擬模式
虛擬模式中，您可以管理之間的互動<xref:System.Windows.Forms.DataGridView>控制項和自訂資料快取。 若要實作虛擬模式時，設定<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>屬性`true`並處理一個或多個本主題中所述的事件。 您通常會處理最少為`CellValueNeeded`事件，可讓資料快取中的值控制查閱。  
  
## <a name="bound-mode-and-virtual-mode"></a>繫結的模式和虛擬模式  
 您需要以補充或取代繫結的模式時才必須虛擬模式。 繫結模式，在您設定<xref:System.Windows.Forms.DataGridView.DataSource%2A>屬性和控制項自動從指定的來源載入資料，並提交給它的使用者變更。 您可以控制顯示哪些繫結的資料行，以及資料來源本身通常會處理作業，例如排序。  
  
## <a name="supplementing-bound-mode"></a>補充繫結的模式  
 您可以透過顯示未繫結的資料行，以及繫結的資料行提供繫結的模式。 這有時稱為 「 混合的模式 」，而且適用於顯示一些作業，例如導出的值或使用者介面 (UI) 控制項。  
  
 因為未繫結的資料行是外部資料來源，資料來源的排序作業會忽略它們。 因此，當您啟用排序在混合模式中，您必須管理在本機快取未繫結的資料，並實作虛擬模式，讓<xref:System.Windows.Forms.DataGridView>控制項互動。  
  
 如需使用保留未繫結的資料行中值的虛擬模式的詳細資訊，請參閱中的範例<xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A?displayProperty=nameWithType>屬性和<xref:System.Windows.Forms.DataGridViewComboBoxColumn?displayProperty=nameWithType>類別參考主題。  
  
## <a name="replacing-bound-mode"></a>取代繫結的模式  
 如果繫結的模式不符合您的效能需求，您可以管理您透過虛擬模式事件處理常式的自訂快取中的所有資料。 例如，您可以使用虛擬模式來實作在 just-in-time 資料載入的機制，只擷取的資料量從網路連接的資料庫，才能獲得最佳效能。 當使用大量的資料，透過低速網路連線或使用用戶端電腦具有有限的 RAM 或儲存空間時，這種情況下就特別有用。  
  
 如需在 just-in-time 案例中使用虛擬模式的詳細資訊，請參閱[以 Just-In-Time 資料載入 Windows Form DataGridView 控制項中實作虛擬模式](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)。  
  
## <a name="virtual-mode-events"></a>虛擬模式事件  
 如果您的資料是唯讀的`CellValueNeeded`事件可能就是僅需要處理的事件。 其他的虛擬模式事件可讓您啟用特定的功能，例如使用者編輯、 資料列新增和刪除及資料列層級的交易。  
  
 某些標準<xref:System.Windows.Forms.DataGridView>事件 （例如，當使用者加入或刪除資料列，或當儲存格的值時所發生的事件是編輯、 剖析、 驗證，或格式化） 可用於虛擬模式。 您也可以處理事件，可讓您維護通常不會儲存在繫結的資料來源，例如儲存格的工具提示文字、 資料格和資料列錯誤文字、 資料格和資料列快顯功能表上的資料，以及資料列高度的值。  
  
 如需實作虛擬模式來管理與資料列層級的認可範圍的讀取/寫入資料的詳細資訊，請參閱[逐步解說： 在 Windows Form DataGridView 控制項中實作虛擬模式](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)。  
  
 如需實作虛擬模式與認可資料格層級範圍的範例，請參閱<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>屬性參考主題。  
  
 只會發生下列事件時<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>屬性設定為`true`。  
  
|Event - 事件|描述|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.DataGridView.CellValueNeeded>|用於控制項所顯示的資料快取中擷取資料格的值。 僅針對未繫結的資料行中的資料格就會發生此事件。|  
|<xref:System.Windows.Forms.DataGridView.CellValuePushed>|用來讓資料快取認可資料格的使用者輸入控制項。 僅針對未繫結的資料行中的資料格就會發生此事件。<br /><br /> 呼叫<xref:System.Windows.Forms.DataGridView.UpdateCellValue%2A>方法時變更快取的值之外的<xref:System.Windows.Forms.DataGridView.CellValuePushed>事件處理常式，以確保目前的值會顯示在控制項中，並套用目前作用中的任何自動調整大小模式。|  
|<xref:System.Windows.Forms.DataGridView.NewRowNeeded>|使用控制項來表示資料快取中的新資料列的需要。|  
|<xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>|使用控制項來判斷資料列是否有任何未認可的變更。|  
|<xref:System.Windows.Forms.DataGridView.CancelRowEdit>|使用控制項來表示資料列應該還原成快取的值。|  
  
 下列事件可用於虛擬模式，但可用不論<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>屬性設定。  
  
|事件|描述|  
|------------|-----------------|  
|<xref:System.Windows.Forms.DataGridView.UserDeletingRow><br /><br /> <xref:System.Windows.Forms.DataGridView.UserDeletedRow><br /><br /> <xref:System.Windows.Forms.DataGridView.RowsRemoved><br /><br /> <xref:System.Windows.Forms.DataGridView.RowsAdded>|使用控制項來表示當資料列遭到刪除，或您加入，以便能據以更新資料快取。|  
|<xref:System.Windows.Forms.DataGridView.CellFormatting><br /><br /> <xref:System.Windows.Forms.DataGridView.CellParsing><br /><br /> <xref:System.Windows.Forms.DataGridView.CellValidating><br /><br /> <xref:System.Windows.Forms.DataGridView.CellValidated><br /><br /> <xref:System.Windows.Forms.DataGridView.RowValidating><br /><br /> <xref:System.Windows.Forms.DataGridView.RowValidated>|使用格式儲存格的值來控制顯示，並且將剖析和驗證使用者輸入。|  
|<xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded>|用來擷取資料格的工具提示文字控制項時<xref:System.Windows.Forms.DataGridView.DataSource%2A>屬性設定或<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>屬性是`true`。<br /><br /> 資料格的工具提示會顯示時，才<xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A>屬性值是`true`。|  
|<xref:System.Windows.Forms.DataGridView.CellErrorTextNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowErrorTextNeeded>|由控制項來擷取資料列的錯誤文字時<xref:System.Windows.Forms.DataGridView.DataSource%2A>屬性設定或<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>屬性是`true`。<br /><br /> 呼叫<xref:System.Windows.Forms.DataGridView.UpdateCellErrorText%2A>方法或<xref:System.Windows.Forms.DataGridView.UpdateRowErrorText%2A>方法，當您變更資料列錯誤文字，以確保在控制項中顯示的目前值。<br /><br /> 資料格和資料列的錯誤圖像會顯示當<xref:System.Windows.Forms.DataGridView.ShowCellErrors%2A>和<xref:System.Windows.Forms.DataGridView.ShowRowErrors%2A>屬性的值為`true`。|  
|<xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowContextMenuStripNeeded>|由控制項用來擷取資料列<xref:System.Windows.Forms.ContextMenuStrip>時控制項<xref:System.Windows.Forms.DataGridView.DataSource%2A>屬性設定或<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>屬性是`true`。|  
|<xref:System.Windows.Forms.DataGridView.RowHeightInfoNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowHeightInfoPushed>|使用控制項來擷取或儲存在資料快取資料列高度的資訊。 呼叫<xref:System.Windows.Forms.DataGridView.UpdateRowHeightInfo%2A>方法時變更的快取的資料列高度資訊外<xref:System.Windows.Forms.DataGridView.RowHeightInfoPushed>事件處理常式，以確定目前的值用於控制項的顯示。|  
  
## <a name="best-practices-in-virtual-mode"></a>虛擬模式中的最佳作法  
 如果您要實作虛擬模式，才能有效地使用大量的資料，您也會想要確保您會使用有效率地<xref:System.Windows.Forms.DataGridView>控制本身。 儲存格樣式、 自動調整大小、 選取項目，和共用資料列的有效率地使用的相關資訊，請參閱[縮放 Windows Form DataGridView 控制項的最佳作法](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 [Windows Forms DataGridView 控制項中的效能微調](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 [縮放 Windows Forms DataGridView 控制項的最佳作法](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 [逐步解說：在 Windows Forms DataGridView 控制項中實作虛擬模式](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)  
 [在 Windows Forms DataGridView 控制項中以 Just-In-Time 資料載入方式實作虛擬模式](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)

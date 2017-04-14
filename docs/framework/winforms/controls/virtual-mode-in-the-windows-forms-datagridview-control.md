---
title: "Windows Form DataGridView 控制項中的虛擬模式 | Microsoft Docs"
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
  - "DataGridView 控制項 [Windows Form], 虛擬模式"
ms.assetid: feae5d43-2848-4b1a-8ea7-77085dc415b5
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# Windows Form DataGridView 控制項中的虛擬模式
使用虛擬模式，您可以管理 <xref:System.Windows.Forms.DataGridView> 控制項和自訂資料快取之間的互動。  若要實作虛擬模式，請將 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> 屬性設定為 `true`，並處理此主題中所描述的一或多個事件。  您通常至少會處理 `CellValueNeeded` 事件，此事件能讓控制項查詢資料快取中的值。  
  
## 繫結模式和虛擬模式  
 只有在需要補充或取代繫結模式時，才必須使用虛擬模式。  在繫結模式中，您設定 <xref:System.Windows.Forms.DataGridView.DataSource%2A> 屬性，控制項會從指定的來源自動載入資料，並傳送回使用者變更。  您可以控制顯示哪個繫結資料行，而資料來源本身通常會處理作業 \(例如排序\)。  
  
## 補充繫結模式  
 您可以顯示未繫結資料行以及繫結資料行，以補充繫結模式。  有時候這也稱為「混合模式」，在顯示像是計算值或使用者介面 \(UI\) 控制項之類的內容時，會非常的有用。  
  
 因為未繫結資料行是在資料來源以外，所以資料來源的排序作業通常會忽略未繫結資料行。  所以，當您啟用混合模式中的排序時，就必須管理本機快取中的未繫結資料並實作虛擬模式，讓 <xref:System.Windows.Forms.DataGridView> 控制項與其互動。  
  
 如需使用虛擬模式以維護未繫結資料行的值的詳細資訊，請參閱 <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A?displayProperty=fullName> 屬性和 <xref:System.Windows.Forms.DataGridViewComboBoxColumn?displayProperty=fullName> 類別參考主題中的範例。  
  
## 取代繫結模式  
 如果繫結模式不符合效能需求，您可以透過虛擬模式事件處理常式，在自訂快取中管理所有資料。  例如，您可以使用虛擬模式來實作 Just\-In\-Time 資料載入機制，此機制會從網路連接的資料庫中，只擷取最佳化效能所需的資料量。  當在緩慢的網路連接上使用大量資料，或使用 RAM 或儲存空間有限的用戶端機器時，這個案例會特別有用。  
  
 如需使用 Just\-In\-Time 案例中虛擬模式的詳細資訊，請參閱[在 Windows Form DataGridView 控制項中以 Just\-In\-Time 資料載入方式實作虛擬模式](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)。  
  
## 虛擬模式事件  
 如果資料為唯讀，則 `CellValueNeeded` 事件可能會是您需要處理的唯一事件。  其他的虛擬模式事件會讓您啟用特定的功能 \(例如使用者編輯、新增和刪除資料列以及資料列層級交易\)。  
  
 某些標準 <xref:System.Windows.Forms.DataGridView> 事件 \(例如，使用者在新增或刪除資料列或當編輯、剖析、驗證或格式化儲存格值時，所發生的事件\) 在虛擬模式中也很有用。  您能處理的事件還包括維護通常不儲存於繫結資料來源的值，例如，儲存格工具提示文字、儲存格和資料列錯誤文字、儲存格和資料列捷徑功能表資料，以及列高資料。  
  
 如需實作虛擬模式以管理資料列層級認可範圍的讀取\/寫入資料，請參閱[逐步解說：在 Windows Form DataGridView 控制項中實作虛擬模式](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)。  
  
 如需實作儲存格層級認可範圍的虛擬模式，請參閱 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> 屬性參考主題。  
  
 只有在將 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> 屬性設定為 `true` 時，才會發生下列事件。  
  
|事件|描述|  
|--------|--------|  
|<xref:System.Windows.Forms.DataGridView.CellValueNeeded>|由控制項用來從資料快取擷取要顯示的儲存格值。  此事件只發生於未繫結資料行中的儲存格。|  
|<xref:System.Windows.Forms.DataGridView.CellValuePushed>|由控制項用來將儲存格的使用者輸入提交至資料快取。  此事件只發生於未繫結資料行中的儲存格。<br /><br /> 當變更 <xref:System.Windows.Forms.DataGridView.CellValuePushed> 事件處理常式以外的快取值時，呼叫 <xref:System.Windows.Forms.DataGridView.UpdateCellValue%2A> 方法，以確保目前的值顯示在控制項中，並套用目前生效的任何自動調整大小模式。|  
|<xref:System.Windows.Forms.DataGridView.NewRowNeeded>|由控制項用來表示資料快取中新資料列的需求。|  
|<xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>|由控制項用來決定控制項是否有任何未認可的變更。|  
|<xref:System.Windows.Forms.DataGridView.CancelRowEdit>|由控制項用來表示資料列應該還原成快取值。|  
  
 下列事件在虛擬模式中會很有用，但不論 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> 屬性設定為何都可以使用。  
  
|事件|描述|  
|--------|--------|  
|<xref:System.Windows.Forms.DataGridView.UserDeletingRow><br /><br /> <xref:System.Windows.Forms.DataGridView.UserDeletedRow><br /><br /> <xref:System.Windows.Forms.DataGridView.RowsRemoved><br /><br /> <xref:System.Windows.Forms.DataGridView.RowsAdded>|由控制項用來表示刪除或加入資料列的時機，讓您可以相對地更新資料快取。|  
|<xref:System.Windows.Forms.DataGridView.CellFormatting><br /><br /> <xref:System.Windows.Forms.DataGridView.CellParsing><br /><br /> <xref:System.Windows.Forms.DataGridView.CellValidating><br /><br /> <xref:System.Windows.Forms.DataGridView.CellValidated><br /><br /> <xref:System.Windows.Forms.DataGridView.RowValidating><br /><br /> <xref:System.Windows.Forms.DataGridView.RowValidated>|由控制項用來格式化要顯示的儲存格值，並且剖析及驗證使用者輸入。|  
|<xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded>|由控制項用來在已經設定 <xref:System.Windows.Forms.DataGridView.DataSource%2A> 屬性或 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> 屬性為 `true` 時，擷取儲存格工具提示文字。<br /><br /> 儲存格工具提示只會在 <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> 屬性值為 `true` 時才會顯示。|  
|<xref:System.Windows.Forms.DataGridView.CellErrorTextNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowErrorTextNeeded>|由控制項用來在已經設定 <xref:System.Windows.Forms.DataGridView.DataSource%2A> 屬性或 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> 屬性為 `true` 時，擷取儲存格或資料列錯誤文字。<br /><br /> 當您變更儲存格或資料列錯誤文字時，請呼叫 <xref:System.Windows.Forms.DataGridView.UpdateCellErrorText%2A> 方法或 <xref:System.Windows.Forms.DataGridView.UpdateRowErrorText%2A> 方法，以確保目前的值是顯示在控制項中。<br /><br /> 當 <xref:System.Windows.Forms.DataGridView.ShowCellErrors%2A> 和 <xref:System.Windows.Forms.DataGridView.ShowRowErrors%2A> 屬性值為 `true` 時，會顯示儲存格和資料列錯誤圖像 \(Glyph\)。|  
|<xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowContextMenuStripNeeded>|當控制項已經設定 <xref:System.Windows.Forms.DataGridView.DataSource%2A> 屬性或 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> 屬性為 `true` 時，由控制項用來擷取儲存格或資料列 <xref:System.Windows.Forms.ContextMenuStrip>。|  
|<xref:System.Windows.Forms.DataGridView.RowHeightInfoNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowHeightInfoPushed>|由控制項用來擷取或儲存資料快取中的列高資訊。  在變更 <xref:System.Windows.Forms.DataGridView.RowHeightInfoPushed> 事件處理常式以外的快取列高資訊時，請呼叫 <xref:System.Windows.Forms.DataGridView.UpdateRowHeightInfo%2A> 方法，以確保目前的值是使用於控制項的顯示中。|  
  
## 虛擬模式中的最佳作法  
 如果是為了要有效使用大量資料而實作虛擬模式，您也會想確保有效使用該 <xref:System.Windows.Forms.DataGridView> 控制項本身。  如需有效使用儲存格樣式、自動調整大小、選取和資料列共用的詳細資訊，請參閱[縮放 Windows Form DataGridView 控制項的最佳作法](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>   
 [Windows Form DataGridView 控制項中的效能微調](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)   
 [縮放 Windows Form DataGridView 控制項的最佳作法](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)   
 [逐步解說：在 Windows Form DataGridView 控制項中實作虛擬模式](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)   
 [在 Windows Form DataGridView 控制項中以 Just\-In\-Time 資料載入方式實作虛擬模式](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)
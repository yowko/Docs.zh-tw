---
title: "DataGridView 控制項 (Windows Form) | Microsoft Docs"
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
  - "資料 [Windows Form], 以表格式格式顯示"
  - "資料格"
  - "資料展示"
  - "DataGridView 控制項 [Windows Form]"
  - "資料集 [Windows Form], 在 DataGridView 控制項中顯示"
  - "資料集 [Windows Form], 使用者介面"
  - "方格控制項 [Windows Form]"
  - "資料表 [Windows Form]"
  - "表格式資料, 在 Windows Form 上顯示"
  - "Windows Form, 顯示資料"
ms.assetid: dbee73f2-bba6-4874-9389-cd21d44309be
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# DataGridView 控制項 (Windows Form)
`DataGridView` 控制項以表格式顯示資料，是一項功能強大、有彈性的方式。  您可以使用 `DataGridView` 控制來顯示少量資料的唯讀檢視，或者您可以調整它的大小，以顯示非常大的資料集之可編輯檢視。  
  
 您可以數種方式擴充 `DataGridView` 控制項，以建置自訂行為到您的應用程式中。  例如，您可以程式設計方式指定自己的排序演算法，而且也可以建立自己的儲存格類型。  您可以在數種屬性間做選擇，輕鬆自訂 `DataGridView` 控制項的外觀。  許多類型的資料儲存區可用來做為資料來源，不然 `DataGridView` 控制項可在不使用與其繫結的資料來源之情況下運作。  
  
 本節中的主題描述您可以用來將 `DataGridView` 功能建置在應用程式中的概念和技術。  
  
## 在本節中  
 [DataGridView 控制項概觀](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)  
 提供描述 Windows Form `DataGridView` 控制項架構和核心概念的主題。  
  
 [Windows Form DataGridView 控制項的預設功能](../../../../docs/framework/winforms/controls/default-functionality-in-the-windows-forms-datagridview-control.md)  
 描述當 Windows Form `DataGridView` 控制項繫結至資料來源時的預設外觀和行為。  
  
 [Windows Form DataGridView 控制項中的資料行類型](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  
 描述在 Windows Form `DataGridView` 控制項中用於顯示資料，並允許使用者修改或加入資料的資料行類型。  
  
 [Windows Form DataGridView 控制項中的基本資料行、資料列和儲存格功能](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 提供描述常用的儲存格、資料列和資料行屬性的主題。  
  
 [Windows Form DataGridView 控制項中的基本格式化和樣式設定](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 提供主題描述如何修改控制項基本外觀和儲存格資料顯示格式。  
  
 [在 Windows Form DataGridView 控制項中顯示資料](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 提供主題描述如何以手動方式或從外部資料來源將資料填入控制項。  
  
 [調整 Windows Form DataGridView 控制項中資料行和資料列的大小](../../../../docs/framework/winforms/controls/resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)  
 提供主題描述資料列和資料行大小可如何自動調整，以符合儲存格內容，或調整控制項可用寬度。  
  
 [在 Windows Form DataGridView 控制項中排序資料](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)  
 提供描述控制項中排序功能的主題。  
  
 [Windows Form DataGridView 控制項中的資料輸入](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 提供主題描述如何變更使用者加入和修改控制項資料的方式。  
  
 [選取範圍和剪貼簿與 Windows Form DataGridView 控制項搭配使用](../../../../docs/framework/winforms/controls/selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)  
 提供主題描述控制項中儲存格、資料列和資料行的選取功能。  
  
 [在 Windows Form DataGridView 控制項中利用儲存格、資料列和資料行進行程式設計](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)  
 提供主題描述如何使用儲存格、資料列和資料行物件進行程式設計。  
  
 [自訂 Windows Form DataGridView 控制項](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 提供主題描述自訂繪製 `DataGridView` 儲存格和資料列，並建立衍生儲存格、資料行和資料列類型。  
  
 [Windows Form DataGridView 控制項中的效能微調](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 提供主題描述處理大量資料時，如何有效率地使用控制項來避免發生效能問題。  
  
 [Windows Form DataGridView 控制項中的預設鍵盤和滑鼠處理](../../../../docs/framework/winforms/controls/default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)  
 描述使用者可如何透過鍵盤和滑鼠與 `DataGridView` 控制項互動。  
  
 [Windows Form DataGridView 和 DataGrid 控制項之間的差異](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)  
 描述 `DataGridView` 控制項如何改良並取代 <xref:System.Windows.Forms.DataGrid> 控制項。  
  
 另請參閱[使用設計工具搭配 Windows Form DataGridView 控制項](http://msdn.microsoft.com/library/ms171593\(v=vs.110\))。  
  
## 參考  
 <xref:System.Windows.Forms.DataGridView>  
 提供 <xref:System.Windows.Forms.DataGridView> 控制項的參考文件。  
  
 <xref:System.Windows.Forms.BindingSource>  
 提供 <xref:System.Windows.Forms.BindingSource> 元件的參考文件。  <xref:System.Windows.Forms.DataGridView> 控制項和 <xref:System.Windows.Forms.BindingSource> 元件設計為可密切合作。  
  
## 請參閱  
 [在 Windows Form 上使用的控制項](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
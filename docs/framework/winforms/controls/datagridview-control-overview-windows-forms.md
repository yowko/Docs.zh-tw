---
title: "DataGridView 控制項概觀 (Windows Form) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DataGridView"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "繫結控制項, DataGridView 控制項"
  - "資料行 [Windows Form], DataGridView 控制項"
  - "資料 [Windows Form], 巡覽"
  - "資料 [Windows Form], 重新排序"
  - "資料繫結, DataGridView 控制項"
  - "資料格, 關於資料格"
  - "資料來源, 繫結至 DataGridView 控制項"
  - "DataGridView 控制項 [Windows Form], 關於 DataGridView 控制項"
  - "DataGridView 控制項 [Windows Form], 資料繫結"
  - "資料集 [Windows Form], 繫結至 DataGridView 控制項"
  - "方格控制項 [Windows Form]"
  - "方格 [Windows Form]"
  - "資料表 [Windows Form], 繫結至 DataGridView 控制項"
  - "資料表 [Windows Form], 在 DataGridView 控制項中顯示"
ms.assetid: 0a45c661-89dc-4390-9cc6-c47eee501488
caps.latest.revision: 23
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 23
---
# DataGridView 控制項概觀 (Windows Form)
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。  如需詳細資訊，請參閱 [Windows Form DataGridView 和 DataGrid 控制項之間的差異](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 透過 <xref:System.Windows.Forms.DataGridView> 控制項，您可以顯示和編輯來自各種不同資料來源的表格式資料。  
  
 將資料繫結至 <xref:System.Windows.Forms.DataGridView> 控制項是直接且直覺的，而且在許多狀況下，它就像設定 <xref:System.Windows.Forms.DataGridView.DataSource%2A> 屬性一樣簡單。  當您繫結至包含多個清單或資料表的資料來源時，請將 <xref:System.Windows.Forms.DataGridView.DataMember%2A> 屬性設定為指定清單或資料表要繫結目標的字串。  
  
 <xref:System.Windows.Forms.DataGridView> 控制項支援標準的 Windows Form 資料繫結模型，因此它會繫結至下列清單中所描述的類別執行個體。  
  
-   實作 <xref:System.Collections.IList> 介面的任何類別，包括一維陣列  
  
-   實作 <xref:System.ComponentModel.IListSource> 介面的任何類別，例如 <xref:System.Data.DataTable> 和 <xref:System.Data.DataSet> 類別  
  
-   實作 <xref:System.ComponentModel.IBindingList> 介面的任何類別，例如 <xref:System.ComponentModel.BindingList%601> 類別  
  
-   實作 <xref:System.ComponentModel.IBindingListView> 介面的任何類別，例如 <xref:System.Windows.Forms.BindingSource> 類別  
  
 當在傳回的物件上實作時，<xref:System.Windows.Forms.DataGridView> 控制項支援將資料繫結至這些介面所傳回之物件的公用屬性，或繫結至 <xref:System.ComponentModel.ICustomTypeDescriptor> 介面所傳回的屬性集合。  
  
 一般而言，您會繫結至 <xref:System.Windows.Forms.BindingSource> 元件，並將 <xref:System.Windows.Forms.BindingSource> 元件繫結至另一個資料來源或將商務物件 \(Business Object\) 填入其中。  <xref:System.Windows.Forms.BindingSource> 元件是慣用的資料來源，因為它可以繫結至各種資料來源，並且可以自動解決許多資料繫結問題。  如需詳細資訊，請參閱 [BindingSource 元件](../../../../docs/framework/winforms/controls/bindingsource-component.md)。  
  
 <xref:System.Windows.Forms.DataGridView> 控制項也可以在沒有基礎資料存放區的情況下用於*未繫結*模式。  如需使用未繫結的 <xref:System.Windows.Forms.DataGridView> 控制項的程式碼範例，請參閱[逐步解說：建立未繫結的 Windows Form DataGridView 控制項](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)。  
  
 <xref:System.Windows.Forms.DataGridView> 控制項可以隨意設定和擴充，並且提供許多屬性、方法和事件來自訂它的外觀及行為。  當您想要 Windows Form 應用程式顯示表格式資料時，請在使用其他控制項 \(例如 <xref:System.Windows.Forms.DataGrid>\) 之前，先考慮使用 <xref:System.Windows.Forms.DataGridView> 控制項。  如果您正在顯示小量的唯讀值，或正在讓使用者編輯具有數百萬資料錄的資料表，<xref:System.Windows.Forms.DataGridView> 控制項將提供您一個立即可程式化、記憶體效率高的方案。  
  
## 本章節內容  
 [DataGridView 控制項技術摘要](../../../../docs/framework/winforms/controls/datagridview-control-technology-summary-windows-forms.md)  
 摘要 <xref:System.Windows.Forms.DataGridView> 控制項的概念和相關類別的使用。  
  
 [DataGridView 控制項架構](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)  
 描述 <xref:System.Windows.Forms.DataGridView> 控制項的架構，並說明它的型別階層架構和繼承結構。  
  
 [DataGridView 控制項案例](../../../../docs/framework/winforms/controls/datagridview-control-scenarios-windows-forms.md)  
 描述使用 <xref:System.Windows.Forms.DataGridView> 控制項的最常見案例。  
  
 [DataGridView 控制項程式碼目錄](../../../../docs/framework/winforms/controls/datagridview-control-code-directory-windows-forms.md)  
 提供文件中各種 <xref:System.Windows.Forms.DataGridView> 工作的程式碼範例連結。  這些範例是以工作類型分類。  
  
## 相關章節  
 [Windows Form DataGridView 控制項中的資料行類型](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  
 討論 Windows Form <xref:System.Windows.Forms.DataGridView> 控制項中用來顯示資訊及讓使用者修改或加入資訊的資料行型別。  
  
 [在 Windows Form DataGridView 控制項中顯示資料](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 提供描述如何在控制項中手動填入資料或從外部資料來源填入資料的主題。  
  
 [自訂 Windows Form DataGridView 控制項](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 提供說明自訂繪製 <xref:System.Windows.Forms.DataGridView> 儲存格和資料列，以及建立衍生之儲存格、資料行及資料列型別的主題。  
  
 [Windows Form DataGridView 控制項中的效能微調](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 提供描述如何在處理大量資料時，有效使用控制項以避免效能問題的主題。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.BindingSource>   
 [DataGridView 控制項](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)   
 [Windows Form DataGridView 控制項的預設功能](../../../../docs/framework/winforms/controls/default-functionality-in-the-windows-forms-datagridview-control.md)   
 [Windows Form DataGridView 控制項中的預設鍵盤和滑鼠處理](../../../../docs/framework/winforms/controls/default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
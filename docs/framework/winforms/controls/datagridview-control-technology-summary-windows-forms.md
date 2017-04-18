---
title: "DataGridView 控制項技術摘要 (Windows Form) | Microsoft Docs"
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
  - "資料格, 關於資料格"
  - "DataGridView 控制項 [Windows Form], 關於 DataGridView 控制項"
ms.assetid: 094498c3-a126-4a3f-83fe-f69e96c7717b
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# DataGridView 控制項技術摘要 (Windows Form)
這個主題摘要說明 `DataGridView` 控制項及支援該控制項用法之類別的相關資訊。  
  
 以表格格式顯示資料是一項您可能會經常執行的工作。  `DataGridView` 控制項就是專為在方格中顯示資料而設計的完整方案。  
  
## Keywords  
 DataGridView、BindingSource、資料表、儲存格、資料繫結、虛擬模式  
  
## 命名空間  
 <xref:System.Windows.Forms?displayProperty=fullName>  
  
 <xref:System.Data?displayProperty=fullName>  
  
## 相關技術  
 `BindingSource`  
  
## 背景  
 使用者介面 \(UI\) 設計人員經常會發現需要為使用者顯示表格式資料。  [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 提供了幾個在資料表或方格中顯示資料的方式。  `DataGridView` 控制項呈現了 Windows Form 應用程式中這項技術的最新演進。  
  
 `DataGridView` 控制項可以顯示資料存放區的資料列。  許多類型的資料存放區都受支援。  資料存放區可以儲存簡單、不具型別的資料 \(例如一維陣列\)，也可以儲存具型別的資料 \(例如 <xref:System.Data.DataSet>\)。  如需詳細資訊，請參閱 [如何：將資料繫結至 Windows Form DataGridView 控制項](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md)。  
  
 `DataGridView` 控制項以表格式顯示資料，是一項功能強大、有彈性的方式。  您可以使用這個控制項，顯示從小型到大型資料集合的唯讀或可編輯式資料檢視表 \(View\)。  
  
 您可以用幾種方式來擴充 `DataGridView` 控制項，將自訂行為建置到應用程式中。  例如，您可以用程式設計方式指定自己的排序演算法，並建立自己的儲存格型別。  藉由選擇不同的屬性，您可以輕鬆地自訂 `DataGridView` 控制項的外觀。  許多類型的資料存放區可以當做資料來源使用，或者 `DataGridView` 控制項可以未繫結資料來源而運作。  
  
## 實作 DataGridView 類別  
 您有幾種方式可以利用 `DataGridView` 控制項的擴充性功能。  您可以透過事件和屬性來自訂控制項的許多方面，但是某些自訂需要從現有的 `DataGridView` 類別衍生以建立新類別。  
  
 最常使用的基底類別有 `DataGridViewCell` 和 `DataGridViewColumn`。  您可以從 `DataGridViewCell` 或其任何子類別衍生自己的儲存格類別。  雖然您可以將任何儲存格型別加入任何資料行，但是您通常也會從 `DataGridViewColumn` \(預設裝載您的自訂儲存格型別的儲存格\) 衍生附屬資料行類別。  
  
 您可以在衍生的儲存格類別中實作 `IDataGridViewEditingCell` 介面，建立具有編輯功能但是不會在編輯模式中裝載控制項的儲存格型別。  若要建立可以在編輯模式中裝載在儲存格裡的控制項，您可以在衍生自 <xref:System.Windows.Forms.Control> 的類別中實作 `IDataGridViewEditingControl` 介面。  
  
 如需詳細資訊，請參閱 [如何：擴充儲存格和資料行的行為和外觀以自訂 Windows Form DataGridView 控制項中的儲存格和資料行](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md) 和 [如何：Windows Form DataGridView 儲存格中的主控制項](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md)。  
  
## DataGridView 類別簡介  
 <xref:System.Windows.Forms>  
  
|技術範圍|類別\/介面\/組態項目|  
|----------|------------------|  
|資料繫結|<xref:System.Windows.Forms.BindingSource>|  
|資料展示|<xref:System.Windows.Forms.DataGridView><br /><br /> <xref:System.Windows.Forms.DataGridViewCell> 和衍生類別<br /><br /> <xref:System.Windows.Forms.DataGridViewRow> 和衍生類別<br /><br /> <xref:System.Windows.Forms.DataGridViewColumn> 和衍生類別<br /><br /> <xref:System.Windows.Forms.DataGridViewCellStyle>|  
|<xref:System.Windows.Forms.DataGridView> 擴充性|<xref:System.Windows.Forms.DataGridViewCell> 和衍生類別<br /><br /> <xref:System.Windows.Forms.DataGridViewColumn> 和衍生類別<br /><br /> <xref:System.Windows.Forms.IDataGridViewEditingCell><br /><br /> <xref:System.Windows.Forms.IDataGridViewEditingControl>|  
  
## 新功能  
 <xref:System.Windows.Forms.DataGridView> 控制項是專為以 Windows Form 顯示表格式資料而設計的完整方案。  當您撰寫新的應用程式時，應該在使用其他方案 \(例如 <xref:System.Windows.Forms.DataGrid>\) 之前先考慮使用 <xref:System.Windows.Forms.DataGridView> 控制項。  如需詳細資訊，請參閱 [Windows Form DataGridView 和 DataGrid 控制項之間的差異](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 <xref:System.Windows.Forms.DataGridView> 控制項可以與 <xref:System.Windows.Forms.BindingSource> 元件密切合作。  這個元件是專為當做表單的主要資料來源所設計。  它可以管理 <xref:System.Windows.Forms.DataGridView> 控制項和其資料來源之間的互動，而不論資料來源的型別。  
  
## 請參閱  
 [DataGridView 控制項概觀](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)   
 [DataGridView 控制項架構](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)   
 [保護連接資訊](../../../../docs/framework/data/adonet/protecting-connection-information.md)
---
title: "Windows Form 支援的資料來源 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "陣列 [Windows Form]"
  - "集合 [Windows Form], 繫結至"
  - "資料 [Windows Form], 資料提供者"
  - "資料提供者 [Windows Form]"
  - "資料來源 [Windows Form]"
  - "DataColumn 類別"
  - "DataSet 類別, 繫結和 Windows Form"
  - "DataTable 類別, 繫結和 Windows Form"
  - "DataView 類別, 繫結和 Windows Form"
  - "DataViewManager 類別, 繫結和 Windows Form"
  - "OLE DB 提供者, Windows Form"
  - "Windows Form, 資料繫結"
  - "Windows Form, 來源資料"
ms.assetid: 3d2c43f6-462b-4d35-9c86-13e9afe012e1
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Windows Form 支援的資料來源
傳統上，在應用程式中使用資料繫結的目的，是為了利用儲存在資料庫中的資料。  Windows Form 資料繫結允許您存取資料庫的資料，也可以從陣列和集合等其他結構存取資料 \(只要您符合某些最低需求\)。  
  
## 可繫結的結構  
 在 Windows Form 之中，您可以繫結至許多種結構，從簡單的物件 \(簡單繫結\) 到複雜如 ADO.NET 資料表的清單 \(複雜繫結\) 都包括在內。  就簡單繫結而言，Windows Form 可支援繫結至簡單物件的公用屬性。  Windows Form 的清單架構繫結通常會需要物件支援 <xref:System.Collections.IList> 介面或 <xref:System.ComponentModel.IListSource> 介面。  此外，如果您透過 <xref:System.Windows.Forms.BindingSource> 元件來繫結，則您可以繫結至支援 <xref:System.Collections.IEnumerable> 介面的物件。  如需與資料繫結相關介面的詳細資訊，請參閱[與資料繫結相關的介面](../../../docs/framework/winforms/interfaces-related-to-data-binding.md)。  
  
 下列清單列出您可以在 Windows Form 中繫結的結構。  
  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.BindingSource> 是最常見的 Windows Form 資料來源，扮演資料來源和 Windows Form 控制項之間的 Proxy。  一般的 <xref:System.Windows.Forms.BindingSource> 使用模式是將您的控制項繫結至 <xref:System.Windows.Forms.BindingSource>，以及將 <xref:System.Windows.Forms.BindingSource> 繫結至資料來源 \(例如 ADO.NET 資料表或一個商務物件\)。  <xref:System.Windows.Forms.BindingSource> 所提供的服務可以啟用和改進資料繫結支援的層級。  例如，Windows Form 的 <xref:System.Windows.Forms.DataGridView> 和 <xref:System.Windows.Forms.ComboBox> 等清單架構控制項並不直接支援繫結至 <xref:System.Collections.IEnumerable> 資料來源，然而您可以改由 <xref:System.Windows.Forms.BindingSource> 繫結來達到此目的。  在這種情況下，<xref:System.Windows.Forms.BindingSource> 會將資料來源轉換成 <xref:System.Collections.IList>。  
  
 簡單物件  
 Windows Form 支援將控制項屬性資料繫結至使用 <xref:System.Windows.Forms.Binding> 型別的物件其執行個體之公用屬性。  當使用 <xref:System.Windows.Forms.BindingSource> 時，Windows Form 也支援將清單架構控制項 \(例如 <xref:System.Windows.Forms.ListControl>\) 繫結至物件的執行個體。  
  
 陣列或集合  
 做為資料來源，清單必須實作 <xref:System.Collections.IList> 介面；例如，身為 <xref:System.Array> 類別的執行個體的某陣列。  如需陣列的詳細資訊，請參閱 [How to: Create an Array of Objects \(Visual Basic\)](http://msdn.microsoft.com/zh-tw/6b64e069-0387-400c-9081-3bdc581020c3)。  
  
 一般而言，當您為資料繫結建立物件清單時，應該使用 <xref:System.ComponentModel.BindingList%601>。  <xref:System.ComponentModel.BindingList%601> 是 <xref:System.ComponentModel.IBindingList> 介面的泛型版本。  <xref:System.ComponentModel.IBindingList> 介面會加入雙向資料繫結所需的屬性、方法和事件，來延伸 <xref:System.Collections.IList> 介面。  
  
 <xref:System.Collections.IEnumerable>  
 如果透過 <xref:System.Windows.Forms.BindingSource> 元件來繫結，Windows Form 控制項可以繫結至只支援 <xref:System.Collections.IEnumerable> 介面的資料來源。  
  
 [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] 資料物件  
 [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] 提供許多適合繫結的資料結構。  在精密度和複雜度上各有不同。  
  
-   <xref:System.Data.DataColumn>.  <xref:System.Data.DataColumn> 是 <xref:System.Data.DataTable> 的基本建置組塊，因為資料表是由一些資料行組成的。  每一個 <xref:System.Data.DataColumn> 都有一個 <xref:System.Data.DataColumn.DataType%2A> 屬性，決定該資料行所儲存資料的種類 \(例如，在描述汽車的資料表當中的汽車車款\)。  您可以將控制項 \(例如 <xref:System.Windows.Forms.TextBox> 控制項的 <xref:System.Windows.Forms.Control.Text%2A> 屬性\) 簡單繫結至資料表中的資料行。  
  
-   <xref:System.Data.DataTable>.  <xref:System.Data.DataTable> 是 [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] 中具有資料列和資料行的資料表表示。  資料表包含兩個集合：代表特定資料表中各資料行的 <xref:System.Data.DataColumn> \(決定最後何種資料可輸入該資料表\)，和代表特定資料表中各資料列的 <xref:System.Data.DataRow>。  您可以將控制項複雜繫結至資料表中包含的資訊 \(例如將 <xref:System.Windows.Forms.DataGridView> 控制項繫結至資料表\)。  但是，當您繫結至 <xref:System.Data.DataTable> 時，您實際上是繫結至該資料表的預設檢視。  
  
-   <xref:System.Data.DataView>.  <xref:System.Data.DataView> 是可篩選或排序之單一資料表的自訂檢視。  資料檢視表是複雜繫結 \(Complex\-Bound\) 控制項所使用的資料「快照」。  您可以簡單繫結或複雜繫結至資料檢視表中的資料，但請注意，您是繫結至資料的固定「畫面」，而不是單純的更新資料來源。  
  
-   <xref:System.Data.DataSet>.  <xref:System.Data.DataSet> 是資料庫中資料表、關聯性與資料條件約束的集合。  您可以簡單繫結或複雜繫結至資料集中的資料，但請注意，您是繫結至 <xref:System.Data.DataSet> 的預設 <xref:System.Data.DataViewManager> \(請參閱下一個項目符號\)。  
  
-   <xref:System.Data.DataViewManager>.  <xref:System.Data.DataViewManager> 是整個 <xref:System.Data.DataSet> 的自訂檢視，類似於 <xref:System.Data.DataView>，但是包含關聯。  <xref:System.Data.DataViewManager.DataViewSettings%2A> 集合可讓您針對特定資料表的 <xref:System.Data.DataViewManager> 所擁有的任何檢視，設定預設篩選條件和排序選項。  
  
## 請參閱  
 [Windows Form 資料繫結中的變更告知](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)   
 [資料繫結和 Windows Form](../../../docs/framework/winforms/data-binding-and-windows-forms.md)   
 [Windows Form 資料繫結](../../../docs/framework/winforms/windows-forms-data-binding.md)
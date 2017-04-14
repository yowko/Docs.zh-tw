---
title: "DataGridView 控制項架構 (Windows Form) | Microsoft Docs"
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
  - "DataGridView 控制項 [Windows Form], 架構"
ms.assetid: 1c6cabf0-02ee-4bbc-9574-b54bb7f5b19e
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# DataGridView 控制項架構 (Windows Form)
<xref:System.Windows.Forms.DataGridView> 控制項及其相關的類別是設計成一個用來顯示和編輯表格式資料的彈性、可擴充系統。  這些類別都包含在 <xref:System.Windows.Forms?displayProperty=fullName> 命名空間中，而且全部都以 "DataGridView" 前置詞命名。  
  
## 架構項目  
 主要的 <xref:System.Windows.Forms.DataGridView> 附屬類別衍生自 <xref:System.Windows.Forms.DataGridViewElement>。  下列物件模型會說明 <xref:System.Windows.Forms.DataGridViewElement> 繼承階層架構。  
  
 ![DataGridViewElement 物件模型](../../../../docs/framework/winforms/controls/media/datagridviewelement.png "DataGridViewElement")  
DataGridViewElement 物件模型  
  
 <xref:System.Windows.Forms.DataGridViewElement> 類別會提供父代 <xref:System.Windows.Forms.DataGridView> 控制項的參考，而且具有 <xref:System.Windows.Forms.DataGridViewElement.State%2A> 屬性，此屬性包含一個值，用來代表來自 <xref:System.Windows.Forms.DataGridViewElementStates> 列舉型別的值組合。  
  
 下列幾節會詳細描述 <xref:System.Windows.Forms.DataGridView> 附屬類別。  
  
### DataGridViewElementStates  
 <xref:System.Windows.Forms.DataGridViewElementStates> 列舉型別包含下列值：  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates>  
  
 這個列舉型別的值可以使用位元邏輯運算子 \(Logical Operator\) 來加以組合，因此 <xref:System.Windows.Forms.DataGridViewElement.State%2A> 屬性可以一次表示超過一個狀態。  例如，<xref:System.Windows.Forms.DataGridViewElement> 可以同時是 <xref:System.Windows.Forms.DataGridViewElementStates>、<xref:System.Windows.Forms.DataGridViewElementStates> 和 <xref:System.Windows.Forms.DataGridViewElementStates>。  
  
### 儲存格和群組列  
 <xref:System.Windows.Forms.DataGridView> 控制項由兩種主要類型的物件組成：儲存格和群組列。  所有儲存格都衍生自 <xref:System.Windows.Forms.DataGridViewCell> 基底類別。  <xref:System.Windows.Forms.DataGridViewColumn> 和 <xref:System.Windows.Forms.DataGridViewRow> 這兩種群組列都是衍生自 <xref:System.Windows.Forms.DataGridViewBand> 基底類別。  
  
 <xref:System.Windows.Forms.DataGridView> 控制項會與幾個類別互通，但是最常遇到的是 <xref:System.Windows.Forms.DataGridViewCell>、<xref:System.Windows.Forms.DataGridViewColumn> 和 <xref:System.Windows.Forms.DataGridViewRow>。  
  
### DataGridViewCell  
 儲存格是 <xref:System.Windows.Forms.DataGridView> 的主要互動單位。  顯示會集中在儲存格上，而資料輸入通常也是透過儲存格執行。  您可以使用 <xref:System.Windows.Forms.DataGridViewRow> 類別的 <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> 集合來存取儲存格，並且可以使用 <xref:System.Windows.Forms.DataGridView> 控制項的 <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> 集合來存取選取的儲存格。  下列物件模型會說明此用法並顯示 <xref:System.Windows.Forms.DataGridViewCell> 繼承階層架構。  
  
 ![DataGridViewCell 物件模型](../../../../docs/framework/winforms/controls/media/datagridviewcell.png "DataGridViewCell")  
DataGridViewCell 物件模型  
  
 <xref:System.Windows.Forms.DataGridViewCell> 型別是一個抽象基底類別，所有資料格型別都是從它衍生出來的。  <xref:System.Windows.Forms.DataGridViewCell> 和其衍生型別都不是 Windows Form 控制項，而是一些裝載 Windows Form 控制項的控制項。  儲存格所支援的任何編輯功能通常都是由裝載控制項處理。  
  
 <xref:System.Windows.Forms.DataGridViewCell> 物件不會用和 Windows Form 控制項相同的方式來控制自己的外觀和繪製功能。  相反地，<xref:System.Windows.Forms.DataGridView> 會負責其 <xref:System.Windows.Forms.DataGridViewCell> 物件的外觀。  您可以透過與 <xref:System.Windows.Forms.DataGridView> 控制項的屬性和事件互動，大幅影響儲存格的外觀和行為。  當您有超過 <xref:System.Windows.Forms.DataGridView> 控制項能力的特殊自訂需求時，可以實作衍生自 <xref:System.Windows.Forms.DataGridViewCell> 或其中一個子類別的類別。  
  
 下列清單顯示衍生自 <xref:System.Windows.Forms.DataGridViewCell> 的類別：  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewButtonCell>  
  
-   <xref:System.Windows.Forms.DataGridViewLinkCell>  
  
-   <xref:System.Windows.Forms.DataGridViewCheckBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewImageCell>  
  
-   <xref:System.Windows.Forms.DataGridViewHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewRowHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewColumnHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell>  
  
-   您的自訂儲存格型別  
  
### DataGridViewColumn  
 <xref:System.Windows.Forms.DataGridView> 控制項的附加資料存放區的結構描述會在 <xref:System.Windows.Forms.DataGridView> 控制項的資料行中表示。  您可以使用 <xref:System.Windows.Forms.DataGridView.Columns%2A> 集合，存取 <xref:System.Windows.Forms.DataGridView> 控制項的資料行。  另外，可以使用 <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> 集合，存取選取的資料行。  下列物件模型會說明此用法並顯示 <xref:System.Windows.Forms.DataGridViewColumn> 繼承階層架構。  
  
 ![DataGridViewColumn 物件模型](../../../../docs/framework/winforms/controls/media/datagridviewcolumn.png "DataGridViewColumn")  
DataGridViewColumn 物件模型  
  
 某些主要的儲存格型別具有對應的資料行型別。  這些型別都是衍生自 <xref:System.Windows.Forms.DataGridViewColumn> 基底類別。  
  
 下列清單顯示衍生自 <xref:System.Windows.Forms.DataGridViewColumn> 的類別：  
  
-   <xref:System.Windows.Forms.DataGridViewButtonColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewImageColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewLinkColumn>  
  
-   您的自訂資料行型別  
  
### DataGridView 編輯控制項  
 支援進階編輯功能的儲存格通常會使用衍生自 Windows Form 控制項的裝載控制項。  這些控制項也實作 <xref:System.Windows.Forms.IDataGridViewEditingControl> 介面。  下列物件模型會說明這些控制項的用法。  
  
 ![DataGridView 編輯控制項物件模型](../../../../docs/framework/winforms/controls/media/datagridviewediting.png "DataGridViewEditing")  
DataGridView 編輯控制項物件模型  
  
 下列編輯控制項是由 <xref:System.Windows.Forms.DataGridView> 控制項所提供：  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>  
  
 如需建立自己的編輯控制項的詳細資訊，請參閱 [如何：Windows Form DataGridView 儲存格中的主控制項](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md)。  
  
 下表說明儲存格型別、資料行型別和編輯控制項之間的關聯性 \(Relationship\)。  
  
|儲存格型別|裝載控制項|資料行型別|  
|-----------|-----------|-----------|  
|<xref:System.Windows.Forms.DataGridViewButtonCell>|N\/A|<xref:System.Windows.Forms.DataGridViewButtonColumn>|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxCell>|N\/A|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewComboBoxCell>|<xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewImageCell>|N\/A|<xref:System.Windows.Forms.DataGridViewImageColumn>|  
|<xref:System.Windows.Forms.DataGridViewLinkCell>|N\/A|<xref:System.Windows.Forms.DataGridViewLinkColumn>|  
|<xref:System.Windows.Forms.DataGridViewTextBoxCell>|<xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|  
  
### DataGridViewRow  
 <xref:System.Windows.Forms.DataGridViewRow> 類別會從附加 <xref:System.Windows.Forms.DataGridView> 控制項的資料存放區，顯示資料錄的資料欄位。  您可以使用 <xref:System.Windows.Forms.DataGridView.Rows%2A> 集合，存取 <xref:System.Windows.Forms.DataGridView> 控制項的資料列。  另外，可以使用 <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> 集合，存取選取的資料列。  下列物件模型會說明此用法並顯示 <xref:System.Windows.Forms.DataGridViewRow> 繼承階層架構。  
  
 ![DataGridViewRow 物件模型](../../../../docs/framework/winforms/controls/media/datagridviewrow.png "DataGridViewRow")  
DataGridViewRow 物件模型  
  
 您可以從 <xref:System.Windows.Forms.DataGridViewRow> 類別衍生自己的型別，雖然通常不必如此。  <xref:System.Windows.Forms.DataGridView> 控制項具有幾個資料列相關的事件和屬性，用來自訂它的 <xref:System.Windows.Forms.DataGridViewRow> 物件的行為。  
  
 如果您啟用 <xref:System.Windows.Forms.DataGridView> 控制項的 <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> 屬性，會在最後一個資料列，顯示一個用來加入新資料列的特殊資料列。  這個資料列是 <xref:System.Windows.Forms.DataGridView.Rows%2A> 集合的一部分，但是它具有可能需要注意的特殊功能。  如需詳細資訊，請參閱 [使用 Windows Form DataGridView 控制項中用於新增資料錄的資料列](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)。  
  
## 請參閱  
 [DataGridView 控制項概觀](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)   
 [自訂 Windows Form DataGridView 控制項](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)   
 [使用 Windows Form DataGridView 控制項中用於新增資料錄的資料列](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
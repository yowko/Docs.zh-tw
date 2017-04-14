---
title: "Windows Form DataGridView 控制項中的資料行類型 | Microsoft Docs"
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
  - "資料行 [Windows Form], 類型"
  - "資料格, 資料行"
  - "DataGridView 控制項 [Windows Form], 資料行類型"
ms.assetid: f0a0a9f1-8757-4bfd-891f-d7d12870dbed
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# Windows Form DataGridView 控制項中的資料行類型
<xref:System.Windows.Forms.DataGridView> 控制項使用數種資料行型別來顯示資訊，並讓使用者可以修改或新增資訊。  
  
 當您繫結 <xref:System.Windows.Forms.DataGridView> 控制項，並將 <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> 屬性設定為 `true` 時，會使用適合繫結資料來源所包含資料型別的預設資料行型別自動產生資料行。  
  
 您也可以自行建立任何資料行類別的執行個體，並將這些執行個體加入至 <xref:System.Windows.Forms.DataGridView.Columns%2A> 屬性所傳回的集合。  您可建立這些執行個體做為未繫結的資料行，或者也可以用手動方式加以繫結。  例如，在您想要使用別種型別的資料行來取代自動產生的某種型別資料行時，以手動方式繫結資料行就非常有用。  
  
 下表說明可以在 <xref:System.Windows.Forms.DataGridView> 控制項中使用的各種資料行類別。  
  
|類別|描述|  
|--------|--------|  
|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|與文字基礎的值搭配使用。  當繫結至數字或字串時會自動產生。|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|與 <xref:System.Boolean> 和 <xref:System.Windows.Forms.CheckState> 值搭配使用。  當繫結至這些型別的值時會自動產生。|  
|<xref:System.Windows.Forms.DataGridViewImageColumn>|用來顯示影像。  當繫結至位元組陣列、<xref:System.Drawing.Image> 物件或 <xref:System.Drawing.Icon> 物件時，便會自動產生。|  
|<xref:System.Windows.Forms.DataGridViewButtonColumn>|用來顯示儲存格中的按鈕。  不會在繫結時自動產生。  通常用來做為未繫結資料行。|  
|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|用來顯示儲存格中的下拉式清單。  不會在繫結時自動產生。  通常以手動方式繫結至資料。|  
|<xref:System.Windows.Forms.DataGridViewLinkColumn>|用來顯示儲存格中的連結。  不會在繫結時自動產生。  通常以手動方式繫結至資料。|  
|您的自訂資料行型別|您可以建立自己的資料行類別，方法是繼承 <xref:System.Windows.Forms.DataGridViewColumn> 類別或其中一個衍生類別，以提供自訂外觀、行為或裝載控制項。  如需詳細資訊，請參閱 [如何：擴充儲存格和資料行的行為和外觀以自訂 Windows Form DataGridView 控制項中的儲存格和資料行](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)|  
  
 這些資料行型別在下列章節中有更詳細的說明。  
  
## DataGridViewTextBoxColumn  
 <xref:System.Windows.Forms.DataGridViewTextBoxColumn> 是一般目的的資料行型別，與文字基礎的值 \(例如數字和字串\) 搭配使用。  在編輯模式中，<xref:System.Windows.Forms.TextBox> 控制項會顯示於現用儲存格，讓使用者可以修改儲存格值。  
  
 儲存格值會自動轉換為顯示的字串。  會自動剖析使用者輸入或修改的值，以建立適當資料型別的儲存格值。  您可以藉由處理 <xref:System.Windows.Forms.DataGridView> 控制項的 <xref:System.Windows.Forms.DataGridView.CellFormatting> 和 <xref:System.Windows.Forms.DataGridView.CellParsing> 事件自訂這些轉換。  
  
 資料行的儲存格值資料型別是在資料行的 <xref:System.Windows.Forms.DataGridViewColumn.ValueType%2A> 屬性中加以指定。  
  
## DataGridViewCheckBoxColumn  
 <xref:System.Windows.Forms.DataGridViewCheckBoxColumn> 會與 <xref:System.Boolean> 和 <xref:System.Windows.Forms.CheckState> 值一起使用。  <xref:System.Boolean> 值會依 <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A> 屬性值而定，顯示為兩種狀態或三種狀態的核取方塊。  當資料行繫結至 <xref:System.Windows.Forms.CheckState> 值時，根據預設 <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A> 屬性值會為 `true`。  
  
 通常核取方塊值的目的是為了儲存 \(例如任何其他資料\) 或執行大量作業。  如果您想要在使用者按下核取方塊儲存格時立即回應，您可以處理 <xref:System.Windows.Forms.DataGridView.CellClick> 事件，但是這個事件會發生在更新此儲存格值之前。  如果當您按下此儲存格時需要有新的值，會有一個選項可以根據目前的值計算需要的值為何。  另一個方式是立即認可變更，以及處理 <xref:System.Windows.Forms.DataGridView.CellValueChanged> 事件來予以回應。  若要在按下儲存格時認可變更，您必須處理 <xref:System.Windows.Forms.DataGridView.CurrentCellDirtyStateChanged> 事件。  在處理常式中，如果目前的儲存格是核取方塊儲存格，則呼叫 <xref:System.Windows.Forms.DataGridView.CommitEdit%2A> 方法，並傳入 <xref:System.Windows.Forms.DataGridViewDataErrorContexts> 值。  
  
## DataGridViewImageColumn  
 <xref:System.Windows.Forms.DataGridViewImageColumn> 是用來顯示影像。  影像資料行可從資料來源自動填入，可以用手動方式為未繫結資料行填入，或動態填入 <xref:System.Windows.Forms.DataGridView.CellFormatting> 事件的處理常式。  
  
 資料來源的影像資料行的自動填入能使用於各種影像格式的位元組陣列，包括 <xref:System.Drawing.Image> 類別支援的所有格式，以及 Microsoft® Access 和 Northwind 範例資料庫的 OLE 圖片格式。  
  
 當您想提供 <xref:System.Windows.Forms.DataGridViewButtonColumn> 的功能，但又要有自訂外觀時，以手動方式填入影像資料行會很有用。  您可以處理 <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=fullName> 事件以回應在影像儲存格內按選的動作。  
  
 當您想為計算值或非影像格式的值提供影像時，在 <xref:System.Windows.Forms.DataGridView.CellFormatting> 事件的處理常式中填入影像資料行的儲存格，會是很有用的方式。  例如，您可能有一個「風險」資料行，其中包含 `"high"`、`"middle"` 和 `"low"` 等您想要顯示為圖示的字串值。  此外，也可能有「影像」資料行，其中包含的是必須載入的影像的位置，而非影像的二進位內容。  
  
## DataGridViewButtonColumn  
 藉由 <xref:System.Windows.Forms.DataGridViewButtonColumn>，可以顯示包含按鈕的儲存格資料行。  當您想為使用者提供在特定資料錄上執行動作的簡易方法 \(例如在不同的視窗中下訂單或顯示子資料錄\)，這將會很有用。  
  
 當資料繫結 <xref:System.Windows.Forms.DataGridView> 控制項時，不會自動產生按鈕資料行。  若要使用按鈕資料行，您必須以手動方式加以建立，並將它們加入至 <xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=fullName> 屬性傳回的集合。  
  
 您可以透過處理 <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=fullName> 事件，回應使用者在按鈕儲存格中的按選動作。  
  
## DataGridViewComboBoxColumn  
 藉由 <xref:System.Windows.Forms.DataGridViewComboBoxColumn>，您可以顯示包含下拉式清單方塊的儲存格資料行。  若要在只能包含特定值的欄位中輸入資料 \(例如，Northwind 範例資料庫中 Products 資料表的 Category 資料行\)，這會非常有用。  
  
 您可以使用填入 <xref:System.Windows.Forms.ComboBox> 下拉式清單的相同方式，填入用於所有儲存格的下拉式清單；一種方法是透過 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> 屬性傳回的集合，以手動方式進行，另一種方法則是透過 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A>、<xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> 和 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> 屬性，將清單繫結至資料來源。  如需詳細資訊，請參閱 [ComboBox 控制項](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md)。  
  
 您可以繫結實際的儲存格值至 <xref:System.Windows.Forms.DataGridView> 控制項所使用的資料來源，方法是設定 <xref:System.Windows.Forms.DataGridViewComboBoxColumn?displayProperty=fullName> 的 <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A> 屬性。  
  
 下拉式方塊資料行不會在資料繫結 <xref:System.Windows.Forms.DataGridView> 控制項時自動產生。  若要使用下拉式方塊資料行，您必須以手動方式加以建立，並將它們加入至 <xref:System.Windows.Forms.DataGridView.Columns%2A> 屬性傳回的集合。  
  
## DataGridViewLinkColumn  
 藉由 <xref:System.Windows.Forms.DataGridViewLinkColumn>，您可以顯示包含超連結的儲存格資料行。  這對於資料來源中的 URL 值，或做為特殊行為 \(例如使用子資料錄開啟視窗\) 按鈕資料行的替代方法，都非常有用。  
  
 在資料繫結 <xref:System.Windows.Forms.DataGridView> 控制項時不會自動產生連結資料行。  若要使用連結資料行，您必須以手動方式加以建立，並將它們加入至 <xref:System.Windows.Forms.DataGridView.Columns%2A> 屬性傳回的集合。  
  
 您可以透過處理 <xref:System.Windows.Forms.DataGridView.CellContentClick> 事件，回應使用者按選連結的動作。  這個事件有別於 <xref:System.Windows.Forms.DataGridView.CellClick> 和 <xref:System.Windows.Forms.DataGridView.CellMouseClick> 事件，後兩者是發生在使用者按選儲存格內的任何位置時。  
  
 <xref:System.Windows.Forms.DataGridViewLinkColumn> 類別會提供數種屬性，可在按選連結前、按選連結的期間和按選連結後修改連結的外觀。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewColumn>   
 <xref:System.Windows.Forms.DataGridViewButtonColumn>   
 <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>   
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn>   
 <xref:System.Windows.Forms.DataGridViewImageColumn>   
 <xref:System.Windows.Forms.DataGridViewTextBoxColumn>   
 <xref:System.Windows.Forms.DataGridViewLinkColumn>   
 [DataGridView 控制項](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)   
 [如何：顯示 Windows Form DataGridView 控制項的儲存格影像](../../../../docs/framework/winforms/controls/how-to-display-images-in-cells-of-the-windows-forms-datagridview-control.md)   
 [如何：使用 Windows Form DataGridView 控制項中的影像資料行](../../../../docs/framework/winforms/controls/how-to-work-with-image-columns-in-the-windows-forms-datagridview-control.md)   
 [自訂 Windows Form DataGridView 控制項](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)
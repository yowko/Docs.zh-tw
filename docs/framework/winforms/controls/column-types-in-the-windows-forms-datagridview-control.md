---
title: DataGridView 控制項中的資料行類型
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], types
- DataGridView control [Windows Forms], column types
- data grids [Windows Forms], columns
ms.assetid: f0a0a9f1-8757-4bfd-891f-d7d12870dbed
ms.openlocfilehash: e918394cca6350854074d4c1567890138b2a1462
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743862"
---
# <a name="column-types-in-the-windows-forms-datagridview-control"></a>Windows Form DataGridView 控制項中的資料行類型
<xref:System.Windows.Forms.DataGridView> 控制項使用數種資料行類型來顯示其資訊，並可讓使用者修改或加入資訊。  
  
 當您系結 <xref:System.Windows.Forms.DataGridView> 控制項並將 <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> 屬性設定為 [`true`] 時，會使用適用于系結資料來源中所包含之資料類型的預設資料行類型，自動產生資料行。  
  
 您也可以自行建立任何資料行類別的實例，並將它們加入至 <xref:System.Windows.Forms.DataGridView.Columns%2A> 屬性所傳回的集合。 您可以建立這些實例作為未系結的資料行，也可以手動系結它們。 手動系結的資料行很有用，例如，當您想要將一個類型的自動產生資料行取代為另一個類型的資料行時。  
  
 下表描述可在 <xref:System.Windows.Forms.DataGridView> 控制項中使用的各種資料行類別。  
  
|類別|描述|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|搭配以文字為基礎的值使用。 系結至數位和字串時自動產生。|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|與 <xref:System.Boolean> 和 <xref:System.Windows.Forms.CheckState> 值搭配使用。 系結至這些類型的值時自動產生。|  
|<xref:System.Windows.Forms.DataGridViewImageColumn>|用來顯示影像。 系結至位元組陣列、<xref:System.Drawing.Image> 物件或 <xref:System.Drawing.Icon> 物件時自動產生。|  
|<xref:System.Windows.Forms.DataGridViewButtonColumn>|用來顯示儲存格中的按鈕。 系結時不會自動產生。 通常當做未系結的資料行使用。|  
|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|用來顯示資料格的下拉式清單。 系結時不會自動產生。 通常是以手動方式進行資料系結。|  
|<xref:System.Windows.Forms.DataGridViewLinkColumn>|用來顯示儲存格中的連結。 系結時不會自動產生。 通常是以手動方式進行資料系結。|  
|您的自訂資料行類型|您可以藉由繼承 <xref:System.Windows.Forms.DataGridViewColumn> 類別或其任何衍生類別來建立自己的資料行類別，以提供自訂的外觀、行為或裝載的控制項。 如需詳細資訊，請參閱[如何：藉由擴充其行為和外觀，自訂 Windows Forms DataGridView 控制項中的儲存格和資料行](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)|  
  
 下列各節將更詳細地描述這些資料行類型。  
  
## <a name="datagridviewtextboxcolumn"></a>[Datagridviewtextboxcolumn]  
 <xref:System.Windows.Forms.DataGridViewTextBoxColumn> 是一般用途的資料行類型，可與以文字為基礎的值（例如數位和字串）搭配使用。 在編輯模式中，[<xref:System.Windows.Forms.TextBox>] 控制項會顯示在使用中的儲存格，讓使用者可以修改資料格的值。  
  
 資料格值會自動轉換成字串以供顯示。 使用者所輸入或修改的值會自動進行剖析，以建立適當資料類型的儲存格值。 您可以藉由處理 <xref:System.Windows.Forms.DataGridView> 控制項的 <xref:System.Windows.Forms.DataGridView.CellFormatting> 和 <xref:System.Windows.Forms.DataGridView.CellParsing> 事件來自訂這些轉換。  
  
 資料行的資料格值資料類型是在資料行的 <xref:System.Windows.Forms.DataGridViewColumn.ValueType%2A> 屬性中指定。  
  
## <a name="datagridviewcheckboxcolumn"></a>DataGridViewCheckBoxColumn  
 <xref:System.Windows.Forms.DataGridViewCheckBoxColumn> 用於 <xref:System.Boolean> 和 <xref:System.Windows.Forms.CheckState> 值。 <xref:System.Boolean> 值會顯示為兩個狀態或三個狀態的核取方塊，視 <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A> 屬性的值而定。 當資料行系結至 <xref:System.Windows.Forms.CheckState> 值時，預設會 `true` <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A> 屬性值。  
  
 一般來說，核取方塊的資料格值適用于儲存體，就像任何其他資料一樣，或用於執行大量作業。 如果您想要在使用者按一下核取方塊資料格時立即回應，您可以處理 <xref:System.Windows.Forms.DataGridView.CellClick> 事件，但在更新資料格值之前，會發生此事件。 如果您在按一下時需要新的值，其中一個選項是根據目前的值計算預期的值。 另一種方法是立即認可變更，並處理 <xref:System.Windows.Forms.DataGridView.CellValueChanged> 事件以回應它。 若要在按一下資料格時認可變更，您必須處理 <xref:System.Windows.Forms.DataGridView.CurrentCellDirtyStateChanged> 事件。 在處理常式中，如果當前儲存格是核取方塊資料格，請呼叫 <xref:System.Windows.Forms.DataGridView.CommitEdit%2A> 方法，並傳入 <xref:System.Windows.Forms.DataGridViewDataErrorContexts.Commit> 值。  
  
## <a name="datagridviewimagecolumn"></a>DataGridViewImageColumn  
 <xref:System.Windows.Forms.DataGridViewImageColumn> 可用來顯示影像。 您可以從資料來源自動填入影像資料行、針對未系結的資料行手動填入，或在 <xref:System.Windows.Forms.DataGridView.CellFormatting> 事件的處理常式中以動態方式填入。  
  
 資料來源中的影像資料行自動填入會使用各種影像格式的位元組陣列，包括 <xref:System.Drawing.Image> 類別支援的所有格式，以及 Microsoft® Access 和 Northwind 範例資料庫所使用的 OLE 圖片格式。  
  
 當您想要提供 <xref:System.Windows.Forms.DataGridViewButtonColumn>的功能，但有自訂的外觀時，手動填入影像資料行非常有用。 您可以處理 <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> 事件，以回應影像資料格內的按下動作。  
  
 當您想要以非影像格式提供計算值或值的影像時，在 <xref:System.Windows.Forms.DataGridView.CellFormatting> 事件的處理常式中填入影像資料行的資料格會很有用。 例如，您可能會有 [風險] 資料行，其中包含您想要顯示為圖示的字串值，例如 `"high"`、`"middle"`和 `"low"`。 或者，您可能會有「影像」資料行，其中包含必須載入的映射位置，而不是影像的二進位內容。  
  
## <a name="datagridviewbuttoncolumn"></a>DataGridViewButtonColumn  
 使用 <xref:System.Windows.Forms.DataGridViewButtonColumn>，您可以顯示包含按鈕的資料格資料行。 當您想要為使用者提供簡單的方式來執行特定記錄的動作（例如，在另一個視窗中放置訂單或顯示子記錄）時，這會很有用。  
  
 資料系結 <xref:System.Windows.Forms.DataGridView> 控制項時，不會自動產生按鈕資料行。 若要使用按鈕資料行，您必須手動建立它們，並將它們加入至 <xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=nameWithType> 屬性所傳回的集合。  
  
 您可以藉由處理 <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> 事件來回應使用者在按鈕資料格中按一下的動作。  
  
## <a name="datagridviewcomboboxcolumn"></a>System.windows.forms.domainupdown system.windows.forms.numericupdown system.windows.forms.datagridviewcomboboxcolumn  
 使用 <xref:System.Windows.Forms.DataGridViewComboBoxColumn>，您可以顯示包含下拉式清單方塊的資料格資料行。 對於只能包含特定值的欄位（例如 Northwind 範例資料庫中 Products 資料表的 Category 資料行），這項功能非常有用。  
  
 您可以用相同的方式填入所有資料格所使用的下拉式清單，<xref:System.Windows.Forms.ComboBox> 方法是手動透過 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> 屬性所傳回的集合，或透過 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A>、<xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A>和 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> 屬性將它系結至資料來源。 如需詳細資訊，請參閱[ComboBox 控制項](combobox-control-windows-forms.md)。  
  
 您可以藉由設定 <xref:System.Windows.Forms.DataGridViewComboBoxColumn?displayProperty=nameWithType>的 <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A> 屬性，將實際的儲存格值系結至 <xref:System.Windows.Forms.DataGridView> 控制項所使用的資料來源。  
  
 當資料系結 <xref:System.Windows.Forms.DataGridView> 控制項時，不會自動產生下拉式方塊資料行。 若要使用下拉式方塊資料行，您必須手動建立它們，並將它們加入至 <xref:System.Windows.Forms.DataGridView.Columns%2A> 屬性所傳回的集合。  
  
## <a name="datagridviewlinkcolumn"></a>DataGridViewLinkColumn  
 使用 <xref:System.Windows.Forms.DataGridViewLinkColumn>，您可以顯示包含超連結之資料格的資料行。 這適用于資料來源中的 URL 值，或做為特殊行為（例如開啟含有子記錄的視窗）的 [按鈕] 欄位的替代方法。  
  
 當資料系結 <xref:System.Windows.Forms.DataGridView> 控制項時，不會自動產生連結資料行。 若要使用連結資料行，您必須手動建立它們，並將它們加入至 <xref:System.Windows.Forms.DataGridView.Columns%2A> 屬性所傳回的集合。  
  
 您可以藉由處理 <xref:System.Windows.Forms.DataGridView.CellContentClick> 事件來回應使用者按一下連結的動作。 這個事件與 <xref:System.Windows.Forms.DataGridView.CellClick> 和 <xref:System.Windows.Forms.DataGridView.CellMouseClick> 的事件不同，這會在使用者按一下資料格中的任何位置時發生。  
  
 <xref:System.Windows.Forms.DataGridViewLinkColumn> 類別提供數個屬性，可在按一下連結之前、期間和之後修改其外觀。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewButtonColumn>
- <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn>
- <xref:System.Windows.Forms.DataGridViewImageColumn>
- <xref:System.Windows.Forms.DataGridViewTextBoxColumn>
- <xref:System.Windows.Forms.DataGridViewLinkColumn>
- [DataGridView 控制項](datagridview-control-windows-forms.md)
- [如何：顯示 Windows Form DataGridView 控制項的儲存格影像](how-to-display-images-in-cells-of-the-windows-forms-datagridview-control.md)
- [操作說明：使用 Windows Forms DataGridView 控制項中的影像資料行](how-to-work-with-image-columns-in-the-windows-forms-datagridview-control.md)
- [自訂 Windows Forms DataGridView 控制項](customizing-the-windows-forms-datagridview-control.md)

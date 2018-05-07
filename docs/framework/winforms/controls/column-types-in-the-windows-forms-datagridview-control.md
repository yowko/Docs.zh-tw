---
title: Windows Form DataGridView 控制項中的資料行類型
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], types
- DataGridView control [Windows Forms], column types
- data grids [Windows Forms], columns
ms.assetid: f0a0a9f1-8757-4bfd-891f-d7d12870dbed
ms.openlocfilehash: 6630323b66265f478151ec80ab8b225c0b653917
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="column-types-in-the-windows-forms-datagridview-control"></a>Windows Form DataGridView 控制項中的資料行類型
<xref:System.Windows.Forms.DataGridView>控制項使用數個資料行類型來顯示它的資訊，並讓使用者修改或新增資訊。  
  
 當您繫結<xref:System.Windows.Forms.DataGridView>控制以及設定<xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A>屬性`true`，會自動產生資料行使用適當繫結的資料來源中所包含的資料類型的預設資料行類型。  
  
 您也可以自行建立的任何資料行類別的執行個體，並將它們加入至所傳回的集合<xref:System.Windows.Forms.DataGridView.Columns%2A>屬性。 您可以建立這些執行個體做為未繫結的資料行，或您可以手動將其繫結。 手動繫結資料行都可用，例如，當您想要取代另一個類型的資料行中的一種類型的自動產生資料行。  
  
 下表描述可用於不同的資料行類別<xref:System.Windows.Forms.DataGridView>控制項。  
  
|類別|描述|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|搭配使用以文字為基礎的值。 繫結至數字與字串時自動產生。|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|搭配<xref:System.Boolean>和<xref:System.Windows.Forms.CheckState>值。 繫結至這些類型的值時自動產生。|  
|<xref:System.Windows.Forms.DataGridViewImageColumn>|用來顯示影像。 繫結至位元組陣列時自動產生<xref:System.Drawing.Image>物件，或<xref:System.Drawing.Icon>物件。|  
|<xref:System.Windows.Forms.DataGridViewButtonColumn>|用來在資料格中顯示的按鈕。 繫結時，不會自動產生。 通常做為未繫結的資料行。|  
|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|用來顯示下拉式清單中的資料格。 繫結時，不會自動產生。 通常資料繫結以手動方式。|  
|<xref:System.Windows.Forms.DataGridViewLinkColumn>|用來在儲存格中顯示的連結。 繫結時，不會自動產生。 通常資料繫結以手動方式。|  
|自訂資料行類型|您可以建立您自己的資料行類別繼承<xref:System.Windows.Forms.DataGridViewColumn>類別或任何其衍生的類別，以提供自訂外觀、 行為或裝載的控制項。 如需詳細資訊，請參閱[How to： 自訂資料格和擴充其行為和外觀的 Windows Form DataGridView 控制項中的資料行](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)|  
  
 在下列各節中詳細說明這些資料行類型。  
  
## <a name="datagridviewtextboxcolumn"></a>DataGridViewTextBoxColumn  
 <xref:System.Windows.Forms.DataGridViewTextBoxColumn>是以文字為基礎的值，例如數字與字串搭配使用的一般用途資料行類型。 在編輯模式下，<xref:System.Windows.Forms.TextBox>控制項會顯示在作用中的資料格，讓使用者修改資料格的值。  
  
 資料格的值會自動轉換成字串來顯示。 若要建立適當的資料類型的資料格的值，會自動剖析值輸入或修改的使用者。 您可以自訂這些轉換處理<xref:System.Windows.Forms.DataGridView.CellFormatting>和<xref:System.Windows.Forms.DataGridView.CellParsing>事件<xref:System.Windows.Forms.DataGridView>控制項。  
  
 資料格的值資料類型資料行中指定<xref:System.Windows.Forms.DataGridViewColumn.ValueType%2A>資料行屬性。  
  
## <a name="datagridviewcheckboxcolumn"></a>DataGridViewCheckBoxColumn  
 <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>搭配<xref:System.Boolean>和<xref:System.Windows.Forms.CheckState>值。 <xref:System.Boolean> 值會顯示兩個狀態或三種狀態核取方塊，根據的值為<xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A>屬性。 當資料行繫結至<xref:System.Windows.Forms.CheckState>值<xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A>屬性值是`true`預設。  
  
 一般而言，核取方塊儲存格的值是用於存放裝置，例如任何其他資料，或執行大量作業。 如果您想要立即當使用者按一下核取方塊儲存格，您可以處理回應<xref:System.Windows.Forms.DataGridView.CellClick>事件，但是此事件發生於儲存格的值會更新之前。 如果您在按一下時需要新的值，其中一個選項是計算預期的值將會根據目前的值。 另一個方法是立即認可變更，並處理<xref:System.Windows.Forms.DataGridView.CellValueChanged>回應它的事件。 若要在按下儲存格時，請認可變更，您必須處理<xref:System.Windows.Forms.DataGridView.CurrentCellDirtyStateChanged>事件。 在處理常式中，核取方塊儲存格的目前儲存格時，呼叫<xref:System.Windows.Forms.DataGridView.CommitEdit%2A>方法並傳入<xref:System.Windows.Forms.DataGridViewDataErrorContexts.Commit>值。  
  
## <a name="datagridviewimagecolumn"></a>DataGridViewImageColumn  
 <xref:System.Windows.Forms.DataGridViewImageColumn>用來顯示影像。 Image 資料行可以從資料來源會自動填入、 手動填入未繫結的資料行，或處理常式中自動填入<xref:System.Windows.Forms.DataGridView.CellFormatting>事件。  
  
 自動母體擴展的影像資料行從資料來源可搭配各種不同的影像格式，包括支援的所有格式的位元組陣列<xref:System.Drawing.Image>類別和 Microsoft® Access 和 Northwind 範例資料庫所使用的 OLE 圖片格式。  
  
 手動擴展 image 資料行時，您想要提供的功能<xref:System.Windows.Forms.DataGridViewButtonColumn>，但使用自訂的外觀。 您可以處理<xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType>事件回應影像資料格內按一下。  
  
 填入映像中的資料行的處理常式的儲存格<xref:System.Windows.Forms.DataGridView.CellFormatting>事件時，您想要提供映像的導出的值或非影像格式的值。 例如，您可能有字串值的 「 風險 」 資料行這類`"high"`， `"middle"`，和`"low"`您想要顯示為圖示。 或者，您可能會有 「 影像 」 資料行包含必須載入而不是二進位內容的映像的映像的位置。  
  
## <a name="datagridviewbuttoncolumn"></a>DataGridViewButtonColumn  
 與<xref:System.Windows.Forms.DataGridViewButtonColumn>，您可以顯示的資料格包含按鈕的資料行。 當您想要提供一個簡單的方式，為您的使用者執行動作的特定記錄，例如訂單或個別視窗中顯示子資料錄時，這非常有用。  
  
 當資料繫結不會自動產生按鈕資料行<xref:System.Windows.Forms.DataGridView>控制項。 若要使用按鈕資料行，您必須手動建立關聯，並將它們加入至所傳回的集合<xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=nameWithType>屬性。  
  
 您可以藉由處理回應使用者按一下按鈕儲存格<xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType>事件。  
  
## <a name="datagridviewcomboboxcolumn"></a>DataGridViewComboBoxColumn  
 與<xref:System.Windows.Forms.DataGridViewComboBoxColumn>，您可以顯示的資料行包含下拉式清單方塊的資料格。 這適用於資料輸入欄位只能包含特定值，例如 Northwind 範例資料庫中的 [產品] 資料表的類別資料行中。  
  
 您可以填入所有儲存格使用相同的方式會填入下拉式清單<xref:System.Windows.Forms.ComboBox>下拉式清單中，以手動方式透過所傳回的集合<xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A>屬性，或繫結至資料來源透過<xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A>， <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A>，和<xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A>屬性。 如需詳細資訊，請參閱[ComboBox 控制項](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md)。  
  
 您可以使用資料來源繫結的實際資料格值<xref:System.Windows.Forms.DataGridView>藉由設定控制<xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A>屬性<xref:System.Windows.Forms.DataGridViewComboBoxColumn?displayProperty=nameWithType>。  
  
 當資料繫結不會自動產生下拉式方塊的資料行<xref:System.Windows.Forms.DataGridView>控制項。 若要使用下拉式方塊的資料行，您必須手動建立關聯，並將它們加入至所傳回的集合<xref:System.Windows.Forms.DataGridView.Columns%2A>屬性。  
  
## <a name="datagridviewlinkcolumn"></a>DataGridViewLinkColumn  
 與<xref:System.Windows.Forms.DataGridViewLinkColumn>，您可以顯示的資料行的資料格包含超連結。 這是適用於資料來源中或特殊行為，例如開啟視窗的子記錄的按鈕資料行的替代方式的 URL 值。  
  
 當資料繫結不會自動產生連結資料行<xref:System.Windows.Forms.DataGridView>控制項。 若要使用連結的資料行，您必須手動建立關聯，並將它們加入至所傳回的集合<xref:System.Windows.Forms.DataGridView.Columns%2A>屬性。  
  
 您可以藉由處理回應使用者按一下連結<xref:System.Windows.Forms.DataGridView.CellContentClick>事件。 此事件會有所區別<xref:System.Windows.Forms.DataGridView.CellClick>和<xref:System.Windows.Forms.DataGridView.CellMouseClick>使用者按一下資料格中的任何地方時，會發生的事件。  
  
 <xref:System.Windows.Forms.DataGridViewLinkColumn>類別提供數個屬性，修改連結的外觀之前,、 期間和之後按一下。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <xref:System.Windows.Forms.DataGridViewButtonColumn>  
 <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
 <xref:System.Windows.Forms.DataGridViewImageColumn>  
 <xref:System.Windows.Forms.DataGridViewTextBoxColumn>  
 <xref:System.Windows.Forms.DataGridViewLinkColumn>  
 [DataGridView 控制項](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [操作說明：顯示 Windows Form DataGridView 控制項的儲存格影像](../../../../docs/framework/winforms/controls/how-to-display-images-in-cells-of-the-windows-forms-datagridview-control.md)  
 [操作說明：使用 Windows Forms DataGridView 控制項中的影像資料行](../../../../docs/framework/winforms/controls/how-to-work-with-image-columns-in-the-windows-forms-datagridview-control.md)  
 [自訂 Windows Forms DataGridView 控制項](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)

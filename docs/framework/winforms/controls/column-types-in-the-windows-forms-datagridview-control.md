---
title: Windows Form DataGridView 控制項中的資料行類型
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], types
- DataGridView control [Windows Forms], column types
- data grids [Windows Forms], columns
ms.assetid: f0a0a9f1-8757-4bfd-891f-d7d12870dbed
ms.openlocfilehash: d4331d5f502165a73c7f322358b2d6ee88d92977
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54591577"
---
# <a name="column-types-in-the-windows-forms-datagridview-control"></a>Windows Form DataGridView 控制項中的資料行類型
<xref:System.Windows.Forms.DataGridView>控制項會用來顯示其資訊，並讓使用者能夠修改或新增資訊的許多資料行類型。  
  
 當您繫結<xref:System.Windows.Forms.DataGridView>控制項，並將<xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A>屬性設`true`，會自動產生資料行使用適當的繫結的資料來源中包含的資料類型的預設資料行類型。  
  
 您也可以自行建立的任何資料行類別的執行個體，並將它們新增至所傳回的集合<xref:System.Windows.Forms.DataGridView.Columns%2A>屬性。 您可以建立這些執行個體做為未繫結的資料行，或者您可以手動將其繫結。 手動繫結資料行是很有用，比方說，當您想要取代另一個類型的資料行中的一種類型的自動產生資料行。  
  
 下表描述可用於不同的資料行類別<xref:System.Windows.Forms.DataGridView>控制項。  
  
|類別|描述|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|搭配使用以文字為基礎的值。 繫結至數字和字串時自動產生。|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|搭配<xref:System.Boolean>和<xref:System.Windows.Forms.CheckState>值。 繫結至這些類型的值時自動產生。|  
|<xref:System.Windows.Forms.DataGridViewImageColumn>|用來顯示影像。 繫結至位元組陣列時自動產生<xref:System.Drawing.Image>物件，或<xref:System.Drawing.Icon>物件。|  
|<xref:System.Windows.Forms.DataGridViewButtonColumn>|用來在儲存格中顯示按鈕。 繫結時，不會自動產生。 通常做為未繫結的資料行。|  
|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|用來顯示下拉式清單中的資料格。 繫結時，不會自動產生。 通常資料繫結以手動方式。|  
|<xref:System.Windows.Forms.DataGridViewLinkColumn>|用來在儲存格中顯示連結。 繫結時，不會自動產生。 通常資料繫結以手動方式。|  
|您的自訂資料行類型|您可以建立您自己的資料行類別繼承<xref:System.Windows.Forms.DataGridViewColumn>類別或任何其衍生的類別，以提供自訂外觀、 行為或裝載的控制項。 如需詳細資訊，請參閱[＜How to：自訂儲存格和 Windows Form DataGridView 控制項中的資料行，藉由擴充其行為和外觀](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)|  
  
 這些資料行類型是以更多詳細資料，在下列各節中所述。  
  
## <a name="datagridviewtextboxcolumn"></a>DataGridViewTextBoxColumn  
 <xref:System.Windows.Forms.DataGridViewTextBoxColumn>是以文字為基礎的值，例如數字和字串搭配使用的一般用途的資料行類型。 在編輯模式中，<xref:System.Windows.Forms.TextBox>控制項顯示在作用中資料格，讓使用者能夠修改儲存格的值。  
  
 資料格的值會自動轉換成供顯示的字串。 輸入，或由使用者修改的值會自動剖析，以建立適當的資料類型的儲存格值。 您可以自訂這些轉換，藉由處理<xref:System.Windows.Forms.DataGridView.CellFormatting>並<xref:System.Windows.Forms.DataGridView.CellParsing>事件的<xref:System.Windows.Forms.DataGridView>控制項。  
  
 中指定資料行的資料格的值資料型別<xref:System.Windows.Forms.DataGridViewColumn.ValueType%2A>資料行屬性。  
  
## <a name="datagridviewcheckboxcolumn"></a>DataGridViewCheckBoxColumn  
 <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>搭配<xref:System.Boolean>和<xref:System.Windows.Forms.CheckState>值。 <xref:System.Boolean> 值會顯示兩個狀態或三態核取方塊，這會根據的值為<xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A>屬性。 當資料行繫結至<xref:System.Windows.Forms.CheckState>值，<xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A>屬性值是`true`預設。  
  
 一般而言，核取方塊儲存格的值是針對儲存體，就像任何其他資料，或針對執行大量作業。 如果您想要回應立即當使用者按一下核取方塊儲存格，您可以處理<xref:System.Windows.Forms.DataGridView.CellClick>事件，但是這個事件發生才會更新資料格的值。 如果您在按一下時需要新的值，其中一個選項是計算預期的值將會根據目前的值。 另一個方法是立即認可變更，並處理<xref:System.Windows.Forms.DataGridView.CellValueChanged>回應事件。 若要認可變更，按一下儲存格時，您必須處理<xref:System.Windows.Forms.DataGridView.CurrentCellDirtyStateChanged>事件。 在處理常式中，核取方塊儲存格的目前儲存格時，呼叫<xref:System.Windows.Forms.DataGridView.CommitEdit%2A>方法並傳入<xref:System.Windows.Forms.DataGridViewDataErrorContexts.Commit>值。  
  
## <a name="datagridviewimagecolumn"></a>DataGridViewImageColumn  
 <xref:System.Windows.Forms.DataGridViewImageColumn>用來顯示影像。 Image 資料行可以從資料來源自動填入、 手動填入未繫結的資料行，或處理常式中動態填入<xref:System.Windows.Forms.DataGridView.CellFormatting>事件。  
  
 自動母體擴展的影像資料行從資料來源搭配各種不同的映像格式，包括支援的所有格式的位元組陣列<xref:System.Drawing.Image>類別和使用 Microsoft® Access 和 Northwind 範例資料庫的 OLE 圖片格式。  
  
 當您想要提供的功能手動填入 image 資料行是有用<xref:System.Windows.Forms.DataGridViewButtonColumn>，但使用自訂的外觀。 您可以處理<xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType>回應按下後的映像資料格內的事件。  
  
 填入映像中的資料行的處理常式的儲存格<xref:System.Windows.Forms.DataGridView.CellFormatting>事件很有用，當您想要提供映像的導出的值或非映像格式的值。 比方說，您可能會有字串值的 「 風險 」 資料行這類`"high"`， `"middle"`，和`"low"`您想要顯示為圖示。 或者，您可能有 「 映像 」 資料行包含必須載入，而不是二進位內容的映像的映像的位置。  
  
## <a name="datagridviewbuttoncolumn"></a>DataGridViewButtonColumn  
 使用<xref:System.Windows.Forms.DataGridViewButtonColumn>，您可以顯示包含按鈕的資料格的資料行。 當您想要提供簡單的方式，讓使用者可在特定的記錄，例如下訂單，或在另一個視窗中顯示子記錄上執行動作時，這非常有用。  
  
 當資料繫結不會自動產生按鈕資料行<xref:System.Windows.Forms.DataGridView>控制項。 若要使用按鈕資料行，您必須手動加以建立，並將它們新增至所傳回的集合<xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=nameWithType>屬性。  
  
 您可以藉由處理回應使用者按一下按鈕儲存格<xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType>事件。  
  
## <a name="datagridviewcomboboxcolumn"></a>DataGridViewComboBoxColumn  
 使用<xref:System.Windows.Forms.DataGridViewComboBoxColumn>，您可以顯示包含下拉式清單方塊的資料格的資料行。 這非常有用的資料中的項目只能包含特定值，例如 Northwind 範例資料庫中的 [產品] 資料表的類別資料行的欄位。  
  
 您可以填入下拉式清單中的所有儲存格使用相同的方式會填入<xref:System.Windows.Forms.ComboBox>下拉式清單中，以手動方式透過所傳回的集合<xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A>屬性，或繫結至資料來源 」、 「 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A>， <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A>，和<xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A>屬性。 如需詳細資訊，請參閱 < [ComboBox 控制項](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md)。  
  
 您可以繫結所使用的資料來源的實際資料格值<xref:System.Windows.Forms.DataGridView>控制項，藉由設定<xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A>屬性<xref:System.Windows.Forms.DataGridViewComboBoxColumn?displayProperty=nameWithType>。  
  
 當資料繫結不會自動產生下拉式方塊資料行<xref:System.Windows.Forms.DataGridView>控制項。 若要使用下拉式方塊資料行，您必須手動加以建立，並將它們新增至所傳回的集合<xref:System.Windows.Forms.DataGridView.Columns%2A>屬性。  
  
## <a name="datagridviewlinkcolumn"></a>DataGridViewLinkColumn  
 使用<xref:System.Windows.Forms.DataGridViewLinkColumn>，您可以顯示包含超連結的資料格的資料行。 這非常有用的資料來源中或作為特殊的行為，例如開啟視窗與子記錄的按鈕資料行的替代方案的 URL 值。  
  
 當資料繫結不會自動產生連結的資料行<xref:System.Windows.Forms.DataGridView>控制項。 若要使用連結的資料行，您必須手動加以建立，並將它們新增至所傳回的集合<xref:System.Windows.Forms.DataGridView.Columns%2A>屬性。  
  
 您可以藉由處理回應使用者按一下連結<xref:System.Windows.Forms.DataGridView.CellContentClick>事件。 此事件會區別<xref:System.Windows.Forms.DataGridView.CellClick>和<xref:System.Windows.Forms.DataGridView.CellMouseClick>當使用者按一下資料格中的任意處時可能發生的事件。  
  
 <xref:System.Windows.Forms.DataGridViewLinkColumn>類別提供數個屬性來修改連結的外觀之前,、 期間和之後在按一下。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewButtonColumn>
- <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn>
- <xref:System.Windows.Forms.DataGridViewImageColumn>
- <xref:System.Windows.Forms.DataGridViewTextBoxColumn>
- <xref:System.Windows.Forms.DataGridViewLinkColumn>
- [DataGridView 控制項](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
- [如何：Windows Forms DataGridView 控制項的儲存格的顯示影像](../../../../docs/framework/winforms/controls/how-to-display-images-in-cells-of-the-windows-forms-datagridview-control.md)
- [如何：使用 Windows Form DataGridView 控制項中的影像資料行](../../../../docs/framework/winforms/controls/how-to-work-with-image-columns-in-the-windows-forms-datagridview-control.md)
- [自訂 Windows Forms DataGridView 控制項](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)

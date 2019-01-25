---
title: Windows Form DataGridView 控制項中的儲存格樣式
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], styles
- data grids [Windows Forms], cell styles
ms.assetid: dbb75ed6-8804-4232-8382-f9920c2e380c
ms.openlocfilehash: 7ff8f8b0c047601e092b8ccb347095d9d1d0a1d1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54575153"
---
# <a name="cell-styles-in-the-windows-forms-datagridview-control"></a>Windows Form DataGridView 控制項中的儲存格樣式
每個資料格內<xref:System.Windows.Forms.DataGridView>控制項可以有它自己的樣式，例如文字格式、 背景色彩、 前景色彩和字型。 一般而言，不過，多個資料格會共用特定樣式特性。  
  
 共用樣式的資料格的群組可能包含特定的資料列或資料行，所有的資料格包含特定值或所有儲存格內的所有資料格控制項中。 因為這些群組重疊，每個資料格可能會收到其樣式資訊從一個以上的位置。 例如，您可以每個資料格<xref:System.Windows.Forms.DataGridView>負數的數字與使用相同的字型，但只使用貨幣格式的貨幣資料行中的資料格和只貨幣資料格，來使用紅色前景色彩的控制項。  
  
## <a name="the-datagridviewcellstyle-class"></a>DataGridViewCellStyle 類別  
 <xref:System.Windows.Forms.DataGridViewCellStyle>類別包含視覺化樣式的相關的下列屬性：  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> 和 <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> 和 <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A>  
  
 這個類別也包含與格式相關的下列屬性：  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> 和 <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> 和 <xref:System.Windows.Forms.DataGridViewCellStyle.DataSourceNullValue%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Padding%2A>  
  
 如需有關這些屬性和其他儲存格樣式屬性的詳細資訊，請參閱<xref:System.Windows.Forms.DataGridViewCellStyle>另請參閱下一節中列出的參考文件和主題。  
  
## <a name="using-datagridviewcellstyle-objects"></a>使用 DataGridViewCellStyle 物件  
 您可以擷取<xref:System.Windows.Forms.DataGridViewCellStyle>物件的各種屬性從<xref:System.Windows.Forms.DataGridView>， <xref:System.Windows.Forms.DataGridViewColumn>， <xref:System.Windows.Forms.DataGridViewRow>，和<xref:System.Windows.Forms.DataGridViewCell>類別和其衍生的類別。 如果其中一個屬性有尚未設定，擷取其值將會建立新<xref:System.Windows.Forms.DataGridViewCellStyle>物件。 您可以也具現化自己<xref:System.Windows.Forms.DataGridViewCellStyle>物件，並將它們指派給這些屬性。  
  
 您可以藉由共用來避免不必要的樣式資訊的重複<xref:System.Windows.Forms.DataGridViewCellStyle>到多個物件<xref:System.Windows.Forms.DataGridView>項目。 因為控制項、 資料行和資料列層級向下篩選至資料格層級的每個層級設定的樣式，您也可以藉由設定不同於上述的層級的每個層級的只有這些樣式屬性來避免樣式重複資料刪除。 這是在樣式繼承一節中詳細描述。  
  
 下表列出的主要屬性，取得或設定<xref:System.Windows.Forms.DataGridViewCellStyle>物件。  
  
|屬性|類別|描述|  
|--------------|-------------|-----------------|  
|`DefaultCellStyle`|<xref:System.Windows.Forms.DataGridView><xref:System.Windows.Forms.DataGridViewColumn>， <xref:System.Windows.Forms.DataGridViewRow>，和衍生類別|取得或設定整個控制項 （包括標題儲存格），在專欄中，或資料列中的所有儲存格所用的預設樣式。|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|取得或設定控制項中的所有資料列所使用的預設儲存格樣式。 這不包括標題儲存格。|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|取得或設定控制項中交替資料列所使用的預設儲存格樣式。 用來建立類似 ledger 的效果。|  
|<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|取得或設定控制項的資料列行首所使用的預設儲存格樣式。 如果啟用視覺化樣式所覆寫目前的佈景主題。|  
|<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|取得或設定控制項的資料行行首所使用的預設儲存格樣式。 如果啟用視覺化樣式所覆寫目前的佈景主題。|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A>|<xref:System.Windows.Forms.DataGridViewCell> 類別和衍生的類別|取得或設定資料格層級指定的樣式。 這些樣式會覆寫繼承自更高層級。|  
|`InheritedStyle`|<xref:System.Windows.Forms.DataGridViewCell><xref:System.Windows.Forms.DataGridViewRow>， <xref:System.Windows.Forms.DataGridViewColumn>，和衍生類別|取得目前套用至資料格、 資料列或資料行，包括樣式繼承自更高層級的所有樣式。|  
  
 如先前所述，會自動取得樣式屬性的值具現化新<xref:System.Windows.Forms.DataGridViewCellStyle>如果屬性尚未先前設定的物件。 若要避免不必要地建立這些物件，資料列和資料行都具有<xref:System.Windows.Forms.DataGridViewBand.HasDefaultCellStyle%2A>屬性，您可以檢查以判斷是否<xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A>屬性已設定。 同樣地，資料格都具有<xref:System.Windows.Forms.DataGridViewCell.HasStyle%2A>屬性，指出是否<xref:System.Windows.Forms.DataGridViewCell.Style%2A>屬性已設定。  
  
 樣式屬性的每個都有對應*PropertyName* `Changed`上的事件<xref:System.Windows.Forms.DataGridView>控制項。 資料列、 資料行和資料格屬性，事件的名稱開頭 「`Row`"，"`Column`"，或 「`Cell`」 (比方說， <xref:System.Windows.Forms.DataGridView.RowDefaultCellStyleChanged>)。 每個事件發生時對應的樣式屬性設定為不同<xref:System.Windows.Forms.DataGridViewCellStyle>物件。 當您擷取這些事件不會發生<xref:System.Windows.Forms.DataGridViewCellStyle>物件的樣式屬性，並修改其屬性值。 若要回應變更儲存格樣式物件本身，處理<xref:System.Windows.Forms.DataGridView.CellStyleContentChanged>事件。  
  
## <a name="style-inheritance"></a>樣式繼承  
 每個<xref:System.Windows.Forms.DataGridViewCell>取得它的外觀，從其<xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>屬性。 <xref:System.Windows.Forms.DataGridViewCellStyle>這個屬性所傳回的物件會繼承類型的屬性階層中的其值<xref:System.Windows.Forms.DataGridViewCellStyle>。 這些屬性如下所列的順序在<xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>非標頭資料格取得其值。  
  
1.  <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
  
2.  <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
3.  <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType> （僅適用於含有奇數索引資料列中的資料格）  
  
4.  <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
  
5.  <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
6.  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 資料列和資料行的標頭資料格，<xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>屬性由從下列清單中指定的順序的來源屬性的值擴展。  
  
1.  <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
  
2.  <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A?displayProperty=nameWithType> 或 <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A?displayProperty=nameWithType>  
  
3.  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 下圖說明此程序。  
  
 ![DataGridViewCellStyle 類型的](../../../../docs/framework/winforms/controls/media/datagridviewcells1.gif "DataGridViewCells1")  
  
 您也可以存取特定的資料列和資料行所繼承的樣式。 資料行<xref:System.Windows.Forms.DataGridViewColumn.InheritedStyle%2A>屬性繼承自下列屬性的值。  
  
1.  <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
2.  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 資料列<xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A>屬性繼承自下列屬性的值。  
  
1.  <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
2.  <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType> （僅適用於含有奇數索引資料列中的資料格）  
  
3.  <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
  
4.  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 中每一個屬性<xref:System.Windows.Forms.DataGridViewCellStyle>所傳回的物件`InheritedStyle`屬性，屬性值取自適當設為值以外的對應屬性的清單中的第一個儲存格樣式<xref:System.Windows.Forms.DataGridViewCellStyle>類別的預設值。  
  
 下表將說明如何<xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>範例資料格的屬性值繼承自其包含的資料行。  
  
|類型屬性 `DataGridViewCellStyle`|範例`ForeColor`擷取物件的值|  
|----------------------------------------------|----------------------------------------------------|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Red%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.DarkBlue%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Black%2A?displayProperty=nameWithType>|  
  
 在此情況下，<xref:System.Drawing.Color.Red%2A?displayProperty=nameWithType>從儲存格的資料列的值是在清單上第一個真正的值。 這會變成<xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>屬性值的儲存格的<xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>。  
  
 下圖說明不同<xref:System.Windows.Forms.DataGridViewCellStyle>屬性可以繼承它們的值，從不同的地方。  
  
 ![DataGridView 屬性&#45;值繼承](../../../../docs/framework/winforms/controls/media/datagridviewcells2.gif "DataGridViewCells2")  
  
 利用樣式繼承，您可以提供適當的樣式整個控制項而不需要在多個位置指定相同的資訊。  
  
 標頭資料格會參與繼承樣式，如所述，雖然所傳回的物件<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>並<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>屬性的<xref:System.Windows.Forms.DataGridView>控制項必須覆寫所傳回之物件的屬性值的初始屬性值<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>屬性。 如果您想為所傳回的物件設定的屬性<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>屬性，將套用至資料列和資料行的標頭，您必須設定對應的屬性所傳回的物件<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>和<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>屬性設為預設值指示針對<xref:System.Windows.Forms.DataGridViewCellStyle>類別。  
  
> [!NOTE]
>  如果啟用視覺化樣式，資料列和資料行標頭 (除了<xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>) 樣式會自動由目前的佈景主題，並覆寫這些屬性指定任何樣式。  
  
 <xref:System.Windows.Forms.DataGridViewButtonColumn>， <xref:System.Windows.Forms.DataGridViewImageColumn>，並<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>型別也會初始化資料行所傳回之物件一些值<xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A>屬性。 如需詳細資訊，請參閱這些類型的參考文件。  
  
## <a name="setting-styles-dynamically"></a>以動態方式設定樣式  
 若要自訂的特定值的資料格的樣式，實作的處理常式<xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>事件。 這個事件處理常式收到的引數<xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs>型別。 此物件包含的屬性，可讓您判斷的值中的位置以及要格式化的儲存格之<xref:System.Windows.Forms.DataGridView>控制項。 此物件也包含<xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.CellStyle%2A>初始化為值的屬性<xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>正在格式化資料格的屬性。 您可以修改以指定適當的資料格的值和位置的樣式資訊的儲存格樣式屬性。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView.RowPrePaint>並<xref:System.Windows.Forms.DataGridView.RowPostPaint>事件也會收到<xref:System.Windows.Forms.DataGridViewCellStyle>在事件物件的資料，但在它們的大小寫的資料列的副本<xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A>唯讀用途，並變更它的屬性不會影響控制項。  
  
 例如您可以也會動態地修改以回應事件的個別儲存格的樣式<xref:System.Windows.Forms.DataGridView.CellMouseEnter?displayProperty=nameWithType>和<xref:System.Windows.Forms.DataGridView.CellMouseLeave>事件。 比方說，在處理常式<xref:System.Windows.Forms.DataGridView.CellMouseEnter>事件，您可以儲存的資料格背景色彩的目前值 (透過儲存格的擷取<xref:System.Windows.Forms.DataGridViewCell.Style%2A>屬性)，然後將它設定為新的色彩，會反白顯示儲存格的滑鼠停留在其上方時。 中的處理常式<xref:System.Windows.Forms.DataGridView.CellMouseLeave>事件，您接著可以還原的背景色彩至原始的值。  
  
> [!NOTE]
>  快取儲存在儲存格的值<xref:System.Windows.Forms.DataGridViewCell.Style%2A>屬性是非常重要，不論是否已設定特定的樣式值。 如果您暫時將樣式設定，將它還原到其原始的 「 未設定 」 狀態可確保儲存格將回送到較高層級繼承樣式設定。 如果您需要決定儲存格值，不管是否繼承樣式是作用中的實際樣式，請使用儲存格的<xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>屬性。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.InheritedStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.InheritedStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellStyleContentChanged?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>
- [Windows Forms DataGridView 控制項中的基本格式化和樣式設定](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [如何：為 Windows Form DataGridView 控制項中的預設儲存格樣式](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView 控制項中的資料格式](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md)

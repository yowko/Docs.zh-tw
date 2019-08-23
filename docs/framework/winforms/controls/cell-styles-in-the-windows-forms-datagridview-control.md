---
title: Windows Form DataGridView 控制項中的儲存格樣式
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], styles
- data grids [Windows Forms], cell styles
ms.assetid: dbb75ed6-8804-4232-8382-f9920c2e380c
ms.openlocfilehash: be4c47db5c56685a84153a9ae4a9a2fe14c6adad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917761"
---
# <a name="cell-styles-in-the-windows-forms-datagridview-control"></a>Windows Form DataGridView 控制項中的儲存格樣式
控制項中的<xref:System.Windows.Forms.DataGridView>每個資料格都可以有自己的樣式, 例如文字格式、背景色彩、前景色彩和字型。 不過, 通常多個資料格會共用特定的樣式特性。  
  
 共用樣式的資料格群組可能包括特定資料列或資料行中的所有儲存格、包含特定值的所有儲存格, 或控制項中的所有儲存格。 因為這些群組會重迭, 所以每個資料格可能會從多個位置取得其樣式資訊。 例如, 您可能希望<xref:System.Windows.Forms.DataGridView>控制項中的每個儲存格都使用相同的字型, 但只有貨幣資料行中的儲存格才會使用貨幣格式, 而只有包含負數的貨幣儲存格才會使用紅色前景色彩。  
  
## <a name="the-datagridviewcellstyle-class"></a>DataGridViewCellStyle 類別  
 <xref:System.Windows.Forms.DataGridViewCellStyle>類別包含下列與視覺化樣式相關的屬性:  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> 和 <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> 和 <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A>  
  
 這個類別也包含下列與格式相關的屬性:  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> 和 <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> 和 <xref:System.Windows.Forms.DataGridViewCellStyle.DataSourceNullValue%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Padding%2A>  
  
 如需這些屬性和其他儲存格樣式屬性的詳細資訊, 請<xref:System.Windows.Forms.DataGridViewCellStyle>參閱參考檔和下一節中所列的主題。  
  
## <a name="using-datagridviewcellstyle-objects"></a>使用 DataGridViewCellStyle 物件  
 您可以<xref:System.Windows.Forms.DataGridViewCellStyle>從<xref:System.Windows.Forms.DataGridView>、 <xref:System.Windows.Forms.DataGridViewColumn>、和類別<xref:System.Windows.Forms.DataGridViewCell>的各種屬性和其衍生類別抓取物件。 <xref:System.Windows.Forms.DataGridViewRow> 如果尚未設定這些屬性的其中一個, 則抓取其值將會建立新<xref:System.Windows.Forms.DataGridViewCellStyle>的物件。 您也可以具現化<xref:System.Windows.Forms.DataGridViewCellStyle>自己的物件, 並將它們指派給這些屬性。  
  
 您可以在多個<xref:System.Windows.Forms.DataGridViewCellStyle> <xref:System.Windows.Forms.DataGridView>專案之間共用物件, 以避免不必要的樣式資訊重複。 由於在控制項、資料行和資料列層級設定的樣式會向下篩選到資料格層級, 因此您也可以在每個層級上設定不同于上述層級的樣式屬性, 以避免樣式重複。 這在下面的 [樣式繼承] 區段中有更詳細的說明。  
  
 下表列出取得或設定<xref:System.Windows.Forms.DataGridViewCellStyle>物件的主要屬性。  
  
|屬性|類別|描述|  
|--------------|-------------|-----------------|  
|`DefaultCellStyle`|<xref:System.Windows.Forms.DataGridView>、 <xref:System.Windows.Forms.DataGridViewColumn> 、<xref:System.Windows.Forms.DataGridViewRow>和衍生類別|取得或設定在整個控制項 (包括標題儲存格)、資料行或資料列中的所有儲存格所使用的預設樣式。|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|取得或設定控制項中所有資料列所使用的預設儲存格樣式。 這不包含標頭資料格。|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|取得或設定控制項中交替資料列所使用的預設儲存格樣式。 用來建立類似總帳的效果。|  
|<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|取得或設定控制項的資料列標頭所使用的預設儲存格樣式。 如果已啟用視覺化樣式, 則會由目前的主題覆寫。|  
|<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|取得或設定控制項的資料行標頭所使用的預設儲存格樣式。 如果已啟用視覺化樣式, 則會由目前的主題覆寫。|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A>|<xref:System.Windows.Forms.DataGridViewCell>和衍生類別|取得或設定在資料格層級指定的樣式。 這些樣式會覆寫繼承自較高層級的那些樣式。|  
|`InheritedStyle`|<xref:System.Windows.Forms.DataGridViewCell>、 <xref:System.Windows.Forms.DataGridViewRow> 、<xref:System.Windows.Forms.DataGridViewColumn>和衍生類別|取得目前套用至儲存格、資料列或資料行的所有樣式, 包括繼承自較高層級的樣式。|  
  
 如前所述, 如果先前尚未設定屬性, 取得 style 屬性的值會自動<xref:System.Windows.Forms.DataGridViewCellStyle>具現化新的物件。 為了避免不必要地建立這些物件, 資料列和資料行<xref:System.Windows.Forms.DataGridViewBand.HasDefaultCellStyle%2A>類別具有可供您檢查的<xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A>屬性, 以判斷屬性是否已設定。 同樣地, 資料格類別具有<xref:System.Windows.Forms.DataGridViewCell.HasStyle%2A>屬性, 可指出<xref:System.Windows.Forms.DataGridViewCell.Style%2A>是否已設定屬性。  
  
 每個樣式屬性在<xref:System.Windows.Forms.DataGridView>控制項上都有對應的*PropertyName* `Changed`事件。 針對資料列、資料行和資料格屬性, 事件的名稱開頭為 "`Row`"、"`Column`" 或 "`Cell`" ( <xref:System.Windows.Forms.DataGridView.RowDefaultCellStyleChanged>例如)。 當對應的樣式屬性設定為不同<xref:System.Windows.Forms.DataGridViewCellStyle>的物件時, 就會發生這些事件。 當您從樣式屬性取得<xref:System.Windows.Forms.DataGridViewCellStyle>物件並修改其屬性值時, 不會發生這些事件。 若要回應儲存格樣式物件本身的變更, 請處理<xref:System.Windows.Forms.DataGridView.CellStyleContentChanged>事件。  
  
## <a name="style-inheritance"></a>樣式繼承  
 每<xref:System.Windows.Forms.DataGridViewCell>個都會從其<xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>屬性取得其外觀。 這個<xref:System.Windows.Forms.DataGridViewCellStyle>屬性所傳回的物件會從類型<xref:System.Windows.Forms.DataGridViewCellStyle>的屬性階層繼承其值。 下列屬性會依照的順序<xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>列在中, 以供非標頭儲存格取得其值。  
  
1. <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
3. <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>(僅適用于具有奇數索引編號的資料列中的儲存格)  
  
4. <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
  
5. <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
6. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 若是資料列和資料行標頭單元<xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>格, 屬性會依指定順序填入下列來源屬性清單中的值。  
  
1. <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A?displayProperty=nameWithType> 或 <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A?displayProperty=nameWithType>  
  
3. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 下圖說明此程式。  
  
 ![DataGridViewCellStyle 類型的屬性](./media/cell-styles-in-the-windows-forms-datagridview-control/datagridviewcells-inheritance-diagram.gif "DataGridViewCells 繼承圖表")  
  
 您也可以存取特定資料列和資料行所繼承的樣式。 Column <xref:System.Windows.Forms.DataGridViewColumn.InheritedStyle%2A>屬性會從下列屬性繼承其值。  
  
1. <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Row <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A>屬性會從下列屬性繼承其值。  
  
1. <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>(僅適用于具有奇數索引編號的資料列中的儲存格)  
  
3. <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
  
4. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 針對<xref:System.Windows.Forms.DataGridViewCellStyle> 屬性`InheritedStyle`所傳回之物件中的每個屬性, 會從適當清單中的第一個儲存格樣式取得屬性值, 而該對應屬性會設定為<xref:System.Windows.Forms.DataGridViewCellStyle>類別預設值以外的值。  
  
 下表說明範例資料格<xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>的屬性值如何繼承自其包含的資料行。  
  
|類型的屬性`DataGridViewCellStyle`|抓取`ForeColor`物件的範例值|  
|----------------------------------------------|----------------------------------------------------|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Red%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.DarkBlue%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Black%2A?displayProperty=nameWithType>|  
  
 在此情況下, <xref:System.Drawing.Color.Red%2A?displayProperty=nameWithType>資料格資料列中的值是清單中的第一個實際值。 這會變成<xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>儲存格的屬性值。  
  
 下圖說明不同<xref:System.Windows.Forms.DataGridViewCellStyle>的屬性如何從不同的位置繼承其值。  
  
 ![DataGridView 屬性&#45;值繼承](./media/cell-styles-in-the-windows-forms-datagridview-control/datagridviewcells-value-inheritance-diagram.gif "DataGridViewCells 值繼承圖表")  
  
 藉由利用樣式繼承, 您可以為整個控制項提供適當的樣式, 而不需要在多個位置指定相同的資訊。  
  
 雖然標頭儲存格會依照所述的方式參與樣式繼承, <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>但<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> <xref:System.Windows.Forms.DataGridView>控制項的和屬性所傳回的物件具有初始屬性值, 可覆寫所傳回之物件的屬性值。<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>屬性。 如果您想要將<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>屬性所傳回之物件的屬性設定為套用到資料列和資料行標頭, 您必須將<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>和<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>屬性所傳回之物件的對應屬性設定為指定的預設值<xref:System.Windows.Forms.DataGridViewCellStyle>類別的。  
  
> [!NOTE]
> 如果啟用視覺化樣式, 則會由目前的主題自動將資料列<xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>和資料行標頭 (除外) 樣式化, 以覆寫這些屬性所指定的任何樣式。  
  
 、和類型也會初始化資料行<xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A>屬性所傳回之物件的一些值。 <xref:System.Windows.Forms.DataGridViewCheckBoxColumn> <xref:System.Windows.Forms.DataGridViewImageColumn> <xref:System.Windows.Forms.DataGridViewButtonColumn> 如需詳細資訊, 請參閱這些類型的參考檔。  
  
## <a name="setting-styles-dynamically"></a>動態設定樣式  
 若要自訂具有特定值的儲存格樣式, 請執行<xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>事件的處理常式。 這個事件的處理常式會接收<xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs>類型的引數。 這個物件所包含的屬性可讓您判斷要格式化的儲存格值, 以及其在<xref:System.Windows.Forms.DataGridView>控制項中的位置。 這個物件也包含一個<xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.CellStyle%2A>屬性, 它會初始化為正在格式化之<xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>儲存格的屬性值。 您可以修改儲存格樣式屬性, 以指定適合儲存格值和位置的樣式資訊。  
  
> [!NOTE]
> 和事件也會在事件<xref:System.Windows.Forms.DataGridViewCellStyle>資料中接收物件, 但在其情況下, 它是唯讀用途的資料列<xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A>屬性複本, 而且對其所做的變更不會影響控制項。 <xref:System.Windows.Forms.DataGridView.RowPostPaint> <xref:System.Windows.Forms.DataGridView.RowPrePaint>  
  
 您也可以動態修改個別資料格的樣式, 以回應事件 (例如<xref:System.Windows.Forms.DataGridView.CellMouseEnter?displayProperty=nameWithType>和<xref:System.Windows.Forms.DataGridView.CellMouseLeave>事件)。 例如, 在<xref:System.Windows.Forms.DataGridView.CellMouseEnter>事件的處理常式中, 您可以儲存儲存格背景色彩的目前值 (透過儲存格的<xref:System.Windows.Forms.DataGridViewCell.Style%2A>屬性抓取), 然後將它設定為新的色彩, 當滑鼠停留在資料格上方時, 就會反白顯示該儲存格。 在<xref:System.Windows.Forms.DataGridView.CellMouseLeave>事件的處理常式中, 您可以將背景色彩還原成原始值。  
  
> [!NOTE]
> 無論是否已設定特定的樣式值<xref:System.Windows.Forms.DataGridViewCell.Style%2A> , 快取儲存在儲存格屬性中的值都很重要。 如果您暫時取代樣式設定, 將它還原成其原始的「未設定」狀態, 可確保資料格會回到繼承較高層級的樣式設定。 如果您需要判斷資料格的實際有效樣式 (不論該樣式是否已繼承), 請使用資料格的<xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>屬性。  
  
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
- [Windows Forms DataGridView 控制項中的基本格式化和樣式設定](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [如何：設定 Windows Forms DataGridView 控制項的預設儲存格樣式](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView 控制項中的資料格式](data-formatting-in-the-windows-forms-datagridview-control.md)

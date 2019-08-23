---
title: Windows Form DataGridView 控制項中的調整大小選項
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], row sizing
- data grids [Windows Forms], column sizing
- DataGridView control [Windows Forms], column sizing
- DataGridView control [Windows Forms], sizing options
- data grids [Windows Forms], row sizing
- data grids [Windows Forms], sizing options
ms.assetid: a5620a9c-0d06-41e3-8934-c25ddb16c9e6
ms.openlocfilehash: a8e2e05877746dfb043b7e8ac2a6c2b7017883c3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960431"
---
# <a name="sizing-options-in-the-windows-forms-datagridview-control"></a>Windows Form DataGridView 控制項中的調整大小選項
<xref:System.Windows.Forms.DataGridView>資料列、資料行和標頭可能會因為許多不同的出現結果而變更大小。 下表顯示這些發生的情況。  
  
|次出現|描述|  
|----------------|-----------------|  
|使用者調整大小|使用者可以藉由拖曳或按兩下列、資料行或標頭分隔線來調整大小。|  
|控制項調整大小|在 [資料行填滿模式] 中, 當控制項寬度變更時, 資料行寬度會變更;例如, 當控制項停駐于其父表單, 且使用者調整表單的大小時。|  
|資料格值變更|在以內容為基礎的自動調整大小模式中, 大小會變更以符合新的顯示值。|  
|方法呼叫|以程式設計的內容為基礎的調整大小, 可讓您根據方法呼叫時的資料格值進行相應調整。|  
|屬性設定|您也可以設定特定的高度和寬度值。|  
  
 根據預設, 會啟用使用者調整大小、停用自動調整大小, 而且會裁剪寬度超出其資料行的儲存格值。  
  
 下表顯示可用來調整預設行為, 或使用特定調整大小選項來達到特定效果的案例。  
  
|狀況|實作|  
|--------------|--------------------|  
|使用 [資料行填滿模式], 在不顯示水準捲軸的情況下, 于相對較少的資料行中顯示類似大小的資料。|將 <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> 屬性設定為 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>。|  
|使用 [資料行填滿] 模式與 [不同大小] 的顯示值。|將 <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> 屬性設定為 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>。 藉由設定資料行<xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>屬性, 或在填滿具有資料的控制項之後呼叫控制項<xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A>方法, 來初始化相對資料行寬度。|  
|使用具有不同重要性值的資料行填滿模式。|將 <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> 屬性設定為 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>。 針對必須<xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A>一律顯示部分資料, 或針對特定資料行使用 [填滿模式] 以外的 [調整大小] 選項的資料行, 設定大數值。|  
|使用資料行填滿模式來避免顯示控制項背景。|將最後一個資料行的<xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill> 屬性設定為,並使用其他資料行的其他調整大小選項。<xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> 如果其他資料行使用太多可用的空間, 請設定<xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A>最後一個資料行的屬性。|  
|顯示固定寬度的資料行, 例如 [圖示] 或 [ID] 資料行。|針對資料<xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None>行, 將設為, 並<xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A>將設定為。 <xref:System.Windows.Forms.DataGridViewTriState.False> 藉由設定<xref:System.Windows.Forms.DataGridViewColumn.Width%2A>屬性, 或在以資料填滿控制項<xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A>之後呼叫控制項方法, 初始化其寬度。|  
|在資料格內容變更時自動調整大小, 以避免裁剪並優化空間的使用。|將 [自動調整大小] 屬性設定為代表以內容為基礎之大小調整模式的值。 若要避免在使用大量資料時造成效能上的負面影響, 請使用調整大小模式, 只計算顯示的列數。|  
|調整大小以符合所顯示資料列中的值, 以避免在處理許多資料列時產生效能的負面影響。|使用適當的調整大小模式列舉值搭配自動或以程式設計方式調整大小。 若要在滾動時調整大小以符合新顯示資料列中的值, 請在<xref:System.Windows.Forms.DataGridView.Scroll>事件處理常式中呼叫調整大小方法。 若要自訂使用者按兩下調整大小, 以便只有顯示的資料列中的值會決定新的大小, <xref:System.Windows.Forms.DataGridView.RowDividerDoubleClick>請<xref:System.Windows.Forms.DataGridView.ColumnDividerDoubleClick>在或事件處理常式中呼叫調整大小方法。|  
|調整大小以僅在特定時間符合資料格內容, 以避免發生效能損失或讓使用者調整大小。|在事件處理常式中呼叫以內容為基礎的調整大小方法。 例如, 使用<xref:System.Windows.Forms.DataGridView.DataBindingComplete>事件來初始化系結後的大小, 並<xref:System.Windows.Forms.DataGridView.CellValidated>處理或<xref:System.Windows.Forms.DataGridView.CellValueChanged>事件來調整大小, 以補償已系結資料來源中的使用者編輯或變更。|  
|調整多行資料格內容的資料列高度。|請確定資料行寬度適合用來顯示文欄位落, 並使用自動或以程式設計方式以內容為基礎的資料列大小來調整高度。 此外, 請確定具有多行內容的資料格<xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>會使用的單元<xref:System.Windows.Forms.DataGridViewTriState.True>格樣式值來顯示。<br /><br /> 一般而言, 您將使用自動資料行調整大小模式來維護資料行寬度, 或在調整資料列高度之前, 將其設定為特定寬度。|  
  
## <a name="resizing-with-the-mouse"></a>使用滑鼠調整大小  
 根據預設, 使用者可以調整不使用以資料格值為基礎之自動調整大小模式的資料列、資料行和標頭大小。 若要防止使用者調整其他模式的大小 (例如資料行填滿模式), 請設定下列<xref:System.Windows.Forms.DataGridView>一個或多個屬性:  
  
- <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A>  
  
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A>  
  
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A>  
  
 您也可以藉由設定<xref:System.Windows.Forms.DataGridViewBand.Resizable%2A>屬性來防止使用者調整個別資料列或資料行的大小。 根據預設, <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A>屬性值會以資料行的<xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A>屬性值和資料列的<xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A>屬性值為基礎。 不過, 如果您<xref:System.Windows.Forms.DataGridViewBand.Resizable%2A>將<xref:System.Windows.Forms.DataGridViewTriState.True>明確<xref:System.Windows.Forms.DataGridViewTriState.False>設定為或, 則指定的值會覆寫該資料列或資料行的控制項值。 將<xref:System.Windows.Forms.DataGridViewBand.Resizable%2A>設定<xref:System.Windows.Forms.DataGridViewTriState.NotSet>為以還原繼承。  
  
 因為<xref:System.Windows.Forms.DataGridViewTriState.NotSet>會還原值繼承<xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> , 除非資料列<xref:System.Windows.Forms.DataGridView>或資料行<xref:System.Windows.Forms.DataGridViewTriState.NotSet>尚未加入控制項, 否則屬性永遠不會傳回值。 如果您需要判斷資料列或<xref:System.Windows.Forms.DataGridViewBand.Resizable%2A>資料行的屬性值是否已繼承, 請檢查其<xref:System.Windows.Forms.DataGridViewElement.State%2A>屬性。 如果值包含旗標, 則<xref:System.Windows.Forms.DataGridViewBand.Resizable%2A>不會繼承屬性值。 <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet> <xref:System.Windows.Forms.DataGridViewElement.State%2A>  
  
## <a name="automatic-sizing"></a>自動調整大小  
 <xref:System.Windows.Forms.DataGridView>控制項中有兩種自動調整大小: 資料行填滿模式和以內容為基礎的自動調整大小。  
  
 資料行填滿模式會使控制項中的可見資料行填滿控制項顯示區域的寬度。 如需此模式的詳細資訊, 請參閱[Windows Forms DataGridView 控制項中的資料行填滿模式](column-fill-mode-in-the-windows-forms-datagridview-control.md)。  
  
 您也可以設定資料列、資料行和標頭, 以自動調整其大小以符合其資料格內容。 在此情況下, 每當資料格內容變更時, 就會進行大小調整。  
  
> [!NOTE]
> 如果您使用虛擬模式來維護自訂資料快取中的儲存格值, 當使用者編輯儲存格值時, 就會發生自動調整大小, 但當您在<xref:System.Windows.Forms.DataGridView.CellValuePushed>事件處理常式之外更改快取值時, 就不會發生這種情況。 在此情況下, 請<xref:System.Windows.Forms.DataGridView.UpdateCellValue%2A>呼叫方法來強制控制項更新儲存格顯示, 並套用目前的自動調整大小模式。  
  
 如果只針對一個維度啟用以內容為基礎的自動調整大小 (也就是針對資料列, 而不是資料行, 或<xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>用於資料行而非資料列), 而且也會啟用, 則在其他維度變更時也會進行大小調整。 例如, 如果資料列 (而不是資料行) 設定為<xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>自動調整大小, 而且已啟用, 使用者可以拖曳資料行分隔線來變更資料行的寬度, 而資料列高度會自動調整, 讓儲存格內容仍然會完整顯示。  
  
 如果您設定以內容為基礎之自動調整大小的資料<xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>列和資料行<xref:System.Windows.Forms.DataGridView> , 而且已啟用, 控制項會在資料格內容變更時調整大小, 並在計算新的大小時, 使用理想的儲存格高度與寬度的比率。  
  
 若要設定標頭和資料列的調整大小模式, 以及不覆寫控制項值的資料行, 請設定下列<xref:System.Windows.Forms.DataGridView>一個或多個屬性:  
  
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A>  
  
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A>  
  
 若要覆寫個別資料行的控制項資料行調整大小模式<xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> , 請將其屬性設定<xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet>為以外的值。 資料行的調整大小模式實際上取決於其<xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A>屬性。 這個屬性的值是以資料行的<xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>屬性值為基礎, 除非該值為<xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet>, 在此情況下, 會繼承控制項的<xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A>值。  
  
 在處理大量資料時, 請小心使用以內容為基礎的自動調整。 若要避免效能受到影響, 請使用自動調整大小模式, 根據顯示的資料列計算大小, 而不是分析控制項中的每個資料列。 為了達到最大效能, 請改用以程式設計方式調整大小, 讓您可以在特定時間重新調整, 例如在載入新資料之後立即。  
  
 以內容為基礎的自動調整大小模式不會影響您已隱藏的資料列、資料行或標頭<xref:System.Windows.Forms.DataGridViewBand.Visible%2A> , 方法是將 [ <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A>資料列`false`] 或 [資料行] 屬性或控制項<xref:System.Windows.Forms.DataGridView.RowHeadersVisible%2A>或屬性設定為。 例如, 如果資料行在自動調整大小以符合大型資料格的值之後隱藏, 則如果刪除包含大型資料格值的資料列, 隱藏的資料行會不會變更其大小。 當可見度變更時, 不會發生自動重設<xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> `true`大小, 因此將資料行屬性變更回, 並不會強制它根據目前的內容重新計算其大小。  
  
 以程式設計內容為基礎的大小調整會影響資料列、資料行和標頭, 而不論其可見度為何。  
  
## <a name="programmatic-resizing"></a>以程式設計方式調整大小  
 停用自動調整大小時, 您可以透過下列屬性, 以程式設計方式設定資料列、資料行或標頭的確切寬度或高度:  
  
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidth%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeight%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.DataGridViewRow.Height%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>  
  
 您也可以使用下列方法, 以程式設計方式調整資料列、資料行和標頭的大小, 以符合其內容:  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A>  
  
 這些方法會調整資料列、資料行或標頭一次的大小, 而不是設定它們以進行連續調整。 新的大小會自動計算, 以顯示所有資料格內容而不進行裁剪。 不過, 當您以程式設計<xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A>方式調整具有<xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill>屬性值之資料行的大小時, 會使用計算的以內容為<xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>基礎的寬度來按比例調整資料行屬性值, 而實際的資料行寬度為然後根據這些新的比例來計算, 讓所有資料行填滿控制項的可用顯示區域。  
  
 以程式設計方式調整大小有助於避免連續調整大小的效能損失。 針對使用者可以調整大小的資料列、資料行和標頭, 以及資料行填滿模式, 提供初始大小也很有用。  
  
 您通常會在特定時間呼叫以程式設計方式調整大小的方法。 例如, 您可能會在載入資料之後, 以程式設計方式調整所有資料行的大小, 或者您可能會在修改特定資料格值之後, 以程式設計方式調整特定資料列的大小  
  
## <a name="customizing-content-based-sizing-behavior"></a>自訂以內容為基礎的調整大小行為  
 您可以藉由覆寫、 <xref:System.Windows.Forms.DataGridView>或<xref:System.Windows.Forms.DataGridViewColumn.GetPreferredWidth%2A?displayProperty=nameWithType>方法, <xref:System.Windows.Forms.DataGridViewRow.GetPreferredHeight%2A?displayProperty=nameWithType>或在衍生<xref:System.Windows.Forms.DataGridView>的中呼叫受保護的<xref:System.Windows.Forms.DataGridViewCell.GetPreferredSize%2A?displayProperty=nameWithType>調整大小方法多載, 在處理衍生的儲存格、資料列和資料行類型時自訂調整大小行為ctrl. 受保護的調整大小方法多載是設計成搭配使用, 以達到理想的儲存格高度與寬度的比率, 以避免過度寬或高度的資料格。 例如`AutoResizeRows(DataGridViewAutoSizeRowsMode,Boolean)` , 如果您呼叫<xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A>方法的多載, 並`false`傳入<xref:System.Boolean>參數的值, 則多載會計算資料列中儲存格的理想高度和寬度, 但它會調整資料列高度才. 接著, 您必須呼叫<xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A>方法, 將資料行寬度調整為計算的理想。  
  
## <a name="content-based-sizing-options"></a>以內容為基礎的調整大小選項  
 調整大小屬性和方法所使用的列舉與以內容為基礎的大小調整有類似的值。 使用這些值, 您可以限制用來計算慣用大小的儲存格。 針對所有大小的列舉, 名稱參考所顯示資料格的值, 會將其計算限制為顯示之資料列中的儲存格。 排除資料列有助於避免在使用大量資料列時造成效能上的負面影響。 您也可以將計算限制為標頭或 nonheader 儲存格中的資料格值。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidth%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeight%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewRow.Height%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeRowMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>
- <xref:System.Windows.Forms.DataGridViewColumnHeadersHeightSizeMode>
- <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>
- [調整 Windows Forms DataGridView 控制項中資料行和資料列的大小](resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView 控制項中的資料行填入模式](column-fill-mode-in-the-windows-forms-datagridview-control.md)
- [如何：設定 Windows Forms DataGridView 控制項的調整大小模式](how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)

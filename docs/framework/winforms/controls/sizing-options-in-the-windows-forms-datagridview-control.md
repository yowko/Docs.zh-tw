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
ms.openlocfilehash: 2f76bbca3d4b6e642c0eec2129c4a2abee752655
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61903158"
---
# <a name="sizing-options-in-the-windows-forms-datagridview-control"></a>Windows Form DataGridView 控制項中的調整大小選項
<xref:System.Windows.Forms.DataGridView> 資料列、 資料行和標頭可以變更大小，因為許多不同的項目。 下表顯示這些項目。  
  
|相符項目|描述|  
|----------------|-----------------|  
|使用者調整大小|使用者可以透過拖曳或按兩下資料列、 資料行或標頭的分隔線來進行調整大小。|  
|控制項調整大小|在資料行填滿模式中，資料行寬度變更時變更控制項的寬度;例如，當控制項停駐到其父表單和使用者調整表單。|  
|儲存格的值變更|在以內容為基礎的自動調整大小模式，大小變更以符合新的顯示值。|  
|方法呼叫|調整大小以程式設計方式以內容為基礎，可讓您根據儲存格的值，在方法呼叫時的伺服器用戶端檔案的大小調整。|  
|屬性設定|您也可以設定特定的高度和寬度值。|  
  
 根據預設，使用者重新調整大小一經啟用，停用自動調整大小，儲存格寬度超過其資料行的值會被裁剪。  
  
 下表顯示案例，您可以使用以調整預設行為，或使用特定的調整大小選項，來達成特定效果。  
  
|情節|實作|  
|--------------|--------------------|  
|使用資料行填入模式的顯示大小相似的相對少量佔用整個控制項的寬度，而不會顯示水平捲軸的資料行中的資料。|將 <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> 屬性設定為 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>。|  
|使用資料行填入模式，來顯示不同大小的值。|將 <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> 屬性設定為 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>。 藉由設定資料行，初始化相對的資料行寬度<xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>屬性或呼叫控制項<xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A>方法之後填入資料的控制項。|  
|使用資料行填入模式的不同重要性的值。|將 <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> 屬性設定為 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>。 設定大型<xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A>必須一律顯示其資料的部分或使用調整大小選項以外的資料行填入模式的特定資料行的值。|  
|若要避免顯示控制項背景中使用資料行填滿模式。|設定<xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>屬性的最後一個資料行<xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill>，並使用其他的調整大小選項的其他資料行。 如果其他資料行使用太多的可用空間，設定<xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A>最後一個資料行的屬性。|  
|顯示固定寬度資料行，例如圖示或識別碼資料行。|設定<xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>要<xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None>並<xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A>到<xref:System.Windows.Forms.DataGridViewTriState.False>資料行。 藉由設定初始化其寬度<xref:System.Windows.Forms.DataGridViewColumn.Width%2A>屬性或呼叫控制項<xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A>方法之後填入資料的控制項。|  
|儲存格的內容變更，以避免裁剪及最佳化的空間使用時，自動調整大小。|設定自動調整大小屬性的值，表示內容為基礎的調整大小模式。 若要使用的大量資料時，請避免對效能帶來負面影響，請使用計算顯示資料列的調整大小模式。|  
|調整大小以符合以避免效能的負面影響，使用多個資料列時顯示的資料列的值。|使用自動或以程式設計方式調整大小適當調整大小模式的列舉值。 若要調整大小，以納入新顯示的資料列中的值，在捲動時，調整大小的方法呼叫中<xref:System.Windows.Forms.DataGridView.Scroll>事件處理常式。 若要自訂使用者按兩下調整大小以便只顯示的資料列中的值會決定新的大小，呼叫調整大小的方法<xref:System.Windows.Forms.DataGridView.RowDividerDoubleClick>或<xref:System.Windows.Forms.DataGridView.ColumnDividerDoubleClick>事件處理常式。|  
|調整大小以符合儲存格的內容只在特定的時間，以避免效能的負面影響，或讓使用者重新調整大小。|呼叫以內容為基礎的調整大小方法中的事件處理常式。 例如，使用<xref:System.Windows.Forms.DataGridView.DataBindingComplete>來初始化繫結之後, 的大小和處理事件<xref:System.Windows.Forms.DataGridView.CellValidated>或<xref:System.Windows.Forms.DataGridView.CellValueChanged>事件，以調整大小，以彌補使用者編輯或變更繫結的資料來源中。|  
|調整為多行的資料格內容的資料列高度。|請確定資料行寬度是適用於顯示文字段落的文字，並使用自動或以程式設計方式以內容為基礎的資料列大小調整高度。 也請確定會顯示使用多行的內容使用的儲存格<xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>資料格的樣式值<xref:System.Windows.Forms.DataGridViewTriState.True>。<br /><br /> 一般而言，您將使用自動的資料行調整大小模式來維護資料行寬度，或將它們設定為特定的寬度之前的資料列高度會調整。|  
  
## <a name="resizing-with-the-mouse"></a>使用滑鼠調整大小  
 根據預設，使用者可以調整資料列、 資料行，以及不使用資料格的值為基礎的自動調整大小模式的標頭。 若要防止使用者調整與其他模式，例如資料行填滿模式中，將設定一或多個項目<xref:System.Windows.Forms.DataGridView>屬性：  
  
-   <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A>  
  
 您也可以防止使用者調整個別的資料列或資料行，藉由設定其<xref:System.Windows.Forms.DataGridViewBand.Resizable%2A>屬性。 根據預設，<xref:System.Windows.Forms.DataGridViewBand.Resizable%2A>屬性值根據<xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A>資料行的屬性值和<xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A>資料列的屬性值。 如果您明確設定<xref:System.Windows.Forms.DataGridViewBand.Resizable%2A>要<xref:System.Windows.Forms.DataGridViewTriState.True>或<xref:System.Windows.Forms.DataGridViewTriState.False>，不過指定的值會覆寫控制項的值是該資料列或資料行。 設定<xref:System.Windows.Forms.DataGridViewBand.Resizable%2A>至<xref:System.Windows.Forms.DataGridViewTriState.NotSet>還原繼承。  
  
 因為<xref:System.Windows.Forms.DataGridViewTriState.NotSet>還原值繼承<xref:System.Windows.Forms.DataGridViewBand.Resizable%2A>屬性永遠不會傳回<xref:System.Windows.Forms.DataGridViewTriState.NotSet>值，除非資料列或資料行尚未加入至<xref:System.Windows.Forms.DataGridView>控制項。 如果您需要決定是否<xref:System.Windows.Forms.DataGridViewBand.Resizable%2A>資料列或資料行的屬性值繼承，請檢查其<xref:System.Windows.Forms.DataGridViewElement.State%2A>屬性。 如果<xref:System.Windows.Forms.DataGridViewElement.State%2A>值會包含<xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet>旗標，<xref:System.Windows.Forms.DataGridViewBand.Resizable%2A>不會繼承屬性值。  
  
## <a name="automatic-sizing"></a>自動調整大小  
 有兩種類型中的自動調整大小的<xref:System.Windows.Forms.DataGridView>控制項： 資料行填滿模式和以內容為基礎的自動調整大小。  
  
 資料行填入模式會導致要填滿控制項的顯示區域寬度的控制項中的可見資料行。 如需有關此模式的詳細資訊，請參閱[Windows Forms DataGridView 控制項中的資料行填滿模式](column-fill-mode-in-the-windows-forms-datagridview-control.md)。  
  
 您也可以設定資料列、 資料行，以及自動調整其大小以適合其儲存格內容的標頭。 在此情況下，儲存格的內容變更時，就會發生大小調整。  
  
> [!NOTE]
>  如果要維護資料格的值，在自訂資料快取中使用的虛擬模式時，自動調整大小發生於使用者編輯儲存格的值，但當您改變之外的快取的值不會發生<xref:System.Windows.Forms.DataGridView.CellValuePushed>事件處理常式。 在此情況下，呼叫<xref:System.Windows.Forms.DataGridView.UpdateCellValue%2A>方法，以強制控制項更新資料格顯示，並且套用目前的自動調整大小模式。  
  
 如果只有一個維度中啟用內容為基礎的自動調整大小，則 — 的是，針對資料列，但沒有資料行，或針對資料行，但沒有資料列 — 和<xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>也是每次變更與其他維度時，也會發生已啟用，大小調整。 例如，如果資料列，但不是資料行設定為自動調整大小和<xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>已啟用，使用者可以拖曳資料行分割線，以變更資料行的寬度和資料列高度會自動調整，仍可獲得完整顯示儲存格的內容。  
  
 如果您設定資料列和資料行的內容為基礎的自動調整大小並<xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>啟用時，<xref:System.Windows.Forms.DataGridView>控制項將會調整大小，當儲存格的內容變更，並會使用理想的儲存格高度與寬度的比率時計算新的大小。  
  
 若要設定調整大小模式的標頭和資料列和資料行不會覆寫控制項的值，設定一或多個項目<xref:System.Windows.Forms.DataGridView>屬性：  
  
-   <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A>  
  
 若要覆寫個別資料行的控制項的資料行調整大小模式，請將其<xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>屬性以外的值為<xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet>。 調整大小模式的資料行實際上由其<xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A>屬性。 這個屬性的值為基礎的資料行<xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>屬性值，該值除非<xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet>，在此情況下控制項的<xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A>繼承值。  
  
 使用以內容為基礎的自動調整大小謹慎處理大量資料時。 若要避免效能的負面影響，請使用計算只根據顯示的資料列，而不是分析在控制項中的每個資料列的大小自動調整大小模式。 為達最佳效能，使用以程式設計方式調整大小相反地，讓您可以調整大小在特定時間，例如新的資料之後，立即載入。  
  
 以內容為基礎的自動調整大小模式的資料列、 資料行或您已經隱藏藉由設定資料列或資料行的標頭不會影響<xref:System.Windows.Forms.DataGridViewBand.Visible%2A>屬性或控制項<xref:System.Windows.Forms.DataGridView.RowHeadersVisible%2A>或是<xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A>屬性，以`false`。 比方說，它會自動調整大小以容納大型的資料格的值之後，會隱藏資料行，隱藏的資料行會變更其大小，如果包含大型的資料格的值的資料列遭到刪除。 自動調整大小不會發生可見性變更時，因此，變更資料行<xref:System.Windows.Forms.DataGridViewColumn.Visible%2A>屬性回`true`將不會強制它重新計算其大小，根據其目前的內容。  
  
 以程式設計方式以內容為基礎的調整會影響資料列、 資料行和標頭，不論其可見性。  
  
## <a name="programmatic-resizing"></a>以程式設計方式調整大小  
 停用自動調整大小後，您可以以程式設計方式設定的確切的寬度或高度的資料列、 資料行或藉由下列屬性的標頭：  
  
-   <xref:System.Windows.Forms.DataGridView.RowHeadersWidth%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeight%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.DataGridViewRow.Height%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>  
  
 您也以程式設計的方式可以調整大小的資料列、 資料行和標頭，以適合其內容，使用下列方法：  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A>  
  
 這些方法會重新調整資料列、 資料行，或一次標頭而不是加以設定的持續調整大小。 新的大小會自動計算要顯示所有儲存格的內容，而不裁剪。 當您以程式設計方式調整資料行具有<xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A>屬性值<xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill>，不過，會按比例調整資料行使用導出的內容為基礎之寬度<xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>屬性值和實際資料行的寬度因此，所有的資料行填滿可用顯示區域的控制項，則計算根據這些新的比例。  
  
 以程式設計方式調整大小最好避免使用連續的調整大小的效能損失。 最好也提供初始大小，使用者可調整大小的資料列、 資料行和標頭，以及資料行填滿模式。  
  
 您通常會在特定時間呼叫以程式設計方式調整大小的方法。 例如，您可能會在載入資料之後，立即以程式設計方式重新調整所有欄位，或可能會修改特定的儲存格的值之後以程式設計方式調整都大小的特定資料列。  
  
## <a name="customizing-content-based-sizing-behavior"></a>自訂內容為基礎的調整大小行為  
 使用衍生時，您可以自訂調整大小行為<xref:System.Windows.Forms.DataGridView>儲存格、 資料列和資料行的類型，藉由覆寫<xref:System.Windows.Forms.DataGridViewCell.GetPreferredSize%2A?displayProperty=nameWithType>， <xref:System.Windows.Forms.DataGridViewRow.GetPreferredHeight%2A?displayProperty=nameWithType>，或<xref:System.Windows.Forms.DataGridViewColumn.GetPreferredWidth%2A?displayProperty=nameWithType>方法或藉由呼叫受保護的調整大小的方法多載中衍生<xref:System.Windows.Forms.DataGridView>控制項。 受保護的調整大小方法多載被設計來用於組，以達到理想的儲存格高度與寬度比率，避免過度寬或更高的資料格。 比方說，如果您呼叫`AutoResizeRows(DataGridViewAutoSizeRowsMode,Boolean)`多載<xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A>方法並傳入值為`false`如<xref:System.Boolean>參數多載會計算的理想高度和寬度的資料列，資料格，但它將會調整資料列高度只有。 然後您必須呼叫<xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A>調整欄寬度，以導出理想的方法。  
  
## <a name="content-based-sizing-options"></a>以內容為基礎的調整大小選項  
 調整大小屬性和方法所使用的列舉型別有類似的值，以內容為基礎的調整大小。 使用這些值，您可以限制哪些儲存格用來計算的慣用的大小。 針對所有的調整大小列舉型別，是指顯示的資料格的名稱的值會限制其顯示的資料列中資料格計算。 不包括資料列是以避免對效能帶來負面影響，當您正在使用的資料列數量龐大時很有用。 您也可以限制資料格的值，在標頭或非行首儲存格的計算。  
  
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
- [如何：設定 Windows Forms DataGridView 控制項的縮放模式](how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)

---
title: "Windows Form DataGridView 控制項中的調整大小選項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], row sizing
- data grids [Windows Forms], column sizing
- DataGridView control [Windows Forms], column sizing
- DataGridView control [Windows Forms], sizing options
- data grids [Windows Forms], row sizing
- data grids [Windows Forms], sizing options
ms.assetid: a5620a9c-0d06-41e3-8934-c25ddb16c9e6
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6cefca8e6856680d509d6166eec4d97855f1babc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="sizing-options-in-the-windows-forms-datagridview-control"></a>Windows Form DataGridView 控制項中的調整大小選項
<xref:System.Windows.Forms.DataGridView>資料列、 資料行和標頭可以變更大小，因為許多不同的項目。 下表顯示這些項目。  
  
|項目|描述|  
|----------------|-----------------|  
|使用者調整大小|使用者可以進行調整大小，拖曳或按兩下資料列、 資料行或標頭的分隔線。|  
|控制項調整大小|在資料行填滿模式中，資料行寬度變更時變更控制項寬度。例如，當控制項停駐於父表單和使用者調整表單的大小。|  
|儲存格值的變更|在以內容為基礎的自動調整大小模式中，大小變更以符合新的顯示值。|  
|方法呼叫|調整大小以程式設計方式以內容為基礎，可讓您在方法呼叫時，根據資料格的值是投機的大小調整。|  
|屬性設定|您也可以設定特定的高度和寬度值。|  
  
 根據預設，使用者重新調整大小啟用、 停用自動調整大小，以及儲存格寬度超過其資料行的值會被裁剪。  
  
 下表顯示案例，您可以使用來調整預設行為，或使用特定的調整大小選項來達到特定的效果。  
  
|情節|實作|  
|--------------|--------------------|  
|使用資料行填入模式顯示同樣的大小相當少量佔用整個控制項的寬度，而不會顯示水平捲軸的資料行中的資料。|將 <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> 屬性設定為 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>。|  
|使用資料行填入模式，來顯示不同大小的值。|將 <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> 屬性設定為 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>。 初始化相對的資料行寬度將資料行設定<xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>屬性或透過呼叫控制項<xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A>方法之後使用資料填入控制項。|  
|使用資料行填滿模式，顯示不同重要性的值。|將 <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> 屬性設定為 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>。 設定大型<xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A>必須永遠顯示其資料的部分或不使用調整大小選項以外的資料行填入模式的特定資料行的值。|  
|若要避免顯示控制項背景中使用資料行填入模式。|設定<xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>的最後一個資料行的屬性<xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill>和其他資料行使用其他的調整大小選項。 如果其他資料行使用太多的可用空間，設定<xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A>的最後一個資料行的屬性。|  
|顯示固定寬度資料行，例如圖示或識別碼資料行。|設定<xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>至<xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None>和<xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A>至<xref:System.Windows.Forms.DataGridViewTriState.False>資料行。 藉由設定初始化其寬度<xref:System.Windows.Forms.DataGridViewColumn.Width%2A>屬性或透過呼叫控制項<xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A>方法之後使用資料填入控制項。|  
|每當資料格內容變更，以避免裁剪及最佳化空間的使用會自動調整大小。|自動調整大小屬性設為值，表示以內容為基礎的調整大小模式。 若要使用大量的資料時，請避免對效能帶來負面影響，請使用會顯示資料列計算的調整大小模式。|  
|調整大小以符合以避免效能的負面影響，使用多個資料列時顯示的資料列的值。|使用自動或以程式設計方式調整大小的適當調整大小模式的列舉值。 若要調整大小以符合顯示新資料列的值，在捲動時，調整大小的方法呼叫中<xref:System.Windows.Forms.DataGridView.Scroll>事件處理常式。 若要自訂使用者按兩下調整大小，以便只顯示資料列中的值決定新的大小，呼叫調整大小的方法<xref:System.Windows.Forms.DataGridView.RowDividerDoubleClick>或<xref:System.Windows.Forms.DataGridView.ColumnDividerDoubleClick>事件處理常式。|  
|調整大小以符合儲存格的內容只在特定時間，以避免效能的負面影響，或啟用使用者重新調整大小。|事件處理常式中呼叫的內容為基礎的調整大小方法。 例如，使用<xref:System.Windows.Forms.DataGridView.DataBindingComplete>來初始化繫結之後, 的大小，以及處理事件<xref:System.Windows.Forms.DataGridView.CellValidated>或<xref:System.Windows.Forms.DataGridView.CellValueChanged>事件，以調整大小，以彌補使用者編輯或變更繫結的資料來源中。|  
|調整多行的資料格內容的資料列高度。|請確定資料行寬度是適合用來顯示的文字段落，並使用自動或以程式設計方式以內容為基礎的資料列大小調整高度。 此外也請確認儲存格以多行的內容會顯示使用<xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>資料格的樣式值<xref:System.Windows.Forms.DataGridViewTriState.True>。<br /><br /> 一般而言，您將使用資料行自動調整大小模式來維護資料行寬度，或將它們設定為特定的寬度之前的資料列高度會調整。|  
  
## <a name="resizing-with-the-mouse"></a>使用滑鼠調整大小  
 根據預設，使用者可以調整資料列、 資料行和標頭不是使用資料格的值為基礎的自動調整大小模式。 若要防止使用者與其他模式，例如資料行填入模式中，調整設定一或多個下列<xref:System.Windows.Forms.DataGridView>屬性：  
  
-   <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A>  
  
 您也可以防止使用者藉由設定調整個別的資料列或資料行其<xref:System.Windows.Forms.DataGridViewBand.Resizable%2A>屬性。 根據預設，<xref:System.Windows.Forms.DataGridViewBand.Resizable%2A>屬性值根據<xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A>資料行的屬性值和<xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A>資料列的屬性值。 如果您明確地設定<xref:System.Windows.Forms.DataGridViewBand.Resizable%2A>至<xref:System.Windows.Forms.DataGridViewTriState.True>或<xref:System.Windows.Forms.DataGridViewTriState.False>，不過指定的值會覆寫控制項的值是該資料列或資料行。 設定<xref:System.Windows.Forms.DataGridViewBand.Resizable%2A>至<xref:System.Windows.Forms.DataGridViewTriState.NotSet>還原繼承。  
  
 因為<xref:System.Windows.Forms.DataGridViewTriState.NotSet>還原繼承的值，<xref:System.Windows.Forms.DataGridViewBand.Resizable%2A>永遠不會傳回屬性<xref:System.Windows.Forms.DataGridViewTriState.NotSet>值的資料列或資料行尚未加入至除非<xref:System.Windows.Forms.DataGridView>控制項。 如果您需要確定是否<xref:System.Windows.Forms.DataGridViewBand.Resizable%2A>資料列或資料行的屬性值繼承時，檢查其<xref:System.Windows.Forms.DataGridViewElement.State%2A>屬性。 如果<xref:System.Windows.Forms.DataGridViewElement.State%2A>值包含<xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet>旗標，<xref:System.Windows.Forms.DataGridViewBand.Resizable%2A>不繼承屬性值。  
  
## <a name="automatic-sizing"></a>自動調整大小  
 有兩種類型中的自動調整大小的<xref:System.Windows.Forms.DataGridView>控制項： 資料行填入模式和以內容為基礎的自動調整大小。  
  
 資料行填入模式會導致以填滿控制項的顯示區域寬度控制項的可見資料行。 如需此模式的詳細資訊，請參閱[Windows Form DataGridView 控制項中的資料行填滿模式](../../../../docs/framework/winforms/controls/column-fill-mode-in-the-windows-forms-datagridview-control.md)。  
  
 您也可以設定資料列、 資料行，以及自動調整大小以適合其儲存格內容的標頭。 在此情況下，每當資料格內容變更時，就會發生大小調整。  
  
> [!NOTE]
>  如果您維持儲存格的值，自訂資料快取中使用的虛擬模式時，自動調整大小發生於使用者編輯儲存格的值，但當您改變之外的快取的值不會發生<xref:System.Windows.Forms.DataGridView.CellValuePushed>事件處理常式。 在此情況下，呼叫<xref:System.Windows.Forms.DataGridView.UpdateCellValue%2A>方法，以強制控制項更新資料格顯示，並且套用目前的自動調整大小模式。  
  
 如果只有一個維度已啟用以內容為基礎的自動調整大小，是針對資料列，但是沒有資料行，或資料行，但不是資料列 — 和<xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>也是每次變更與其他維度時，也會發生啟用，大小調整。 例如，如果資料列，但不是資料行設定為自動調整大小和<xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>已啟用，使用者可以拖曳資料行分隔線來變更資料行寬度及資料列的高度會自動調整儲存格的內容仍然完整顯示。  
  
 如果您設定資料列和資料行的內容為基礎的自動調整大小和<xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>已啟用，<xref:System.Windows.Forms.DataGridView>控制項將會調整大小，每當儲存格內容變更，將會使用一個理想的儲存格的高度與寬度比時計算新的大小。  
  
 若要設定標頭和資料列以及不會覆寫控制項值的資料行的調整模式，請設定一或多個下列<xref:System.Windows.Forms.DataGridView>屬性：  
  
-   <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A>  
  
 若要覆寫控制項的資料行調整大小模式個別資料行，請將其<xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>屬性以外的值為<xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet>。 資料行的調整大小模式實際上由其<xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A>屬性。 這個屬性的值為基礎的資料行<xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>屬性值，除非該值<xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet>的情況下的控制項<xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A>值繼承。  
  
 使用以內容為基礎的自動調整大小謹慎使用大量的資料時。 若要避免效能的負面影響，請使用計算只根據顯示的資料列，而不是分析控制項中的每個資料列的大小自動調整大小模式。 最大效能，使用以程式設計方式調整，改為因此您可以調整大小在特定時間，例如新的資料之後，立即載入。  
  
 以內容為基礎的自動調整大小模式不會影響資料列、 資料行或您隱藏資料列或資料行設定的標頭<xref:System.Windows.Forms.DataGridViewBand.Visible%2A>屬性或控制項<xref:System.Windows.Forms.DataGridView.RowHeadersVisible%2A>或<xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A>屬性`false`。 例如，如果資料行隱藏的自動調整大小以容納大型的資料格的值之後，隱藏資料行不會變更其大小如果包含大型的資料格的值的資料列遭到刪除。 自動調整大小不會發生變更可見性，因此變更資料行<xref:System.Windows.Forms.DataGridViewColumn.Visible%2A>屬性設回`true`將不會強制它重新計算其根據其目前內容的大小。  
  
 調整大小以程式設計方式以內容為基礎，會影響資料列、 資料行和標頭，不論其可見性。  
  
## <a name="programmatic-resizing"></a>以程式設計方式調整大小  
 停用自動調整大小，以程式設計方式設定正確的寬度或高度的資料列、 資料行或藉由下列屬性的標頭：  
  
-   <xref:System.Windows.Forms.DataGridView.RowHeadersWidth%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeight%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.DataGridViewRow.Height%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>  
  
 您也可以也以程式設計方式調整資料列、 資料行和標頭，以適合其內容，使用下列方法：  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A>  
  
 這些方法會重新調整資料列、 資料行，或一次標頭而不是設定這些持續調整大小。 新的大小會自動計算，以顯示所有儲存格內容，而不裁剪。 當您以程式設計方式調整資料行具有<xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A>屬性值<xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill>，不過，會按比例調整資料行使用以內容為基礎的計算的寬度<xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>屬性值和實際資料行的寬度然後根據計算這些新的比例，讓所有資料行填滿可用顯示區域的控制項。  
  
 以程式設計方式調整大小適合避免持續調整大小的效能負面影響。 它也很有用來提供使用者可調整大小的資料列、 資料行和標頭，以及資料行填入模式的初始大小。  
  
 您通常會在特定時間呼叫以程式設計方式調整大小的方法。 例如，您可能會在載入資料之後，立即以程式設計方式重新調整所有欄位，或可能會修改特定的資料格的值之後以程式設計方式調整都大小的特定資料列。  
  
## <a name="customizing-content-based-sizing-behavior"></a>自訂內容為基礎的調整大小行為  
 使用衍生時，您可以自訂調整大小行為<xref:System.Windows.Forms.DataGridView>資料格、 列和資料行的類型，藉由覆寫<xref:System.Windows.Forms.DataGridViewCell.GetPreferredSize%2A?displayProperty=nameWithType>， <xref:System.Windows.Forms.DataGridViewRow.GetPreferredHeight%2A?displayProperty=nameWithType>，或<xref:System.Windows.Forms.DataGridViewColumn.GetPreferredWidth%2A?displayProperty=nameWithType>方法或藉由呼叫受保護的調整大小的方法多載中衍生<xref:System.Windows.Forms.DataGridView>控制項。 受保護的調整大小方法多載專為搭配成對達到理想的儲存格高度與寬度比例，避免過度寬或更高的資料格。 例如，如果您呼叫`AutoResizeRows(DataGridViewAutoSizeRowsMode,Boolean)`多載<xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A>方法並傳入的值`false`如<xref:System.Boolean>參數，多載會計算的理想高度和資料列，資料格的寬度，但它將會調整資料列高度只有。 然後您必須呼叫<xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A>調整欄寬度，以在導出理想的方法。  
  
## <a name="content-based-sizing-options"></a>以內容為基礎的調整大小選項  
 調整大小屬性和方法所使用的列舉型別有類似的值，以內容為基礎的大小。 使用這些值，您可以限制哪些儲存格用來計算的慣用的大小。 所有的調整大小列舉名稱來指稱顯示的資料格的值會將計算中顯示的資料列的資料格限制。 排除的資料列適合您正在使用大量資料列時避免對效能帶來負面影響。 您也可以限制在標頭或非行首儲存格的計算。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowHeadersWidth%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeight%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewRow.Height%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeRowMode>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>  
 <xref:System.Windows.Forms.DataGridViewColumnHeadersHeightSizeMode>  
 <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>  
 [調整 Windows Forms DataGridView 控制項中資料行和資料列的大小](../../../../docs/framework/winforms/controls/resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView 控制項中的資料行填入模式](../../../../docs/framework/winforms/controls/column-fill-mode-in-the-windows-forms-datagridview-control.md)  
 [操作說明：設定 Windows Forms DataGridView 控制項的縮放模式](../../../../docs/framework/winforms/controls/how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)

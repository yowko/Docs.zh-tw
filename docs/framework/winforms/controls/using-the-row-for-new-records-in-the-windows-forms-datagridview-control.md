---
title: 使用 DataGridView 控制項中的新記錄資料列
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], adding rows for new records
- rows [Windows Forms], new records
- DataGridView control [Windows Forms], data entry
ms.assetid: 6110f1ea-9794-442c-a98a-f104a1feeaf4
ms.openlocfilehash: 2fcd35f8c4d04909cdbc26f6a4293fdd570385b8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728344"
---
# <a name="using-the-row-for-new-records-in-the-windows-forms-datagridview-control"></a>使用 Windows Form DataGridView 控制項中用於新增資料錄的資料列
當您使用 <xref:System.Windows.Forms.DataGridView> 來編輯應用程式中的資料時，您通常會想要讓使用者能夠將新的資料列新增至資料存放區。 <xref:System.Windows.Forms.DataGridView> 控制項支援這項功能，方法是提供新記錄的資料列，這一律會顯示為最後一個資料列。 它會在其資料列行首中以星號（*）符號標示。 下列各節將討論當您使用已啟用新記錄的資料列進行程式設計時，應該考慮的一些事項。  
  
## <a name="displaying-the-row-for-new-records"></a>顯示新記錄的資料列  
 使用 [<xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A>] 屬性，表示是否顯示新記錄的資料列。 此屬性的預設值為 `true`。  
  
 針對資料系結案例，如果控制項的 [<xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A>] 屬性和資料來源的 [<xref:System.ComponentModel.IBindingList.AllowNew%2A?displayProperty=nameWithType>] 屬性同時 `true`，就會顯示新記錄的資料列。 如果其中一個 `false`，則不會顯示該資料列。  
  
## <a name="populating-the-row-for-new-records-with-default-data"></a>以預設資料填入新記錄的資料列  
 當使用者選取新記錄的資料列做為目前的資料列時，<xref:System.Windows.Forms.DataGridView> 控制項會引發 <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> 事件。  
  
 此事件可讓您存取新的 <xref:System.Windows.Forms.DataGridViewRow>，並可讓您將預設資料填入新的資料列。 如需詳細資訊，請參閱[如何：在 Windows Forms DataGridView 控制項中指定新資料列的預設值](specify-default-values-for-new-rows-in-the-datagrid.md)  
  
## <a name="the-rows-collection"></a>Rows 集合  
 新記錄的資料列包含在 <xref:System.Windows.Forms.DataGridView> 控制項的 <xref:System.Windows.Forms.DataGridView.Rows%2A> 集合中，但在兩方面有不同的行為：  
  
- 新記錄的資料列無法以程式設計方式從 <xref:System.Windows.Forms.DataGridView.Rows%2A> 集合中移除。 如果嘗試這麼做，則會擲回 <xref:System.InvalidOperationException>。 使用者也無法刪除新記錄的資料列。 <xref:System.Windows.Forms.DataGridViewRowCollection.Clear%2A?displayProperty=nameWithType> 方法不會從 <xref:System.Windows.Forms.DataGridView.Rows%2A> 集合中移除此資料列。  
  
- 在新記錄的資料列之後，就無法加入任何資料列。 如果嘗試這種情況，就會引發 <xref:System.InvalidOperationException>。 因此，新記錄的資料列一律是 <xref:System.Windows.Forms.DataGridView> 控制項中的最後一個資料列。 <xref:System.Windows.Forms.DataGridViewRowCollection> 上的方法會加入資料列（<xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A>、<xref:System.Windows.Forms.DataGridViewRowCollection.AddCopy%2A>和 <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopies%2A>），這是當有新記錄的資料列存在時，在內部進行的所有呼叫插入方法。  
  
## <a name="visual-customization-of-the-row-for-new-records"></a>新記錄之資料列的視覺自訂  
 當新記錄的資料列建立時，它會根據 <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> 屬性所指定的資料列。 未為此資料列指定的任何儲存格樣式，都是繼承自其他屬性。 如需有關儲存格樣式繼承的詳細資訊，請參閱[Windows Forms DataGridView 控制項中的儲存格樣式](cell-styles-in-the-windows-forms-datagridview-control.md)。  
  
 新記錄之資料列中的儲存格所顯示的初始值，會從每一個資料格的 <xref:System.Windows.Forms.DataGridViewCell.DefaultNewRowValue%2A> 屬性中抓取。 對於 <xref:System.Windows.Forms.DataGridViewImageCell>類型的資料格，此屬性會傳回預留位置影像。 否則，這個屬性會傳回 `null`。 您可以覆寫這個屬性來傳回自訂值。 不過，當焦點進入新記錄的資料列時，這些初始值可以由 <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> 事件處理常式取代。  
  
 此資料列標頭的標準圖示（也就是箭號或星號）不會公開公開。 如果您想要自訂圖示，您將需要建立自訂的 <xref:System.Windows.Forms.DataGridViewRowHeaderCell> 類別。  
  
 標準圖示會使用資料列行首儲存格所使用之 <xref:System.Windows.Forms.DataGridViewCellStyle> 的 <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> 屬性。 如果沒有足夠的空間可以完全顯示標準圖示，則不會轉譯這些圖示。  
  
 如果資料列標頭儲存格已設定字串值，而且文字和圖示沒有足夠的空間，則會先卸載圖示。  
  
## <a name="sorting"></a>排序  
 在解除系結模式中，即使使用者已排序 <xref:System.Windows.Forms.DataGridView>的內容，新的記錄仍會新增至 <xref:System.Windows.Forms.DataGridView> 的結尾。 使用者必須再次套用排序，以便將資料列排序到正確的位置。這個行為類似于 <xref:System.Windows.Forms.ListView> 控制項。  
  
 在 [資料系結] 和 [虛擬模式] 中，套用排序時的插入行為將取決於資料模型的執行。 若為 ADO.NET，資料列會立即排序為正確的位置。  
  
## <a name="other-notes-on-the-row-for-new-records"></a>新記錄之資料列的其他注意事項  
 您無法將此資料列的 <xref:System.Windows.Forms.DataGridViewRow.Visible%2A> 屬性設定為 `false`。 如果嘗試這種情況，就會引發 <xref:System.InvalidOperationException>。  
  
 新記錄的資料列一律會以未選取的狀態建立。  
  
## <a name="virtual-mode"></a>虛擬模式  
 如果您要執行虛擬模式，您必須追蹤資料模型中何時需要新記錄的資料列，以及何時要回復加入的資料列。 這項功能的確切執行取決於資料模型的執行及其交易語義，例如，認可範圍是在儲存格或資料列層級。 如需詳細資訊，請參閱[Windows Forms DataGridView 控制項中的虛擬模式](virtual-mode-in-the-windows-forms-datagridview-control.md)。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>
- [Windows Forms DataGridView 控制項中的資料輸入](data-entry-in-the-windows-forms-datagridview-control.md)
- [操作說明：指定 Windows Forms DataGridView 控制項新資料列的預設值](specify-default-values-for-new-rows-in-the-datagrid.md)

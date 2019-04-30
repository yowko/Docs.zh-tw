---
title: 使用 Windows Form DataGridView 控制項中用於新增資料錄的資料列
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], adding rows for new records
- rows [Windows Forms], new records
- DataGridView control [Windows Forms], data entry
ms.assetid: 6110f1ea-9794-442c-a98a-f104a1feeaf4
ms.openlocfilehash: 67c87b28f04b028f329663d6cf8215370a00ef2f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009165"
---
# <a name="using-the-row-for-new-records-in-the-windows-forms-datagridview-control"></a>使用 Windows Form DataGridView 控制項中用於新增資料錄的資料列
當您使用<xref:System.Windows.Forms.DataGridView>編輯您的應用程式中的資料，您通常想要讓使用者能夠將新的資料列加入至資料存放區。 <xref:System.Windows.Forms.DataGridView>控制項支援藉由提供一個資料列的新記錄，這一律會顯示為最後一個資料列的這項功能。 它是使用星號 （*） 的符號標示其資料列行首。 下列各節將討論您的程式與新記錄的資料列的啟用時，您應該考慮的事項。  
  
## <a name="displaying-the-row-for-new-records"></a>顯示新資料錄的資料列  
 使用<xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A>屬性，指出是否要顯示新記錄的資料列。 此屬性的預設值為 `true`。  
  
 新記錄的資料列資料繫結案例，將會顯示如果<xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A>控制項的屬性和<xref:System.ComponentModel.IBindingList.AllowNew%2A?displayProperty=nameWithType>資料來源的屬性都`true`。 如果任何一種`false`則不會顯示資料列。  
  
## <a name="populating-the-row-for-new-records-with-default-data"></a>填入預設資料的新資料錄的資料列  
 當使用者為目前的資料列中，選取新的記錄的資料列<xref:System.Windows.Forms.DataGridView>控制引發<xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded>事件。  
  
 這個事件會提供存取新<xref:System.Windows.Forms.DataGridViewRow>並可讓您填入預設資料與新的資料列。 如需詳細資訊，請參閱[如何：指定 Windows Form DataGridView 控制項中的新資料列的預設值](specify-default-values-for-new-rows-in-the-datagrid.md)  
  
## <a name="the-rows-collection"></a>資料列集合  
 新記錄的資料列內<xref:System.Windows.Forms.DataGridView>控制項的<xref:System.Windows.Forms.DataGridView.Rows%2A>集合但行為以不同的方式在兩個方面：  
  
- 新記錄的資料列無法移除從<xref:System.Windows.Forms.DataGridView.Rows%2A>集合以程式設計的方式。 <xref:System.InvalidOperationException>如果嘗試這麼做會擲回。 使用者也無法刪除新記錄的資料列。 <xref:System.Windows.Forms.DataGridViewRowCollection.Clear%2A?displayProperty=nameWithType>方法並不會移除此資料列從<xref:System.Windows.Forms.DataGridView.Rows%2A>集合。  
  
- 新記錄的資料列之後，就可以不加入任何資料列。 <xref:System.InvalidOperationException>如果嘗試這麼做會引發。 如此一來，新資料錄的資料列一律是中的最後一個資料列<xref:System.Windows.Forms.DataGridView>控制項。 上的方法<xref:System.Windows.Forms.DataGridViewRowCollection>，將資料列 —<xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A>， <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopy%2A>，和<xref:System.Windows.Forms.DataGridViewRowCollection.AddCopies%2A>— 所有呼叫插入方法在內部有新的記錄的資料列時。  
  
## <a name="visual-customization-of-the-row-for-new-records"></a>資料列的新記錄的視覺自訂  
 建立新記錄的資料列時，它根據所指定的資料列<xref:System.Windows.Forms.DataGridView.RowTemplate%2A>屬性。 未指定這個資料列的任何儲存格樣式被繼承自其他屬性。 如需有關儲存格樣式繼承的詳細資訊，請參閱[Windows Forms DataGridView 控制項中的儲存格樣式](cell-styles-in-the-windows-forms-datagridview-control.md)。  
  
 新的記錄會擷取每個資料格的資料列中的儲存格所顯示的起始值<xref:System.Windows.Forms.DataGridViewCell.DefaultNewRowValue%2A>屬性。 類型的儲存格的<xref:System.Windows.Forms.DataGridViewImageCell>，這個屬性會傳回預留位置影像。 否則，此屬性會傳回`null`。 您可以覆寫這個屬性，以傳回自訂值。 不過，這些初始的值可以藉由取代<xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded>生於焦點進入的資料列的新記錄的事件處理常式。  
  
 這個資料列的標頭，也就是一個箭號，或是使用星號的標準圖示不會公開。 如果您想要自訂圖示，您必須建立自訂<xref:System.Windows.Forms.DataGridViewRowHeaderCell>類別。  
  
 使用標準的圖示<xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>屬性<xref:System.Windows.Forms.DataGridViewCellStyle>中使用的資料列標題儲存格。 如果沒有可用的空間不足，無法完整顯示，不會轉譯標準圖示。  
  
 如果資料列的標頭資料格具有字串值設定，而且如果沒有足夠的空間為文字和圖示，圖示會先卸除。  
  
## <a name="sorting"></a>排序  
 在未繫結模式中，新的記錄會一律會新增至結尾<xref:System.Windows.Forms.DataGridView>即使使用者已排序的內容<xref:System.Windows.Forms.DataGridView>。 使用者必須重新套用排序，以正確的位置，來排序資料列此行為會類似於<xref:System.Windows.Forms.ListView>控制項。  
  
 在資料繫結和虛擬模式中，插入時的行為套用排序會取決於資料模型的實作。 針對[!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]，資料列立即排序到正確的位置。  
  
## <a name="other-notes-on-the-row-for-new-records"></a>在新記錄的資料列上的其他注意事項  
 您無法設定<xref:System.Windows.Forms.DataGridViewRow.Visible%2A>屬性到這個資料列`false`。 <xref:System.InvalidOperationException>如果嘗試這麼做會引發。  
  
 未選取狀態一律被建立新記錄的資料列。  
  
## <a name="virtual-mode"></a>虛擬模式  
 如果您要實作虛擬模式，您必須在必要時，新資料錄的資料列是在資料模型，以及何時要復原的資料列加入追蹤。 這項功能的實際實作取決於實作的資料模型和其交易語意，比方說，在資料列層級上是否為認可範圍。 如需詳細資訊，請參閱 < [Windows Forms DataGridView 控制項中的虛擬模式](virtual-mode-in-the-windows-forms-datagridview-control.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>
- [Windows Forms DataGridView 控制項中的資料輸入](data-entry-in-the-windows-forms-datagridview-control.md)
- [如何：指定 Windows Form DataGridView 控制項中的新資料列的預設值](specify-default-values-for-new-rows-in-the-datagrid.md)

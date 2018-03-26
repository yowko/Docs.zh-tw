---
title: 使用 Windows Form DataGridView 控制項中用於新增資料錄的資料列
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], adding rows for new records
- rows [Windows Forms], new records
- DataGridView control [Windows Forms], data entry
ms.assetid: 6110f1ea-9794-442c-a98a-f104a1feeaf4
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e349a33c90d08606da09ebdf32de6dedb8d6a52c
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/26/2018
---
# <a name="using-the-row-for-new-records-in-the-windows-forms-datagridview-control"></a>使用 Windows Form DataGridView 控制項中用於新增資料錄的資料列
當您使用<xref:System.Windows.Forms.DataGridView>進行編輯您的應用程式中的資料，您通常想要讓使用者能夠將新的資料列加入至資料存放區。 <xref:System.Windows.Forms.DataGridView>控制項支援藉由提供一個資料列給新的記錄，這一律會顯示為最後一個資料列的這項功能。 它會標示有星號 （*） 符號，其資料列行首。 下列各節會討論一些程式與資料列的新記錄啟用時，您應該考慮的事項。  
  
## <a name="displaying-the-row-for-new-records"></a>顯示新資料錄的資料列  
 使用<xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A>屬性，指出是否顯示為新的記錄資料列。 此屬性的預設值為 `true`。  
  
 資料繫結案例，將會顯示為新的記錄資料列如果<xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A>控制項的屬性和<xref:System.ComponentModel.IBindingList.AllowNew%2A?displayProperty=nameWithType>資料來源的屬性都`true`。 如果任何一種`false`則不會顯示資料列。  
  
## <a name="populating-the-row-for-new-records-with-default-data"></a>新的記錄，預設的資料填入的資料列  
 當使用者為目前的資料列中，選取新的記錄的資料列<xref:System.Windows.Forms.DataGridView>控制引發<xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded>事件。  
  
 此事件提供新的存取<xref:System.Windows.Forms.DataGridViewRow>並可讓您擴展新的資料列，預設的資料。 如需詳細資訊，請參閱[How to： 指定 Windows Form DataGridView 控制項中的新資料列的預設值的值](../../../../docs/framework/winforms/controls/specify-default-values-for-new-rows-in-the-datagrid.md)  
  
## <a name="the-rows-collection"></a>資料列集合  
 新記錄的資料列包含在<xref:System.Windows.Forms.DataGridView>控制項的<xref:System.Windows.Forms.DataGridView.Rows%2A>集合但的行為方式會在兩個方面：  
  
-   無法移除新記錄的資料列，從<xref:System.Windows.Forms.DataGridView.Rows%2A>集合以程式設計的方式。 <xref:System.InvalidOperationException>如果嘗試這麼做會擲回。 使用者也無法刪除新記錄的資料列。 <xref:System.Windows.Forms.DataGridViewRowCollection.Clear%2A?displayProperty=nameWithType>方法不會移除這個資料列從<xref:System.Windows.Forms.DataGridView.Rows%2A>集合。  
  
-   新記錄的資料列之後，就可以加入沒有資料列。 <xref:System.InvalidOperationException>如果嘗試這麼做會引發。 如此一來，新資料錄的資料列永遠是中的最後一個資料列<xref:System.Windows.Forms.DataGridView>控制項。 上的方法<xref:System.Windows.Forms.DataGridViewRowCollection>將資料列加入 —<xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A>， <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopy%2A>，和<xref:System.Windows.Forms.DataGridViewRowCollection.AddCopies%2A>— 呼叫所有插入方法內部新記錄的資料列存在時。  
  
## <a name="visual-customization-of-the-row-for-new-records"></a>視覺自訂資料列的新資料錄  
 建立新記錄的資料列時，它根據指定的資料列<xref:System.Windows.Forms.DataGridView.RowTemplate%2A>屬性。 未指定這個資料列的任何儲存格樣式被繼承自其他屬性。 如需儲存格樣式繼承的詳細資訊，請參閱[Windows Form DataGridView 控制項中的儲存格樣式](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)。  
  
 從每個資料格會擷取新的記錄資料列中的儲存格所顯示的起始值<xref:System.Windows.Forms.DataGridViewCell.DefaultNewRowValue%2A>屬性。 類型的儲存格的<xref:System.Windows.Forms.DataGridViewImageCell>，這個屬性會傳回預留位置影像。 否則，這個屬性會傳回`null`。 您可以覆寫這個屬性，以傳回自訂值。 不過，這些初始的值可能會取代<xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded>當焦點資料列中輸入新記錄的事件處理常式。  
  
 不會公開公開此資料列標頭，也就是箭號或星號的標準圖示。 如果您想要自訂圖示，您必須建立自訂<xref:System.Windows.Forms.DataGridViewRowHeaderCell>類別。  
  
 使用標準的圖示<xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>屬性<xref:System.Windows.Forms.DataGridViewCellStyle>中使用資料列的標頭資料格。 如果空間不足，無法完整顯示，不會轉譯標準圖示。  
  
 如果資料列的標頭資料格具有字串值設定，而且如果沒有足夠的空間為文字和圖示，圖示會先卸除。  
  
## <a name="sorting"></a>排序  
 在未繫結模式中，新的記錄會一律加入至結尾<xref:System.Windows.Forms.DataGridView>即使使用者已排序的內容<xref:System.Windows.Forms.DataGridView>。 使用者必須再次套用排序，若要排序資料列到正確的位置。此行為是類似的<xref:System.Windows.Forms.ListView>控制項。  
  
 在資料繫結和虛擬模式，插入時的行為套用排序將會相依於資料模型的實作。 如[!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]，資料列會立即根據排序的正確位置。  
  
## <a name="other-notes-on-the-row-for-new-records"></a>其他的資料列的新記錄的注意事項  
 您不能設定<xref:System.Windows.Forms.DataGridViewRow.Visible%2A>屬性到此資料列的`false`。 <xref:System.InvalidOperationException>如果嘗試這麼做會引發。  
  
 未選取狀態永遠被建立新記錄的資料列。  
  
## <a name="virtual-mode"></a>虛擬模式  
 如果您實作虛擬模式時，您必須為新記錄的資料列中的資料模型和何時要復原的資料列加入需要時加以追蹤。 確切實作這項功能的實作而定的資料模型和交易語意，例如，認可範圍是否在資料列層級。 如需詳細資訊，請參閱[Windows Form DataGridView 控制項中的虛擬模式](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>  
 [Windows Forms DataGridView 控制項中的資料輸入](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 [操作說明：指定 Windows Forms DataGridView 控制項新資料列的預設值](../../../../docs/framework/winforms/controls/specify-default-values-for-new-rows-in-the-datagrid.md)

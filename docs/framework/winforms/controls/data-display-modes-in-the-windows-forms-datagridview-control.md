---
title: DataGridView 控制項中的資料顯示模式
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], display modes
- data grids [Windows Forms], display modes
- DataGridView control [Windows Forms], display modes
ms.assetid: 9755a030-3f3f-4705-a661-ba5a48a81875
ms.openlocfilehash: ad6be647e3a36904b055fd6771f539df28938fab
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744015"
---
# <a name="data-display-modes-in-the-windows-forms-datagridview-control"></a>Windows Form DataGridView 控制項的資料顯示模式
<xref:System.Windows.Forms.DataGridView> 控制項可以用三種不同的模式顯示資料：系結、解除系結和虛擬。 根據您的需求選擇最適合的模式。  
  
## <a name="unbound"></a>未繫結  
 「解除系結模式」適合用來顯示以程式設計方式管理的相對較少量資料。 您不會將 <xref:System.Windows.Forms.DataGridView> 控制項直接附加至以系結模式為的資料來源。 相反地，您必須自行填入控制項，通常是使用 <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> 方法。  
  
 解除系結模式對於靜態、唯讀資料而言特別有用，或者當您想要提供您自己的程式碼來與外部資料存放區互動時，是非常實用的。 不過，當您想要讓使用者與外部資料源互動時，通常會使用系結模式。  
  
 如需使用唯讀未系結 <xref:System.Windows.Forms.DataGridView>的範例，請參閱[如何：建立未系結的 Windows Forms DataGridView 控制項](how-to-create-an-unbound-windows-forms-datagridview-control.md)。  
  
## <a name="bound"></a>繫結  
 系結模式適用于使用與資料存放區的自動互動來管理資料。 您可以藉由設定 <xref:System.Windows.Forms.DataGridView.DataSource%2A> 屬性，將 <xref:System.Windows.Forms.DataGridView> 控制項直接附加至其資料來源。 當控制項是資料系結時，資料列就會推送並提取，而不需要您的明確管理。 `true`<xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> 屬性時，資料來源中的每個資料行都會導致在控制項中建立對應的資料行。 如果您想要建立自己的資料行，可以將此屬性設定為 `false` 並使用 <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A> 屬性，在設定每個資料行時加以系結。 當您想要使用預設產生的類型以外的資料行類型時，這會很有用。 如需詳細資訊，請參閱[Windows Forms DataGridView 控制項中的資料行類型](column-types-in-the-windows-forms-datagridview-control.md)。  
  
 如需使用系結 <xref:System.Windows.Forms.DataGridView> 控制項的範例，請參閱[逐步解說：驗證 Windows Forms DataGridView 控制項中的資料](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)。  
  
 您也可以將未系結的資料行加入至系結模式中的 <xref:System.Windows.Forms.DataGridView> 控制項。 當您想要顯示可讓使用者在特定資料列上執行動作的按鈕或連結的資料行時，這會很有用。 使用從系結的資料行計算出的值，也很有用。 您可以在 <xref:System.Windows.Forms.DataGridView.CellFormatting> 事件的處理常式中，填入計算結果欄的資料格值。 不過，如果您使用 <xref:System.Data.DataSet> 或 <xref:System.Data.DataTable> 做為資料來源，您可能會想要改為使用 <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType> 屬性來建立計算結果欄。 在這種情況下，<xref:System.Windows.Forms.DataGridView> 控制項將會處理匯出資料行，就像資料來源中的任何其他資料行一樣。  
  
 不支援以系結模式的未系結資料行排序。 如果您在系結模式中建立包含使用者可編輯值的未系結資料行，當控制項依系結的資料行排序時，您必須執行虛擬模式來維護這些值。  
  
## <a name="virtual"></a>Virtual  
 透過虛擬模式，您可以執行自己的資料管理作業。 當控制項依系結的資料行排序時，必須使用這項功能來維護系結模式中未系結之資料行的值。 不過，虛擬模式的主要用途是在與大量資料互動時，將效能優化。  
  
 您會將 <xref:System.Windows.Forms.DataGridView> 控制項附加至您所管理的快取，而您的程式碼會控制何時推送和提取資料列。 為了讓記憶體耗用量變小，快取的大小應該與目前顯示的資料列數目相似。 當使用者將新的資料列滾動到 view 時，您的程式碼會向快取要求新資料，並選擇性地從記憶體中清除舊資料。  
  
 當您正在執行虛擬模式時，您必須追蹤何時需要在資料模型中建立新的資料列，以及何時要復原新資料列的加入。 這項功能的確切執行將取決於資料模型的執行和資料模型的交易語義;認可範圍是否在資料格或資料列層級。  
  
 如需虛擬模式的詳細資訊，請參閱[Windows Forms DataGridView 控制項中的虛擬模式](virtual-mode-in-the-windows-forms-datagridview-control.md)。 如需顯示如何使用虛擬模式事件的範例，請參閱[逐步解說：在 Windows Forms DataGridView 控制項中執行虛擬模式](implementing-virtual-mode-wf-datagridview-control.md)。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A?displayProperty=nameWithType>
- [在 Windows Forms DataGridView 控制項中顯示資料](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView 控制項中的資料行類型](column-types-in-the-windows-forms-datagridview-control.md)
- [逐步解說：建立未繫結的 Windows Forms DataGridView 控制項](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)
- [操作說明：將資料繫結至 Windows Forms DataGridView 控制項](how-to-bind-data-to-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView 控制項中的虛擬模式](virtual-mode-in-the-windows-forms-datagridview-control.md)
- [逐步解說：在 Windows Forms DataGridView 控制項中實作虛擬模式](implementing-virtual-mode-wf-datagridview-control.md)

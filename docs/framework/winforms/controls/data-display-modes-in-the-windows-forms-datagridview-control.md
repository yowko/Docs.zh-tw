---
title: Windows Form DataGridView 控制項的資料顯示模式
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], display modes
- data grids [Windows Forms], display modes
- DataGridView control [Windows Forms], display modes
ms.assetid: 9755a030-3f3f-4705-a661-ba5a48a81875
ms.openlocfilehash: 673780909f6d66168548893e99d79bbfec70a0e0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011403"
---
# <a name="data-display-modes-in-the-windows-forms-datagridview-control"></a>Windows Form DataGridView 控制項的資料顯示模式
<xref:System.Windows.Forms.DataGridView>控制項可以顯示三種不同模式中的資料： 繫結、 解除繫結和虛擬。 選擇最適合的模式，根據您的需求。  
  
## <a name="unbound"></a>未繫結  
 未繫結的模式適合用來顯示相對少量的資料，您以程式設計方式管理。 您不要附加<xref:System.Windows.Forms.DataGridView>控制項直接繫結模式與資料來源。 相反地，您必須自行填入控制項，通常使用<xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType>方法。  
  
 未繫結的模式可以是靜態的唯讀資料，或當您想要使用外部資料存放區提供自己的程式碼互動時特別有用。 當您想您與外部資料來源互動的使用者時，不過，您通常會使用繫結的模式。  
  
 如需範例，會使用唯讀未繫結<xref:System.Windows.Forms.DataGridView>，請參閱[How to:建立未繫結的 Windows Forms DataGridView 控制項](how-to-create-an-unbound-windows-forms-datagridview-control.md)。  
  
## <a name="bound"></a>繫結  
 繫結的模式適合用來管理使用與資料存放區的自動互動的資料。 您可以將附加<xref:System.Windows.Forms.DataGridView>直接藉由設定其資料來源控制項<xref:System.Windows.Forms.DataGridView.DataSource%2A>屬性。 資料繫結控制項時，資料列會推送和提取而不需要明確的管理組件上。 當<xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A>屬性是`true`，在您的資料來源中的每個資料行，會導致在控制項中建立的對應資料行。 如果您想要建立您自己的資料行，您可以設定這個屬性為`false`並用<xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A>要繫結每個資料行，當您在設定屬性。 當您想要使用非預設產生的型別資料行類型，這非常有用。 如需詳細資訊，請參閱 < [Windows Forms DataGridView 控制項中的資料行類型](column-types-in-the-windows-forms-datagridview-control.md)。  
  
 如需範例，會使用繫結至<xref:System.Windows.Forms.DataGridView>控制項，請參閱[逐步解說：驗證資料，在 Windows Form DataGridView 控制項](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)。  
  
 您也可以加入未繫結的資料行以<xref:System.Windows.Forms.DataGridView>繫結模式中的控制項。 當您想要顯示的按鈕或連結，可讓使用者執行動作的特定資料列的資料行時，這非常有用。 它也很有用，顯示資料行值從繫結資料行計算的。 您可以填入處理常式中的導出資料行的資料格值<xref:System.Windows.Forms.DataGridView.CellFormatting>事件。 如果您使用<xref:System.Data.DataSet>或是<xref:System.Data.DataTable>做為資料來源，不過，您可能想要使用<xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType>改為建立導出資料行的屬性。 在此情況下，<xref:System.Windows.Forms.DataGridView>控制項便會將導出資料行，就像任何其他資料行中的資料來源。  
  
 不支援未繫結中繫結模式的資料行排序。 如果您建立未繫結的資料行，其中包含使用者可編輯的值繫結模式中時，您必須實作虛擬模式來維護這些值，當控制項所繫結的資料行排序時。  
  
## <a name="virtual"></a>虛擬  
 虛擬模式中，您可以實作您自己的資料管理作業。 這是為了維護未繫結的資料行的值繫結模式中，當控制項所繫結資料行排序時。 不過，虛擬模式中，主要用途是互動的大量資料時將效能最佳化。  
  
 您將附加<xref:System.Windows.Forms.DataGridView>您管理的快取的控制及您的程式碼控制何時推送和提取資料的資料列。 為了維持這種記憶體耗用量，快取應該會類似大小目前顯示的資料列數目。 當使用者將新的資料列捲動至檢視時，您的程式碼會從快取要求新的資料，並選擇性地從記憶體清除舊資料。  
  
 當您要實作虛擬模式時，您必須追蹤新的資料列，才能在資料模型時復原加入新的資料列時。 這項功能的實際實作取決於資料模型的實作和交易的語意資料模型中;認可範圍是否在資料列層級。  
  
 如需有關虛擬模式的詳細資訊，請參閱[Windows Forms DataGridView 控制項中的虛擬模式](virtual-mode-in-the-windows-forms-datagridview-control.md)。 如需示範如何使用虛擬模式事件的範例，請參閱[逐步解說：實作虛擬模式中的 Windows Form DataGridView 控制項](implementing-virtual-mode-wf-datagridview-control.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A?displayProperty=nameWithType>
- [在 Windows Forms DataGridView 控制項中顯示資料](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView 控制項中的資料行類型](column-types-in-the-windows-forms-datagridview-control.md)
- [逐步解說：建立未繫結的 Windows Form DataGridView 控制項](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)
- [如何：將資料繫結至 Windows Form DataGridView 控制項](how-to-bind-data-to-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView 控制項中的虛擬模式](virtual-mode-in-the-windows-forms-datagridview-control.md)
- [逐步解說：在 Windows Form DataGridView 控制項中實作虛擬模式](implementing-virtual-mode-wf-datagridview-control.md)

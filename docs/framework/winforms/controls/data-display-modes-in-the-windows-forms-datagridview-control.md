---
title: Windows Form DataGridView 控制項的資料顯示模式
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], display modes
- data grids [Windows Forms], display modes
- DataGridView control [Windows Forms], display modes
ms.assetid: 9755a030-3f3f-4705-a661-ba5a48a81875
ms.openlocfilehash: f97576218df651553ed1ac5f681d1ec0b4ab5ef3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="data-display-modes-in-the-windows-forms-datagridview-control"></a>Windows Form DataGridView 控制項的資料顯示模式
<xref:System.Windows.Forms.DataGridView>控制項可以顯示三種不同模式中的資料： 繫結、 繫結，與虛擬。 選擇最適合您的需求為基礎的模式。  
  
## <a name="unbound"></a>未繫結  
 未繫結的模式適合用來顯示相對較小的大量資料，您以程式設計方式管理。 您不要附加<xref:System.Windows.Forms.DataGridView>直接到資料來源與繫結模式的控制項。 相反地，您必須自行填入控制項，通常使用<xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType>方法。  
  
 未繫結的模式可以是靜態的唯讀資料，或當您想要使用外部資料存放區提供自己的程式碼互動時特別有用。 當您想讓使用者互動的外部資料來源時，不過，您通常會使用繫結的模式。  
  
 如需範例，會使用唯讀未繫結<xref:System.Windows.Forms.DataGridView>，請參閱[How to： 建立未繫結的 Windows Form DataGridView 控制項](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md)。  
  
## <a name="bound"></a>繫結  
 繫結的模式適合用來管理使用與資料存放區的自動互動的資料。 您可以將附加<xref:System.Windows.Forms.DataGridView>直接藉由設定其資料來源控制項<xref:System.Windows.Forms.DataGridView.DataSource%2A>屬性。 資料繫結控制項時，資料列會推送和提取而不需要明確管理組件。 當<xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A>屬性是`true`，資料來源中的每個資料行，會導致控制項中建立對應資料行。 如果您想要建立您自己的資料行，您可以設定這個屬性為`false`並用<xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A>繫結每個資料行，當您設定它的屬性。 當您想要使用資料行以外的類型會預設產生的型別時，這非常有用。 如需詳細資訊，請參閱[Windows Form DataGridView 控制項中的資料行類型](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)。  
  
 如需範例，會使用繫結至<xref:System.Windows.Forms.DataGridView>控制，請參閱[逐步解說： 驗證 Windows Form DataGridView 控制項中的資料](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)。  
  
 您也可以加入未繫結的資料行以<xref:System.Windows.Forms.DataGridView>中繫結模式的控制項。 當您想要顯示的按鈕或連結，可讓使用者執行動作的特定資料列的資料行時，這非常有用。 它也很有用，顯示資料行值從繫結資料行計算而得。 您可以填入處理常式中的導出資料行的資料格值<xref:System.Windows.Forms.DataGridView.CellFormatting>事件。 如果您使用<xref:System.Data.DataSet>或<xref:System.Data.DataTable>做為資料來源，不過，您可能想要使用<xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType>改為建立導出資料行的屬性。 在此情況下，<xref:System.Windows.Forms.DataGridView>控制項便會將導出資料行，就像任何其他資料行中的資料來源。  
  
 不支援的繫結模式的未繫結資料行排序。 如果您建立未繫結的資料行，其中包含使用者可編輯的值繫結模式中，您必須實作虛擬模式，以維護這些值，當控制項所繫結的資料行排序時。  
  
## <a name="virtual"></a>虛擬  
 虛擬模式中，您可以實作您自己的資料管理作業。 這是為了維護未繫結的資料行的值繫結模式中，當控制項繫結資料行來排序。 不過，虛擬模式的主要用途是大量的資料和互動時，將效能最佳化。  
  
 您將附加<xref:System.Windows.Forms.DataGridView>管理時，快取控制項和您的程式碼會控制何時發送和提取資料的資料列。 若要維持記憶體耗用量，快取應該的大小類似的目前顯示的資料列數目。 當使用者將新的資料列捲動到檢視中時，您的程式碼會從快取要求新的資料，並選擇性地從記憶體清除舊資料。  
  
 當您實作虛擬模式時，您必須視需要新的資料列是在資料模型時復原新的資料列加入追蹤。 確切實作這項功能將取決於資料模型的實作和交易的語意資料模型。認可範圍是否在資料列層級。  
  
 如需虛擬模式的詳細資訊，請參閱[Windows Form DataGridView 控制項中的虛擬模式](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)。 如需示範如何使用虛擬模式事件的範例，請參閱[逐步解說： 在 Windows Form DataGridView 控制項中實作虛擬模式](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A?displayProperty=nameWithType>  
 [在 Windows Forms DataGridView 控制項中顯示資料](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView 控制項中的資料行類型](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  
 [逐步解說：建立未繫結的 Windows Forms DataGridView 控制項](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)  
 [操作說明：將資料繫結至 Windows Forms DataGridView 控制項](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView 控制項中的虛擬模式](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)  
 [逐步解說：在 Windows Forms DataGridView 控制項中實作虛擬模式](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)

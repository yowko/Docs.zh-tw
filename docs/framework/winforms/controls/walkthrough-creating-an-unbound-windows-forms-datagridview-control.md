---
title: 建立未系結的 DataGridView 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [Windows Forms], displaying without binding to data source
- DataGridView control [Windows Forms], unbound data
- DataGridView control [Windows Forms], displaying data without binding to a data source
- data [Windows Forms], unbound
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 5a8d6afa-1b4b-4b24-8db8-501086ffdebe
ms.openlocfilehash: ceb75d4ee845d1f643d4d88d5a9f1bde73edcc70
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740182"
---
# <a name="walkthrough-creating-an-unbound-windows-forms-datagridview-control"></a>逐步解說：建立未繫結的 Windows Form DataGridView 控制項
您可能經常想要顯示不是源自資料庫的表格式資料。 例如，您可能會想要顯示字串二維陣列的內容。 <xref:System.Windows.Forms.DataGridView> 類別提供簡單且可高度自訂的方式來顯示資料，而不需要系結至資料來源。 本逐步解說示範如何在「未系結」模式中填入 <xref:System.Windows.Forms.DataGridView> 控制項，以及管理資料列的加入和刪除。 根據預設，使用者可以加入新的資料列。 若要避免加入資料列，請將 <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> 屬性設為 `false`。  
  
 若要將本主題中的程式碼複製成單一清單，請參閱[如何：建立未系結的 Windows Forms DataGridView 控制項](how-to-create-an-unbound-windows-forms-datagridview-control.md)。  
  
## <a name="creating-the-form"></a>建立表單  
  
#### <a name="to-use-an-unbound-datagridview-control"></a>使用未系結的 DataGridView 控制項  
  
1. 建立衍生自 <xref:System.Windows.Forms.Form> 的類別，並包含下列變數宣告和 `Main` 方法。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#02)]  
  
2. 在表單的類別定義中執行 `SetupLayout` 方法，以設定表單的版面配置。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#20)]  
  
3. 建立 `SetupDataGridView` 方法來設定 <xref:System.Windows.Forms.DataGridView> 的資料行和屬性。  
  
     這個方法會先將 <xref:System.Windows.Forms.DataGridView> 控制項新增至表單的 <xref:System.Windows.Forms.Control.Controls%2A> 集合。 接下來，會使用 <xref:System.Windows.Forms.DataGridView.ColumnCount%2A> 屬性來設定要顯示的資料行數目。 資料行標頭的預設樣式是藉由設定 [<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>] 屬性所傳回之 <xref:System.Windows.Forms.DataGridViewCellStyle> 的 [<xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A>]、[<xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>] 和 [<xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A> 屬性] 來設定。  
  
     設定版面配置和外觀屬性，然後指派資料行名稱。 當這個方法結束時，就可以填入 <xref:System.Windows.Forms.DataGridView> 控制項。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#30)]  
  
4. 建立 `PopulateDataGridView` 方法，將資料列加入 <xref:System.Windows.Forms.DataGridView> 控制項。  
  
     每個資料列都代表一個歌曲和其相關資訊。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#40)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#40)]  
  
5. 備妥公用程式方法之後，您就可以附加事件處理常式。  
  
     您將處理 [**加入**] 和 [**刪除**] 按鈕的 <xref:System.Windows.Forms.Control.Click> 事件、表單的 <xref:System.Windows.Forms.Form.Load> 事件和 <xref:System.Windows.Forms.DataGridView> 控制項的 <xref:System.Windows.Forms.DataGridView.CellFormatting> 事件。  
  
     當引發 [**加入**] 按鈕的 <xref:System.Windows.Forms.Control.Click> 事件時，新的空白資料列就會加入至 <xref:System.Windows.Forms.DataGridView>。  
  
     當 [**刪除**] 按鈕的 <xref:System.Windows.Forms.Control.Click> 事件引發時，會刪除選取的資料列，除非它是新記錄的資料列，讓使用者可以加入新的資料列。 這個資料列一律是 <xref:System.Windows.Forms.DataGridView> 控制項中的最後一個資料列。  
  
     當表單的 <xref:System.Windows.Forms.Form.Load> 事件引發時，會呼叫 `SetupLayout`、`SetupDataGridView`和 `PopulateDataGridView` 公用程式方法。  
  
     當 <xref:System.Windows.Forms.DataGridView.CellFormatting> 事件引發時，`Date` 資料行中的每個儲存格都會格式化為完整日期，除非無法剖析儲存格的值。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#10)]  
  
## <a name="testing-the-application"></a>測試應用程式  
 您現在可以測試表單，以確定它會如預期般運作。  
  
#### <a name="to-test-the-form"></a>測試表單  
  
- 按 F5 執行應用程式。  
  
     您會看到 <xref:System.Windows.Forms.DataGridView> 控制項，其中顯示 `PopulateDataGridView`中列出的歌曲。 您可以使用 [**加入資料列**] 按鈕加入新的資料列，也可以使用 [**刪除資料列**] 按鈕來刪除選取的資料列。 未系結的 <xref:System.Windows.Forms.DataGridView> 控制項是資料存放區，而且其資料與任何外部來源（例如 <xref:System.Data.DataSet> 或陣列）無關。  
  
## <a name="next-steps"></a>後續步驟  
 此應用程式可讓您對 <xref:System.Windows.Forms.DataGridView> 控制項的功能有基本瞭解。 您可以透過數種方式自訂 <xref:System.Windows.Forms.DataGridView> 控制項的外觀和行為：  
  
- 變更框線和標題樣式。 如需詳細資訊，請參閱[如何：變更 Windows Forms DataGridView 控制項中的框線和格線樣式](change-the-border-and-gridline-styles-in-the-datagrid.md)。  
  
- 啟用或限制 <xref:System.Windows.Forms.DataGridView> 控制項的使用者輸入。 如需詳細資訊，請參閱[如何：防止在 Windows Forms Datagridview 控制項中新增和刪除](prevent-row-addition-and-deletion-datagridview.md)資料[列和如何：將 Windows Forms DataGridView 控制項中](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)的資料行設為唯讀。  
  
- 檢查使用者輸入中是否有資料庫相關錯誤。 如需詳細資訊，請參閱[逐步解說：處理 Windows Forms DataGridView 控制項中的資料輸入期間所發生的錯誤](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)。  
  
- 使用虛擬模式處理非常大型的資料集。 如需詳細資訊，請參閱[逐步解說：在 Windows Forms DataGridView 控制項中執行虛擬模式](implementing-virtual-mode-wf-datagridview-control.md)。  
  
- 自訂儲存格的外觀。 如需詳細資訊，請參閱[如何：在 Windows Forms Datagridview 控制項中自訂儲存格的外觀](customize-the-appearance-of-cells-in-the-datagrid.md)和[如何：設定 Windows Forms DataGridView 控制項的預設儲存格樣式](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- [在 Windows Forms DataGridView 控制項中顯示資料](displaying-data-in-the-windows-forms-datagridview-control.md)
- [操作說明：建立未繫結的 Windows Forms DataGridView 控制項](how-to-create-an-unbound-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView 控制項的資料顯示模式](data-display-modes-in-the-windows-forms-datagridview-control.md)

---
title: 逐步解說：建立未繫結的 Windows Form DataGridView 控制項
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
ms.openlocfilehash: 26c2241f4b0a3b23255de15b3d0c9f8bdd15de02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-creating-an-unbound-windows-forms-datagridview-control"></a>逐步解說：建立未繫結的 Windows Form DataGridView 控制項
您可能常要顯示不是來自資料庫的表格式資料。 比方說，您可能想要顯示字串的二維陣列的內容。 <xref:System.Windows.Forms.DataGridView>類別會提供簡單高度可自訂的方式顯示資料，而不繫結至資料來源。 本逐步解說示範如何以填入<xref:System.Windows.Forms.DataGridView>控制和管理的新增和刪除 「 未繫結 」 模式中的資料列。 根據預設，使用者可以加入新的資料列。 若要避免資料列加入，將<xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A>屬性是`false`。  
  
 若要為單一列出本主題中複製的程式碼，請參閱[How to： 建立未繫結的 Windows Form DataGridView 控制項](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md)。  
  
## <a name="creating-the-form"></a>建立表單  
  
#### <a name="to-use-an-unbound-datagridview-control"></a>若要使用未繫結的 DataGridView 控制項  
  
1.  建立衍生自類別<xref:System.Windows.Forms.Form>而且包含下列變數宣告和`Main`方法。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#01](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#01](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#02](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#02](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#02)]  
  
2.  實作`SetupLayout`表單的類別定義，若要設定表單的版面配置中的方法。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#20)]  
  
3.  建立`SetupDataGridView`方法來設定<xref:System.Windows.Forms.DataGridView>資料行和屬性。  
  
     這個方法會先加入<xref:System.Windows.Forms.DataGridView>控制項加入表單<xref:System.Windows.Forms.Control.Controls%2A>集合。 接下來，使用設定要顯示的資料行數目<xref:System.Windows.Forms.DataGridView.ColumnCount%2A>屬性。 資料行標頭的預設樣式設定藉由設定<xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A>， <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>，和<xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A>屬性<xref:System.Windows.Forms.DataGridViewCellStyle>傳回<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>屬性。  
  
     設定版面配置和外觀屬性，，然後指派資料行名稱。 當這個方法會結束時，<xref:System.Windows.Forms.DataGridView>控制項已經準備要被填入。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#30)]  
  
4.  建立`PopulateDataGridView`方法，以將資料列加入<xref:System.Windows.Forms.DataGridView>控制項。  
  
     每個資料列都代表一首歌曲和其相關的資訊。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#40](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#40)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#40](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#40)]  
  
5.  使用就地公用程式方法，您可以附加事件處理常式。  
  
     將處理**新增**和**刪除**按鈕<xref:System.Windows.Forms.Control.Click>事件、 將表單的<xref:System.Windows.Forms.Form.Load>事件，而<xref:System.Windows.Forms.DataGridView>控制項的<xref:System.Windows.Forms.DataGridView.CellFormatting>事件。  
  
     當**新增**按鈕的<xref:System.Windows.Forms.Control.Click>引發事件時，新的空白資料列加入至<xref:System.Windows.Forms.DataGridView>。  
  
     當**刪除**按鈕的<xref:System.Windows.Forms.Control.Click>就會引發事件，會刪除選取的資料列，除非它是新的記錄，可讓使用者的資料列加入新的資料列。 這個資料列永遠是中的最後一個資料列<xref:System.Windows.Forms.DataGridView>控制項。  
  
     當表單的<xref:System.Windows.Forms.Form.Load>引發事件時， `SetupLayout`， `SetupDataGridView`，和`PopulateDataGridView`呼叫公用程式方法。  
  
     當<xref:System.Windows.Forms.DataGridView.CellFormatting>引發事件時，每個儲存格`Date`除非儲存格的值無法剖析，將會格式化為完整日期的資料行。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#10)]  
  
## <a name="testing-the-application"></a>測試應用程式  
 您現在可以測試表單，以確定其如預期般運作。  
  
#### <a name="to-test-the-form"></a>若要測試表單  
  
-   按 F5 執行應用程式。  
  
     您會看到<xref:System.Windows.Forms.DataGridView>顯示中所列的歌曲控制項`PopulateDataGridView`。 您可以加入新資料列與**加入資料列** 按鈕，而且您可以刪除選取的資料列與**刪除資料列** 按鈕。 未繫結<xref:System.Windows.Forms.DataGridView>控制項的資料存放區，以及其資料是獨立於任何外部來源，例如<xref:System.Data.DataSet>或陣列。  
  
## <a name="next-steps"></a>後續步驟  
 此應用程式可讓您基本的了解<xref:System.Windows.Forms.DataGridView>控制項的功能。 您可以自訂的外觀和行為<xref:System.Windows.Forms.DataGridView>數種方式控制：  
  
-   變更框線和標題的樣式。 如需詳細資訊，請參閱[如何： 變更 Windows Form DataGridView 控制項中的格線樣式和框線](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md)。  
  
-   啟用或限制使用者輸入到<xref:System.Windows.Forms.DataGridView>控制項。 如需詳細資訊，請參閱[如何： 防止資料列新增和刪除 Windows Form DataGridView 控制項中的](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md)，和[如何： 使 Windows Form DataGridView 控制項中的資料行唯讀](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)。  
  
-   檢查使用者輸入的資料庫相關的錯誤。 如需詳細資訊，請參閱[逐步解說： 處理所發生的錯誤在 Windows Form DataGridView 控制項中的資料輸入期間](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md)。  
  
-   處理非常大型的資料集使用的虛擬模式。 如需詳細資訊，請參閱[逐步解說： 在 Windows Form DataGridView 控制項中實作虛擬模式](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)。  
  
-   自訂儲存格的外觀。 如需詳細資訊，請參閱[How to： 自訂 Windows Form DataGridView 控制項中的儲存格外觀](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)和[How to： 設定預設儲存格樣式的 Windows Form DataGridView 控制項](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.DataGridView>  
 [在 Windows Forms DataGridView 控制項中顯示資料](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [操作說明：建立未繫結的 Windows Forms DataGridView 控制項](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView 控制項的資料顯示模式](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)

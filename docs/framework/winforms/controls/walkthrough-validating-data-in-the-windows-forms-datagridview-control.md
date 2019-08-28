---
title: 逐步解說：驗證 Windows Forms DataGridView 控制項的資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- validating data [Windows Forms], Windows Forms
- data [Windows Forms], validation
- DataGridView control [Windows Forms], data validation
- data grids [Windows Forms], validating data
- data validation [Windows Forms], Windows Forms
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: a4f1d015-2969-430c-8ea2-b612d179c290
ms.openlocfilehash: 89569feb0cb741f56d09f4e58154b4eecb5a89d4
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046385"
---
# <a name="walkthrough-validating-data-in-the-windows-forms-datagridview-control"></a>逐步解說：驗證 Windows Forms DataGridView 控制項的資料

當您向使用者顯示資料輸入功能時, 您經常需要驗證輸入表單中的資料。 <xref:System.Windows.Forms.DataGridView>類別提供便利的方式來執行驗證, 再將資料認可到資料存放區。 您可以藉由處理<xref:System.Windows.Forms.DataGridView.CellValidating>事件來驗證資料, <xref:System.Windows.Forms.DataGridView>當目前的儲存格變更時, 就會引發。

在此逐步解說中, 您將從 Northwind `Customers`範例資料庫中的資料表抓取資料列, 並將<xref:System.Windows.Forms.DataGridView>其顯示在控制項中。 當使用者編輯資料`CompanyName`行中的儲存格並嘗試離開儲存格時<xref:System.Windows.Forms.DataGridView.CellValidating> , 事件處理常式會檢查新的公司名稱字串以確定它不是空的; 如果新的值是空字串, 則<xref:System.Windows.Forms.DataGridView>會防止使用者的資料指標離開儲存格, 直到輸入非空白字串為止。

若要將此主題中的程式碼複製為單一清單，請參閱[如何：驗證 Windows Forms DataGridView 控制項](how-to-validate-data-in-the-windows-forms-datagridview-control.md)中的資料。

## <a name="prerequisites"></a>必要條件

若要完成這個逐步解說，您將需要：

- 具有 Northwind SQL Server 範例資料庫之伺服器的存取權。

## <a name="creating-the-form"></a>建立表單

#### <a name="to-validate-data-entered-in-a-datagridview"></a>驗證 DataGridView 中輸入的資料

1. 建立衍生自<xref:System.Windows.Forms.Form>的類別, 並<xref:System.Windows.Forms.DataGridView>包含控制項和<xref:System.Windows.Forms.BindingSource>元件。

    下列程式碼範例提供基本的`Main`初始化, 並包含方法。

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#01)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#01)]
    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#02)]

2. 在表單的類別定義中執行方法, 以處理連接至資料庫的詳細資料。

    這個程式碼範例會`GetData`使用方法來傳回已<xref:System.Data.DataTable>填入的物件。 請務必將`connectionString`變數設定為適用于您資料庫的值。

    > [!IMPORTANT]
    > 在連接字串內儲存機密資訊 (例如密碼) 會影響應用程式的安全性。 使用 Windows 驗證 (也稱為整合式安全性) 是控制資料庫存取的更安全方式。 如需詳細資訊，請參閱[保護連線資訊](../../data/adonet/protecting-connection-information.md)。

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#30)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#30)]

3. 為表單的<xref:System.Windows.Forms.Form.Load>事件執行處理常式, 以<xref:System.Windows.Forms.DataGridView>初始化和<xref:System.Windows.Forms.BindingSource> , 並設定資料系結。

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#10)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#10)]

4. 執行<xref:System.Windows.Forms.DataGridView> 控制項和<xref:System.Windows.Forms.DataGridView.CellEndEdit>事件的處理常式。 <xref:System.Windows.Forms.DataGridView.CellValidating>

    事件處理常式可讓您判斷資料`CompanyName`行中資料格的值是否為空白。 <xref:System.Windows.Forms.DataGridView.CellValidating> 如果資料格值驗證失敗, 請將<xref:System.ComponentModel.CancelEventArgs.Cancel%2A> <xref:System.Windows.Forms.DataGridViewCellValidatingEventArgs?displayProperty=nameWithType>類別的屬性設定為`true`。 這會導致<xref:System.Windows.Forms.DataGridView>控制項防止游標離開儲存格。 將資料<xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A>列上的屬性設定為說明性字串。 這會顯示錯誤圖示, 其中包含含有錯誤文字的工具提示。 在事件處理常式中, 將<xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A>資料列上的屬性設定為空字串。 <xref:System.Windows.Forms.DataGridView.CellEndEdit> 只有<xref:System.Windows.Forms.DataGridView.CellEndEdit>當儲存格離開編輯模式時, 才會發生此事件, 如果驗證失敗, 就無法執行此動作。

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#20)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#20)]

## <a name="testing-the-application"></a>測試應用程式

您現在可以測試表單, 以確定它會如預期般運作。

#### <a name="to-test-the-form"></a>測試表單

- 編譯並執行應用程式。

  您會看到<xref:System.Windows.Forms.DataGridView>填入`Customers`資料表中的資料。 當您按兩下資料`CompanyName`行中的資料格時, 您可以編輯此值。 如果您刪除所有字元, 並按 TAB 鍵來結束資料格, 則<xref:System.Windows.Forms.DataGridView>會導致無法結束。 當您將非空白字串輸入儲存格時, <xref:System.Windows.Forms.DataGridView>控制項可讓您結束儲存格。

## <a name="next-steps"></a>後續步驟

此應用程式可讓您對<xref:System.Windows.Forms.DataGridView>控制項的功能有基本瞭解。 您可以透過數種方式自訂<xref:System.Windows.Forms.DataGridView>控制項的外觀和行為:

- 變更框線和標題樣式。 如需詳細資訊，請參閱[如何：變更 Windows Forms DataGridView 控制項](change-the-border-and-gridline-styles-in-the-datagrid.md)中的框線和格線樣式。

- 啟用或限制控制項的<xref:System.Windows.Forms.DataGridView>使用者輸入。 如需詳細資訊，請參閱[如何：防止在 Windows Forms DataGridView 控制項](prevent-row-addition-and-deletion-datagridview.md)中新增和刪除資料列, 以及[如何:將 Windows Forms DataGridView 控制項](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)中的資料行設為唯讀。

- 檢查使用者輸入中是否有資料庫相關錯誤。 如需詳細資訊，請參閱[逐步解說：處理 Windows Forms DataGridView 控制項](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)中的資料輸入期間所發生的錯誤。

- 使用虛擬模式處理非常大型的資料集。 如需詳細資訊，請參閱[逐步解說：在 Windows Forms DataGridView 控制項](implementing-virtual-mode-wf-datagridview-control.md)中執行虛擬模式。

- 自訂儲存格的外觀。 如需詳細資訊，請參閱[如何：在 Windows Forms DataGridView 控制項](customize-the-appearance-of-cells-in-the-datagrid.md)中自訂儲存格的外觀, 以及[如何:設定 Windows Forms DataGridView 控制項](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)中的字型和色彩樣式。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Windows Forms DataGridView 控制項中的資料輸入](data-entry-in-the-windows-forms-datagridview-control.md)
- [如何：驗證 Windows Forms DataGridView 控制項中的資料](how-to-validate-data-in-the-windows-forms-datagridview-control.md)
- [逐步解說：處理 Windows Forms DataGridView 控制項中的資料輸入期間所發生的錯誤](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [保護連線資訊](../../data/adonet/protecting-connection-information.md)

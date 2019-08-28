---
title: 逐步解說：處理 Windows Forms DataGridView 控制項在資料輸入期間發生的錯誤
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- error handling [Windows Forms], dataGridView control
- data grids [Windows Forms], error handling
- DataGridView control [Windows Forms], error handling
- data entry [Windows Forms], error handling
- error handling [Windows Forms], data entry
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 30a68b85-d3af-4946-83c1-1e2d010d0511
ms.openlocfilehash: cee6fe3b049378fa7bbe2585a3607049eaf231bc
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046083"
---
# <a name="walkthrough-handling-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a>逐步解說：處理 Windows Forms DataGridView 控制項在資料輸入期間發生的錯誤

從基礎資料存放區處理錯誤是資料輸入應用程式的必要功能。 Windows Forms <xref:System.Windows.Forms.DataGridView>控制項藉由公開事件來簡化這<xref:System.Windows.Forms.DataGridView.DataError>項工作, 這會在資料存放區偵測到條件約束違規或中斷的商務規則時引發。

在此逐步解說中, 您將從 Northwind `Customers`範例資料庫中的資料表抓取資料列, 並將<xref:System.Windows.Forms.DataGridView>其顯示在控制項中。 在新的`CustomerID`資料列或已編輯的現有資料列中偵測到重複的<xref:System.Windows.Forms.DataGridView.DataError>值時, 將會發生此事件, 這會<xref:System.Windows.Forms.MessageBox>藉由顯示描述例外狀況的來處理。

若要將此主題中的程式碼複製為單一清單，請參閱[如何：處理 Windows Forms DataGridView 控制項](handle-errors-that-occur-during-data-entry-in-the-datagrid.md)中的資料輸入期間所發生的錯誤。

## <a name="prerequisites"></a>必要條件

若要完成這個逐步解說，您將需要：

- 具有 Northwind SQL Server 範例資料庫之伺服器的存取權。

## <a name="creating-the-form"></a>建立表單

#### <a name="to-handle-data-entry-errors-in-the-datagridview-control"></a>處理 DataGridView 控制項中的資料輸入錯誤

1. 建立衍生自<xref:System.Windows.Forms.Form>的類別, 並<xref:System.Windows.Forms.DataGridView>包含控制項和<xref:System.Windows.Forms.BindingSource>元件。

    下列程式碼範例提供基本的`Main`初始化, 並包含方法。

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#01)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#01)]
    [!code-csharp[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#02)]

2. 在表單的類別定義中執行方法, 以處理連接至資料庫的詳細資料。

    這個程式碼範例會`GetData`使用方法來傳回已<xref:System.Data.DataTable>填入的物件。 請務必將`connectionString`變數設定為適用于您資料庫的值。

    > [!IMPORTANT]
    > 在連接字串內儲存機密資訊 (例如密碼) 會影響應用程式的安全性。 使用 Windows 驗證 (也稱為整合式安全性) 是控制資料庫存取的更安全方式。 如需詳細資訊，請參閱[保護連線資訊](../../data/adonet/protecting-connection-information.md)。

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#30)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#30)]

3. 為表單的<xref:System.Windows.Forms.Form.Load>事件執行處理常式, 以<xref:System.Windows.Forms.DataGridView>初始化和<xref:System.Windows.Forms.BindingSource> , 並設定資料系結。

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#10)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#10)]

4. <xref:System.Windows.Forms.DataGridView.DataError> 處理<xref:System.Windows.Forms.DataGridView>上的事件。

    如果錯誤的內容是認可作業, 則會在中<xref:System.Windows.Forms.MessageBox>顯示錯誤。

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#20)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#20)]

## <a name="testing-the-application"></a>測試應用程式

您現在可以測試表單, 以確定它會如預期般運作。

#### <a name="to-test-the-form"></a>測試表單

- 按 F5 執行應用程式。

  您會看到<xref:System.Windows.Forms.DataGridView>已填入 [Customers] 資料表之資料的控制項。 如果您為輸入重複的`CustomerID`值, 並認可編輯, 資料格值將會自動還原, 而您會<xref:System.Windows.Forms.MessageBox>看到顯示資料項目錯誤的。

## <a name="next-steps"></a>後續步驟

此應用程式可讓您對<xref:System.Windows.Forms.DataGridView>控制項的功能有基本瞭解。 您可以透過數種方式自訂<xref:System.Windows.Forms.DataGridView>控制項的外觀和行為:

- 變更框線和標題樣式。 如需詳細資訊，請參閱[如何：變更 Windows Forms DataGridView 控制項](change-the-border-and-gridline-styles-in-the-datagrid.md)中的框線和格線樣式。

- 啟用或限制控制項的<xref:System.Windows.Forms.DataGridView>使用者輸入。 如需詳細資訊，請參閱[如何：防止在 Windows Forms DataGridView 控制項](prevent-row-addition-and-deletion-datagridview.md)中新增和刪除資料列, 以及[如何:將 Windows Forms DataGridView 控制項](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)中的資料行設為唯讀。

- 驗證控制項的<xref:System.Windows.Forms.DataGridView>使用者輸入。 如需詳細資訊，請參閱[逐步解說：驗證 Windows Forms DataGridView 控制項](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)中的資料。

- 使用虛擬模式處理非常大型的資料集。 如需詳細資訊，請參閱[逐步解說：在 Windows Forms DataGridView 控制項](implementing-virtual-mode-wf-datagridview-control.md)中執行虛擬模式。

- 自訂儲存格的外觀。 如需詳細資訊，請參閱[如何：在 Windows Forms DataGridView 控制項](customize-the-appearance-of-cells-in-the-datagrid.md)中自訂儲存格的外觀, 以及[如何:設定 Windows Forms DataGridView 控制項](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)的預設儲存格樣式。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Windows Forms DataGridView 控制項中的資料輸入](data-entry-in-the-windows-forms-datagridview-control.md)
- [如何：處理 Windows Forms DataGridView 控制項中的資料輸入期間所發生的錯誤](handle-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [逐步解說：驗證 Windows Forms DataGridView 控制項中的資料](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [保護連線資訊](../../data/adonet/protecting-connection-information.md)

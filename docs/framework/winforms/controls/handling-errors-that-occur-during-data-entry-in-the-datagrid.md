---
title: 逐步解說：處理 Windows Form DataGridView 控制項中的資料輸入期間所發生的錯誤
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
ms.openlocfilehash: a8eb4584060924684eacc99d46b88408451f1c82
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708232"
---
# <a name="walkthrough-handling-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a>逐步解說：處理 Windows Form DataGridView 控制項中的資料輸入期間所發生的錯誤
處理錯誤，從基礎資料存放區是輸入資料的應用程式的必要的功能。 Windows Forms<xref:System.Windows.Forms.DataGridView>控制項提供了簡單的藉由公開<xref:System.Windows.Forms.DataGridView.DataError>條件約束違規或損毀的商務規則，會偵測到資料存放區時所引發的事件。  
  
 在本逐步解說中，您將擷取的資料列`Customers`Northwind 範例資料庫中的表格，以及它們顯示在<xref:System.Windows.Forms.DataGridView>控制項。 當重複`CustomerID`中新的資料列或編輯現有的資料列，偵測到的值<xref:System.Windows.Forms.DataGridView.DataError>事件就會發生，這會顯示處理<xref:System.Windows.Forms.MessageBox>，描述例外狀況。  
  
 若要將此主題中的程式碼複製為單一清單，請參閱[如何：在 Windows 中的資料輸入期間所發生處理錯誤 Form DataGridView 控制項](handle-errors-that-occur-during-data-entry-in-the-datagrid.md)。  
  
## <a name="prerequisites"></a>必要條件  
 若要完成這個逐步解說，您將需要：  
  
-   存取權可 Northwind SQL Server 範例資料庫的伺服器。  
  
## <a name="creating-the-form"></a>建立表單  
  
#### <a name="to-handle-data-entry-errors-in-the-datagridview-control"></a>若要處理 DataGridView 控制項中的資料輸入錯誤  
  
1.  建立衍生自類別<xref:System.Windows.Forms.Form>且包含<xref:System.Windows.Forms.DataGridView>控制項和<xref:System.Windows.Forms.BindingSource>元件。  
  
     下列程式碼範例提供基本的初始化，而且包含`Main`方法。  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#02)]  
  
2.  在您的表單類別定義處理資料庫連接的詳細資料中實作的方法。  
  
     此程式碼範例會使用`GetData`方法會傳回填入<xref:System.Data.DataTable>物件。 請確定您設定`connectionString`變數的值，適用於您的資料庫。  
  
    > [!IMPORTANT]
    >  在連接字串內儲存機密資訊 (例如密碼) 會影響應用程式的安全性。 使用 Windows 驗證 (也稱為整合式安全性) 是控制資料庫存取的更安全方式。 如需詳細資訊，請參閱[保護連線資訊](../../data/adonet/protecting-connection-information.md)。  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#30)]  
  
3.  實作您的表單的處理常式<xref:System.Windows.Forms.Form.Load>初始化的事件<xref:System.Windows.Forms.DataGridView>和<xref:System.Windows.Forms.BindingSource>和設定資料繫結。  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#10)]  
  
4.  處理<xref:System.Windows.Forms.DataGridView.DataError>上的事件<xref:System.Windows.Forms.DataGridView>。  
  
     如果此錯誤的內容是 「 認可 」 作業，顯示中的錯誤<xref:System.Windows.Forms.MessageBox>。  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#20)]  
  
## <a name="testing-the-application"></a>測試應用程式  
 您現在可以測試表單，以確定它如預期般運作。  
  
#### <a name="to-test-the-form"></a>若要測試表單  
  
-   按 F5 執行應用程式。  
  
     您會看到<xref:System.Windows.Forms.DataGridView>控制項填入 Customers 資料表中的資料。 如果您輸入的值重複`CustomerID`和認可編輯、 儲存格的值將會自動還原，您會看到<xref:System.Windows.Forms.MessageBox>顯示資料的項目時發生錯誤。  
  
## <a name="next-steps"></a>後續步驟  
 此應用程式可讓您的基本了解<xref:System.Windows.Forms.DataGridView>控制項的功能。 您可以自訂外觀和行為<xref:System.Windows.Forms.DataGridView>控制項以數種方式：  
  
-   變更框線和標題的樣式。 如需詳細資訊，請參閱[如何：變更框線和格線樣式，在 Windows Form DataGridView 控制項](change-the-border-and-gridline-styles-in-the-datagrid.md)。  
  
-   啟用或限制使用者的輸入<xref:System.Windows.Forms.DataGridView>控制項。 如需詳細資訊，請參閱[如何：防止資料列中新增和刪除 Windows Form DataGridView 控制項](prevent-row-addition-and-deletion-datagridview.md)，和[How to:資料行設為唯讀模式中的 Windows Form DataGridView 控制項](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)。  
  
-   驗證使用者輸入，<xref:System.Windows.Forms.DataGridView>控制項。 如需詳細資訊，請參閱[逐步解說：驗證資料，在 Windows Form DataGridView 控制項](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)。  
  
-   處理非常大型的資料集使用的虛擬模式。 如需詳細資訊，請參閱[逐步解說：實作虛擬模式中的 Windows Form DataGridView 控制項](implementing-virtual-mode-wf-datagridview-control.md)。  
  
-   自訂儲存格的外觀。 如需詳細資訊，請參閱[如何：自訂 Windows Form DataGridView 控制項中的儲存格的外觀](customize-the-appearance-of-cells-in-the-datagrid.md)和[How to:設定 Windows Form DataGridView 控制項的預設儲存格樣式](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Windows Forms DataGridView 控制項中的資料輸入](data-entry-in-the-windows-forms-datagridview-control.md)
- [如何：處理 Windows Form DataGridView 控制項中的資料輸入期間所發生的錯誤](handle-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [逐步解說：驗證 Windows Form DataGridView 控制項中的資料](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [保護連線資訊](../../data/adonet/protecting-connection-information.md)

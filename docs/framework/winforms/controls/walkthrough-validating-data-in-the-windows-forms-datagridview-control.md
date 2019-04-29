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
ms.openlocfilehash: a4bf0850b28b7101ba76f1c1fedc6633eccb81a1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61759852"
---
# <a name="walkthrough-validating-data-in-the-windows-forms-datagridview-control"></a>逐步解說：驗證 Windows Forms DataGridView 控制項的資料
當您向使用者顯示的項目資料功能時，您經常必須驗證您的表單中輸入的資料。 <xref:System.Windows.Forms.DataGridView>類別提供便利的方式，資料就會認可到資料存放區之前先執行驗證。 您可以藉由處理驗證資料<xref:System.Windows.Forms.DataGridView.CellValidating>事件，會引發<xref:System.Windows.Forms.DataGridView>目前儲存格的變更時。  
  
 在本逐步解說中，您將擷取的資料列`Customers`Northwind 範例資料庫中的表格，以及它們顯示在<xref:System.Windows.Forms.DataGridView>控制項。 當使用者編輯中的資料格`CompanyName`資料行，嘗試將資料格，保留<xref:System.Windows.Forms.DataGridView.CellValidating>事件處理常式會檢查新的公司名稱字串，以確定它是不是空的; 如果新的值為空字串，<xref:System.Windows.Forms.DataGridView>會造成使用者的資料指標從輸入非空白字串之前，請將儲存格。  
  
 若要將此主題中的程式碼複製為單一清單，請參閱[如何：驗證 Windows Form DataGridView 控制項中的資料](how-to-validate-data-in-the-windows-forms-datagridview-control.md)。  
  
## <a name="prerequisites"></a>必要條件  
 若要完成這個逐步解說，您將需要：  
  
- 存取權可 Northwind SQL Server 範例資料庫的伺服器。  
  
## <a name="creating-the-form"></a>建立表單  
  
#### <a name="to-validate-data-entered-in-a-datagridview"></a>若要驗證在 DataGridView 中輸入的資料  
  
1. 建立衍生自類別<xref:System.Windows.Forms.Form>且包含<xref:System.Windows.Forms.DataGridView>控制項和<xref:System.Windows.Forms.BindingSource>元件。  
  
     下列程式碼範例提供基本的初始化，而且包含`Main`方法。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#02)]  
  
2. 在您的表單類別定義處理資料庫連接的詳細資料中實作的方法。  
  
     此程式碼範例會使用`GetData`方法會傳回填入<xref:System.Data.DataTable>物件。 請確定您設定`connectionString`變數的值，適用於您的資料庫。  
  
    > [!IMPORTANT]
    >  在連接字串內儲存機密資訊 (例如密碼) 會影響應用程式的安全性。 使用 Windows 驗證，也稱為整合式安全性，是更安全的方式，來控制資料庫的存取權。 如需詳細資訊，請參閱[保護連線資訊](../../data/adonet/protecting-connection-information.md)。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#30)]  
  
3. 實作您的表單的處理常式<xref:System.Windows.Forms.Form.Load>初始化的事件<xref:System.Windows.Forms.DataGridView>和<xref:System.Windows.Forms.BindingSource>和設定資料繫結。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#10)]  
  
4. 實作的處理常式<xref:System.Windows.Forms.DataGridView>控制項的<xref:System.Windows.Forms.DataGridView.CellValidating>和<xref:System.Windows.Forms.DataGridView.CellEndEdit>事件。  
  
     <xref:System.Windows.Forms.DataGridView.CellValidating>事件處理常式是在您判定是否在儲存格的值`CompanyName`是空的資料行。 如果驗證失敗的儲存格的值，設定<xref:System.ComponentModel.CancelEventArgs.Cancel%2A>的屬性<xref:System.Windows.Forms.DataGridViewCellValidatingEventArgs?displayProperty=nameWithType>類別`true`。 這會導致<xref:System.Windows.Forms.DataGridView>以防止資料指標離開儲存格的控制項。 設定<xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A>說明的字串資料列上的屬性。 這會顯示錯誤圖示與包含的錯誤文字的工具提示。 在 <xref:System.Windows.Forms.DataGridView.CellEndEdit>事件處理常式中，設定<xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A>為空字串的資料列上的屬性。 <xref:System.Windows.Forms.DataGridView.CellEndEdit>只儲存格結束編輯模式，它無法這麼做，如果它驗證失敗時，事件就會發生。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#20)]  
  
## <a name="testing-the-application"></a>測試應用程式  
 您現在可以測試表單，以確定它如預期般運作。  
  
#### <a name="to-test-the-form"></a>若要測試表單  
  
- 編譯並執行應用程式。  
  
     您會看到<xref:System.Windows.Forms.DataGridView>填滿資料從`Customers`資料表。 當您按兩下中的資料格`CompanyName` 欄中，您可以編輯的值。 如果您刪除所有字元，然後按 TAB 鍵以結束資料格，<xref:System.Windows.Forms.DataGridView>防止您離開。 當您在儲存格中輸入非空白字串<xref:System.Windows.Forms.DataGridView>控制項可讓您結束資料格。  
  
## <a name="next-steps"></a>後續步驟  
 此應用程式可讓您的基本了解<xref:System.Windows.Forms.DataGridView>控制項的功能。 您可以自訂外觀和行為<xref:System.Windows.Forms.DataGridView>控制項以數種方式：  
  
- 變更框線和標題的樣式。 如需詳細資訊，請參閱[如何：變更框線和格線樣式，在 Windows Form DataGridView 控制項](change-the-border-and-gridline-styles-in-the-datagrid.md)。  
  
- 啟用或限制使用者的輸入<xref:System.Windows.Forms.DataGridView>控制項。 如需詳細資訊，請參閱[如何：防止資料列中新增和刪除 Windows Form DataGridView 控制項](prevent-row-addition-and-deletion-datagridview.md)，和[How to:資料行設為唯讀模式中的 Windows Form DataGridView 控制項](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)。  
  
- 檢查使用者輸入的資料庫相關的錯誤。 如需詳細資訊，請參閱[逐步解說：處理在 Windows 中的資料輸入期間所發生的錯誤 Form DataGridView 控制項](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)。  
  
- 處理非常大型的資料集使用的虛擬模式。 如需詳細資訊，請參閱[逐步解說：實作虛擬模式中的 Windows Form DataGridView 控制項](implementing-virtual-mode-wf-datagridview-control.md)。  
  
- 自訂儲存格的外觀。 如需詳細資訊，請參閱[如何：自訂 Windows Form DataGridView 控制項中的儲存格的外觀](customize-the-appearance-of-cells-in-the-datagrid.md)和[How to:設定 Windows Form DataGridView 控制項中的 字型和色彩樣式](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Windows Forms DataGridView 控制項中的資料輸入](data-entry-in-the-windows-forms-datagridview-control.md)
- [如何：驗證 Windows Form DataGridView 控制項中的資料](how-to-validate-data-in-the-windows-forms-datagridview-control.md)
- [逐步解說：處理 Windows Form DataGridView 控制項中的資料輸入期間所發生的錯誤](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [保護連線資訊](../../data/adonet/protecting-connection-information.md)

---
title: 逐步解說：驗證 Windows Form DataGridView 控制項中的資料
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
ms.openlocfilehash: 8ad8caef5db13b1f917a6c27da523d3ded915d84
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540959"
---
# <a name="walkthrough-validating-data-in-the-windows-forms-datagridview-control"></a>逐步解說：驗證 Windows Form DataGridView 控制項中的資料
當您向使用者顯示資料輸入功能時，您經常需要驗證您的表單中輸入的資料。 <xref:System.Windows.Forms.DataGridView>類別會提供便利的方式，資料就會認可至資料存放區之前，先執行驗證。 您可以藉由處理驗證資料<xref:System.Windows.Forms.DataGridView.CellValidating>事件，就會引發<xref:System.Windows.Forms.DataGridView>目前儲存格的變更時。  
  
 在本逐步解說中，您將會擷取資料列從`Customers`Northwind 範例資料庫中資料表，並顯示在<xref:System.Windows.Forms.DataGridView>控制項。 當使用者編輯中的資料格`CompanyName`資料行，並嘗試將資料格，保留<xref:System.Windows.Forms.DataGridView.CellValidating>事件處理常式會檢查新的公司名稱字串，以確定它是不是空的; 如果新的值為空字串，<xref:System.Windows.Forms.DataGridView>會防止使用者的資料指標從輸入非空白字串之前離開儲存格。  
  
 若要為單一列出本主題中複製的程式碼，請參閱[How to： 驗證 Windows Form DataGridView 控制項中的資料](../../../../docs/framework/winforms/controls/how-to-validate-data-in-the-windows-forms-datagridview-control.md)。  
  
## <a name="prerequisites"></a>必要條件  
 若要完成這個逐步解說，您將需要：  
  
-   Northwind SQL Server 範例資料庫的伺服器存取。  
  
## <a name="creating-the-form"></a>建立表單  
  
#### <a name="to-validate-data-entered-in-a-datagridview"></a>若要驗證在 DataGridView 中輸入的資料  
  
1.  建立衍生自類別<xref:System.Windows.Forms.Form>且包含<xref:System.Windows.Forms.DataGridView>控制項和<xref:System.Windows.Forms.BindingSource>元件。  
  
     下列程式碼範例提供基本的初始化，並包含`Main`方法。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#01](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#01](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#02](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#02](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#02)]  
  
2.  在您的表單類別定義處理資料庫連接的詳細資料中實作的方法。  
  
     這個程式碼範例會使用`GetData`方法會傳回已填入<xref:System.Data.DataTable>物件。 請確定您設定`connectionString`變數的值，適用於您的資料庫。  
  
    > [!IMPORTANT]
    >  在連接字串內儲存機密資訊 (例如密碼) 會影響應用程式的安全性。 使用 Windows 驗證，也稱為整合式安全性，是更安全的方式來控制資料庫的存取權。 如需詳細資訊，請參閱[保護連線資訊](../../../../docs/framework/data/adonet/protecting-connection-information.md)。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#30)]  
  
3.  實作您的表單的處理常式<xref:System.Windows.Forms.Form.Load>初始化的事件<xref:System.Windows.Forms.DataGridView>和<xref:System.Windows.Forms.BindingSource>並設定資料繫結。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#10)]  
  
4.  實作的處理常式<xref:System.Windows.Forms.DataGridView>控制項的<xref:System.Windows.Forms.DataGridView.CellValidating>和<xref:System.Windows.Forms.DataGridView.CellEndEdit>事件。  
  
     <xref:System.Windows.Forms.DataGridView.CellValidating>事件處理常式是在您判定是否中的資料格的值`CompanyName`是空的資料行。 如果驗證失敗的儲存格的值，設定<xref:System.ComponentModel.CancelEventArgs.Cancel%2A>屬性<xref:System.Windows.Forms.DataGridViewCellValidatingEventArgs?displayProperty=nameWithType>類別`true`。 這會導致<xref:System.Windows.Forms.DataGridView>以防止資料指標離開儲存格的控制項。 設定<xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A>要說明的字串之資料列上的屬性。 這會顯示錯誤圖示，工具提示的範例，其中包含錯誤文字。 在<xref:System.Windows.Forms.DataGridView.CellEndEdit>事件處理常式中，設定<xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A>為空字串的資料列上的屬性。 <xref:System.Windows.Forms.DataGridView.CellEndEdit>只儲存格離開編輯模式，如果它驗證失敗，它無法執行時，事件就會發生。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#20)]  
  
## <a name="testing-the-application"></a>測試應用程式  
 您現在可以測試表單，以確定其如預期般運作。  
  
#### <a name="to-test-the-form"></a>若要測試表單  
  
-   編譯並執行應用程式。  
  
     您會看到<xref:System.Windows.Forms.DataGridView>填滿資料從`Customers`資料表。 當您按兩下儲存格中`CompanyName`資料行中，您可以編輯的值。 如果您刪除的所有字元，然後按 TAB 鍵以結束資料格，<xref:System.Windows.Forms.DataGridView>防止您離開。 當您在儲存格中輸入非空白字串<xref:System.Windows.Forms.DataGridView>控制項可讓您結束資料格。  
  
## <a name="next-steps"></a>後續步驟  
 此應用程式可讓您基本的了解<xref:System.Windows.Forms.DataGridView>控制項的功能。 您可以自訂的外觀和行為<xref:System.Windows.Forms.DataGridView>數種方式控制：  
  
-   變更框線和標題的樣式。 如需詳細資訊，請參閱[如何： 變更 Windows Form DataGridView 控制項中的格線樣式和框線](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md)。  
  
-   啟用或限制使用者輸入到<xref:System.Windows.Forms.DataGridView>控制項。 如需詳細資訊，請參閱[如何： 防止資料列新增和刪除 Windows Form DataGridView 控制項中的](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md)，和[如何： 使 Windows Form DataGridView 控制項中的資料行唯讀](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)。  
  
-   檢查使用者輸入的資料庫相關的錯誤。 如需詳細資訊，請參閱[逐步解說： 處理所發生的錯誤在 Windows Form DataGridView 控制項中的資料輸入期間](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md)。  
  
-   處理非常大型的資料集使用的虛擬模式。 如需詳細資訊，請參閱[逐步解說： 在 Windows Form DataGridView 控制項中實作虛擬模式](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)。  
  
-   自訂儲存格的外觀。 如需詳細資訊，請參閱[How to： 自訂 Windows Form DataGridView 控制項中的儲存格外觀](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)和[How to： 設定字型和色彩樣式，在 Windows Form DataGridView 控制項中](../../../../docs/framework/winforms/controls/how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [Windows Forms DataGridView 控制項中的資料輸入](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 [操作說明：驗證 Windows Forms DataGridView 控制項中的資料](../../../../docs/framework/winforms/controls/how-to-validate-data-in-the-windows-forms-datagridview-control.md)  
 [逐步解說：處理 Windows Forms DataGridView 控制項中的資料輸入期間所發生的錯誤](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md)  
 [保護連線資訊](../../../../docs/framework/data/adonet/protecting-connection-information.md)

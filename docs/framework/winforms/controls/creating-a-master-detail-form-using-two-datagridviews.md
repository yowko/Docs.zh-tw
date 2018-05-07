---
title: 逐步解說： 建立主從式表單使用兩個 Windows Form DataGridView 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], master/detail form
- parent-child tables [Windows Forms], displaying on Windows Forms
- master-details lists [Windows Forms], displaying on Windows Forms
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: c5fa29e8-47f7-4691-829b-0e697a691f36
ms.openlocfilehash: 38f7c6197fb3ee79119e41ab9620bc3aa2b21900
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-creating-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a>逐步解說：使用兩個 Windows Form DataGridView 控制項建立主要/詳細表單
其中一個最常見的案例使用<xref:System.Windows.Forms.DataGridView>控制項是*主從式*表單，其中會顯示兩個資料庫資料表之間的父子式關聯性。 主要資料表中選取資料列會讓使用對應的子資料來更新詳細資料資料表。  
  
 實作主要/詳細表單很容易使用之間的互動<xref:System.Windows.Forms.DataGridView>控制項和<xref:System.Windows.Forms.BindingSource>元件。 在本逐步解說，您將建立使用兩個表單<xref:System.Windows.Forms.DataGridView>控制項及兩個<xref:System.Windows.Forms.BindingSource>元件。 表單會顯示兩個相關 Northwind SQL Server 範例資料庫中的資料表：`Customers`和`Orders`。 當您完成時，您必須在 master 資料庫中會顯示所有客戶表單<xref:System.Windows.Forms.DataGridView>和詳細資料中所選客戶的訂單<xref:System.Windows.Forms.DataGridView>。  
  
 若要為單一列出本主題中複製的程式碼，請參閱[How to： 建立主從式表單使用兩個 Windows Form DataGridView 控制項](../../../../docs/framework/winforms/controls/create-a-master-detail-form-using-two-datagridviews.md)。  
  
## <a name="prerequisites"></a>必要條件  
 若要完成這個逐步解說，您將需要：  
  
-   Northwind SQL Server 範例資料庫的伺服器存取。  
  
## <a name="creating-the-form"></a>建立表單  
  
#### <a name="to-create-a-masterdetail-form"></a>若要建立主要/詳細表單  
  
1.  建立衍生自類別<xref:System.Windows.Forms.Form>和包含兩個<xref:System.Windows.Forms.DataGridView>控制項及兩個<xref:System.Windows.Forms.BindingSource>元件。 下列程式碼提供基本的形式初始化，而且包含`Main`方法。 如果您使用 Visual Studio 設計工具來建立表單時，您可以使用設計工具產生的程式碼，而不是這個程式碼，但請務必使用變數宣告中所顯示的名稱。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#01](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#01](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#02](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#02](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#02)]  
  
2.  在您的表單類別定義處理資料庫連接的詳細資料中實作的方法。 這個範例會使用`GetData`方法填入<xref:System.Data.DataSet>物件時，會新增<xref:System.Data.DataRelation>資料集，以及繫結物件<xref:System.Windows.Forms.BindingSource>元件。 請務必將 `connectionString` 變數設定為適用於您資料庫的值。  
  
    > [!IMPORTANT]
    >  在連接字串內儲存機密資訊 (例如密碼) 會影響應用程式的安全性。 使用 Windows 驗證 (也稱為整合式安全性) 是控制資料庫存取的更安全方式。 如需詳細資訊，請參閱[保護連線資訊](../../../../docs/framework/data/adonet/protecting-connection-information.md)。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#20)]  
  
3.  實作您的表單的處理常式<xref:System.Windows.Forms.Form.Load>繫結的事件<xref:System.Windows.Forms.DataGridView>控制項<xref:System.Windows.Forms.BindingSource>元件並呼叫`GetData`方法。 下列範例包含調整大小的程式碼<xref:System.Windows.Forms.DataGridView>欄位至最適大小所顯示的資料。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#10)]  
  
## <a name="testing-the-application"></a>測試應用程式  
 您現在可以測試表單，以確定其如預期般運作。  
  
#### <a name="to-test-the-form"></a>若要測試表單  
  
-   編譯並執行應用程式。  
  
     您會看到兩個<xref:System.Windows.Forms.DataGridView>控制項，在彼此上方。 在最上層是 northwind 客戶`Customers`資料表，並在下方是`Orders`對應至選取的客戶。 當您選取不同的資料列的上方<xref:System.Windows.Forms.DataGridView>，較低的內容<xref:System.Windows.Forms.DataGridView>據此變更。  
  
## <a name="next-steps"></a>後續步驟  
 此應用程式可讓您基本的了解<xref:System.Windows.Forms.DataGridView>控制項的功能。 您可以自訂的外觀和行為<xref:System.Windows.Forms.DataGridView>數種方式控制：  
  
-   變更框線和標題的樣式。 如需詳細資訊，請參閱[如何： 變更 Windows Form DataGridView 控制項中的格線樣式和框線](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md)。  
  
-   啟用或限制使用者輸入到<xref:System.Windows.Forms.DataGridView>控制項。 如需詳細資訊，請參閱[如何： 防止資料列新增和刪除 Windows Form DataGridView 控制項中的](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md)，和[如何： 使 Windows Form DataGridView 控制項中的資料行唯讀](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)。  
  
-   驗證使用者輸入，<xref:System.Windows.Forms.DataGridView>控制項。 如需詳細資訊，請參閱[逐步解說： 驗證 Windows Form DataGridView 控制項中的資料](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)。  
  
-   處理非常大型的資料集使用的虛擬模式。 如需詳細資訊，請參閱[逐步解說： 在 Windows Form DataGridView 控制項中實作虛擬模式](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)。  
  
-   自訂儲存格的外觀。 如需詳細資訊，請參閱[How to： 自訂 Windows Form DataGridView 控制項中的儲存格外觀](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)和[How to： 設定預設儲存格樣式的 Windows Form DataGridView 控制項](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [在 Windows Forms DataGridView 控制項中顯示資料](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [操作說明：使用兩個 Windows Forms DataGridView 控制項建立主從式表單](../../../../docs/framework/winforms/controls/create-a-master-detail-form-using-two-datagridviews.md)  
 [保護連線資訊](../../../../docs/framework/data/adonet/protecting-connection-information.md)

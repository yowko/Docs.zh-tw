---
title: 將資料網格控制綁定到資料來源
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- datasets [Windows Forms], binding to DataGrid control
- data binding [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], data binding
- bound controls [Windows Forms], DataGrid control
- Windows Forms controls, data binding
- bound controls [Windows Forms]
- data-bound controls [Windows Forms], DataGrid
ms.assetid: 128cdb07-dfd3-4d60-9d6a-902847667c36
ms.openlocfilehash: 42514c6a0ab9cf912a32b13675a069976632ece5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182248"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source"></a>如何：將 Windows Form DataGrid 控制項繫結至資料來源
> [!NOTE]
> <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。 如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 Windows 表單<xref:System.Windows.Forms.DataGrid>控制項專為顯示資料來源中的資訊而設計。 通過調用<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>方法在運行時繫結控制項。 儘管可以顯示來自各種資料來源的資料，但最典型的來源是資料集和資料檢視。  
  
### <a name="to-data-bind-the-datagrid-control-programmatically"></a>以程式設計方式綁定 DataGrid 控制項  
  
1. 編寫代碼以填充資料集。  
  
     如果資料來源是基於資料集表的資料集或資料檢視，請向表單添加代碼以填充資料集。  
  
     您使用的確切代碼取決於資料集獲取資料的位置。 如果資料集直接從資料庫填充，則通常調用資料配接器`Fill`的方法，如以下示例所示，該方法填充名為 的`DsCategories1`資料集：  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
     如果資料集是從 XML Web 服務填充的，則通常在代碼中創建服務的實例，然後調用其方法之一來返回資料集。 然後，將 XML Web 服務中的資料集合併到本地資料集中。 下面的示例演示如何創建名為`CategoriesService`的 XML Web 服務的實例， 調用其`GetCategories`方法，並將生成的資料集合併到稱為`DsCategories1`：  
  
    ```vb  
    Dim ws As New MyProject.localhost.CategoriesService()  
    ws.Credentials = System.Net.CredentialCache.DefaultCredentials  
    DsCategories1.Merge(ws.GetCategories())  
    ```  
  
    ```csharp  
    MyProject.localhost.CategoriesService ws = new MyProject.localhost.CategoriesService();  
    ws.Credentials = System.Net.CredentialCache.DefaultCredentials;  
    DsCategories1.Merge(ws.GetCategories());  
    ```  
  
    ```cpp  
    MyProject::localhost::CategoriesService^ ws =
       new MyProject::localhost::CategoriesService();  
    ws->Credentials = System::Net::CredentialCache::DefaultCredentials;  
    dsCategories1->Merge(ws->GetCategories());  
    ```  
  
2. 調用控制項<xref:System.Windows.Forms.DataGrid><xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>的方法，傳遞資料來源和資料成員。 如果不需要顯式傳遞資料成員，則傳遞一個空字串。  
  
    > [!NOTE]
    > 如果首次綁定網格，則可以設置控制項和<xref:System.Windows.Forms.DataGrid.DataSource%2A><xref:System.Windows.Forms.DataGrid.DataMember%2A>屬性。 但是，在設置這些屬性後，無法重置這些屬性。 因此，建議您始終使用 方法<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>。  
  
     下面的示例演示如何在稱為`DsCustomers1`： 的資料集中以程式設計方式綁定到客戶表：  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "Customers");  
    ```  
  
     如果"客戶"表是資料集中的唯一表，則可以以這種方式綁定網格：  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "");  
    ```  
  
3. （可選）將適當的表樣式和列樣式添加到網格中。 如果沒有表樣式，您將看到該表，但格式最小且所有列可見。  
  
## <a name="see-also"></a>另請參閱

- [DataGrid 控制項概觀](datagrid-control-overview-windows-forms.md)
- [如何：將資料表和資料行加入至 Windows Form DataGrid 控制項](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [DataGrid 控制項](datagrid-control-windows-forms.md)
- [Windows Form 資料繫結](../windows-forms-data-binding.md)

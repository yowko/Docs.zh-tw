---
title: HOW TO：將 Windows Forms DataGrid 控制項繫結至資料來源
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
ms.openlocfilehash: bac24c2dd622ea780408e902d08708ac09561044
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922731"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source"></a>HOW TO：將 Windows Forms DataGrid 控制項繫結至資料來源
> [!NOTE]
> <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。 如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 Windows Forms <xref:System.Windows.Forms.DataGrid>控制項是特別設計來顯示資料來源中的資訊。 您可以藉由呼叫<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>方法, 在執行時間系結控制項。 雖然您可以顯示來自各種資料來源的資料, 但最常見的來源是資料集和資料檢視。  
  
### <a name="to-data-bind-the-datagrid-control-programmatically"></a>若要以程式設計方式將 DataGrid 控制項進行資料系結  
  
1. 撰寫程式碼以填滿資料集。  
  
     如果資料來源是資料集或根據資料集資料表的資料檢視, 請將程式碼加入至表單, 以填滿資料集。  
  
     您所使用的確切程式碼取決於資料集取得資料的位置。 如果直接從資料庫填入資料集, 您通常會呼叫`Fill`資料介面卡的方法, 如下列範例所示, 它會填入名`DsCategories1`為的資料集:  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
     如果要從 XML Web Service 填入資料集, 您通常會在程式碼中建立服務的實例, 然後呼叫其中一個方法來傳回資料集。 接著, 您可以將資料集從 XML Web Service 合併到本機資料集。 下列範例會示範如何建立名`CategoriesService`為的 XML Web Service 實例、呼叫其`GetCategories`方法, 並將產生的資料集合併到名`DsCategories1`為的本機資料集:  
  
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
  
2. 呼叫控制項的<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>方法, 將資料來源和資料成員傳遞給它。 <xref:System.Windows.Forms.DataGrid> 如果您不需要明確地傳遞資料成員, 請傳遞空字串。  
  
    > [!NOTE]
    > 如果您是第一次系結方格, 則可以設定控制項的<xref:System.Windows.Forms.DataGrid.DataSource%2A>和<xref:System.Windows.Forms.DataGrid.DataMember%2A>屬性。 不過, 一旦設定這些屬性之後, 就無法重設這些屬性。 因此, 建議您一律使用<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>方法。  
  
     下列範例會示範如何以程式設計方式系結至資料集內的 Customers `DsCustomers1`資料表, 名為:  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "Customers");  
    ```  
  
     如果 [Customers] 資料表是資料集中的唯一資料表, 您也可以透過這種方式來系結格線:  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "");  
    ```  
  
3. 選擇性在方格中加入適當的資料表樣式和資料行樣式。 如果沒有資料表樣式, 您會看到資料表, 但最小的格式和所有資料行都是可見的。  
  
## <a name="see-also"></a>另請參閱

- [DataGrid 控制項概觀](datagrid-control-overview-windows-forms.md)
- [如何：將資料表和資料行加入至 Windows Forms DataGrid 控制項](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [DataGrid 控制項](datagrid-control-windows-forms.md)
- [Windows Forms 資料繫結](../windows-forms-data-binding.md)

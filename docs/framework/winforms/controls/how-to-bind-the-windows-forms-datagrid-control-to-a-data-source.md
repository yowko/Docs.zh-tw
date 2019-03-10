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
ms.openlocfilehash: 5da74abb107bc93bff496a35ecfc7a1233e5a76d
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57702954"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source"></a>HOW TO：將 Windows Forms DataGrid 控制項繫結至資料來源
> [!NOTE]
>  
  <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。 如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 Windows Form<xref:System.Windows.Forms.DataGrid>控制項專為顯示從資料來源的資訊。 您將控制項繫結在執行階段藉由呼叫<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>方法。 雖然您可以顯示來自各種資料來源的資料，但最常見的來源是資料集] 和 [資料檢視。  
  
### <a name="to-data-bind-the-datagrid-control-programmatically"></a>若要進行資料繫結 DataGrid 控制項中以程式設計的方式  
  
1.  撰寫程式碼以填入資料集。  
  
     如果資料來源之資料集或資料集資料表為基礎的資料檢視，請將程式碼加入表單，以填入資料集。  
  
     您使用的確切程式碼取決於資料集從何處取得資料。 如果直接從資料庫填入資料集，您通常會呼叫`Fill`方法的資料配接器，如下列的範例中，於其中填入資料集所示`DsCategories1`:  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
     如果從 XML Web service 所填滿資料集，您通常會在您的程式碼中建立的服務執行個體，並接著呼叫其中一個方法來傳回資料集。 您接著會合併到您本機的資料集的 XML Web service 中的資料集。 下列範例示範如何建立 XML Web service 呼叫的執行個體`CategoriesService`，呼叫其`GetCategories`方法，並合併至本機資料集產生的資料集稱為`DsCategories1`:  
  
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
  
2.  呼叫<xref:System.Windows.Forms.DataGrid>控制項的<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>方法，並傳遞它的資料來源和資料成員。 如果您不需要明確地傳遞的資料成員，則傳遞空字串。  
  
    > [!NOTE]
    >  如果您第一次將方格繫結，您可以設定控制項的<xref:System.Windows.Forms.DataGrid.DataSource%2A>和<xref:System.Windows.Forms.DataGrid.DataMember%2A>屬性。 不過，您無法重設這些屬性一旦有尚未設定。 因此，建議您一律使用<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>方法。  
  
     下列範例示範如何可以以程式設計方式繫結至 Customers 資料表中資料集`DsCustomers1`:  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "Customers");  
    ```  
  
     如果 「 客戶 」 資料表中資料集的唯一資料表，您無法或者方格繫結這種方式：  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "");  
    ```  
  
3.  （選擇性）將適當的資料表樣式和資料行樣式加入方格中。 如果不有任何資料表樣式，您會看到資料表，但搭配最少的格式與可見的所有資料行。  
  
## <a name="see-also"></a>另請參閱
- [DataGrid 控制項概觀](datagrid-control-overview-windows-forms.md)
- [如何：將資料表和資料行新增至 Windows Forms DataGrid 控制項](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [DataGrid 控制項](datagrid-control-windows-forms.md)
- [Windows Forms 資料繫結](../windows-forms-data-binding.md)

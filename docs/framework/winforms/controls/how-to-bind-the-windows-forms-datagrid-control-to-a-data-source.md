---
title: "如何：將 Windows Form DataGrid 控制項繫結至資料來源"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 185c094b32f0de7a1a26da144601961d92a625b9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source"></a>如何：將 Windows Form DataGrid 控制項繫結至資料來源
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。 如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 Windows Form<xref:System.Windows.Forms.DataGrid>控制項特別設計來顯示資料來源的資訊。 您將控制項繫結在執行階段藉由呼叫<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>方法。 雖然您可以顯示來自各種資料來源的資料，但最常見的來源是資料集和資料的檢視。  
  
### <a name="to-data-bind-the-datagrid-control-programmatically"></a>若要以程式設計方式的資料繫結 DataGrid 控制項  
  
1.  撰寫程式碼以填入資料集。  
  
     如果資料來源之資料集或資料集資料表為基礎的資料檢視，請將程式碼加入至表單，以填入資料集。  
  
     您使用的實際程式碼會取決於資料集從何處取得資料。 如果直接從資料庫填入資料集，您通常會呼叫`Fill`資料配接器，如下列範例會填入資料集呼叫的方法`DsCategories1`:  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
     如果要從 XML Web service 填滿資料集，您通常會在程式碼中建立的服務執行個體，，然後呼叫其中一個方法來傳回資料集。 您接著會合併到您本機的資料集的 XML Web service 中的資料集。 下列範例示範如何建立 XML Web service 呼叫的執行個體`CategoriesService`，呼叫其`GetCategories`方法，以及合併至本機的資料集產生的資料集稱為`DsCategories1`:  
  
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
  
2.  呼叫<xref:System.Windows.Forms.DataGrid>控制項的<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>方法，將其傳遞資料來源和資料成員。 如果您不需要明確傳遞的資料成員，請傳送空字串。  
  
    > [!NOTE]
    >  如果您要繫結方格中，第一次，您可以設定控制項的<xref:System.Windows.Forms.DataGrid.DataSource%2A>和<xref:System.Windows.Forms.DataGrid.DataMember%2A>屬性。 不過，您無法重設這些屬性一旦已設定。 因此，建議您一定要使用<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>方法。  
  
     下列範例示範如何您以程式設計方式連接到資料集呼叫中的 Customers 資料表`DsCustomers1`:  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "Customers");  
    ```  
  
     如果 「 客戶 」 資料表中資料集的資料表，您無法或者方格繫結這種方式：  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "");  
    ```  
  
3.  （選擇性）將適當的資料表樣式和資料行樣式加入至方格中。 如果有任何資料表樣式，您會看到資料表，但最少的格式和可見的所有資料行。  
  
## <a name="see-also"></a>另請參閱  
 [DataGrid 控制項概觀](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)  
 [操作說明：將資料表和資料行新增至 Windows Forms DataGrid 控制項](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)  
 [DataGrid 控制項](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [Windows Forms 資料繫結](../../../../docs/framework/winforms/windows-forms-data-binding.md)

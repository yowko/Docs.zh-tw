---
title: "如何：將 Windows Form DataGrid 控制項繫結至資料來源 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "繫結控制項"
  - "繫結控制項, DataGrid 控制項"
  - "資料繫結, DataGrid 控制項"
  - "資料繫結控制項, DataGrid"
  - "DataGrid 控制項 [Windows Form], 資料繫結"
  - "資料集 [Windows Form], 繫結至 DataGrid 控制項"
  - "Windows Form 控制項, 資料繫結"
ms.assetid: 128cdb07-dfd3-4d60-9d6a-902847667c36
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 如何：將 Windows Form DataGrid 控制項繫結至資料來源
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。  如需詳細資訊，請參閱 [Windows Form DataGridView 和 DataGrid 控制項之間的差異](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 Windows Form <xref:System.Windows.Forms.DataGrid> 控制項是特別設計來顯示資料來源的資訊。  您可以在執行階段呼叫 <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> 方法來繫結此控制項。  雖然您可顯示來自各種不同資料來源的資料，但最常見的來源是資料集和資料檢視。  
  
### 若要以程式設計的方式資料繫結 DataGrid 控制項  
  
1.  撰寫程式碼以填滿資料集。  
  
     如果資料來源是資料集或以資料集資料表為基礎的資料檢視，請將程式碼加入表單來填滿資料集。  
  
     您實際上使用的程式碼要視資料集從何處取得資料而定。  如果資料集是直接從資料庫填入，您通常會呼叫資料配接器 \(Adapter\) 的 `Fill`  方法，如下列範例所示，其中會填入名為 `DsCategories1` 的資料集：  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
     如果資料集是從 XML Web Service 填滿，您通常會在程式碼中建立服務的執行個體，接著呼叫其中一個方法來傳回資料集。  接著您會將 XML Web Service 的資料集合併至您的本機資料集。  下列範例示範如何建立名為 `CategoriesService` 的 XML Web Service 執行個體，呼叫其 `GetCategories` 方法，接著將產生的資料集合併至名為 `DsCategories1` 的本機資料集：  
  
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
  
2.  呼叫 <xref:System.Windows.Forms.DataGrid> 控制項的 <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> 方法，將資料來源和資料成員傳遞給它。  如果您不需要明確傳遞資料成員，請傳遞空字串。  
  
    > [!NOTE]
    >  如果是第一次繫結方格，可以設定控制項的 <xref:System.Windows.Forms.DataGrid.DataSource%2A> 和 <xref:System.Windows.Forms.DataGrid.DataMember%2A> 屬性。  不過一旦設定這些屬性之後，您就無法重設它們。  因此，建議您永遠使用 <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> 方法。  
  
     下列範例顯示如何以程式設計的方式繫結至名為 `DsCustomers1` 的資料集中的 Customers 資料表：  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers")  
  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers");  
  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "Customers");  
    ```  
  
     如果 Customers 資料表是該資料集中唯一的資料表，您也可以用這種方式來繫結方格：  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "")  
  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "");  
  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "");  
    ```  
  
3.  \(選擇性\) 將適當的資料表樣式和資料行樣式加入至資料格。  如果沒有資料表樣式，您將看到資料表，但只能看到最少的格式和所有的資料行。  
  
## 請參閱  
 [DataGrid 控制項概觀](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)   
 [如何：將資料表和資料行加入至 Windows Form DataGrid 控制項](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)   
 [DataGrid 控制項](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)   
 [Windows Form 資料繫結](../../../../docs/framework/winforms/windows-forms-data-binding.md)
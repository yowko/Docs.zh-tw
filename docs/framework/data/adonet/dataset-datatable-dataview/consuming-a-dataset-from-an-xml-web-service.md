---
title: "從 XML Web Service 使用 DataSet | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9edd6b71-0fa5-4649-ae1d-ac1c12541019
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 從 XML Web Service 使用 DataSet
<xref:System.Data.DataSet> 採用中斷連接設計為架構，而部分原因是為了使網際網路的資料傳輸更方便。  **DataSet** 具有「可序列化」的特性，可以指定為輸入至或輸出自 XML Web Service 的內容，不需要另外撰寫程式碼，即可將 **DataSet** 內容透過資料流從 XML Web Service 傳遞給用戶端，並從用戶端傳回。  **DataSet** 使用 DiffGram 格式隱含轉換為 XML 資料流後在網路上傳送，然後在接收端上，從 XML 資料流重新建構為 **DataSet**。  您可以採用這種簡單靈活的方式，以 XML Web Service 來傳輸和傳回關聯式資料。  如需 DiffGram 格式的詳細資訊，請參閱 [DiffGram](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)。  
  
 下列範例顯示如何建立 XML Web Service 和用戶端，以使用 **DataSet** 來傳輸關聯式資料 \(包括修改資料\)，以及將任何更新解析回原始資料來源。  
  
> [!NOTE]
>  建立 XML Web Service 時，建議您務必考量涉及的安全性課題。  如需設定 XML Web Service 安全性的詳細資訊，請參閱 [Securing XML Web Services Created Using ASP.NET](http://msdn.microsoft.com/zh-tw/354b2ab1-2782-4542-b32a-dc560178b90c)。  
  
### 若要建立傳回和使用 DataSet 的 XML Web Service  
  
1.  建立 XML Web Service  
  
     範例中建立的 XML Web Service 可傳回資料 \(在本案例中為來自 **Northwind** 資料庫的客戶清單\)，並收到 **DataSet** 的更新資料，由 XML Web Service 解析回原始資料來源。  
  
     XML Web Service 公開兩種方法：**GetCustomers** \(用來傳回客戶清單\) 和 **UpdateCustomers** \(用來將更新解析到資料來源\)。  XML Web Service 以 DataSetSample.asmx 為檔案名稱儲存在 Web 伺服器內。  下列程式碼列出 DataSetSample.asmx 的內容大綱。  
  
    ```vb  
    <% @ WebService Language = "vb" Class = "Sample" %>  
    Imports System  
    Imports System.Data  
    Imports System.Data.SqlClient  
    Imports System.Web.Services  
  
    <WebService(Namespace:="http://microsoft.com/webservices/")> _  
    Public Class Sample  
  
    Public connection As SqlConnection = New SqlConnection("Data Source=(local);Integrated Security=SSPI;Initial Catalog=Northwind")  
  
      <WebMethod( Description := "Returns Northwind Customers", EnableSession := False )> _  
      Public Function GetCustomers() As DataSet  
        Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
          "SELECT CustomerID, CompanyName FROM Customers", connection)  
  
        Dim custDS As DataSet = New DataSet()  
        adapter.MissingSchemaAction = MissingSchemaAction.AddWithKey  
        adapter.Fill(custDS, "Customers")  
  
        Return custDS  
      End Function  
  
      <WebMethod( Description := "Updates Northwind Customers", EnableSession := False )> _  
      Public Function UpdateCustomers(custDS As DataSet) As DataSet  
        Dim adapter As SqlDataAdapter = New SqlDataAdapter()  
  
        adapter.InsertCommand = New SqlCommand( _  
          "INSERT INTO Customers (CustomerID, CompanyName) " & _  
          "Values(@CustomerID, @CompanyName)", connection)  
        adapter.InsertCommand.Parameters.Add( _  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
        adapter.InsertCommand.Parameters.Add( _  
          "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
  
        adapter.UpdateCommand = New SqlCommand( _  
          "UPDATE Customers Set CustomerID = @CustomerID, " & _  
          "CompanyName = @CompanyName WHERE CustomerID = " & _  
          @OldCustomerID", connection)  
        adapter.UpdateCommand.Parameters.Add( _  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
        adapter.UpdateCommand.Parameters.Add( _  
          "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
  
        Dim parameter As SqlParameter = _  
          adapter.UpdateCommand.Parameters.Add( _  
          "@OldCustomerID", SqlDbType.NChar, 5, "CustomerID")  
        parameter.SourceVersion = DataRowVersion.Original  
  
        adapter.DeleteCommand = New SqlCommand( _  
          "DELETE FROM Customers WHERE CustomerID = @CustomerID", _  
          connection)  
        parameter = adapter.DeleteCommand.Parameters.Add( _  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
        parameter.SourceVersion = DataRowVersion.Original  
  
        adapter.Update(custDS, "Customers")  
  
        Return custDS  
      End Function  
    End Class  
  
    ```  
  
    ```csharp  
    <% @ WebService Language = "C#" Class = "Sample" %>  
    using System;  
    using System.Data;  
    using System.Data.SqlClient;  
    using System.Web.Services;  
  
    [WebService(Namespace="http://microsoft.com/webservices/")]  
    public class Sample  
    {  
      public SqlConnection connection = new SqlConnection("Data Source=(local);Integrated Security=SSPI;Initial Catalog=Northwind");  
  
      [WebMethod( Description = "Returns Northwind Customers", EnableSession = false )]  
      public DataSet GetCustomers()  
      {  
        SqlDataAdapter adapter = new SqlDataAdapter(  
          "SELECT CustomerID, CompanyName FROM Customers", connection);  
  
        DataSet custDS = new DataSet();  
        adapter.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
        adapter.Fill(custDS, "Customers");  
  
        return custDS;  
      }  
  
      [WebMethod( Description = "Updates Northwind Customers",  
        EnableSession = false )]  
      public DataSet UpdateCustomers(DataSet custDS)  
      {  
        SqlDataAdapter adapter = new SqlDataAdapter();  
  
        adapter.InsertCommand = new SqlCommand(  
          "INSERT INTO Customers (CustomerID, CompanyName) " +  
          "Values(@CustomerID, @CompanyName)", connection);  
        adapter.InsertCommand.Parameters.Add(  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
        adapter.InsertCommand.Parameters.Add(  
          "@CompanyName", SqlDbType.NChar, 15, "CompanyName");  
  
        adapter.UpdateCommand = new SqlCommand(  
          "UPDATE Customers Set CustomerID = @CustomerID, " +  
          "CompanyName = @CompanyName WHERE CustomerID = " +  
          "@OldCustomerID", connection);  
        adapter.UpdateCommand.Parameters.Add(  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
        adapter.UpdateCommand.Parameters.Add(  
          "@CompanyName", SqlDbType.NChar, 15, "CompanyName");  
        SqlParameter parameter = adapter.UpdateCommand.Parameters.Add(  
          "@OldCustomerID", SqlDbType.NChar, 5, "CustomerID");  
        parameter.SourceVersion = DataRowVersion.Original;  
  
        adapter.DeleteCommand = new SqlCommand(  
        "DELETE FROM Customers WHERE CustomerID = @CustomerID",  
         connection);  
        parameter = adapter.DeleteCommand.Parameters.Add(  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
        parameter.SourceVersion = DataRowVersion.Original;  
  
        adapter.Update(custDS, "Customers");  
  
        return custDS;  
      }  
    }  
    ```  
  
     典型案例中，撰寫 **UpdateCustomers** 方法來攔截開放式同步存取違規。  為了簡化起見，這個範例並不包括這項步驟。  如需開放式並行存取的詳細資訊，請參閱[開放式並行存取](../../../../../docs/framework/data/adonet/optimistic-concurrency.md)。  
  
2.  建立 XML Web Service Proxy  
  
     XML Web Service 的用戶端需要 SOAP Proxy，才能使用公開方法。  您可以命令 Visual Studio 產生這個 Proxy。  藉由從 Visual Studio 中設定現有 Web 服務的 Web 參考，會透明地執行這個步驟所說明的所有行為。  如果要自行建立 Proxy 類別，請繼續這些說明。  然而在大多數情況下，使用 Visual Studio 來建立用戶端應用程式的 Proxy 類別已足以因應。  
  
     Proxy 可使用 Web 服務描述語言工具建立。  例如，若 XML Web Service 於 URL \(http:\/\/myserver\/data\/DataSetSample.asmx\) 處公開，請發出類似下列的命令來建立命名空間為 **WebData.DSSample** 的 Visual Basic .NET Proxy，並將其儲存在 sample.vb 檔案中。  
  
    ```  
    wsdl /l:VB /out:sample.vb http://myserver/data/DataSetSample.asmx /n:WebData.DSSample  
    ```  
  
     若要在 sample.cs 檔案中建立 C\# Proxy，請發出下列命令。  
  
    ```  
    wsdl /l:CS /out:sample.cs http://myserver/data/DataSetSample.asmx /n:WebData.DSSample  
    ```  
  
     接下來 Proxy 可編譯為程式庫，並匯入 XML Web Service 用戶端。  若要將儲存在 sample.vb 內的 Visual Basic .NET Proxy 程式碼編譯為 sample.dll，請發出下列命令。  
  
    ```  
    vbc /t:library /out:sample.dll sample.vb /r:System.dll /r:System.Web.Services.dll /r:System.Data.dll /r:System.Xml.dll  
    ```  
  
     若要將儲存在 sample.cs 的 C\# Proxy 程式碼編譯為 sample.dll，請發出下列命令。  
  
    ```  
    csc /t:library /out:sample.dll sample.cs /r:System.dll /r:System.Web.Services.dll /r:System.Data.dll /r:System.Xml.dll  
    ```  
  
3.  建立 XML Web Service 用戶端。  
  
     若要讓 Visual Studio 產生 Web 服務 Proxy 類別，則只要建立用戶端專案，並在 \[方案總管\] 視窗中，於專案上按一下滑鼠右鍵，按 \[**加入 Web 參考**\]，並從可用的 Web 服務清單中選取 Web 服務 \(如果目前的方案或電腦上沒有可用的 Web 服務，則可能需要提供 Web 服務端點的位址\)。如果您自行建立 XML Web Service Proxy \(如上述步驟所述\)，您可以將它匯入您的用戶端程式碼，並使用 XML Web Service 方法。  下列程式碼範例為匯入 Proxy 程式庫，呼叫 **GetCustomers** 以取得客戶清單，接著加入新客戶並傳回具有 **UpdateCustomers** 更新的 **DataSet**。  
  
     請注意，範例中將 **DataSet.GetChanges** 傳回的 **DataSet** 傳遞給 **UpdateCustomers**，因為僅有修改過的資料列才需要傳遞給 **UpdateCustomers**。  **UpdateCustomers** 傳回已解析的 **DataSet**，接下來將它**合併**到現有的 **DataSet**，納入解析過的變更和任何來自更新的資料列錯誤資訊。  下列程式碼假設已使用 Visual Studio 來建立 Web 參考，而且已在 \[**加入 Web 參考**\] 對話方塊中，將 Web 參考重新命名為 DsSample。  
  
    ```vb  
    Imports System  
    Imports System.Data  
  
    Public Class Client  
  
      Public Shared Sub Main()  
        Dim proxySample As New DsSample.Sample ()  ' Proxy object.  
        Dim customersDataSet As DataSet = proxySample.GetCustomers()  
        Dim customersTable As DataTable = _  
          customersDataSet.Tables("Customers")  
  
        Dim rowAs DataRow = customersTable.NewRow()  
        row("CustomerID") = "ABCDE"  
        row("CompanyName") = "New Company Name"  
        customersTable.Rows.Add(row)  
  
        Dim updateDataSet As DataSet = _  
          proxySample.UpdateCustomers(customersDataSet.GetChanges())  
  
        customersDataSet.Merge(updateDataSet)  
        customersDataSet.AcceptChanges()  
      End Sub  
    End Class  
  
    ```  
  
    ```csharp  
    using System;  
    using System.Data;  
  
    public class Client  
    {  
      public static void Main()  
      {  
        Sample proxySample = new DsSample.Sample();  // Proxy object.  
        DataSet customersDataSet = proxySample.GetCustomers();  
        DataTable customersTable = customersDataSet.Tables["Customers"];  
  
        DataRow row = customersTable.NewRow();  
        row["CustomerID"] = "ABCDE";  
        row["CompanyName"] = "New Company Name";  
        customersTable.Rows.Add(row);  
  
        DataSet updateDataSet = new DataSet();  
  
        updateDataSet =   
          proxySample.UpdateCustomers(customersDataSet.GetChanges());  
  
        customersDataSet.Merge(updateDataSet);  
        customersDataSet.AcceptChanges();  
      }  
    }  
    ```  
  
     如果您決定自行建立 Proxy 類別，則必須採取下列其餘步驟。  若要編譯範例，請提供已建立的 Proxy 程式庫 \(sample.dll\) 和相關的 .NET 程式庫。  若要編譯儲存於 client.vb 檔案的 Visual Basic .NET 版本範例，請發出下列命令。  
  
    ```  
    vbc client.vb /r:sample.dll /r:System.dll /r:System.Data.dll /r:System.Xml.dll /r:System.Web.Services.dll  
    ```  
  
     若要編譯儲存於 client.cs 檔案的 C\# 版本範例，請發出下列命令。  
  
    ```  
    csc client.cs /r:sample.dll /r:System.dll /r:System.Data.dll /r:System.Xml.dll /r:System.Web.Services.dll  
    ```  
  
## 請參閱  
 [ADO.NET](../../../../../docs/framework/data/adonet/index.md)   
 [DataSet、DataTable 及 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)   
 [從 DataAdapter 填入資料集](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)   
 [以 DataAdapter 更新資料來源](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)   
 [DataAdapter 參數](../../../../../docs/framework/data/adonet/dataadapter-parameters.md)   
 [Web Services Description Language Tool \(Wsdl.exe\)](http://msdn.microsoft.com/zh-tw/b9210348-8bc2-4367-8c91-d1a04b403e88)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
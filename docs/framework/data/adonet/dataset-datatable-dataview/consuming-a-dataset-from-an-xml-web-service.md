---
title: 從 XML Web Service 使用資料集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9edd6b71-0fa5-4649-ae1d-ac1c12541019
ms.openlocfilehash: 7b284a8f085ab7e93651c829ac16e47fb63a8b51
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034472"
---
# <a name="consuming-a-dataset-from-an-xml-web-service"></a>從 XML Web Service 使用資料集
<xref:System.Data.DataSet> 採用中斷連接設計為架構，而部分原因是為了使網際網路的資料傳輸更方便。 **資料集**，它可以指定為輸入或輸出自 XML Web service，而不需要任何額外的程式碼所需資料流的內容是 「 序列化 」 **DataSet**從 XML Web service用戶端和上一步。 **資料集**是隱含地轉換成使用 DiffGram 格式的 XML 資料流傳送透過網路，然後重新建構 XML 資料流，做為從**DataSet**在接收端。 您可以採用這種簡單靈活的方式，以 XML Web Service 來傳輸和傳回關聯式資料。 如需有關 DiffGram 格式的詳細資訊，請參閱[DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)。  
  
 下列範例示範如何建立 XML Web service 和使用的用戶端**資料集**傳輸關聯式資料 （包括已修改的資料） 和任何更新解析回原始資料來源。  
  
> [!NOTE]
>  建立 XML Web Service 時，建議您務必考量涉及的安全性課題。 如需有關保護 XML Web service，請參閱[保護 Web 服務使用 ASP.NET 建立 XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100))。  
  
### <a name="to-create-an-xml-web-service-that-returns-and-consumes-a-dataset"></a>若要建立傳回和使用 DataSet 的 XML Web Service  
  
1. 建立 XML Web Service  
  
     在此範例中，XML Web service 會建立傳回資料，在此情況下從客戶的清單**Northwind**資料庫，然後接收**資料集**與更新資料，其中 XML Web service解析回原始的資料來源。  
  
     XML Web Service 公開兩種方法：**GetCustomers**，以傳回客戶清單，並**UpdateCustomers**，來將更新解析回資料來源。 XML Web Service 以 DataSetSample.asmx 為檔案名稱儲存在 Web 伺服器內。 下列程式碼列出 DataSetSample.asmx 的內容大綱。  
  
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
  
     在典型的案例中， **UpdateCustomers**會寫入方法，來攔截開放式同步存取違規。 為了簡化起見，這個範例並不包括這項步驟。 如需有關開放式並行存取的詳細資訊，請參閱[開放式並行存取](../../../../../docs/framework/data/adonet/optimistic-concurrency.md)。  
  
2. 建立 XML Web Service Proxy  
  
     XML Web Service 的用戶端需要 SOAP Proxy，才能使用公開方法。 您可以命令 Visual Studio 產生這個 Proxy。 藉由從 Visual Studio 中設定現有 Web 服務的 Web 參考，會透明地執行這個步驟所說明的所有行為。 如果要自行建立 Proxy 類別，請繼續這些說明。 然而在大多數情況下，使用 Visual Studio 來建立用戶端應用程式的 Proxy 類別已足以因應。  
  
     Proxy 可使用 Web 服務描述語言工具建立。 例如，如果 XML Web service 會在 URL 中公開`http://myserver/data/DataSetSample.asmx`，發出如下所示的命令來建立 Visual Basic.NET proxy 的命名空間**WebData.DSSample**並將它儲存在 sample.vb 檔案中。  
  
    ```console
    wsdl /l:VB -out:sample.vb http://myserver/data/DataSetSample.asmx /n:WebData.DSSample  
    ```  
  
     若要在 sample.cs 檔案中建立 C# Proxy，請發出下列命令。  
  
    ```console
    wsdl -l:CS -out:sample.cs http://myserver/data/DataSetSample.asmx -n:WebData.DSSample  
    ```  
  
     接下來 Proxy 可編譯為程式庫，並匯入 XML Web Service 用戶端。 若要將儲存在 sample.vb 內的 Visual Basic .NET Proxy 程式碼編譯為 sample.dll，請發出下列命令。  
  
    ```console  
    vbc -t:library -out:sample.dll sample.vb -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
     若要將儲存在 sample.cs 的 C# Proxy 程式碼編譯為 sample.dll，請發出下列命令。  
  
    ```console
    csc -t:library -out:sample.dll sample.cs -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
3. 建立 XML Web Service 用戶端。  
  
     如果您想要有 Visual Studio 為您產生 Web 服務 proxy 類別，只要建立用戶端專案中，在 方案總管 視窗中，以滑鼠右鍵按一下專案，請按一下**加入 Web 參考**，然後選取 從 Web 服務清單中可用的 Web 服務 （這可能需要提供 Web 服務端點的位址，如果 Web 服務無法使用目前的方案，或目前的電腦上）。如果您自行建立 XML Web Service Proxy (如上述步驟所述)，您可以將它匯入您的用戶端程式碼，並使用 XML Web Service 方法。 下列範例程式碼會匯入 proxy 程式庫，呼叫**GetCustomers**若要取得一份客戶，將新的客戶，然後傳回**資料集**更新**UpdateCustomers**.  
  
     請注意，範例會傳遞**資料集**由**DataSet.GetChanges**來**UpdateCustomers**傳遞至要修改的資料列因為**UpdateCustomers**。 **UpdateCustomers**傳回已解析**資料集**，然後您便可以**合併**至現有**資料集**來納入已解析的變更和任何更新資料列錯誤資訊。 下列程式碼假設您已建立 Web 參考，使用 Visual Studio，且您已重新命名為 DsSample 中的 Web 參考**加入 Web 參考** 對話方塊。  
  
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
  
     如果您決定自行建立 Proxy 類別，則必須採取下列其餘步驟。 若要編譯範例，請提供已建立的 Proxy 程式庫 (sample.dll) 和相關的 .NET 程式庫。 若要編譯儲存於 client.vb 檔案的 Visual Basic .NET 版本範例，請發出下列命令。  
  
    ```console
    vbc client.vb -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
     若要編譯儲存於 client.cs 檔案的 C# 版本範例，請發出下列命令。  
  
    ```console
    csc client.cs -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
## <a name="see-also"></a>另請參閱

- [ADO.NET](../../../../../docs/framework/data/adonet/index.md)
- [DataSet、DataTable 和 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [從 DataAdapter 填入 DataSet](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)
- [使用 DataAdapter 更新資料來源](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)
- [DataAdapter 參數](../../../../../docs/framework/data/adonet/dataadapter-parameters.md)
- [Web 服務描述語言工具 (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100))
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)

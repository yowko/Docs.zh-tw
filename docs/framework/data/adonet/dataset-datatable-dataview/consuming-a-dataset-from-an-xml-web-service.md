---
title: 從 XML Web Service 使用資料集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9edd6b71-0fa5-4649-ae1d-ac1c12541019
ms.openlocfilehash: 962163b51507647fd975815c214891a6d692e66c
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203953"
---
# <a name="consuming-a-dataset-from-an-xml-web-service"></a>從 XML Web Service 使用資料集
<xref:System.Data.DataSet> 採用中斷連接設計為架構，而部分原因是為了使網際網路的資料傳輸更方便。 此**資料集**是「可序列化」, 因為它可以指定為 XML Web Service 的輸入或輸出, 而不需要任何額外的編碼, 將**資料集**的內容從 XML Web Service 串流至用戶端並返回。 **資料集會**使用 DiffGram 格式 (透過網路傳送) 隱含轉換成 xml 資料流程, 然後從 XML 資料流程重建為接收端上的**資料集**。 您可以採用這種簡單靈活的方式，以 XML Web Service 來傳輸和傳回關聯式資料。 如需 DiffGram 格式的詳細資訊, 請參閱[diffgram](diffgrams.md)。  
  
 下列範例示範如何建立使用**資料集**的 XML Web Service 和用戶端, 以傳輸關聯式資料 (包括修改過的資料), 並將任何更新解析回原始資料來源。  
  
> [!NOTE]
> 建立 XML Web Service 時，建議您務必考量涉及的安全性課題。 如需保護 XML Web Service 的詳細資訊, 請參閱[保護使用 ASP.NET 所建立的 XML Web Service](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100))。  
  
### <a name="to-create-an-xml-web-service-that-returns-and-consumes-a-dataset"></a>若要建立傳回和使用 DataSet 的 XML Web Service  
  
1. 建立 XML Web Service  
  
     在此範例中, 會建立一個會傳回資料的 XML Web Service (在此案例中為來自**Northwind**資料庫的客戶清單), 並接收包含資料更新的資料**集**, XML Web Service 會解析回原始資料來源。  
  
     XML Web Service 公開兩種方法：**GetCustomers**, 以傳回客戶清單和**UpdateCustomers**, 以將更新解析回資料來源。 XML Web Service 以 DataSetSample.asmx 為檔案名稱儲存在 Web 伺服器內。 下列程式碼列出 DataSetSample.asmx 的內容大綱。  
  
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
  
     在典型的案例中, 會撰寫**UpdateCustomers**方法來攔截開放式平行存取違規。 為了簡化起見，這個範例並不包括這項步驟。 如需開放式平行存取的詳細資訊, 請參閱[開放式並行](../optimistic-concurrency.md)存取。  
  
2. 建立 XML Web Service Proxy  
  
     XML Web Service 的用戶端需要 SOAP Proxy，才能使用公開方法。 您可以命令 Visual Studio 產生這個 Proxy。 藉由從 Visual Studio 中設定現有 Web 服務的 Web 參考，會透明地執行這個步驟所說明的所有行為。 如果要自行建立 Proxy 類別，請繼續這些說明。 然而在大多數情況下，使用 Visual Studio 來建立用戶端應用程式的 Proxy 類別已足以因應。  
  
     Proxy 可使用 Web 服務描述語言工具建立。 例如, 如果 XML Web Service 在 URL `http://myserver/data/DataSetSample.asmx`中公開, 請發出如下所示的命令, 以建立命名空間為**已 dssample**的 Visual Basic .net proxy, 並將它儲存在檔案範例 .vb 中。  
  
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
  
     如果您想要讓 Visual Studio 為您產生 Web 服務 proxy 類別, 只需建立用戶端專案, 然後在 [方案總管] 視窗中, 以滑鼠右鍵按一下專案, 按一下 [**加入 Web 參考**], 然後從可用的 web 清單中選取 web 服務服務 (這可能需要提供 Web 服務端點的位址, 如果 Web 服務無法在目前的解決方案中使用, 或在目前的電腦上)。如果您自行建立 XML Web Service Proxy (如上述步驟所述)，您可以將它匯入您的用戶端程式碼，並使用 XML Web Service 方法。 下列範例程式碼會匯入 proxy 程式庫、呼叫**GetCustomers**以取得客戶清單、加入新的客戶, 然後傳回具有**UpdateCustomers**更新的**資料集**。  
  
     請注意, 此範例會將**GetChanges**傳回的**資料集**傳遞至**UpdateCustomers** , 因為只需要將修改過的資料列傳遞至**UpdateCustomers**。 **UpdateCustomers**會傳回已解析的**資料集**, 然後您可以將它**合併**到現有的**資料集**, 以併入已解決的變更和更新中的任何資料列錯誤資訊。 下列程式碼假設您已使用 Visual Studio 建立 Web 參考, 而且您已在 [**加入 Web 參考**] 對話方塊中將 web 參考重新命名為已 dssample。  
  
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

- [ADO.NET](../index.md)
- [DataSet、DataTable 和 DataView](index.md)
- [DataTable](datatables.md)
- [從 DataAdapter 填入 DataSet](../populating-a-dataset-from-a-dataadapter.md)
- [使用 DataAdapter 更新資料來源](../updating-data-sources-with-dataadapters.md)
- [DataAdapter 參數](../dataadapter-parameters.md)
- [Web 服務描述語言工具 (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100))
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)

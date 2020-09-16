---
title: 從 XML Web Service 使用資料集
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
ms.assetid: 9edd6b71-0fa5-4649-ae1d-ac1c12541019
ms.openlocfilehash: d4f4d5d34698fbb9a7986f4628b282d4425da3f7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554693"
---
# <a name="consume-a-dataset-from-an-xml-web-service"></a>從 XML web service 使用資料集

<xref:System.Data.DataSet> 採用中斷連接設計為架構，而部分原因是為了使網際網路的資料傳輸更方便。 **DataSet**是「可序列化」，因為它可以指定為 xml web service 的輸入或輸出，而不需要任何額外的程式碼，就能將**資料集**的內容從 xml web service 串流至用戶端，然後再傳回。 **資料集會**使用 DiffGram 格式隱含轉換成 xml 資料流程、透過網路傳送，然後從 XML 資料流程重建為接收端上的**資料集**。 這可讓您以簡單且彈性的方式，使用 XML Web Service 來傳輸和傳回關聯式資料。 如需 DiffGram 格式的詳細資訊，請參閱 [diffgram](diffgrams.md)。  
  
 下列範例示範如何建立 XML Web Service 和用戶端，以使用 **資料集** 來傳輸關聯式資料 (包括修改過的資料) 並將更新解析回原始資料來源。  
  
> [!NOTE]
> `DataSet` `DataTable` 如果輸入不受信任，則以 XML Web 服務呼叫的形式傳送或實例是不安全的。 如需詳細資訊，請參閱 [資料集和 DataTable 安全性指引](security-guidance.md)。
> 我們也建議您在建立 XML Web Service 時，一律考慮安全性含意。 如需保護 XML Web Service 的相關資訊，請參閱 [使用 ASP.NET 保護建立的 Xml web](/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100))service。  
  
## <a name="create-an-xml-web-service"></a>建立 XML web service
  
1. 建立 XML Web Service  
  
     在此範例中，會建立一個會傳回資料的 XML Web 服務（在此案例中為 **Northwind** 資料庫的客戶清單），並接收包含資料更新的資料 **集** ，讓 XML Web Service 解析回原始資料來源。  
  
     XML Web Service 會公開兩種方法： **GetCustomers**，以傳回客戶清單和 **UpdateCustomers**，將更新解析回資料來源。 XML Web Service 以 DataSetSample.asmx 為檔案名稱儲存在 Web 伺服器內。 下列程式碼列出 DataSetSample.asmx 的內容大綱。  
  
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
  
     在一般案例中，會撰寫 **UpdateCustomers** 方法來攔截開放式平行存取違規。 為了簡化起見，這個範例並不包括這項步驟。 如需開放式平行存取的詳細資訊，請參閱 [開放式並行](../optimistic-concurrency.md)存取。  
  
2. 建立 XML Web Service Proxy  
  
     XML Web Service 的用戶端需要 SOAP Proxy，才能使用公開方法。 您可以命令 Visual Studio 產生這個 Proxy。 藉由從 Visual Studio 中設定現有 Web 服務的 Web 參考，會透明地執行這個步驟所說明的所有行為。 如果要自行建立 Proxy 類別，請繼續這些說明。 然而在大多數情況下，使用 Visual Studio 來建立用戶端應用程式的 Proxy 類別已足以因應。  
  
     Proxy 可使用 Web 服務描述語言工具建立。 例如，如果 XML Web Service 是在 URL 公開 `http://myserver/data/DataSetSample.asmx` ，請發出如下所示的命令，以建立具有 **web 資料已 dssample** 命名空間的 Visual Basic .net proxy，然後將它儲存在檔案範例中。  
  
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
  
     如果您想要讓 Visual Studio 為您產生 Web 服務 proxy 類別，只要建立用戶端專案，然後在方案總管視窗中，以滑鼠右鍵按一下專案，然後選取 [**加入**  >  **服務參考**]。 在 [ **加入服務參考** ] 對話方塊中，選取 [ **Advanced**]，然後選取 [ **加入 Web 參考**]。 從可用的 Web 服務清單中選取 Web 服務 (如果目前的解決方案或目前的電腦) 無法使用 Web 服務，則可能需要提供 Web 服務端點的位址。 如果您自行建立 XML Web Service Proxy (如上述步驟所述)，您可以將它匯入您的用戶端程式碼，並使用 XML Web Service 方法。

     下列範例程式碼會匯入 proxy 程式庫、呼叫**GetCustomers**以取得客戶清單、新增客戶，然後傳回具有**UpdateCustomers**更新的**資料集**。  
  
     此範例會將**資料集 GetChanges**傳回的**資料集**傳遞至**UpdateCustomers** ，因為只有修改過的資料列必須傳遞至**UpdateCustomers**。 **UpdateCustomers** 會傳回已解析的 **資料集**，接著您可以將其 **合併** 到現有的 **資料集** ，以納入已解決的變更，以及來自更新的任何資料列錯誤資訊。 下列程式碼假設您已使用 Visual Studio 建立 Web 參考，且您已在 [ **加入 Web 參考** ] 對話方塊中，將 web 參考重新命名為已 dssample。  
  
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
- [DataTables](datatables.md)
- [從 DataAdapter 填入資料集](../populating-a-dataset-from-a-dataadapter.md)
- [使用 DataAdapter 更新資料來源](../updating-data-sources-with-dataadapters.md)
- [DataAdapter 的參數](../dataadapter-parameters.md)
- [Web 服務描述語言工具 ( # A0) ](/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100))
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)

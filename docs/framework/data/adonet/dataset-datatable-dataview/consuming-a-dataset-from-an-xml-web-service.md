---
title: 從 XML Web Service 使用資料集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9edd6b71-0fa5-4649-ae1d-ac1c12541019
ms.openlocfilehash: d835ffe7a10492ee731de8e5301e6d34545f9c32
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151386"
---
# <a name="consuming-a-dataset-from-an-xml-web-service"></a>從 XML Web Service 使用資料集
<xref:System.Data.DataSet> 採用中斷連接設計為架構，而部分原因是為了使網際網路的資料傳輸更方便。 **DataSet**是"可序列化的"，因為它可以指定為 XML Web 服務的輸入或輸出，而無需任何其他編碼才能將**DataSet**的內容從 XML Web 服務資料流到用戶端並返回。 **DataSet**使用 DiffGram 格式隱式轉換為 XML 流，通過網路發送，然後從 XML 流重建為接收端的**DataSet。** 您可以採用這種簡單靈活的方式，以 XML Web Service 來傳輸和傳回關聯式資料。 有關 DiffGram 格式的詳細資訊，請參閱[DiffGram](diffgrams.md)。  
  
 下面的示例演示如何創建使用**DataSet**傳輸關係資料（包括修改資料）的 XML Web 服務和用戶端，並將任何更新解析回原始資料來源。  
  
> [!NOTE]
> 建立 XML Web Service 時，建議您務必考量涉及的安全性課題。 有關保護 XML Web 服務的資訊，請參閱[保護使用 ASP.NET 創建的 XML Web 服務](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100))。  
  
### <a name="to-create-an-xml-web-service-that-returns-and-consumes-a-dataset"></a>若要建立傳回和使用 DataSet 的 XML Web Service  
  
1. 建立 XML Web Service  
  
     在此示例中，將創建一個返回資料的 XML Web 服務，在此示例中，從**Northwind**資料庫中返回客戶清單，並接收包含資料更新**的 DataSet，XML** Web 服務將這些資料解析回原始資料來源。  
  
     XML Web 服務公開了兩種方法 **：GetCustomers，** 以返回客戶清單和**更新客戶**，以解析更新回資料來源。 XML Web Service 以 DataSetSample.asmx 為檔案名稱儲存在 Web 伺服器內。 下列程式碼列出 DataSetSample.asmx 的內容大綱。  
  
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
  
     在典型方案中，將編寫**UpdateCustomers**方法來捕獲樂觀的併發衝突。 為了簡化起見，這個範例並不包括這項步驟。 有關樂觀併發的詳細資訊，請參閱[樂觀併發](../optimistic-concurrency.md)。  
  
2. 建立 XML Web Service Proxy  
  
     XML Web Service 的用戶端需要 SOAP Proxy，才能使用公開方法。 您可以命令 Visual Studio 產生這個 Proxy。 藉由從 Visual Studio 中設定現有 Web 服務的 Web 參考，會透明地執行這個步驟所說明的所有行為。 如果要自行建立 Proxy 類別，請繼續這些說明。 然而在大多數情況下，使用 Visual Studio 來建立用戶端應用程式的 Proxy 類別已足以因應。  
  
     Proxy 可使用 Web 服務描述語言工具建立。 例如，如果 XML Web 服務在 URL`http://myserver/data/DataSetSample.asmx`上公開，則發出如下命令，以創建具有**WebData.DSSample**命名空間的 Visual Basic .NET 代理，並將其存儲在檔示例.vb 中。  
  
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
  
     如果要讓 Visual Studio 為您生成 Web 服務代理類，只需創建用戶端專案，並在"解決方案資源管理器"視窗中按右鍵專案，按一下"**添加 Web 參考**"，然後從可用 Web 服務清單中選擇 Web 服務（如果 Web 服務在當前解決方案中不可用，則可能需要提供 Web 服務終結點的位址，如果 Web 服務在當前解決方案中不可用，則在當前電腦上）。如果自己創建 XML Web 服務代理（如上一步所述），則可以將其導入到用戶端代碼中並使用 XML Web 服務方法。 以下示例代碼導入代理庫，調用**GetCustomer**以獲取客戶清單，添加新客戶，然後返回帶有**更新客戶**更新的**DataSet。**  
  
     請注意，該示例將**DataSet 返回的 DataSet** **獲取更改**傳遞給**更新客戶，** 因為只有修改的行需要傳遞給**更新客戶**。 **UpdateCustomers**返回已解析**的 DataSet**，然後可以**合併**到現有**DataSet**中，以合併已解決的更改和更新中的任何行錯誤資訊。 以下代碼假定您已使用 Visual Studio 創建 Web 參考，並且您在 **"添加 Web 參考"** 對話方塊中將 Web 參考重命名為 DsSample。  
  
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
- [從 DataAdapter 填入資料集](../populating-a-dataset-from-a-dataadapter.md)
- [使用 DataAdapter 更新資料來源](../updating-data-sources-with-dataadapters.md)
- [DataAdapter 的參數](../dataadapter-parameters.md)
- [Web 服務描述語言工具 （Wsdl.exe）](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100))
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)

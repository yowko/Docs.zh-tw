---
title: 從 XML Web Service 使用資料集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9edd6b71-0fa5-4649-ae1d-ac1c12541019
ms.openlocfilehash: dbb45b890ddfab3f771d4b4a8932f970036b346d
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2019
ms.locfileid: "55828289"
---
# <a name="consuming-a-dataset-from-an-xml-web-service"></a><span data-ttu-id="474c2-102">從 XML Web Service 使用資料集</span><span class="sxs-lookup"><span data-stu-id="474c2-102">Consuming a DataSet from an XML Web Service</span></span>
<span data-ttu-id="474c2-103"><xref:System.Data.DataSet> 採用中斷連接設計為架構，而部分原因是為了使網際網路的資料傳輸更方便。</span><span class="sxs-lookup"><span data-stu-id="474c2-103">The <xref:System.Data.DataSet> was architected with a disconnected design, in part to facilitate the convenient transport of data over the Internet.</span></span> <span data-ttu-id="474c2-104">**資料集**，它可以指定為輸入或輸出自 XML Web service，而不需要任何額外的程式碼所需資料流的內容是 「 序列化 」 **DataSet**從 XML Web service用戶端和上一步。</span><span class="sxs-lookup"><span data-stu-id="474c2-104">The **DataSet** is "serializable" in that it can be specified as an input to or output from XML Web services without any additional coding required to stream the contents of the **DataSet** from an XML Web service to a client and back.</span></span> <span data-ttu-id="474c2-105">**資料集**是隱含地轉換成使用 DiffGram 格式的 XML 資料流傳送透過網路，然後重新建構 XML 資料流，做為從**DataSet**在接收端。</span><span class="sxs-lookup"><span data-stu-id="474c2-105">The **DataSet** is implicitly converted to an XML stream using the DiffGram format, sent over the network, and then reconstructed from the XML stream as a **DataSet** on the receiving end.</span></span> <span data-ttu-id="474c2-106">您可以採用這種簡單靈活的方式，以 XML Web Service 來傳輸和傳回關聯式資料。</span><span class="sxs-lookup"><span data-stu-id="474c2-106">This gives you a very simple and flexible method for transmitting and returning relational data using XML Web services.</span></span> <span data-ttu-id="474c2-107">如需有關 DiffGram 格式的詳細資訊，請參閱[DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)。</span><span class="sxs-lookup"><span data-stu-id="474c2-107">For more information about the DiffGram format, see [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).</span></span>  
  
 <span data-ttu-id="474c2-108">下列範例示範如何建立 XML Web service 和使用的用戶端**資料集**傳輸關聯式資料 （包括已修改的資料） 和任何更新解析回原始資料來源。</span><span class="sxs-lookup"><span data-stu-id="474c2-108">The following example shows how to create an XML Web service and client that use the **DataSet** to transport relational data (including modified data) and resolve any updates back to the original data source.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="474c2-109">建立 XML Web Service 時，建議您務必考量涉及的安全性課題。</span><span class="sxs-lookup"><span data-stu-id="474c2-109">We recommend that you always consider security implications when creating an XML Web service.</span></span> <span data-ttu-id="474c2-110">如需有關保護 XML Web service，請參閱[保護 Web 服務使用 ASP.NET 建立 XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="474c2-110">For information on securing an XML Web service, see [Securing XML Web Services Created Using ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100)).</span></span>  
  
### <a name="to-create-an-xml-web-service-that-returns-and-consumes-a-dataset"></a><span data-ttu-id="474c2-111">若要建立傳回和使用 DataSet 的 XML Web Service</span><span class="sxs-lookup"><span data-stu-id="474c2-111">To create an XML Web service that returns and consumes a DataSet</span></span>  
  
1.  <span data-ttu-id="474c2-112">建立 XML Web Service</span><span class="sxs-lookup"><span data-stu-id="474c2-112">Create the XML Web service.</span></span>  
  
     <span data-ttu-id="474c2-113">在此範例中，XML Web service 會建立傳回資料，在此情況下從客戶的清單**Northwind**資料庫，然後接收**資料集**與更新資料，其中 XML Web service解析回原始的資料來源。</span><span class="sxs-lookup"><span data-stu-id="474c2-113">In the example, an XML Web service is created that returns data, in this case a list of customers from the **Northwind** database, and receives a **DataSet** with updates to the data, which the XML Web service resolves back to the original data source.</span></span>  
  
     <span data-ttu-id="474c2-114">XML Web Service 公開兩種方法：**GetCustomers**，以傳回客戶清單，並**UpdateCustomers**，來將更新解析回資料來源。</span><span class="sxs-lookup"><span data-stu-id="474c2-114">The XML Web service exposes two methods: **GetCustomers**, to return the list of customers, and **UpdateCustomers**, to resolve updates back to the data source.</span></span> <span data-ttu-id="474c2-115">XML Web Service 以 DataSetSample.asmx 為檔案名稱儲存在 Web 伺服器內。</span><span class="sxs-lookup"><span data-stu-id="474c2-115">The XML Web service is stored in a file on the Web server called DataSetSample.asmx.</span></span> <span data-ttu-id="474c2-116">下列程式碼列出 DataSetSample.asmx 的內容大綱。</span><span class="sxs-lookup"><span data-stu-id="474c2-116">The following code outlines the contents of DataSetSample.asmx.</span></span>  
  
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
  
     <span data-ttu-id="474c2-117">在典型的案例中， **UpdateCustomers**會寫入方法，來攔截開放式同步存取違規。</span><span class="sxs-lookup"><span data-stu-id="474c2-117">In a typical scenario, the **UpdateCustomers** method would be written to catch optimistic concurrency violations.</span></span> <span data-ttu-id="474c2-118">為了簡化起見，這個範例並不包括這項步驟。</span><span class="sxs-lookup"><span data-stu-id="474c2-118">For simplicity, the example does not include this.</span></span> <span data-ttu-id="474c2-119">如需有關開放式並行存取的詳細資訊，請參閱[開放式並行存取](../../../../../docs/framework/data/adonet/optimistic-concurrency.md)。</span><span class="sxs-lookup"><span data-stu-id="474c2-119">For more information about optimistic concurrency, see [Optimistic Concurrency](../../../../../docs/framework/data/adonet/optimistic-concurrency.md).</span></span>  
  
2.  <span data-ttu-id="474c2-120">建立 XML Web Service Proxy</span><span class="sxs-lookup"><span data-stu-id="474c2-120">Create an XML Web service proxy.</span></span>  
  
     <span data-ttu-id="474c2-121">XML Web Service 的用戶端需要 SOAP Proxy，才能使用公開方法。</span><span class="sxs-lookup"><span data-stu-id="474c2-121">Clients of the XML Web service require a SOAP proxy in order to consume the exposed methods.</span></span> <span data-ttu-id="474c2-122">您可以命令 Visual Studio 產生這個 Proxy。</span><span class="sxs-lookup"><span data-stu-id="474c2-122">You can have Visual Studio generate this proxy for you.</span></span> <span data-ttu-id="474c2-123">藉由從 Visual Studio 中設定現有 Web 服務的 Web 參考，會透明地執行這個步驟所說明的所有行為。</span><span class="sxs-lookup"><span data-stu-id="474c2-123">By setting a Web reference to an existing Web service from within Visual Studio, all the behavior described in this step occurs transparently.</span></span> <span data-ttu-id="474c2-124">如果要自行建立 Proxy 類別，請繼續這些說明。</span><span class="sxs-lookup"><span data-stu-id="474c2-124">If you want to create the proxy class yourself, continue with this discussion.</span></span> <span data-ttu-id="474c2-125">然而在大多數情況下，使用 Visual Studio 來建立用戶端應用程式的 Proxy 類別已足以因應。</span><span class="sxs-lookup"><span data-stu-id="474c2-125">In most circumstances, however, using Visual Studio to create the proxy class for the client application is sufficient.</span></span>  
  
     <span data-ttu-id="474c2-126">Proxy 可使用 Web 服務描述語言工具建立。</span><span class="sxs-lookup"><span data-stu-id="474c2-126">A proxy can be created using the Web Services Description Language Tool.</span></span> <span data-ttu-id="474c2-127">例如，如果 XML Web service 會在 URL 中公開`http://myserver/data/DataSetSample.asmx`，發出如下所示的命令來建立 Visual Basic.NET proxy 的命名空間**WebData.DSSample**並將它儲存在 sample.vb 檔案中。</span><span class="sxs-lookup"><span data-stu-id="474c2-127">For example, if the XML Web service is exposed at the URL `http://myserver/data/DataSetSample.asmx`, issue a command such as the following to create a Visual Basic .NET proxy with a namespace of **WebData.DSSample** and store it in the file sample.vb.</span></span>  
  
    ```console
    wsdl /l:VB -out:sample.vb http://myserver/data/DataSetSample.asmx /n:WebData.DSSample  
    ```  
  
     <span data-ttu-id="474c2-128">若要在 sample.cs 檔案中建立 C# Proxy，請發出下列命令。</span><span class="sxs-lookup"><span data-stu-id="474c2-128">To create a C# proxy in the file sample.cs, issue the following command.</span></span>  
  
    ```console
    wsdl -l:CS -out:sample.cs http://myserver/data/DataSetSample.asmx -n:WebData.DSSample  
    ```  
  
     <span data-ttu-id="474c2-129">接下來 Proxy 可編譯為程式庫，並匯入 XML Web Service 用戶端。</span><span class="sxs-lookup"><span data-stu-id="474c2-129">The proxy can then be compiled as a library and imported into the XML Web service client.</span></span> <span data-ttu-id="474c2-130">若要將儲存在 sample.vb 內的 Visual Basic .NET Proxy 程式碼編譯為 sample.dll，請發出下列命令。</span><span class="sxs-lookup"><span data-stu-id="474c2-130">To compile the Visual Basic .NET proxy code stored in sample.vb as sample.dll, issue the following command.</span></span>  
  
    ```console  
    vbc -t:library -out:sample.dll sample.vb -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
     <span data-ttu-id="474c2-131">若要將儲存在 sample.cs 的 C# Proxy 程式碼編譯為 sample.dll，請發出下列命令。</span><span class="sxs-lookup"><span data-stu-id="474c2-131">To compile the C# proxy code stored in sample.cs as sample.dll, issue the following command.</span></span>  
  
    ```console
    csc -t:library -out:sample.dll sample.cs -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
3.  <span data-ttu-id="474c2-132">建立 XML Web Service 用戶端。</span><span class="sxs-lookup"><span data-stu-id="474c2-132">Create an XML Web service client.</span></span>  
  
     <span data-ttu-id="474c2-133">如果您想要有 Visual Studio 為您產生 Web 服務 proxy 類別，只要建立用戶端專案中，在 方案總管 視窗中，以滑鼠右鍵按一下專案，請按一下**加入 Web 參考**，然後選取 從 Web 服務清單中可用的 Web 服務 （這可能需要提供 Web 服務端點的位址，如果 Web 服務無法使用目前的方案，或目前的電腦上）。如果您自行建立 XML Web Service Proxy (如上述步驟所述)，您可以將它匯入您的用戶端程式碼，並使用 XML Web Service 方法。</span><span class="sxs-lookup"><span data-stu-id="474c2-133">If you want to have Visual Studio generate the Web service proxy class for you, simply create the client project, and, in the Solution Explorer window, right-click the project, click **Add Web Reference**, and select the Web service from the list of available Web services (this may require supplying the address of the Web service endpoint, if the Web service isn't available within the current solution, or on the current computer.) If you create the XML Web service proxy yourself (as described in the previous step), you can import it into your client code and consume the XML Web service methods.</span></span> <span data-ttu-id="474c2-134">下列範例程式碼會匯入 proxy 程式庫，呼叫**GetCustomers**若要取得一份客戶，將新的客戶，然後傳回**資料集**更新**UpdateCustomers**.</span><span class="sxs-lookup"><span data-stu-id="474c2-134">The following sample code imports the proxy library, calls **GetCustomers** to get a list of customers, adds a new customer, and then returns a **DataSet** with the updates to **UpdateCustomers**.</span></span>  
  
     <span data-ttu-id="474c2-135">請注意，範例會傳遞**資料集**由**DataSet.GetChanges**來**UpdateCustomers**傳遞至要修改的資料列因為**UpdateCustomers**。</span><span class="sxs-lookup"><span data-stu-id="474c2-135">Notice that the example passes the **DataSet** returned by **DataSet.GetChanges** to **UpdateCustomers** because only modified rows need to be passed to **UpdateCustomers**.</span></span> <span data-ttu-id="474c2-136">**UpdateCustomers**傳回已解析**資料集**，然後您便可以**合併**至現有**資料集**來納入已解析的變更和任何更新資料列錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="474c2-136">**UpdateCustomers** returns the resolved **DataSet**, which you can then **Merge** into the existing **DataSet** to incorporate the resolved changes and any row error information from the update.</span></span> <span data-ttu-id="474c2-137">下列程式碼假設您已建立 Web 參考，使用 Visual Studio，且您已重新命名為 DsSample 中的 Web 參考**加入 Web 參考** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="474c2-137">The following code assumes that you have used Visual Studio to create the Web reference, and that you have renamed the Web reference to DsSample in the **Add Web Reference** dialog box.</span></span>  
  
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
  
     <span data-ttu-id="474c2-138">如果您決定自行建立 Proxy 類別，則必須採取下列其餘步驟。</span><span class="sxs-lookup"><span data-stu-id="474c2-138">If you decide to create the proxy class yourself, you must take the following extra steps.</span></span> <span data-ttu-id="474c2-139">若要編譯範例，請提供已建立的 Proxy 程式庫 (sample.dll) 和相關的 .NET 程式庫。</span><span class="sxs-lookup"><span data-stu-id="474c2-139">To compile the sample, supply the proxy library that was created (sample.dll) and the related .NET libraries.</span></span> <span data-ttu-id="474c2-140">若要編譯儲存於 client.vb 檔案的 Visual Basic .NET 版本範例，請發出下列命令。</span><span class="sxs-lookup"><span data-stu-id="474c2-140">To compile the Visual Basic .NET version of the sample, stored in the file client.vb, issue the following command.</span></span>  
  
    ```console
    vbc client.vb -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
     <span data-ttu-id="474c2-141">若要編譯儲存於 client.cs 檔案的 C# 版本範例，請發出下列命令。</span><span class="sxs-lookup"><span data-stu-id="474c2-141">To compile the C# version of the sample, stored in the file client.cs, issue the following command.</span></span>  
  
    ```console
    csc client.cs -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="474c2-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="474c2-142">See also</span></span>
- [<span data-ttu-id="474c2-143">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="474c2-143">ADO.NET</span></span>](../../../../../docs/framework/data/adonet/index.md)
- [<span data-ttu-id="474c2-144">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="474c2-144">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="474c2-145">DataTable</span><span class="sxs-lookup"><span data-stu-id="474c2-145">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [<span data-ttu-id="474c2-146">從 DataAdapter 填入 DataSet</span><span class="sxs-lookup"><span data-stu-id="474c2-146">Populating a DataSet from a DataAdapter</span></span>](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)
- [<span data-ttu-id="474c2-147">使用 DataAdapter 更新資料來源</span><span class="sxs-lookup"><span data-stu-id="474c2-147">Updating Data Sources with DataAdapters</span></span>](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="474c2-148">DataAdapter 參數</span><span class="sxs-lookup"><span data-stu-id="474c2-148">DataAdapter Parameters</span></span>](../../../../../docs/framework/data/adonet/dataadapter-parameters.md)
- <span data-ttu-id="474c2-149">[Web 服務描述語言工具 (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="474c2-149">[Web Services Description Language Tool (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100))</span></span>
- [<span data-ttu-id="474c2-150">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="474c2-150">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)

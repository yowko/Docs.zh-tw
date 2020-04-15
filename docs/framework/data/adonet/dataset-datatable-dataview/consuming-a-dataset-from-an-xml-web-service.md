---
title: 從 XML Web Service 使用資料集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9edd6b71-0fa5-4649-ae1d-ac1c12541019
ms.openlocfilehash: d7328949e3eb4822b1a645bb5f0c1866f01ecb0a
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389739"
---
# <a name="consume-a-dataset-from-an-xml-web-service"></a><span data-ttu-id="0fc92-102">使用 XML Web 服務的資料集</span><span class="sxs-lookup"><span data-stu-id="0fc92-102">Consume a DataSet from an XML web service</span></span>

<span data-ttu-id="0fc92-103"><xref:System.Data.DataSet> 採用中斷連接設計為架構，而部分原因是為了使網際網路的資料傳輸更方便。</span><span class="sxs-lookup"><span data-stu-id="0fc92-103">The <xref:System.Data.DataSet> was architected with a disconnected design, in part to facilitate the convenient transport of data over the Internet.</span></span> <span data-ttu-id="0fc92-104">**DataSet**是"可序列化的",因為它可以指定為 XML Web 服務的輸入或輸出,而無需任何其他編碼才能將**DataSet**的內容從 XML Web 服務流式傳輸到用戶端並返回。</span><span class="sxs-lookup"><span data-stu-id="0fc92-104">The **DataSet** is "serializable" in that it can be specified as an input to or output from XML Web services without any additional coding required to stream the contents of the **DataSet** from an XML Web service to a client and back.</span></span> <span data-ttu-id="0fc92-105">**DataSet**使用 DiffGram 格式隱式轉換為 XML 串流,透過網路發送,然後從 XML 串流重建為接收端的**DataSet。**</span><span class="sxs-lookup"><span data-stu-id="0fc92-105">The **DataSet** is implicitly converted to an XML stream using the DiffGram format, sent over the network, and then reconstructed from the XML stream as a **DataSet** on the receiving end.</span></span> <span data-ttu-id="0fc92-106">您可以採用這種簡單靈活的方式，以 XML Web Service 來傳輸和傳回關聯式資料。</span><span class="sxs-lookup"><span data-stu-id="0fc92-106">This gives you a very simple and flexible method for transmitting and returning relational data using XML Web services.</span></span> <span data-ttu-id="0fc92-107">有關 DiffGram 格式的詳細資訊,請參閱[DiffGram](diffgrams.md)。</span><span class="sxs-lookup"><span data-stu-id="0fc92-107">For more information about the DiffGram format, see [DiffGrams](diffgrams.md).</span></span>  
  
 <span data-ttu-id="0fc92-108">下面的範例展示如何建立使用**DataSet**傳輸關係資料(包括修改資料)的XML Web服務和用戶端,並將任何更新解析回原始資料來源。</span><span class="sxs-lookup"><span data-stu-id="0fc92-108">The following example shows how to create an XML Web service and client that use the **DataSet** to transport relational data (including modified data) and resolve any updates back to the original data source.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0fc92-109">建立 XML Web Service 時，建議您務必考量涉及的安全性課題。</span><span class="sxs-lookup"><span data-stu-id="0fc92-109">We recommend that you always consider security implications when creating an XML Web service.</span></span> <span data-ttu-id="0fc92-110">有關保護 XML Web 服務的資訊,請參閱[保護使用 ASP.NET 建立的 XML Web 服務](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="0fc92-110">For information on securing an XML Web service, see [Securing XML Web Services Created Using ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100)).</span></span>  
  
## <a name="create-an-xml-web-service"></a><span data-ttu-id="0fc92-111">建立 XML Web 服務</span><span class="sxs-lookup"><span data-stu-id="0fc92-111">Create an XML web service</span></span>
  
1. <span data-ttu-id="0fc92-112">建立 XML Web Service</span><span class="sxs-lookup"><span data-stu-id="0fc92-112">Create the XML Web service.</span></span>  
  
     <span data-ttu-id="0fc92-113">在此範例中,將建立一個傳回資料的 XML Web 服務,在此範例中,從**Northwind**資料庫中傳回客戶清單,並接收包含資料更新**的 DataSet,XML** Web 服務將這些資料解析回原始資料來源。</span><span class="sxs-lookup"><span data-stu-id="0fc92-113">In the example, an XML Web service is created that returns data, in this case a list of customers from the **Northwind** database, and receives a **DataSet** with updates to the data, which the XML Web service resolves back to the original data source.</span></span>  
  
     <span data-ttu-id="0fc92-114">XML Web 服務公開了兩種方法 **:GetCustomers,** 以返回客戶清單和**更新客戶**,以解析更新回資料來源。</span><span class="sxs-lookup"><span data-stu-id="0fc92-114">The XML Web service exposes two methods: **GetCustomers**, to return the list of customers, and **UpdateCustomers**, to resolve updates back to the data source.</span></span> <span data-ttu-id="0fc92-115">XML Web Service 以 DataSetSample.asmx 為檔案名稱儲存在 Web 伺服器內。</span><span class="sxs-lookup"><span data-stu-id="0fc92-115">The XML Web service is stored in a file on the Web server called DataSetSample.asmx.</span></span> <span data-ttu-id="0fc92-116">下列程式碼列出 DataSetSample.asmx 的內容大綱。</span><span class="sxs-lookup"><span data-stu-id="0fc92-116">The following code outlines the contents of DataSetSample.asmx.</span></span>  
  
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
  
     <span data-ttu-id="0fc92-117">在典型方案中,將編寫**UpdateCustomers**方法來捕獲樂觀的併發衝突。</span><span class="sxs-lookup"><span data-stu-id="0fc92-117">In a typical scenario, the **UpdateCustomers** method would be written to catch optimistic concurrency violations.</span></span> <span data-ttu-id="0fc92-118">為了簡化起見，這個範例並不包括這項步驟。</span><span class="sxs-lookup"><span data-stu-id="0fc92-118">For simplicity, the example does not include this.</span></span> <span data-ttu-id="0fc92-119">有關樂觀併發的詳細資訊,請參閱[樂觀併發](../optimistic-concurrency.md)。</span><span class="sxs-lookup"><span data-stu-id="0fc92-119">For more information about optimistic concurrency, see [Optimistic Concurrency](../optimistic-concurrency.md).</span></span>  
  
2. <span data-ttu-id="0fc92-120">建立 XML Web Service Proxy</span><span class="sxs-lookup"><span data-stu-id="0fc92-120">Create an XML Web service proxy.</span></span>  
  
     <span data-ttu-id="0fc92-121">XML Web Service 的用戶端需要 SOAP Proxy，才能使用公開方法。</span><span class="sxs-lookup"><span data-stu-id="0fc92-121">Clients of the XML Web service require a SOAP proxy in order to consume the exposed methods.</span></span> <span data-ttu-id="0fc92-122">您可以命令 Visual Studio 產生這個 Proxy。</span><span class="sxs-lookup"><span data-stu-id="0fc92-122">You can have Visual Studio generate this proxy for you.</span></span> <span data-ttu-id="0fc92-123">藉由從 Visual Studio 中設定現有 Web 服務的 Web 參考，會透明地執行這個步驟所說明的所有行為。</span><span class="sxs-lookup"><span data-stu-id="0fc92-123">By setting a Web reference to an existing Web service from within Visual Studio, all the behavior described in this step occurs transparently.</span></span> <span data-ttu-id="0fc92-124">如果要自行建立 Proxy 類別，請繼續這些說明。</span><span class="sxs-lookup"><span data-stu-id="0fc92-124">If you want to create the proxy class yourself, continue with this discussion.</span></span> <span data-ttu-id="0fc92-125">然而在大多數情況下，使用 Visual Studio 來建立用戶端應用程式的 Proxy 類別已足以因應。</span><span class="sxs-lookup"><span data-stu-id="0fc92-125">In most circumstances, however, using Visual Studio to create the proxy class for the client application is sufficient.</span></span>  
  
     <span data-ttu-id="0fc92-126">Proxy 可使用 Web 服務描述語言工具建立。</span><span class="sxs-lookup"><span data-stu-id="0fc92-126">A proxy can be created using the Web Services Description Language Tool.</span></span> <span data-ttu-id="0fc92-127">例如,如果 XML Web`http://myserver/data/DataSetSample.asmx`服務在 URL 上公開,則發出如下命令,以建立具有**WebData.DSSample**命名空間的 Visual Basic .NET 代理,並將其儲存在檔案範例.vb 中。</span><span class="sxs-lookup"><span data-stu-id="0fc92-127">For example, if the XML Web service is exposed at the URL `http://myserver/data/DataSetSample.asmx`, issue a command such as the following to create a Visual Basic .NET proxy with a namespace of **WebData.DSSample** and store it in the file sample.vb.</span></span>  
  
    ```console
    wsdl /l:VB -out:sample.vb http://myserver/data/DataSetSample.asmx /n:WebData.DSSample  
    ```  
  
     <span data-ttu-id="0fc92-128">若要在 sample.cs 檔案中建立 C# Proxy，請發出下列命令。</span><span class="sxs-lookup"><span data-stu-id="0fc92-128">To create a C# proxy in the file sample.cs, issue the following command.</span></span>  
  
    ```console
    wsdl -l:CS -out:sample.cs http://myserver/data/DataSetSample.asmx -n:WebData.DSSample  
    ```  
  
     <span data-ttu-id="0fc92-129">接下來 Proxy 可編譯為程式庫，並匯入 XML Web Service 用戶端。</span><span class="sxs-lookup"><span data-stu-id="0fc92-129">The proxy can then be compiled as a library and imported into the XML Web service client.</span></span> <span data-ttu-id="0fc92-130">若要將儲存在 sample.vb 內的 Visual Basic .NET Proxy 程式碼編譯為 sample.dll，請發出下列命令。</span><span class="sxs-lookup"><span data-stu-id="0fc92-130">To compile the Visual Basic .NET proxy code stored in sample.vb as sample.dll, issue the following command.</span></span>  
  
    ```console  
    vbc -t:library -out:sample.dll sample.vb -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
     <span data-ttu-id="0fc92-131">若要將儲存在 sample.cs 的 C# Proxy 程式碼編譯為 sample.dll，請發出下列命令。</span><span class="sxs-lookup"><span data-stu-id="0fc92-131">To compile the C# proxy code stored in sample.cs as sample.dll, issue the following command.</span></span>  
  
    ```console
    csc -t:library -out:sample.dll sample.cs -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
3. <span data-ttu-id="0fc92-132">建立 XML Web Service 用戶端。</span><span class="sxs-lookup"><span data-stu-id="0fc92-132">Create an XML Web service client.</span></span>  
  
     <span data-ttu-id="0fc92-133">如果要讓 Visual Studio 為您生成 Web 服務代理類,只需創建用戶端專案,並在解決方案資源管理器視窗中右鍵單擊專案,然後選擇「**添加** > **服務引用**」 。</span><span class="sxs-lookup"><span data-stu-id="0fc92-133">If you want to have Visual Studio generate the Web service proxy class for you, simply create the client project, and, in the Solution Explorer window, right-click the project, and then select **Add** > **Service Reference**.</span></span> <span data-ttu-id="0fc92-134">在 **"添加服務參考"** 對話方塊中,選擇 **「進階**」,然後選擇「**添加 Web 引用**」。。</span><span class="sxs-lookup"><span data-stu-id="0fc92-134">In the **Add Service Reference** dialog box, select **Advanced**, and then select **Add Web Reference**.</span></span> <span data-ttu-id="0fc92-135">從可用 Web 服務清單中選擇 Web 服務(如果 Web 服務在當前解決方案或當前電腦上不可用,則可能需要提供 Web 服務終結點的位址)。</span><span class="sxs-lookup"><span data-stu-id="0fc92-135">Select the Web service from the list of available Web services (this may require supplying the address of the Web service endpoint if the Web service isn't available within the current solution or on the current computer).</span></span> <span data-ttu-id="0fc92-136">如果您自行建立 XML Web Service Proxy (如上述步驟所述)，您可以將它匯入您的用戶端程式碼，並使用 XML Web Service 方法。</span><span class="sxs-lookup"><span data-stu-id="0fc92-136">If you create the XML Web service proxy yourself (as described in the previous step), you can import it into your client code and consume the XML Web service methods.</span></span>

     <span data-ttu-id="0fc92-137">以下範例代碼匯入代理庫,呼叫**GetCustomer**以取得客戶清單,添加新客戶,然後返回帶有**更新客戶**更新的**DataSet。**</span><span class="sxs-lookup"><span data-stu-id="0fc92-137">The following sample code imports the proxy library, calls **GetCustomers** to get a list of customers, adds a new customer, and then returns a **DataSet** with the updates to **UpdateCustomers**.</span></span>  
  
     <span data-ttu-id="0fc92-138">這個範例將**DataSet 傳回的資料集\*\*\*\*傳遞給\*\*\*\*更新客戶,** 因為只有修改的行需要傳遞給**更新客戶**。</span><span class="sxs-lookup"><span data-stu-id="0fc92-138">The example passes the **DataSet** returned by **DataSet.GetChanges** to **UpdateCustomers** because only modified rows need to be passed to **UpdateCustomers**.</span></span> <span data-ttu-id="0fc92-139">**UpdateCustomers**傳回已解析**的 DataSet**,然後可以**合併**到現有**DataSet**中,以合併已解決的更改和更新中的任何行錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="0fc92-139">**UpdateCustomers** returns the resolved **DataSet**, which you can then **Merge** into the existing **DataSet** to incorporate the resolved changes and any row error information from the update.</span></span> <span data-ttu-id="0fc92-140">以下代碼假定您已使用 Visual Studio 建立 Web 引用,並且您在 **「新增 Web 引用」** 對話框中將 Web 引用重新命名為 DsSample。</span><span class="sxs-lookup"><span data-stu-id="0fc92-140">The following code assumes that you have used Visual Studio to create the Web reference, and that you have renamed the Web reference to DsSample in the **Add Web Reference** dialog box.</span></span>  
  
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
  
     <span data-ttu-id="0fc92-141">如果您決定自行建立 Proxy 類別，則必須採取下列其餘步驟。</span><span class="sxs-lookup"><span data-stu-id="0fc92-141">If you decide to create the proxy class yourself, you must take the following extra steps.</span></span> <span data-ttu-id="0fc92-142">若要編譯範例，請提供已建立的 Proxy 程式庫 (sample.dll) 和相關的 .NET 程式庫。</span><span class="sxs-lookup"><span data-stu-id="0fc92-142">To compile the sample, supply the proxy library that was created (sample.dll) and the related .NET libraries.</span></span> <span data-ttu-id="0fc92-143">若要編譯儲存於 client.vb 檔案的 Visual Basic .NET 版本範例，請發出下列命令。</span><span class="sxs-lookup"><span data-stu-id="0fc92-143">To compile the Visual Basic .NET version of the sample, stored in the file client.vb, issue the following command.</span></span>  
  
    ```console
    vbc client.vb -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
     <span data-ttu-id="0fc92-144">若要編譯儲存於 client.cs 檔案的 C# 版本範例，請發出下列命令。</span><span class="sxs-lookup"><span data-stu-id="0fc92-144">To compile the C# version of the sample, stored in the file client.cs, issue the following command.</span></span>  
  
    ```console
    csc client.cs -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="0fc92-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0fc92-145">See also</span></span>

- [<span data-ttu-id="0fc92-146">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0fc92-146">ADO.NET</span></span>](../index.md)
- [<span data-ttu-id="0fc92-147">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="0fc92-147">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="0fc92-148">DataTable</span><span class="sxs-lookup"><span data-stu-id="0fc92-148">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="0fc92-149">從 DataAdapter 填入資料集</span><span class="sxs-lookup"><span data-stu-id="0fc92-149">Populating a DataSet from a DataAdapter</span></span>](../populating-a-dataset-from-a-dataadapter.md)
- [<span data-ttu-id="0fc92-150">使用 DataAdapter 更新資料來源</span><span class="sxs-lookup"><span data-stu-id="0fc92-150">Updating Data Sources with DataAdapters</span></span>](../updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="0fc92-151">DataAdapter 的參數</span><span class="sxs-lookup"><span data-stu-id="0fc92-151">DataAdapter Parameters</span></span>](../dataadapter-parameters.md)
- <span data-ttu-id="0fc92-152">[Web 服務描述語言工具 (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="0fc92-152">[Web Services Description Language Tool (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100))</span></span>
- <span data-ttu-id="0fc92-153">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="0fc92-153">[ADO.NET Overview](../ado-net-overview.md)</span></span>

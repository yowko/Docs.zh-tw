---
title: "使用 WCF 用戶端存取服務"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: clients [WCF], consuming services
ms.assetid: d780af9f-73c5-42db-9e52-077a5e4de7fe
caps.latest.revision: "36"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d8698e0657de31d78699df478da5e716bf831fc4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="accessing-services-using-a-wcf-client"></a><span data-ttu-id="69723-102">使用 WCF 用戶端存取服務</span><span class="sxs-lookup"><span data-stu-id="69723-102">Accessing Services Using a WCF Client</span></span>
<span data-ttu-id="69723-103">建立服務之後，下一個步驟就是建立 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端 Proxy。</span><span class="sxs-lookup"><span data-stu-id="69723-103">After you create a service, the next step is to create a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client proxy.</span></span> <span data-ttu-id="69723-104">用戶端應用程式會使用 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端 Proxy 與服務進行通訊。</span><span class="sxs-lookup"><span data-stu-id="69723-104">A client application uses the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client proxy to communicate with the service.</span></span> <span data-ttu-id="69723-105">用戶端應用程式通常會匯入服務的中繼資料，以產生可用來叫用服務的 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端程式碼。</span><span class="sxs-lookup"><span data-stu-id="69723-105">Client applications usually import a service's metadata to generate [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client code that can be used to invoke the service.</span></span>  
  
 <span data-ttu-id="69723-106">建立 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端的基本步驟包含下列各項：</span><span class="sxs-lookup"><span data-stu-id="69723-106">The basic steps for creating a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client include the following:</span></span>  
  
1.  <span data-ttu-id="69723-107">編譯服務程式碼。</span><span class="sxs-lookup"><span data-stu-id="69723-107">Compile the service code.</span></span>  
  
2.  <span data-ttu-id="69723-108">產生 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端 Proxy。</span><span class="sxs-lookup"><span data-stu-id="69723-108">Generate the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client proxy.</span></span>  
  
3.  <span data-ttu-id="69723-109">具現化 WCF 用戶端 Proxy。</span><span class="sxs-lookup"><span data-stu-id="69723-109">Instantiate the WCF client proxy.</span></span>  
  
 <span data-ttu-id="69723-110">可以手動產生 WCF 用戶端 proxy，利用 Service Model Metadata Utility Tool (SvcUtil.exe) 的詳細資訊，請參閱[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="69723-110">The WCF client proxy can be generated manually by using the Service Model Metadata Utility Tool (SvcUtil.exe) for more information see, [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="69723-111">在 Visual Studio 中，也可以使用 [加入服務參考] 功能產生 WCF 用戶端 Proxy。</span><span class="sxs-lookup"><span data-stu-id="69723-111">The WCF client proxy can also be generated within Visual Studio using the Add Service Reference  feature.</span></span> <span data-ttu-id="69723-112">若要使用上述任一方法來產生 WCF 用戶端 Proxy，服務都必須正在執行中。</span><span class="sxs-lookup"><span data-stu-id="69723-112">To generate the WCF client proxy using either method the service must be running.</span></span> <span data-ttu-id="69723-113">如果服務是自我裝載的，則必須執行主機。</span><span class="sxs-lookup"><span data-stu-id="69723-113">If the service is self-hosted you must run the host.</span></span> <span data-ttu-id="69723-114">如果服務裝載於 IIS/WAS，就不需要執行任何其他動作。</span><span class="sxs-lookup"><span data-stu-id="69723-114">If the service is hosted in IIS/WAS you do not need to do anything else.</span></span>  
  
## <a name="servicemodel-metadata-utility-tool"></a><span data-ttu-id="69723-115">ServiceModel 中繼資料公用程式工具</span><span class="sxs-lookup"><span data-stu-id="69723-115">ServiceModel Metadata Utility Tool</span></span>  
 <span data-ttu-id="69723-116">[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)是用於從中繼資料產生程式碼的命令列工具。</span><span class="sxs-lookup"><span data-stu-id="69723-116">The [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) is a command-line tool for generating code from metadata.</span></span> <span data-ttu-id="69723-117">下列用法是基本 Svcutil.exe 命令的範例。</span><span class="sxs-lookup"><span data-stu-id="69723-117">The following use is an example of a basic Svcutil.exe command.</span></span>  
  
```  
Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
```  
  
 <span data-ttu-id="69723-118">或者，您也可以在檔案系統上，搭配 Web 服務描述語言 (WSDL) 和 XML 結構描述定義語言 (XSD) 檔案來使用 Svcutil.exe。</span><span class="sxs-lookup"><span data-stu-id="69723-118">Alternatively, you can use Svcutil.exe with Web Services Description Language (WSDL) and XML Schema definition language (XSD) files on the file system.</span></span>  
  
```  
Svcutil.exe <list of WSDL and XSD files on file system>  
```  
  
 <span data-ttu-id="69723-119">如此會產生包含 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端程式碼的程式碼檔案，其中的用戶端程式碼可讓用戶端應用程式使用，藉此叫用服務。</span><span class="sxs-lookup"><span data-stu-id="69723-119">The result is a code file that contains [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client code that the client application can use to invoke the service.</span></span>  
  
 <span data-ttu-id="69723-120">您也可以使用工具來產生組態檔。</span><span class="sxs-lookup"><span data-stu-id="69723-120">You can also use the tool to generate configuration files.</span></span>  
  
```  
Svcutil.exe <file1 [,file2]>  
```  
  
 <span data-ttu-id="69723-121">如果僅提供一個檔案名稱，這就會是輸出檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="69723-121">If only one file name is given, that is the name of the output file.</span></span> <span data-ttu-id="69723-122">如果提供兩個檔案名稱，則第一個檔案為輸入組態檔，其內容會與產生的組態合併，並寫入至第二個檔案。</span><span class="sxs-lookup"><span data-stu-id="69723-122">If two file names are given, then the first file is an input configuration file whose contents are merged with the generated configuration and written out into the second file.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="69723-123">組態，請參閱[設定服務的繫結](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="69723-123"> configuration, see [Configuring Bindings for Services](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="69723-124">未受保護的中繼資料要求和未受保護的網路要求一樣，都會構成某些風險：如果您無法確定正在進行通訊的端點是否為名符其實的端點，那麼您所擷取的資料很可能是來自於惡意服務的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="69723-124">Unsecured metadata requests pose certain risks in the same way that any unsecured network request does: If you are not certain that the endpoint you are communicating with is who it says it is, the information you retrieve might be metadata from a malicious service.</span></span>  
  
## <a name="add-service-reference-in-visual-studio"></a><span data-ttu-id="69723-125">在 Visual Studio 中加入服務參考</span><span class="sxs-lookup"><span data-stu-id="69723-125">Add Service Reference in Visual Studio</span></span>  
 <span data-ttu-id="69723-126">服務正在執行中，以滑鼠右鍵按一下專案，將包含 WCF 用戶端 proxy，並且選取**加入服務參考**。</span><span class="sxs-lookup"><span data-stu-id="69723-126">With the service running, right click the project that will contain the WCF client proxy and select **Add Service Reference**.</span></span> <span data-ttu-id="69723-127">在**加入服務參考對話方塊**至您想要呼叫，並按一下 [服務 URL 中的型別**移**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="69723-127">In the **Add Service Reference Dialog** type in the URL to the service you want to call and click the **Go** button.</span></span> <span data-ttu-id="69723-128">對話將會顯示您所指定之位址上的可用服務清單。</span><span class="sxs-lookup"><span data-stu-id="69723-128">The dialog will display a list of services available at the address you specify.</span></span> <span data-ttu-id="69723-129">按兩下服務查看可用合約和作業中，指定產生的程式碼的命名空間，然後按一下**確定** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="69723-129">Double click the service to see the contracts and operations available, specify a namespace for the generated code and click the **OK** button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="69723-130">範例</span><span class="sxs-lookup"><span data-stu-id="69723-130">Example</span></span>  
 <span data-ttu-id="69723-131">下列程式碼範例會顯示對服務建立的服務合約。</span><span class="sxs-lookup"><span data-stu-id="69723-131">The following code example shows a service contract created for a service.</span></span>  
  
```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface ICalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    // Other methods are not shown here.
}
```
  
```vb
' Define a service contract.
<ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _
Public Interface ICalculator
    <OperationContract()>  _
    Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
    ' Other methods are not shown here.
End Interface
```
  
 <span data-ttu-id="69723-132">Visual Studio 中的 ServiceModel 中繼資料公用程式工具和 [加入服務參考] 會產生下列 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端類別。</span><span class="sxs-lookup"><span data-stu-id="69723-132">The ServiceModel Metadata utility tool and Add Service Reference in Visual Studio generates the following [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client class.</span></span> <span data-ttu-id="69723-133">該類別是繼承自一般 <xref:System.ServiceModel.ClientBase%601> 類別，而且會實作 `ICalculator` 介面。</span><span class="sxs-lookup"><span data-stu-id="69723-133">The class inherits from the generic <xref:System.ServiceModel.ClientBase%601> class and implements the `ICalculator` interface.</span></span> <span data-ttu-id="69723-134">這個工具也會產生 `ICalculator` 介面 (此處未顯示)。</span><span class="sxs-lookup"><span data-stu-id="69723-134">The tool also generates the `ICalculator` interface (not shown here).</span></span>  
  
```csharp
public partial class CalculatorClient : System.ServiceModel.ClientBase<ICalculator>, ICalculator
{
    public CalculatorClient()
    {}

    public CalculatorClient(string endpointConfigurationName) :
            base(endpointConfigurationName)
    {}

    public CalculatorClient(string endpointConfigurationName, string remoteAddress) :
            base(endpointConfigurationName, remoteAddress)
    {}

    public CalculatorClient(string endpointConfigurationName,
        System.ServiceModel.EndpointAddress remoteAddress) :
            base(endpointConfigurationName, remoteAddress)
    {}

    public CalculatorClient(System.ServiceModel.Channels.Binding binding,
        System.ServiceModel.EndpointAddress remoteAddress) :
            base(binding, remoteAddress)
    {}

    public double Add(double n1, double n2)
    {
        return base.Channel.Add(n1, n2);
    }
}
```  
  
```vb  
Partial Public Class CalculatorClient
    Inherits System.ServiceModel.ClientBase(Of ICalculator)
    Implements ICalculator

    Public Sub New()
        MyBase.New
    End Sub

    Public Sub New(ByVal endpointConfigurationName As String)
        MyBase.New(endpointConfigurationName)
    End Sub

    Public Sub New(ByVal endpointConfigurationName As String, ByVal remoteAddress As String)
        MyBase.New(endpointConfigurationName, remoteAddress)
    End Sub

    Public Sub New(ByVal endpointConfigurationName As String,
        ByVal remoteAddress As System.ServiceModel.EndpointAddress)
        MyBase.New(endpointConfigurationName, remoteAddress)
    End Sub

    Public Sub New(ByVal binding As System.ServiceModel.Channels.Binding,
        ByVal remoteAddress As System.ServiceModel.EndpointAddress)
        MyBase.New(binding, remoteAddress)
    End Sub

    Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
        Implements ICalculator.Add
        Return MyBase.Channel.Add(n1, n2)
    End Function
End Class
```
  
## <a name="using-the-wcf-client"></a><span data-ttu-id="69723-135">使用 WCF 用戶端</span><span class="sxs-lookup"><span data-stu-id="69723-135">Using the WCF Client</span></span>  
 <span data-ttu-id="69723-136">若要使用 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端，請建立 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端的執行個體，然後呼叫其方法，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="69723-136">To use the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client, create an instance of the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client, and then call its methods, as shown in the following code.</span></span>  
  
```csharp
// Create a client object with the given client endpoint configuration.
CalculatorClient calcClient = new CalculatorClient("CalculatorEndpoint"));
// Call the Add service operation.
double value1 = 100.00D;
double value2 = 15.99D;
double result = calcClient.Add(value1, value2);
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
```
  
```vb
' Create a client object with the given client endpoint configuration.
Dim calcClient As CalculatorClient = _
New CalculatorClient("CalculatorEndpoint")

' Call the Add service operation.
Dim value1 As Double = 100.00D
Dim value2 As Double = 15.99D
Dim result As Double = calcClient.Add(value1, value2)
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)
```
  
## <a name="debugging-exceptions-thrown-by-a-client"></a><span data-ttu-id="69723-137">對用戶端擲回的例外狀況進行偵錯</span><span class="sxs-lookup"><span data-stu-id="69723-137">Debugging Exceptions Thrown by a Client</span></span>  
 <span data-ttu-id="69723-138">許多由 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端擲回的例外狀況是由服務上的例外狀況所造成。</span><span class="sxs-lookup"><span data-stu-id="69723-138">Many exceptions thrown by a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client are caused by an exception on the service.</span></span> <span data-ttu-id="69723-139">以下提供一些這類範例：</span><span class="sxs-lookup"><span data-stu-id="69723-139">Some examples of this are:</span></span>  
  
-   <span data-ttu-id="69723-140"><xref:System.Net.Sockets.SocketException>：現有的連接遭遠端主機強制關閉。</span><span class="sxs-lookup"><span data-stu-id="69723-140"><xref:System.Net.Sockets.SocketException>: An existing connection was forcibly closed by the remote host.</span></span>  
  
-   <span data-ttu-id="69723-141"><xref:System.ServiceModel.CommunicationException>：基礎連接意外關閉。</span><span class="sxs-lookup"><span data-stu-id="69723-141"><xref:System.ServiceModel.CommunicationException>: The underlying connection was closed unexpectedly.</span></span>  
  
-   <span data-ttu-id="69723-142"><xref:System.ServiceModel.CommunicationObjectAbortedException>：通訊端連接中止。</span><span class="sxs-lookup"><span data-stu-id="69723-142"><xref:System.ServiceModel.CommunicationObjectAbortedException>: The socket connection was aborted.</span></span> <span data-ttu-id="69723-143">這種情況可能是處理訊息時發生錯誤、遠端主機超過接收逾時時間，或基礎網路資源問題所造成。</span><span class="sxs-lookup"><span data-stu-id="69723-143">This could be caused by an error processing your message, a receive time-out being exceeded by the remote host, or an underlying network resource issue.</span></span>  
  
 <span data-ttu-id="69723-144">發生這類例外狀況時，最佳的解決方式是開啟服務端的追蹤功能，並且判斷該處發生哪種例外狀況。</span><span class="sxs-lookup"><span data-stu-id="69723-144">When these types of exceptions occur, the best way to solve the problem is to turn on tracing on the service side and determine what exception occurred there.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="69723-145">追蹤，請參閱[追蹤](../../../docs/framework/wcf/diagnostics/tracing/index.md)和[使用追蹤疑難排解您的應用程式](../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)。</span><span class="sxs-lookup"><span data-stu-id="69723-145"> tracing, see [Tracing](../../../docs/framework/wcf/diagnostics/tracing/index.md) and [Using Tracing to Troubleshoot Your Application](../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69723-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69723-146">See Also</span></span>  
 [<span data-ttu-id="69723-147">如何：建立用戶端</span><span class="sxs-lookup"><span data-stu-id="69723-147">How to: Create a Client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [<span data-ttu-id="69723-148">如何： 存取使用雙工合約的服務</span><span class="sxs-lookup"><span data-stu-id="69723-148">How to: Access Services with a Duplex Contract</span></span>](../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)  
 [<span data-ttu-id="69723-149">如何： 以非同步方式呼叫服務作業</span><span class="sxs-lookup"><span data-stu-id="69723-149">How to: Call Service Operations Asynchronously</span></span>](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)  
 [<span data-ttu-id="69723-150">如何： 存取服務使用單向和要求-回覆合約</span><span class="sxs-lookup"><span data-stu-id="69723-150">How to: Access Services with One-Way and Request-Reply Contracts</span></span>](../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)  
 [<span data-ttu-id="69723-151">如何： 存取 WSE 3.0 服務</span><span class="sxs-lookup"><span data-stu-id="69723-151">How to: Access a WSE 3.0 Service</span></span>](../../../docs/framework/wcf/feature-details/how-to-access-a-wse-3-0-service-with-a-wcf-client.md)  
 [<span data-ttu-id="69723-152">了解產生的用戶端程式碼</span><span class="sxs-lookup"><span data-stu-id="69723-152">Understanding Generated Client Code</span></span>](../../../docs/framework/wcf/feature-details/understanding-generated-client-code.md)  
 [<span data-ttu-id="69723-153">如何： 改善啟動時間的 WCF 用戶端應用程式使用 XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="69723-153">How to: Improve the Startup Time of WCF Client Applications using the XmlSerializer</span></span>](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)  
 [<span data-ttu-id="69723-154">指定用端執行階段行為</span><span class="sxs-lookup"><span data-stu-id="69723-154">Specifying Client Run-Time Behavior</span></span>](../../../docs/framework/wcf/specifying-client-run-time-behavior.md)  
 [<span data-ttu-id="69723-155">設定用戶端行為</span><span class="sxs-lookup"><span data-stu-id="69723-155">Configuring Client Behaviors</span></span>](../../../docs/framework/wcf/configuring-client-behaviors.md)

---
title: 使用者入門範例
description: 瞭解如何使用 WCF 來執行一般服務和一般用戶端。 這個範例是所有其他基本技術範例的基礎。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- basic samples [WCF], getting started
ms.assetid: 967a3d94-0261-49ff-b85a-20bb07f1af20
ms.openlocfilehash: b23be1b33f227154b916429c063ec4106229bb3c
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246229"
---
# <a name="getting-started-sample"></a><span data-ttu-id="bbf5d-104">使用者入門範例</span><span class="sxs-lookup"><span data-stu-id="bbf5d-104">Getting Started Sample</span></span>

<span data-ttu-id="bbf5d-105">消費者入門範例示範如何使用 Windows Communication Foundation （WCF）來執行一般服務和一般用戶端。</span><span class="sxs-lookup"><span data-stu-id="bbf5d-105">The Getting Started sample demonstrates how to implement a typical service and a typical client using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="bbf5d-106">這個範例是所有其他基本技術範例的基礎。</span><span class="sxs-lookup"><span data-stu-id="bbf5d-106">This sample is the basis for all other basic technology samples.</span></span>

> [!NOTE]
> <span data-ttu-id="bbf5d-107">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="bbf5d-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bbf5d-108">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="bbf5d-108">The samples may already be installed on your computer.</span></span> <span data-ttu-id="bbf5d-109">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="bbf5d-109">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="bbf5d-110">如果此目錄不存在，請移至[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）範例](https://www.microsoft.com/download/details.aspx?id=21459)，以下載所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="bbf5d-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bbf5d-111">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="bbf5d-111">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\GettingStarted\GettingStarted`

<span data-ttu-id="bbf5d-112">此服務會描述其在服務合約中 (即服務公開為中繼資料的服務合約) 所執行的作業。</span><span class="sxs-lookup"><span data-stu-id="bbf5d-112">The service describes the operations it performs in a service contract that it exposes publicly as metadata.</span></span> <span data-ttu-id="bbf5d-113">此服務也包含會實作這些作業的程式碼。</span><span class="sxs-lookup"><span data-stu-id="bbf5d-113">The service also contains the code to implement the operations.</span></span>

<span data-ttu-id="bbf5d-114">用戶端包含服務合約的定義，以及用來存取服務的 Proxy 類別。</span><span class="sxs-lookup"><span data-stu-id="bbf5d-114">The client contains a definition of the service contract and a proxy class for accessing the service.</span></span> <span data-ttu-id="bbf5d-115">使用[System.servicemodel 中繼資料公用程式工具（Svcutil.exe）](../servicemodel-metadata-utility-tool-svcutil-exe.md)從服務中繼資料產生 proxy 程式碼。</span><span class="sxs-lookup"><span data-stu-id="bbf5d-115">The proxy code is generated from the service metadata using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>

<span data-ttu-id="bbf5d-116">在 Windows Vista 上，服務裝載于 Windows 啟用服務（WAS）中。</span><span class="sxs-lookup"><span data-stu-id="bbf5d-116">On Windows Vista, the service is hosted in the Windows Activation Service (WAS).</span></span> <span data-ttu-id="bbf5d-117">在 Windows XP 和 Windows Server 2003 上，它是由 Internet Information Services （IIS）和 ASP.NET 所主控。</span><span class="sxs-lookup"><span data-stu-id="bbf5d-117">On Windows XP and Windows Server 2003, it is hosted by Internet Information Services (IIS) and ASP.NET.</span></span> <span data-ttu-id="bbf5d-118">使用 IIS 或 WAS 裝載服務，便可以讓服務在第一次存取時就自動啟動。</span><span class="sxs-lookup"><span data-stu-id="bbf5d-118">Hosting a service in IIS or WAS allows the service to be activated automatically when it is accessed for the first time.</span></span>

> [!NOTE]
> <span data-ttu-id="bbf5d-119">如果您想要開始使用在主控台應用程式（而不是 IIS）中裝載服務的範例，請參閱[自我裝載](self-host.md)範例。</span><span class="sxs-lookup"><span data-stu-id="bbf5d-119">If you would prefer to get started with a sample that hosts the service in a console application instead of IIS, see the [Self-Host](self-host.md) sample.</span></span>

<span data-ttu-id="bbf5d-120">服務與用戶端會在組態檔設定中指定存取詳細資訊，而這些設定可提供部署期間的彈性。</span><span class="sxs-lookup"><span data-stu-id="bbf5d-120">The service and client specify access details in configuration file settings, which provide flexibility at the time of deployment.</span></span> <span data-ttu-id="bbf5d-121">其中包含指定位址、繫結與合約的端點定義。</span><span class="sxs-lookup"><span data-stu-id="bbf5d-121">This includes an endpoint definition that specifies an address, binding, and contract.</span></span> <span data-ttu-id="bbf5d-122">繫結會指定如何存取服務的傳輸與安全性詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="bbf5d-122">The binding specifies transport and security details for how the service is to be accessed.</span></span>

<span data-ttu-id="bbf5d-123">服務會將執行階段行為設定成發行其中繼資料。</span><span class="sxs-lookup"><span data-stu-id="bbf5d-123">The service configures a run-time behavior to publish its metadata.</span></span>

<span data-ttu-id="bbf5d-124">服務會實作定義要求-回覆通訊模式的合約。</span><span class="sxs-lookup"><span data-stu-id="bbf5d-124">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="bbf5d-125">合約是由 `ICalculator` 介面所定義，這個介面會公開數學運算作業 (加、減、乘、除)。</span><span class="sxs-lookup"><span data-stu-id="bbf5d-125">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="bbf5d-126">用戶端會對指定的數學運算作業提出要求，服務則會以結果回覆。</span><span class="sxs-lookup"><span data-stu-id="bbf5d-126">The client makes requests to a given math operation and the service replies with the result.</span></span> <span data-ttu-id="bbf5d-127">此服務會實作 `ICalculator` 合約，如下列程式碼中所定義。</span><span class="sxs-lookup"><span data-stu-id="bbf5d-127">The service implements an `ICalculator` contract that is defined in the following code.</span></span>

```vb
' Define a service contract.
    <ServiceContract(Namespace:="http://Microsoft.Samples.GettingStarted")>
     Public Interface ICalculator
        <OperationContract()>
        Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()>
        Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()>
        Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()>
        Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double
    End Interface
```

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface ICalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    [OperationContract]
    double Subtract(double n1, double n2);
    [OperationContract]
    double Multiply(double n1, double n2);
    [OperationContract]
    double Divide(double n1, double n2);
}
```

<span data-ttu-id="bbf5d-128">服務實作會計算並傳回適當的結果，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="bbf5d-128">The service implementation calculates and returns the appropriate result, as shown in the following example code.</span></span>

```vb
' Service class which implements the service contract.
Public Class CalculatorService
Implements ICalculator
Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Add
Return n1 + n2
End Function

Public Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Subtract
Return n1 - n2
End Function

Public Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Multiply
Return n1 * n2
End Function

Public Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Divide
Return n1 / n2
End Function
End Class
```

```csharp
// Service class that implements the service contract.
public class CalculatorService : ICalculator
{
    public double Add(double n1, double n2)
    {
        return n1 + n2;
    }
    public double Subtract(double n1, double n2)
    {
        return n1 - n2;
    }
    public double Multiply(double n1, double n2)
    {
        return n1 * n2;
    }
    public double Divide(double n1, double n2)
    {
        return n1 / n2;
    }
}
```

<span data-ttu-id="bbf5d-129">此服務會公開 (Expose) 單一的端點來與已使用組態檔 (Web.config) 定義之服務進行通訊，如下列範例組態所示。</span><span class="sxs-lookup"><span data-stu-id="bbf5d-129">The service exposes an endpoint for communicating with the service, defined using a configuration file (Web.config), as shown in the following sample configuration.</span></span>

```xaml
<services>
    <service
        name="Microsoft.ServiceModel.Samples.CalculatorService"
        behaviorConfiguration="CalculatorServiceBehavior">
        <!-- ICalculator is exposed at the base address provided by
         host: http://localhost/servicemodelsamples/service.svc.  -->
       <endpoint address=""
              binding="wsHttpBinding"
              contract="Microsoft.ServiceModel.Samples.ICalculator" />
       ...
    </service>
</services>
```

<span data-ttu-id="bbf5d-130">服務會公開位在 IIS 或 WAS 主機提供之基底位址上的端點。</span><span class="sxs-lookup"><span data-stu-id="bbf5d-130">The service exposes the endpoint at the base address provided by the IIS or WAS host.</span></span> <span data-ttu-id="bbf5d-131">繫結會設定為標準 <xref:System.ServiceModel.WSHttpBinding>，此繫結會提供用於定址和安全性的 HTTP 通訊與標準 Web 服務通訊協定。</span><span class="sxs-lookup"><span data-stu-id="bbf5d-131">The binding is configured with a standard <xref:System.ServiceModel.WSHttpBinding>, which provides HTTP communication and standard Web service protocols for addressing and security.</span></span> <span data-ttu-id="bbf5d-132">此合約是服務實作的 `ICalculator`。</span><span class="sxs-lookup"><span data-stu-id="bbf5d-132">The contract is the `ICalculator` implemented by the service.</span></span>

<span data-ttu-id="bbf5d-133">如已設定，服務可 `http://localhost/servicemodelsamples/service.svc` 由同一部電腦上的用戶端存取。</span><span class="sxs-lookup"><span data-stu-id="bbf5d-133">As configured, the service can be accessed at `http://localhost/servicemodelsamples/service.svc` by a client on the same computer.</span></span> <span data-ttu-id="bbf5d-134">為了讓遠端電腦上的用戶端存取服務，這時必須指定完整網域名稱，而不要指定 localhost。</span><span class="sxs-lookup"><span data-stu-id="bbf5d-134">For clients on remote computers to access the service, a fully-qualified domain name must be specified instead of localhost.</span></span>

<span data-ttu-id="bbf5d-135">根據預設，此架構不會公開任何中繼資料。</span><span class="sxs-lookup"><span data-stu-id="bbf5d-135">The framework does not expose metadata by default.</span></span> <span data-ttu-id="bbf5d-136">因此，服務會開啟 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 並公開中的中繼資料交換（MEX）端點 `http://localhost/servicemodelsamples/service.svc/mex` 。</span><span class="sxs-lookup"><span data-stu-id="bbf5d-136">As such, the service turns on the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> and exposes a metadata exchange (MEX) endpoint at `http://localhost/servicemodelsamples/service.svc/mex`.</span></span> <span data-ttu-id="bbf5d-137">下列組態會示範這個作業。</span><span class="sxs-lookup"><span data-stu-id="bbf5d-137">The following configuration demonstrates this.</span></span>

```xaml
<system.serviceModel>
  <services>
    <service
        name="Microsoft.ServiceModel.Samples.CalculatorService"
        behaviorConfiguration="CalculatorServiceBehavior">
      ...
      <!-- the mex endpoint is exposed at
       http://localhost/servicemodelsamples/service.svc/mex -->
      <endpoint address="mex"
                binding="mexHttpBinding"
                contract="IMetadataExchange" />
    </service>
  </services>

  <!--For debugging purposes set the includeExceptionDetailInFaults
   attribute to true-->
  <behaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior">
        <serviceMetadata httpGetEnabled="True"/>
        <serviceDebug includeExceptionDetailInFaults="False" />
      </behavior>
    </serviceBehaviors>
  </behaviors>
</system.serviceModel>
```

<span data-ttu-id="bbf5d-138">用戶端會使用由[System.servicemodel 中繼資料公用程式工具（Svcutil.exe）](../servicemodel-metadata-utility-tool-svcutil-exe.md)所產生的用戶端類別，透過指定的合約型別進行通訊。</span><span class="sxs-lookup"><span data-stu-id="bbf5d-138">The client communicates using a given contract type by using a client class that is generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="bbf5d-139">這個產生的用戶端會包含在 generatedClient.cs 或 generatedClient.vb 檔中。</span><span class="sxs-lookup"><span data-stu-id="bbf5d-139">This generated client is contained in the file generatedClient.cs or generatedClient.vb.</span></span> <span data-ttu-id="bbf5d-140">這個公用程式會擷取指定服務的中繼資料，然後產生用戶端應用程式透過指定合約型別來進行通訊的用戶端。</span><span class="sxs-lookup"><span data-stu-id="bbf5d-140">This utility retrieves metadata for a given service and generates a client for use by the client application to communicate using a given contract type.</span></span> <span data-ttu-id="bbf5d-141">裝載的服務必須可用來產生用戶端程式碼，因為該服務將被用來擷取更新的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="bbf5d-141">The hosted service must be available to generate the client code, because the service is used to retrieve the updated metadata.</span></span>

 <span data-ttu-id="bbf5d-142">從用戶端目錄中的 SDK 命令提示字元執行下列命令，以產生具型別的 Proxy：</span><span class="sxs-lookup"><span data-stu-id="bbf5d-142">Run the following command from the SDK command prompt in the client directory to generate the typed proxy:</span></span>

```console
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs
```

<span data-ttu-id="bbf5d-143">若要在 Visual Basic 中產生用戶端，請在 SDK 命令提示字元輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="bbf5d-143">To generate client in Visual Basic type the following from the SDK command prompt:</span></span>

`Svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb`

<span data-ttu-id="bbf5d-144">藉由使用產生的用戶端，用戶端便可以設定適當的位址與繫結來存取指定服務端點。</span><span class="sxs-lookup"><span data-stu-id="bbf5d-144">By using the generated client, the client can access a given service endpoint by configuring the appropriate address and binding.</span></span> <span data-ttu-id="bbf5d-145">就跟服務一樣，用戶端會使用組態檔 (App.config) 來指定其想要進行通訊的端點。</span><span class="sxs-lookup"><span data-stu-id="bbf5d-145">Like the service, the client uses a configuration file (App.config) to specify the endpoint with which it wants to communicate.</span></span> <span data-ttu-id="bbf5d-146">用戶端端點組態是由服務端點的絕對位址、繫結和合約所組成，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="bbf5d-146">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract, as shown in the following example.</span></span>

```xaml
<client>
     <endpoint
         address="http://localhost/servicemodelsamples/service.svc"
         binding="wsHttpBinding"
         contract=" Microsoft.ServiceModel.Samples.ICalculator" />
</client>
```

<span data-ttu-id="bbf5d-147">用戶端實作會產生用戶端，並且使用具型別介面開始與服務進行通訊，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="bbf5d-147">The client implementation instantiates the client and uses the typed interface to begin communicating with the service, as shown in the following example code.</span></span>

```vb
' Create a client
Dim client As New CalculatorClient()

' Call the Add service operation.
            Dim value1 = 100.0R
            Dim value2 = 15.99R
            Dim result = client.Add(value1, value2)
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)

' Call the Subtract service operation.
value1 = 145.00R
value2 = 76.54R
result = client.Subtract(value1, value2)
Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result)

' Call the Multiply service operation.
value1 = 9.00R
value2 = 81.25R
result = client.Multiply(value1, value2)
Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result)

' Call the Divide service operation.
value1 = 22.00R
value2 = 7.00R
result = client.Divide(value1, value2)
Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result)

'Closing the client gracefully closes the connection and cleans up resources
```

```csharp
// Create a client.
CalculatorClient client = new CalculatorClient();

// Call the Add service operation.
double value1 = 100.00D;
double value2 = 15.99D;
double result = client.Add(value1, value2);
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

// Call the Subtract service operation.
value1 = 145.00D;
value2 = 76.54D;
result = client.Subtract(value1, value2);
Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);

// Call the Multiply service operation.
value1 = 9.00D;
value2 = 81.25D;
result = client.Multiply(value1, value2);
Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);

// Call the Divide service operation.
value1 = 22.00D;
value2 = 7.00D;
result = client.Divide(value1, value2);
Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);

//Closing the client releases all communication resources.
client.Close();
```

<span data-ttu-id="bbf5d-148">當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="bbf5d-148">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="bbf5d-149">在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="bbf5d-149">Press ENTER in the client window to shut down the client.</span></span>

```output
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

<span data-ttu-id="bbf5d-150">使用者入門範例會示範建立服務與用戶端的標準方式。</span><span class="sxs-lookup"><span data-stu-id="bbf5d-150">The Getting Started sample shows the standard way to create a service and client.</span></span> <span data-ttu-id="bbf5d-151">此範例上的另一個[基本](basic-sample.md)組建，示範特定的產品功能。</span><span class="sxs-lookup"><span data-stu-id="bbf5d-151">The other [Basic](basic-sample.md) build on this sample to demonstrate specific product features.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="bbf5d-152">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="bbf5d-152">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="bbf5d-153">請確定您已[針對 Windows Communication Foundation 範例執行一次安裝程式](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="bbf5d-153">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="bbf5d-154">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="bbf5d-154">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="bbf5d-155">若要在單一或跨電腦設定中執行範例，請遵循執行[Windows Communication Foundation 範例](running-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="bbf5d-155">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bbf5d-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bbf5d-156">See also</span></span>

- [<span data-ttu-id="bbf5d-157">如何：於受管理的應用程式中裝載 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="bbf5d-157">How to: Host a WCF Service in a Managed Application</span></span>](../how-to-host-a-wcf-service-in-a-managed-application.md)
- [<span data-ttu-id="bbf5d-158">How to: Host a WCF Service in IIS</span><span class="sxs-lookup"><span data-stu-id="bbf5d-158">How to: Host a WCF Service in IIS</span></span>](../feature-details/how-to-host-a-wcf-service-in-iis.md)

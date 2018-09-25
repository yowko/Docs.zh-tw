---
title: Net.TCP Port Sharing 範例
ms.date: 03/30/2017
ms.assetid: 03da5959-0574-4e91-8a53-05854b6c55dc
ms.openlocfilehash: db4cd5be73e3c170f2feaa1e76f275eb7d9cd226
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47089733"
---
# <a name="nettcp-port-sharing-sample"></a><span data-ttu-id="4f681-102">Net.TCP Port Sharing 範例</span><span class="sxs-lookup"><span data-stu-id="4f681-102">Net.TCP Port Sharing Sample</span></span>
<span data-ttu-id="4f681-103">TCP/IP 通訊協定使用一個 16 位元的數字 (稱為連接埠) 來區分在同一部電腦上執行的多個網路應用程式連線。</span><span class="sxs-lookup"><span data-stu-id="4f681-103">The TCP/IP protocol uses a 16-bit number, called a port, to differentiate connections to multiple network applications running on the same machine.</span></span> <span data-ttu-id="4f681-104">如果應用程式正在接聽某個連接埠，則該連接埠的所有 TCP 流量就會流向該應用程式。</span><span class="sxs-lookup"><span data-stu-id="4f681-104">If an application is listening on a port, then all TCP traffic for that port goes to that application.</span></span> <span data-ttu-id="4f681-105">其他應用程式將無法同時接聽該連接埠。</span><span class="sxs-lookup"><span data-stu-id="4f681-105">Other applications cannot listen on that port at the same time.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4f681-106">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="4f681-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4f681-107">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="4f681-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4f681-108">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="4f681-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4f681-109">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="4f681-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\TCP\PortSharing`  
  
 <span data-ttu-id="4f681-110">許多通訊協定都使用一個標準或預設的連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="4f681-110">Many protocols have a standard or default port number that they use.</span></span> <span data-ttu-id="4f681-111">例如，HTTP 通訊協定通常使用 TCP 通訊埠 80。</span><span class="sxs-lookup"><span data-stu-id="4f681-111">For example, the HTTP protocol typically uses TCP port 80.</span></span> <span data-ttu-id="4f681-112">Internet Information Services (IIS) 有一個可在多個 HTTP 應用程式之間共用通訊埠的接聽項。</span><span class="sxs-lookup"><span data-stu-id="4f681-112">Internet Information Services (IIS) has a listener to share a port between multiple HTTP applications.</span></span> <span data-ttu-id="4f681-113">IIS 會直接接聽連接埠，並依照訊息資料流內的資訊將訊息轉送至適當的應用程式。</span><span class="sxs-lookup"><span data-stu-id="4f681-113">IIS listens on the port directly and forwards messages to the appropriate application based on information inside the message stream.</span></span> <span data-ttu-id="4f681-114">這樣一來，多個 HTTP 應用程式就可以使用相同的連接埠號碼，而不用競相保留該連接埠以接收訊息。</span><span class="sxs-lookup"><span data-stu-id="4f681-114">This allows multiple HTTP applications to use the same port number without having to compete to reserve the port for receiving messages.</span></span>  
  
 <span data-ttu-id="4f681-115">NetTcp Port Sharing 是一種 Windows Communication Foundation (WCF) 功能，同樣可讓多個網路應用程式共用單一連接埠。</span><span class="sxs-lookup"><span data-stu-id="4f681-115">NetTcp Port Sharing is a Windows Communication Foundation (WCF)feature that similarly allows multiple network applications to share a single port.</span></span> <span data-ttu-id="4f681-116">NetTcp Port Sharing Service 會透過 net.tcp 通訊協定來接受連線，並依據該連線的目的地位址來轉送訊息。</span><span class="sxs-lookup"><span data-stu-id="4f681-116">The NetTcp Port Sharing Service accepts connections using the net.tcp protocol and forwards messages based on their destination address.</span></span>  
  
 <span data-ttu-id="4f681-117">NetTcp Port Sharing Service 預設並未啟用。</span><span class="sxs-lookup"><span data-stu-id="4f681-117">The NetTcp Port Sharing Service is not enabled by default.</span></span> <span data-ttu-id="4f681-118">在執行此範例之前，您必須手動啟用服務。</span><span class="sxs-lookup"><span data-stu-id="4f681-118">Before running this sample, you must manually enable the service.</span></span> <span data-ttu-id="4f681-119">如需詳細資訊，請參閱 <<c0> [ 如何： 啟用 Net.TCP Port Sharing Service](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md)。</span><span class="sxs-lookup"><span data-stu-id="4f681-119">For more information, see [How to: Enable the Net.TCP Port Sharing Service](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md).</span></span> <span data-ttu-id="4f681-120">如果服務已停用，則當啟動伺服器應用程式時，會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4f681-120">If the service is disabled, an exception is thrown when the server application is started.</span></span>  
  
```  
Unhandled Exception: System.ServiceModel.CommunicationException: The TransportManager failed to listen on the supplied URI using the NetTcpPortSharing service: failed to start the service because it is disabled. An administrator can enable it by running 'sc.exe config NetTcpPortSharing start= demand'.. ---> System.InvalidOperationException: Cannot start service NetTcpPortSharing on computer '.'. ---> System.ComponentModel.Win32Exception: The service cannot be started, either because it is disabled or because it has no enabled devices associated with it  
```  
  
 <span data-ttu-id="4f681-121">您可以設定 <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> 繫結上的 <xref:System.ServiceModel.NetTcpBinding> 屬性，或是設定 <xref:System.ServiceModel.Channels.TcpTransportBindingElement> 繫結項目，來啟用伺服器上的連接埠共用。</span><span class="sxs-lookup"><span data-stu-id="4f681-121">Port sharing is enabled on the server by setting the <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property of the <xref:System.ServiceModel.NetTcpBinding> binding or the <xref:System.ServiceModel.Channels.TcpTransportBindingElement> binding element.</span></span> <span data-ttu-id="4f681-122">用戶端不需要知道連接埠共用該如何設定才可運用在伺服器上。</span><span class="sxs-lookup"><span data-stu-id="4f681-122">The client does not have to know how port sharing has been configured to use it on the server.</span></span>  
  
## <a name="enabling-port-sharing"></a><span data-ttu-id="4f681-123">啟用連接埠共用</span><span class="sxs-lookup"><span data-stu-id="4f681-123">Enabling Port Sharing</span></span>  
 <span data-ttu-id="4f681-124">下列程式碼範例會示範在伺服器上啟用連接埠共用的方式。</span><span class="sxs-lookup"><span data-stu-id="4f681-124">The following code demonstrates enabling port sharing on the server.</span></span> <span data-ttu-id="4f681-125">一開始它會在包含隨機 URI 路徑的固定連接埠上啟動 `ICalculator` 服務的執行個體。</span><span class="sxs-lookup"><span data-stu-id="4f681-125">It starts an instance of the `ICalculator` service on a fixed port with a random URI path.</span></span> <span data-ttu-id="4f681-126">即使兩個服務可以共用相同的連接埠，它們的整體端點位址仍舊必須維持唯一，以便 NetTcp Port Sharing Service 可以將訊息路由至正確的應用程式中。</span><span class="sxs-lookup"><span data-stu-id="4f681-126">Even though two services can share the same port, their overall endpoint addresses still must be unique so that the NetTcp Port Sharing Service can route messages to the correct application.</span></span>  

```csharp
// Configure a binding with TCP port sharing enabled  
NetTcpBinding binding = new NetTcpBinding();  
binding.PortSharingEnabled = true;  
  
// Start a service on a fixed TCP port  
ServiceHost host = new ServiceHost(typeof(CalculatorService));  
ushort salt = (ushort)new Random().Next();  
string address =  
   String.Format("net.tcp://localhost:9000/calculator/{0}", salt);  
host.AddServiceEndpoint(typeof(ICalculator), binding, address);  
host.Open();  
```

 <span data-ttu-id="4f681-127">啟用了連接埠共用後，您可以多次執行服務，而不用擔心會碰到連接埠號碼衝突情況。</span><span class="sxs-lookup"><span data-stu-id="4f681-127">With port sharing enabled, you can run the service multiple times without having a conflict over the port number.</span></span> <span data-ttu-id="4f681-128">如果您變更程式碼來停用連接埠共用，啟動兩組相同的服務會導致第二個服務失敗並傳回 <xref:System.ServiceModel.AddressAlreadyInUseException>。</span><span class="sxs-lookup"><span data-stu-id="4f681-128">If you change the code to disable port sharing, starting up two copies of the service results in the second failing with an <xref:System.ServiceModel.AddressAlreadyInUseException>.</span></span>  
  
```  
Unhandled Exception: System.ServiceModel.AddressAlreadyInUseException: There is already a listener on IP endpoint 0.0.0.0:9000.  Make sure that you are not trying to use this endpoint multiple times in your application and that there are no other applications listening on this endpoint. ---> System.Net.Sockets.SocketException: Only one usage of each socket address (protocol/network address/port) is normally permitted  
```  
  
## <a name="running-the-sample"></a><span data-ttu-id="4f681-129">執行範例</span><span class="sxs-lookup"><span data-stu-id="4f681-129">Running the Sample</span></span>  
 <span data-ttu-id="4f681-130">您可以使用測試用戶端，檢查訊息是否已正確路由至共用該連接埠的服務中。</span><span class="sxs-lookup"><span data-stu-id="4f681-130">You can use the test client to check that messages are correctly routed to services sharing the port.</span></span>  

```csharp
class client  
{  
   static void Main(string[] args)  
   {  
      Console.Write("Enter the service number to test: ");  
      ushort salt = ushort.Parse(Console.ReadLine());  
      string address = String.Format("net.tcp://localhost:9000/calculator/{0}", salt);  
      ChannelFactory<ICalculator> factory = new ChannelFactory<ICalculator>(new NetTcpBinding());  
      ICalculator proxy = factory.CreateChannel(new EndpointAddress(address));  
  
      // Call the Add service operation.  
      double value1 = 100.00D;  
      double value2 = 15.99D;  
      double result = proxy.Add(value1, value2);  
      Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
      // Call the Subtract service operation.  
      value1 = 145.00D;  
      value2 = 76.54D;  
      result = proxy.Subtract(value1, value2);  
      Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
      // Call the Multiply service operation.  
      value1 = 9.00D;  
      value2 = 81.25D;  
      result = proxy.Multiply(value1, value2);  
      Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
      // Call the Divide service operation.  
      value1 = 22.00D;  
      value2 = 7.00D;  
      result = proxy.Divide(value1, value2);  
      Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
  
      Console.WriteLine();  
      Console.WriteLine("Press <ENTER> to terminate client.");  
      Console.ReadLine();  
  
      factory.Close();  
   }  
}  
```

 <span data-ttu-id="4f681-131">每個服務的執行個體都會列出自己的唯一號碼與位址。</span><span class="sxs-lookup"><span data-stu-id="4f681-131">Each instance of the service prints out its unique number and address.</span></span> <span data-ttu-id="4f681-132">例如，當您執行 service.exe 時，可能會看到下列文字。</span><span class="sxs-lookup"><span data-stu-id="4f681-132">For instance, you may see the following text when you run service.exe.</span></span>  
  
```  
Service #4381 listening on net.tcp://localhost:9000/calculator/4381.  
Press <ENTER> to terminate service.  
```  
  
 <span data-ttu-id="4f681-133">輸入當您執行 client.exe 時，在此處看到的服務號碼。</span><span class="sxs-lookup"><span data-stu-id="4f681-133">Enter the service number you see here when you run client.exe.</span></span>  
  
```  
Enter the service number to test: 4381  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="4f681-134">您可以變更用戶所端使用的已產生位址，在跨電腦組態中執行此範例。</span><span class="sxs-lookup"><span data-stu-id="4f681-134">This sample can be run in a cross-machine configuration by changing the generated address that the client uses.</span></span> <span data-ttu-id="4f681-135">在 Client.cs 中，變更端點位址格式字串來符合服務的新位址。</span><span class="sxs-lookup"><span data-stu-id="4f681-135">In the Client.cs, change the endpoint address format string to match the new address of your service.</span></span> <span data-ttu-id="4f681-136">使用伺服器電腦的 IP 位址來取代任何的 "localhost" 參考。</span><span class="sxs-lookup"><span data-stu-id="4f681-136">Replace any references to "localhost" with the IP address of the server machine.</span></span> <span data-ttu-id="4f681-137">在執行此變更之後，您必須重新編譯範例。</span><span class="sxs-lookup"><span data-stu-id="4f681-137">You must recompile the sample after making this change.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4f681-138">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="4f681-138">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="4f681-139">使用下列命令安裝 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0。</span><span class="sxs-lookup"><span data-stu-id="4f681-139">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="4f681-140">請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="4f681-140">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="4f681-141">如先前在簡介一節所述，啟用 NetTcp Port Sharing Service。</span><span class="sxs-lookup"><span data-stu-id="4f681-141">Enable the NetTcp Port Sharing Service as previously described in the introduction section.</span></span>  
  
4.  <span data-ttu-id="4f681-142">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="4f681-142">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
5.  <span data-ttu-id="4f681-143">若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="4f681-143">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span> <span data-ttu-id="4f681-144">有關執行本範例的特定詳細資訊，已經包含在先前的「執行範例」一節中。</span><span class="sxs-lookup"><span data-stu-id="4f681-144">Specific details for running this sample are included previously in the Running the Sample section.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f681-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f681-145">See Also</span></span>

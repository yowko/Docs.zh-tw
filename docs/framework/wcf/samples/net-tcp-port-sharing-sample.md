---
title: Net.TCP Port Sharing 範例
ms.date: 03/30/2017
ms.assetid: 03da5959-0574-4e91-8a53-05854b6c55dc
ms.openlocfilehash: 62642daffb7e41fb4e023bdd18c221c9dcfd9f2f
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2019
ms.locfileid: "65876372"
---
# <a name="nettcp-port-sharing-sample"></a>Net.TCP Port Sharing 範例
TCP/IP 通訊協定使用一個 16 位元的數字 (稱為連接埠) 來區分在同一部電腦上執行的多個網路應用程式連線。 如果應用程式正在接聽某個連接埠，則該連接埠的所有 TCP 流量就會流向該應用程式。 其他應用程式將無法同時接聽該連接埠。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\TCP\PortSharing`  
  
 許多通訊協定都使用一個標準或預設的連接埠號碼。 例如，HTTP 通訊協定通常使用 TCP 通訊埠 80。 Internet Information Services (IIS) 有一個可在多個 HTTP 應用程式之間共用通訊埠的接聽項。 IIS 會直接接聽連接埠，並依照訊息資料流內的資訊將訊息轉送至適當的應用程式。 這樣一來，多個 HTTP 應用程式就可以使用相同的連接埠號碼，而不用競相保留該連接埠以接收訊息。  
  
 NetTcp Port Sharing 是一種 Windows Communication Foundation (WCF) 功能，同樣可讓多個網路應用程式共用單一連接埠。 NetTcp Port Sharing Service 會透過 net.tcp 通訊協定來接受連線，並依據該連線的目的地位址來轉送訊息。  
  
 NetTcp Port Sharing Service 預設並未啟用。 在執行此範例之前，您必須手動啟用服務。 如需詳細資訊，請參閱[如何：啟用 Net.TCP Port Sharing Service](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md)。 如果服務已停用，則當啟動伺服器應用程式時，會擲回例外狀況。  
  
```  
Unhandled Exception: System.ServiceModel.CommunicationException: The TransportManager failed to listen on the supplied URI using the NetTcpPortSharing service: failed to start the service because it is disabled. An administrator can enable it by running 'sc.exe config NetTcpPortSharing start= demand'.. ---> System.InvalidOperationException: Cannot start service NetTcpPortSharing on computer '.'. ---> System.ComponentModel.Win32Exception: The service cannot be started, either because it is disabled or because it has no enabled devices associated with it  
```  
  
 您可以設定 <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> 繫結上的 <xref:System.ServiceModel.NetTcpBinding> 屬性，或是設定 <xref:System.ServiceModel.Channels.TcpTransportBindingElement> 繫結項目，來啟用伺服器上的連接埠共用。 用戶端不需要知道連接埠共用該如何設定才可運用在伺服器上。  
  
## <a name="enabling-port-sharing"></a>啟用連接埠共用  
 下列程式碼範例會示範在伺服器上啟用連接埠共用的方式。 一開始它會在包含隨機 URI 路徑的固定連接埠上啟動 `ICalculator` 服務的執行個體。 即使兩個服務可以共用相同的連接埠，它們的整體端點位址仍舊必須維持唯一，以便 NetTcp Port Sharing Service 可以將訊息路由至正確的應用程式中。  

```csharp
// Configure a binding with TCP port sharing enabled  
NetTcpBinding binding = new NetTcpBinding();  
binding.PortSharingEnabled = true;  
  
// Start a service on a fixed TCP port  
ServiceHost host = new ServiceHost(typeof(CalculatorService));  
ushort salt = (ushort)new Random().Next();  
string address = $"net.tcp://localhost:9000/calculator/{salt}";
host.AddServiceEndpoint(typeof(ICalculator), binding, address);  
host.Open();  
```

 啟用了連接埠共用後，您可以多次執行服務，而不用擔心會碰到連接埠號碼衝突情況。 如果您變更程式碼來停用連接埠共用，啟動兩組相同的服務會導致第二個服務失敗並傳回 <xref:System.ServiceModel.AddressAlreadyInUseException>。  
  
```  
Unhandled Exception: System.ServiceModel.AddressAlreadyInUseException: There is already a listener on IP endpoint 0.0.0.0:9000.  Make sure that you are not trying to use this endpoint multiple times in your application and that there are no other applications listening on this endpoint. ---> System.Net.Sockets.SocketException: Only one usage of each socket address (protocol/network address/port) is normally permitted  
```  
  
## <a name="running-the-sample"></a>執行範例  
 您可以使用測試用戶端，檢查訊息是否已正確路由至共用該連接埠的服務中。  

```csharp
class client  
{  
   static void Main(string[] args)  
   {  
      Console.Write("Enter the service number to test: ");  
      ushort salt = ushort.Parse(Console.ReadLine());  
      string address = $"net.tcp://localhost:9000/calculator/{salt}";
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

 每個服務的執行個體都會列出自己的唯一號碼與位址。 例如，當您執行 service.exe 時，可能會看到下列文字。  
  
```  
Service #4381 listening on net.tcp://localhost:9000/calculator/4381.  
Press <ENTER> to terminate service.  
```  
  
 輸入當您執行 client.exe 時，在此處看到的服務號碼。  
  
```  
Enter the service number to test: 4381  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 您可以變更用戶所端使用的已產生位址，在跨電腦組態中執行此範例。 在 Client.cs 中，變更端點位址格式字串來符合服務的新位址。 使用伺服器電腦的 IP 位址來取代任何的 "localhost" 參考。 在執行此變更之後，您必須重新編譯範例。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 安裝 ASP.NET 4.0 使用下列命令。  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. 請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
3. 如先前在簡介一節所述，啟用 NetTcp Port Sharing Service。  
  
4. 若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
5. 若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。 有關執行本範例的特定詳細資訊，已經包含在先前的「執行範例」一節中。  

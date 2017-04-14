---
title: "使用 WCF 用戶端存取服務 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "用戶端 [WCF], 使用服務"
ms.assetid: d780af9f-73c5-42db-9e52-077a5e4de7fe
caps.latest.revision: 36
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 36
---
# 使用 WCF 用戶端存取服務
建立服務之後，下一個步驟就是建立 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端 Proxy。  用戶端應用程式會使用 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端 Proxy 與服務進行通訊。  用戶端應用程式通常會匯入服務的中繼資料，以產生可用來叫用服務的 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端程式碼。  
  
 建立 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端的基本步驟包含下列各項：  
  
1.  編譯服務程式碼。  
  
2.  產生 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端 Proxy。  
  
3.  具現化 WCF 用戶端 Proxy。  
  
 使用「服務模型中繼資料公用程式工具」\(SvcUtil.exe\) 可以手動產生 WCF 用戶端 Proxy。如需詳細資訊，請參閱 [ServiceModel 中繼資料公用程式工具 \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)。  在 Visual Studio 中，也可以使用 \[加入服務參考\] 功能產生 WCF 用戶端 Proxy。  若要使用上述任一方法來產生 WCF 用戶端 Proxy，服務都必須正在執行中。  如果服務是自我裝載的，則必須執行主機。  如果服務裝載於 IIS\/WAS，就不需要執行任何其他動作。  
  
## ServiceModel 中繼資料公用程式工具  
 [ServiceModel 中繼資料公用程式工具 \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) 是從中繼資料產生程式碼的命令列工具。  下列用法是基本 Svcutil.exe 命令的範例。  
  
```  
Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
```  
  
 或者，您也可以在檔案系統上，搭配 Web 服務描述語言 \(WSDL\) 和 XML 結構描述定義語言 \(XSD\) 檔案來使用 Svcutil.exe。  
  
```  
Svcutil.exe <list of WSDL and XSD files on file system>  
```  
  
 如此會產生包含 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端程式碼的程式碼檔案，其中的用戶端程式碼可讓用戶端應用程式使用，藉此叫用服務。  
  
 您也可以使用工具來產生組態檔。  
  
```  
Svcutil.exe <file1 [,file2]>  
```  
  
 如果僅提供一個檔案名稱，這就會是輸出檔的名稱。  如果提供兩個檔案名稱，則第一個檔案為輸入組態檔，其內容會與產生的組態合併，並寫入至第二個檔案。  [!INCLUDE[crabout](../../../includes/crabout-md.md)] 組態的詳細資訊，請參閱 [設定服務的繫結](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)。  
  
> [!IMPORTANT]
>  未受保護的中繼資料要求和未受保護的網路要求一樣，都會構成某些風險：如果您無法確定正在進行通訊的端點是否為名符其實的端點，那麼您所擷取的資料很可能是來自於惡意服務的中繼資料。  
  
## 在 Visual Studio 中加入服務參考  
 在服務執行的情況下，以滑鼠右鍵按一下要包含 WCF 用戶端 Proxy 的專案，並選取 \[**加入服務參考**\]。  在 \[**加入服務參考**\] 對話方塊中輸入您要呼叫之服務的 URL，並按一下 \[**移至**\] 按鈕。  對話將會顯示您所指定之位址上的可用服務清單。  按兩下服務查看可用的合約和作業，指定產生之程式碼的命名空間，然後按一下 \[**確定**\] 按鈕。  
  
## 範例  
 下列程式碼範例會顯示對服務建立的服務合約。  
  
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
<ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")> _  
Public Interface ICalculator  
    <OperationContract()>  _  
    Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double   
    ' Other methods are not shown here.  
End Interface   
```  
  
 Visual Studio 中的 ServiceModel 中繼資料公用程式工具和 \[加入服務參考\] 會產生下列 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端類別。  該類別是繼承自一般 <xref:System.ServiceModel.ClientBase%601> 類別，而且會實作 `ICalculator` 介面。  這個工具也會產生 `ICalculator` 介面 \(此處未顯示\)。  
  
```csharp  
public partial class CalculatorClient : System.ServiceModel.ClientBase<ICalculator>, ICalculator  
{  
    public CalculatorClient(){}  
  
    public CalculatorClient(string configurationName) :   
            base(configurationName)  
    {}  
  
    public CalculatorClient(System.ServiceModel.Binding binding) :   
            base(binding)  
    {}  
  
    public CalculatorClient(System.ServiceModel.EndpointAddress address,  
    System.ServiceModel.Binding binding) :   
            base(address, binding)  
    {}  
  
    public double Add(double n1, double n2)  
    {  
        return base.InnerChannel.Add(n1, n2);  
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
  
    Public Sub New(ByVal configurationName As String)  
        MyBase.New(configurationName)  
    End Sub  
  
    Public Sub New(ByVal binding As System.ServiceModel.Binding)  
        MyBase.New(binding)  
    End Sub  
  
    Public Sub New(ByVal address As _  
    System.ServiceModel.EndpointAddress, _  
    ByVal binding As System.ServiceModel.Binding)  
        MyBase.New(address, binding)  
    End Sub  
  
    Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As _  
    Double Implements ICalculator.Add  
        Return MyBase.InnerChannel.Add(n1, n2)  
    End Function   
End Class  
  
```  
  
## 使用 WCF 用戶端  
 若要使用 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端，請建立 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端的執行個體，然後呼叫其方法，如下列程式碼所示。  
  
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
  
## 對用戶端擲回的例外狀況進行偵錯  
 許多由 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端擲回的例外狀況是由服務上的例外狀況所造成。  以下提供一些這類範例：  
  
-   <xref:System.Net.Sockets.SocketException>：現有的連接遭遠端主機強制關閉。  
  
-   <xref:System.ServiceModel.CommunicationException>：基礎連接意外關閉。  
  
-   <xref:System.ServiceModel.CommunicationObjectAbortedException>：通訊端連接中止。  這種情況可能是處理訊息時發生錯誤、遠端主機超過接收逾時時間，或基礎網路資源問題所造成。  
  
 發生這類例外狀況時，最佳的解決方式是開啟服務端的追蹤功能，並且判斷該處發生哪種例外狀況。  [!INCLUDE[crabout](../../../includes/crabout-md.md)]追蹤的詳細資訊，請參閱 [追蹤](../../../docs/framework/wcf/diagnostics/tracing/index.md) 和 [使用追蹤來疑難排解應用程式](../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)。  
  
## 請參閱  
 [HOW TO：建立用戶端](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)   
 [HOW TO：使用雙工合約存取服務](../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)   
 [HOW TO：以非同步方式呼叫 WCF 服務作業](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)   
 [HOW TO：使用單向和要求\-回覆合約來存取服務](../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)   
 [HOW TO：存取 WSE 3.0 服務](../../../docs/framework/wcf/feature-details/how-to-access-a-wse-3-0-service-with-a-wcf-client.md)   
 [了解產生的用戶端程式碼](../../../docs/framework/wcf/feature-details/understanding-generated-client-code.md)   
 [HOW TO：使用 XmlSerializer 改善 WCF 用戶端應用程式的啟動時間](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)   
 [指定用戶端執行階段行為](../../../docs/framework/wcf/specifying-client-run-time-behavior.md)   
 [設定用戶端行為](../../../docs/framework/wcf/configuring-client-behaviors.md)
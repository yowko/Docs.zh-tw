---
title: 使用 WCF 用戶端存取服務
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], consuming services
ms.assetid: d780af9f-73c5-42db-9e52-077a5e4de7fe
ms.openlocfilehash: 6bf683cdd0a03a5d1dbc452c28e7b33911464f09
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59297248"
---
# <a name="accessing-services-using-a-wcf-client"></a>使用 WCF 用戶端存取服務

建立服務之後下, 一個步驟是建立 WCF 用戶端 proxy。 用戶端應用程式會使用 WCF 用戶端 proxy 與服務進行通訊。 用戶端應用程式通常會匯入服務的中繼資料來產生可用來叫用服務的 WCF 用戶端程式碼。

 建立 WCF 用戶端的基本步驟如下：

1. 編譯服務程式碼。

2. 產生 WCF 用戶端 proxy。

3. 具現化 WCF 用戶端 Proxy。

可以手動產生 WCF 用戶端 proxy，使用服務模型中繼資料公用程式工具 (SvcUtil.exe)，如需詳細資訊，請參閱[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)。 WCF 用戶端 proxy 也會產生 Visual Studio 內使用**加入服務參考**功能。 若要使用上述任一方法來產生 WCF 用戶端 Proxy，服務都必須正在執行中。 如果服務是自我裝載的，則必須執行主機。 如果服務裝載於 IIS/WAS，就不需要執行任何其他動作。

## <a name="servicemodel-metadata-utility-tool"></a>ServiceModel 中繼資料公用程式工具
 [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)是用於從中繼資料產生程式碼的命令列工具。 下列用法是基本 Svcutil.exe 命令的範例。

```
Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
```

 或者，您也可以在檔案系統上，搭配 Web 服務描述語言 (WSDL) 和 XML 結構描述定義語言 (XSD) 檔案來使用 Svcutil.exe。

```
Svcutil.exe <list of WSDL and XSD files on file system>
```

 結果是包含用戶端應用程式可用來叫用服務的 WCF 用戶端程式碼的程式碼檔案。

 您也可以使用工具來產生組態檔。

```
Svcutil.exe <file1 [,file2]>
```

 如果僅提供一個檔案名稱，這就會是輸出檔的名稱。 如果提供兩個檔案名稱，則第一個檔案為輸入組態檔，其內容會與產生的組態合併，並寫入至第二個檔案。 如需有關組態的詳細資訊，請參閱 <<c0> [ 服務的設定繫結](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)。

> [!IMPORTANT]
> 不安全的中繼資料要求的任何不安全的網路要求的相同方式來構成某些風險：如果您不確定您正在與通訊的端點是它會，您所擷取的資訊可能來自於惡意服務的中繼資料。

## <a name="add-service-reference-in-visual-studio"></a>在 Visual Studio 中加入服務參考

 服務正在執行中，以滑鼠右鍵按一下專案，將會包含 WCF 用戶端 proxy，並選取**新增** > **服務參考**。 在**加入服務參考對話方塊**，輸入您想要呼叫，然後按一下 [服務 URL**移**] 按鈕。 對話將會顯示您所指定之位址上的可用服務清單。 按兩下服務查看可用作業與合約，指定產生的程式碼的命名空間，然後按一下 [**確定**] 按鈕。

## <a name="example"></a>範例
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
<ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _
Public Interface ICalculator
    <OperationContract()>  _
    Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
    ' Other methods are not shown here.
End Interface
```

 ServiceModel 中繼資料公用程式工具和**加入服務參考**在 Visual Studio 會產生下列的 WCF 用戶端類別。 該類別是繼承自一般 <xref:System.ServiceModel.ClientBase%601> 類別，而且會實作 `ICalculator` 介面。 這個工具也會產生 `ICalculator` 介面 (此處未顯示)。

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

## <a name="using-the-wcf-client"></a>使用 WCF 用戶端
 若要使用 WCF 用戶端，建立 WCF 用戶端的執行個體，然後呼叫其方法，如下列程式碼所示。

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

## <a name="debugging-exceptions-thrown-by-a-client"></a>對用戶端擲回的例外狀況進行偵錯

許多由 WCF 用戶端擲回的例外狀況是由服務上的例外狀況造成的。 以下提供一些這類範例：

-   <xref:System.Net.Sockets.SocketException>：遠端主機已強制關閉現有的連接。

-   <xref:System.ServiceModel.CommunicationException>：基礎連接意外關閉。

-   <xref:System.ServiceModel.CommunicationObjectAbortedException>：通訊端連線已中止。 這種情況可能是處理訊息時發生錯誤、遠端主機超過接收逾時時間，或基礎網路資源問題所造成。

發生這類例外狀況時，最佳的解決方式是開啟服務端的追蹤功能，並且判斷該處發生哪種例外狀況。 如需有關追蹤的詳細資訊，請參閱 <<c0> [ 追蹤](../../../docs/framework/wcf/diagnostics/tracing/index.md)並[使用追蹤疑難排解您的應用程式](../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)。

## <a name="see-also"></a>另請參閱

- [如何：建立用戶端](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [如何：Access Services 搭配雙工合約](../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)
- [如何：以非同步方式呼叫服務作業](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)
- [如何：存取服務使用單向和要求-回覆合約](../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)
- [如何：存取 WSE 3.0 服務](../../../docs/framework/wcf/feature-details/how-to-access-a-wse-3-0-service-with-a-wcf-client.md)
- [了解產生的用戶端程式碼](../../../docs/framework/wcf/feature-details/understanding-generated-client-code.md)
- [如何：改善啟動時間的 WCF 用戶端應用程式的使用 XmlSerializer](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)
- [指定用端執行階段行為](../../../docs/framework/wcf/specifying-client-run-time-behavior.md)
- [設定用戶端行為](../../../docs/framework/wcf/configuring-client-behaviors.md)

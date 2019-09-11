---
title: 使用 WCF 用戶端存取服務
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], consuming services
ms.assetid: d780af9f-73c5-42db-9e52-077a5e4de7fe
ms.openlocfilehash: ae589e1c418b1cf13fe9f5b34648bdf7a2210eed
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855668"
---
# <a name="accessing-services-using-a-wcf-client"></a>使用 WCF 用戶端存取服務

建立服務之後，下一個步驟是建立 WCF 用戶端 proxy。 用戶端應用程式會使用 WCF 用戶端 proxy 與服務進行通訊。 用戶端應用程式通常會匯入服務的中繼資料，以產生可用來叫用服務的 WCF 用戶端程式代碼。

 建立 WCF 用戶端的基本步驟包括下列各項：

1. 編譯服務程式碼。

2. 產生 WCF 用戶端 proxy。

3. 具現化 WCF 用戶端 Proxy。

您可以使用服務模型中繼資料公用程式工具（SvcUtil）手動產生 WCF 用戶端 proxy。如需詳細資訊，請參閱[System.servicemodel 中繼資料公用程式工具（SvcUtil）](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)。 WCF 用戶端 proxy 也可以使用**加入服務參考**功能，在 Visual Studio 內產生。 若要使用上述任一方法來產生 WCF 用戶端 Proxy，服務都必須正在執行中。 如果服務是自我裝載的，則必須執行主機。 如果服務裝載於 IIS/WAS，就不需要執行任何其他動作。

## <a name="servicemodel-metadata-utility-tool"></a>ServiceModel 中繼資料公用程式工具
 [System.servicemodel 中繼資料公用程式工具（Svcutil）](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)是一種命令列工具，可用於從中繼資料產生程式碼。 下列用法是基本 Svcutil.exe 命令的範例。

```console
Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
```

 或者，您也可以在檔案系統上，搭配 Web 服務描述語言 (WSDL) 和 XML 結構描述定義語言 (XSD) 檔案來使用 Svcutil.exe。

```console
Svcutil.exe <list of WSDL and XSD files on file system>
```

 結果是程式碼檔案，其中包含用戶端應用程式可用來叫用服務的 WCF 用戶端程式代碼。

 您也可以使用工具來產生組態檔。

```console
Svcutil.exe <file1 [,file2]>
```

 如果僅提供一個檔案名稱，這就會是輸出檔的名稱。 如果提供兩個檔案名稱，則第一個檔案為輸入組態檔，其內容會與產生的組態合併，並寫入至第二個檔案。 如需設定的詳細資訊，請參閱設定[服務的](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)系結。

> [!IMPORTANT]
> 不安全的中繼資料要求會以任何不安全的網路要求的相同方式來造成某些風險：如果您不確定要與其通訊的端點是誰，則您所取得的資訊可能是來自惡意服務的中繼資料。

## <a name="add-service-reference-in-visual-studio"></a>在 Visual Studio 中加入服務參考

 在服務執行的情況下，以滑鼠右鍵按一下將包含 WCF 用戶端 proxy 的專案，然後選取 [**加入** > **服務參考**]。 在 [**加入服務參考] 對話方塊**中，輸入您要呼叫之服務的 URL，然後按一下 [**移至**] 按鈕。 對話將會顯示您所指定之位址上的可用服務清單。 按兩下服務查看可用的合約和作業，指定產生之程式碼的命名空間，然後按一下 [**確定]** 按鈕。

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

 在 Visual Studio 中的 System.servicemodel 中繼資料公用程式工具和**加入服務參考**會產生下列 WCF 用戶端類別。 該類別是繼承自一般 <xref:System.ServiceModel.ClientBase%601> 類別，而且會實作 `ICalculator` 介面。 這個工具也會產生 `ICalculator` 介面 (此處未顯示)。

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
 若要使用 WCF 用戶端，請建立 WCF 用戶端的實例，然後呼叫其方法，如下列程式碼所示。

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

WCF 用戶端擲出的許多例外狀況是由服務上的例外狀況所造成。 以下提供一些這類範例：

- <xref:System.Net.Sockets.SocketException>：遠端主機已強制關閉現有的連接。

- <xref:System.ServiceModel.CommunicationException>：基礎連接未預期地關閉。

- <xref:System.ServiceModel.CommunicationObjectAbortedException>：通訊端連接已中止。 這種情況可能是處理訊息時發生錯誤、遠端主機超過接收逾時時間，或基礎網路資源問題所造成。

發生這類例外狀況時，最佳的解決方式是開啟服務端的追蹤功能，並且判斷該處發生哪種例外狀況。 如需追蹤的詳細資訊，請參閱[追蹤](../../../docs/framework/wcf/diagnostics/tracing/index.md)和[使用追蹤來疑難排解您的應用程式](../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)。

## <a name="see-also"></a>另請參閱

- [如何：建立用戶端](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [如何：使用雙工合約存取服務](../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)
- [如何：以非同步方式呼叫服務作業](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)
- [如何：使用單向和要求-回復合約來存取服務](../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)
- [如何：存取 WSE 3.0 服務](../../../docs/framework/wcf/feature-details/how-to-access-a-wse-3-0-service-with-a-wcf-client.md)
- [了解產生的用戶端程式碼](../../../docs/framework/wcf/feature-details/understanding-generated-client-code.md)
- [如何：使用 XmlSerializer 改善 WCF 用戶端應用程式的啟動時間](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)
- [指定用端執行階段行為](../../../docs/framework/wcf/specifying-client-run-time-behavior.md)
- [設定用戶端行為](../../../docs/framework/wcf/configuring-client-behaviors.md)

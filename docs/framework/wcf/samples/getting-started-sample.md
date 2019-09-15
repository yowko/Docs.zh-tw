---
title: 使用者入門範例
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- basic samples [WCF], getting started
ms.assetid: 967a3d94-0261-49ff-b85a-20bb07f1af20
ms.openlocfilehash: 5f5418da63b2bc5fc9b20f5c262890b7a06ce5dd
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989915"
---
# <a name="getting-started-sample"></a>使用者入門範例

消費者入門範例示範如何使用 Windows Communication Foundation （WCF）來執行一般服務和一般用戶端。 這個範例是所有其他基本技術範例的基礎。

> [!NOTE]
> 此範例的安裝程序與建置指示位於本主題的結尾。

> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> 如果此目錄不存在, 請移至[.NET Framework 4 的 Windows Communication Foundation (wcf) 和 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780), 以下載所有 Windows Communication Foundation (wcf) [!INCLUDE[wf1](../../../../includes/wf1-md.md)]和範例。 此範例位於下列目錄。
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\GettingStarted\GettingStarted`

此服務會描述其在服務合約中 (即服務公開為中繼資料的服務合約) 所執行的作業。 此服務也包含會實作這些作業的程式碼。

用戶端包含服務合約的定義，以及用來存取服務的 Proxy 類別。 使用[System.servicemodel 中繼資料公用程式工具（Svcutil）](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)，從服務中繼資料產生 proxy 程式碼。

在 [!INCLUDE[wv](../../../../includes/wv-md.md)] 上，服務會裝載在 Windows Activation Service (WAS) 中。 在 [!INCLUDE[wxp](../../../../includes/wxp-md.md)][!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]和 上，服務會由網際網路資訊服務 (IIS) 與 ASP.NET 加以裝載。 使用 IIS 或 WAS 裝載服務，便可以讓服務在第一次存取時就自動啟動。

> [!NOTE]
> 如果您想要開始使用在主控台應用程式（而不是 IIS）中裝載服務的範例，請參閱[自我裝載](../../../../docs/framework/wcf/samples/self-host.md)範例。

服務與用戶端會在組態檔設定中指定存取詳細資訊，而這些設定可提供部署期間的彈性。 其中包含指定位址、繫結與合約的端點定義。 繫結會指定如何存取服務的傳輸與安全性詳細資訊。

服務會將執行階段行為設定成發行其中繼資料。

服務會實作定義要求-回覆通訊模式的合約。 合約是由 `ICalculator` 介面所定義，這個介面會公開數學運算作業 (加、減、乘、除)。 用戶端會對指定的數學運算作業提出要求，服務則會以結果回覆。 此服務會實作 `ICalculator` 合約，如下列程式碼中所定義。

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

服務實作會計算並傳回適當的結果，如下列範例程式碼所示。

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

此服務會公開 (Expose) 單一的端點來與已使用組態檔 (Web.config) 定義之服務進行通訊，如下列範例組態所示。

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

服務會公開位在 IIS 或 WAS 主機提供之基底位址上的端點。 繫結會設定為標準 <xref:System.ServiceModel.WSHttpBinding>，此繫結會提供用於定址和安全性的 HTTP 通訊與標準 Web 服務通訊協定。 此合約是服務實作的 `ICalculator`。

在設定，可以存取的服務在 `http://localhost/servicemodelsamples/service.svc` 在同一部電腦上的用戶端。 為了讓遠端電腦上的用戶端存取服務，這時必須指定完整網域名稱，而不要指定 localhost。

根據預設，此架構不會公開任何中繼資料。 因此，服務會開啟<xref:System.ServiceModel.Description.ServiceMetadataBehavior>並公開在中繼資料交換 (MEX) 端點 `http://localhost/servicemodelsamples/service.svc/mex` 。 下列組態會示範這個作業。

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

用戶端會使用由[System.servicemodel 中繼資料公用程式工具（Svcutil）](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)所產生的用戶端類別，透過指定的合約型別進行通訊。 這個產生的用戶端會包含在 generatedClient.cs 或 generatedClient.vb 檔中。 這個公用程式會擷取指定服務的中繼資料，然後產生用戶端應用程式透過指定合約型別來進行通訊的用戶端。 裝載的服務必須可用來產生用戶端程式碼，因為該服務將被用來擷取更新的中繼資料。

 從用戶端目錄中的 SDK 命令提示字元執行下列命令，以產生具型別的 Proxy：

```console
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs
```

若要在 Visual Basic 中產生用戶端，請在 SDK 命令提示字元輸入下列命令：

`Svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb`

藉由使用產生的用戶端，用戶端便可以設定適當的位址與繫結來存取指定服務端點。 就跟服務一樣，用戶端會使用組態檔 (App.config) 來指定其想要進行通訊的端點。 用戶端端點組態是由服務端點的絕對位址、繫結和合約所組成，如下列範例所示。

```xaml
<client>
     <endpoint
         address="http://localhost/servicemodelsamples/service.svc"
         binding="wsHttpBinding"
         contract=" Microsoft.ServiceModel.Samples.ICalculator" />
</client>
```

用戶端實作會產生用戶端，並且使用具型別介面開始與服務進行通訊，如下列範例程式碼所示。

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

當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。 在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。

```output
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

使用者入門範例會示範建立服務與用戶端的標準方式。 此範例上的另一個[基本](../../../../docs/framework/wcf/samples/basic-sample.md)組建，示範特定的產品功能。

### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例

1. 請確定您已[針對 Windows Communication Foundation 範例執行一次安裝程式](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。

2. 若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。

3. 若要在單一或跨電腦設定中執行範例，請遵循執行[Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的指示。

## <a name="see-also"></a>另請參閱

- [如何：在受控應用程式中裝載 WCF 服務](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
- [如何：在 IIS 中裝載 WCF 服務](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)

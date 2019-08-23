---
title: 定址
ms.date: 03/30/2017
ms.assetid: d438e6f2-d0f3-43aa-b259-b51b5bda2e64
ms.openlocfilehash: 290c4648c0904135d11ad3d62280a30cd25bcbe5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945247"
---
# <a name="addressing"></a>定址
此定址範例會示範端點位址的各方面與功能。 此範例是以[消費者入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)為基礎。 在此範例中的服務會自動裝載。 服務和用戶端都是主控台應用程式。 服務會定義使用相對與絕對端點位址組合的多個端點。  
  
> [!NOTE]
> 此範例的安裝程序與建置指示位於本主題的結尾。  
  
 服務組態檔會指定基底位址與四個端點。 基底位址是以 service/host/baseAddresses 下的新增項目所指定，如下列範例組態中所示。  
  
```xml  
<service name="Microsoft.ServiceModel.Samples.CalculatorService"  
         behaviorConfiguration="CalculatorServiceBehavior">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />  
    </baseAddresses>  
  </host>  
</service>  
```  
  
 在下列範例組態中所示的第一個端點定義是指定相對位址，這表示端點位址是遵守 URI 組合規則之基底位址與相對位址的組合。  
  
```xml
<!-- Empty relative address specified:   
     use the base address provided by the host. -->  
<!-- The endpoint address is  
     http://localhost:8000/ServiceModelSamples/service. -->  
<endpoint address=""  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 在此範例中，相對位址是空白的 ("")，因此端點位址會與基底位址相同。 實際的端點位址是`http://localhost:8000/servicemodelsamples/service`。
  
 第二個端點定義也是指定相對位址，如下列範例組態所示。  
  
```xml  
<!-- The relative address specified: use the base address -->  
<!-- provided by the host + path. The endpoint address is -->  
<!-- http://localhost:8000/servicemodelsamples/service/test. -->  
<endpoint address="/test"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 此相對位址 "test" 會附加在基底位址。 實際的端點位址是`http://localhost:8000/servicemodelsamples/service/test`。
  
 第三個端點定義是指定絕對位址，如下列範例組態所示。  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 位址中不需要基底位址。 實際的端點位址是`http://localhost:8001/hello/servicemodelsamples`。
  
 第四個端點位址是指定絕對位址以及不同的傳輸 (TCP)。 位址中不需要基底位址。 實際的端點位址是`net.tcp://localhost:9000/servicemodelsamples/service`。
  
```xml  
<!-- The absolute address specified, different transport: -->  
<!-- use the specified address, and ignore the base address. -->  
<!-- The endpoint address is -->  
<!-- net.tcp://localhost:9000/servicemodelsamples/service. -->  
<endpoint address=  
          "net.tcp://localhost:9000/servicemodelsamples/service"  
          binding="netTcpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
</service>  
```  
  
 用戶端只會存取這四種服務端點的其中一個，但是這四種端點都會定義在其組態檔中。 用戶端會在建立 `CalculatorProxy` 物件時選取端點。 透過變更從 `CalculatorEndpoint1` 到 `CalculatorEndpoint4` 的組態名稱，您便可以執行其中每一個端點。  
  
 當您執行範例時，服務會列舉其每個端點的位址、繫結名稱與合約名稱。 中繼資料交換 (MEX) 端點對 ServiceHost 而言只是另一個端點，因此它會出現在清單中。  
  
```  
Service endpoints:  
Endpoint - address:  http://localhost:8000/ServiceModelSamples/service  
           binding:  WSHttpBinding  
           contract: ICalculator  
Endpoint - address:  http://localhost:8000/ServiceModelSamples/service/test  
           binding:  WSHttpBinding  
           contract: ICalculator  
Endpoint - address:  http://localhost:8001/hello/servicemodelsamples  
           binding:  WSHttpBinding  
           contract: ICalculator  
Endpoint - address:  net.tcp://localhost:9000/servicemodelsamples/service  
           binding:  NetTcpBinding  
           contract: ICalculator  
Endpoint - address:  http://localhost:8000/ServiceModelSamples/service/mex  
           binding:  MetadataExchangeHttpBinding  
           contract: IMetadataExchange  
  
The service is ready.  
Press <ENTER> to terminate service.  
```  
  
 當您執行用戶端時，作業要求和回應會顯示在服務與用戶端主控台視窗中。 在每個主控台視窗中按下 ENTER 鍵，即可關閉服務與用戶端。  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 請確定您已[針對 Windows Communication Foundation 範例執行一次安裝程式](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2. 若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3. 若要在單一或跨電腦設定中執行範例, 請遵循執行[Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的指示。  
  
    > [!NOTE]
    >  如果您使用 Svcutil.exe 重新產生這個範例的組態，請務必修改用戶端組態中的端點名稱，以符合用戶端程式碼。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在, 請移至[.NET Framework 4 的 Windows Communication Foundation (wcf) 和 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780), 以下載所有 Windows Communication Foundation (wcf) [!INCLUDE[wf1](../../../../includes/wf1-md.md)]和範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Addressing`  

---
title: 自訂繫結可靠工作階段
ms.date: 03/30/2017
ms.assetid: c5fcd409-246f-4f3e-b3f1-629506ca4c04
ms.openlocfilehash: 76c701aaae368171bc7047784e1dc126937c84f0
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463932"
---
# <a name="custom-binding-reliable-session"></a>自訂繫結可靠工作階段

自訂繫結由經過排序的獨立繫結項目清單所定義。 此範例示範如何使用各種傳輸與訊息編碼項目設定自訂繫結，特別是啟用可靠工作階段。

> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> 如果此目錄不存在,請轉到[Windows 通信基礎 (WCF) 和 Windows 工作流基礎 (WF) 範例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通訊基礎 (WCF) 和示例。 此範例位於下列目錄。
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\ReliableSession`

## <a name="sample-details"></a>範例詳細資料

可靠的工作階段會提供可靠傳訊和工作階段功能。 可靠的傳訊失敗時會重試通訊，而且允許指定傳遞保證，例如訊息依序到達。 工作階段會保持呼叫之間的用戶端狀態。 此範例會實作維持用戶端狀態的工作階段，並且指定依序傳遞保證。 此範例以計算器服務的[入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)。 可靠工作階段的功能已在用戶端和服務的應用程式組態檔中啟用和設定。

> [!NOTE]
> 此範例的安裝程序與建置指示位於本主題的結尾。

綁定元素的順序在定義自定義綁定時非常重要,因為每個綁定都表示通道堆疊中的一個圖層(請參閱[自定義綁定](../../../../docs/framework/wcf/extending/custom-bindings.md))。

範例的服務組態會如下列程式碼範例所示加以定義。

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"
          behaviorConfiguration="CalculatorServiceBehavior">
        <!-- This endpoint is exposed at the base address provided by host: http://localhost/servicemodelsamples/service.svc  -->
        <!-- specify customBinding binding and a binding configuration to use -->
        <endpoint address=""
                  binding="customBinding"
                  bindingConfiguration="Binding1"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- The mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>

    <!-- custom binding configuration - configures HTTP transport, reliable sessions -->
    <bindings>
      <customBinding>
        <binding name="Binding1">
          <reliableSession />
          <security authenticationMode="SecureConversation"
                     requireSecurityContextCancellation="true">
          </security>
          <compositeDuplex />
          <oneWay />
          <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8" />
          <httpTransport authenticationScheme="Anonymous" bypassProxyOnLocal="false"
                        hostNameComparisonMode="StrongWildcard"
                        proxyAuthenticationScheme="Anonymous" realm=""
                        useDefaultWebProxy="true" />
        </binding>
      </customBinding>
    </bindings>

    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata httpGetEnabled="True"/>
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>

  </system.serviceModel>

</configuration>
```

執行跨電腦案例時，您必須變更用戶端的端點位址以反映出服務的主機名稱。

當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。 在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例

1. 使用以下指令安裝ASP.NET 4.0:

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. 確保已為 Windows[通訊基礎範例執行一次性設定 。](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)

3. 若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。

4. 要在單機或跨計算機配置中運行範例,請按照[運行 Windows 通信基礎範例中的](../../../../docs/framework/wcf/samples/running-the-samples.md)說明操作。

    > [!IMPORTANT]
    > 在跨計算機配置中運行用戶端時,請確保將`address`[\<終結點>](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)元素的屬性中的「本地主機」和[\<複合Duplex>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md)`clientBaseAddress`的屬性替換為相應計算機的名稱,如下例所示。

    ```xml
    <endpoint name = ""
    address="http://service_machine_name/servicemodelsamples/service.svc" />
    <compositeDuplex clientBaseAddress="http://client_machine_name:8000/myClient/" />
    ```

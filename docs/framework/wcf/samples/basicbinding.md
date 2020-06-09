---
title: BasicBinding
ms.date: 03/30/2017
ms.assetid: 86fbeb87-4d89-4b61-9577-867e0ac12945
ms.openlocfilehash: 84bfe78aa9e82b9600c48e0a32514f669fcc7d77
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575650"
---
# <a name="basicbinding"></a>BasicBinding

這個範例會示範 `basicHttpBinding` 的使用方式，此繫結會搭配第一代和第二代 Web 服務來提供 HTTP 通訊和最大的互通性。

> [!NOTE]
> 此範例的安裝程序與建置指示位於本主題的結尾。

> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> 如果此目錄不存在，請移至[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）範例](https://www.microsoft.com/download/details.aspx?id=21459)，以下載所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Basic\Http`

## <a name="sample-details"></a>範例詳細資料

這個範例是以執行計算機服務的[消費者入門](getting-started-sample.md)為基礎。

若要使用包含預設行為的基本繫結，則只需要繫結區段名稱。 如果您要設定基本繫結，並變更其部分設定，則必須定義繫結組態。 端點必須使用 <> 元素的屬性，依名稱參考系結設定 `bindingConfiguration` `endpoint` ，如下列範例程式碼所示。

```xml
<services>
    <service
        type="Microsoft.ServiceModel.Samples.CalculatorService"
        behaviorConfiguration="CalculatorServiceBehavior">
       <endpoint address=""
             binding="basicHttpBinding"
             bindingConfiguration="Binding1"
             contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
</services>
```

在此範例中，繫結組態會命名為 `"Binding1"`，且如下列程式碼範例所示定義。

```xml
<bindings>
   <basicHttpBinding>
      <binding name="Binding1"
               hostNameComparisonMode="StrongWildcard"
               receiveTimeout="00:10:00"
               sendTimeout="00:10:00"
               openTimeout="00:10:00"
               closeTimeout="00:10:00"
               maxMessageSize="65536"
               maxBufferSize="65536"
               maxBufferPoolSize="524288"
               transferMode="Buffered"
               messageEncoding="Text"
               textEncoding="utf-8"
               bypassProxyOnLocal="false"
               useDefaultWebProxy="true" >
         <security mode="None" />
      </binding>
   </basicHttpBinding>
</bindings>
```

繫結項目會提供設定主機名稱比較模式、訊息大小上限、Proxy 選項、逾時、訊息編碼以及其他選項的屬性。

當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。 在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例

1. 使用下列命令安裝 ASP.NET 4.0。

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. 請確定您已[針對 Windows Communication Foundation 範例執行一次安裝程式](one-time-setup-procedure-for-the-wcf-samples.md)。

3. 若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的指示。

4. 若要在單一或跨電腦設定中執行範例，請遵循執行[Windows Communication Foundation 範例](running-the-samples.md)中的指示。

---
title: WS 可靠工作階段
ms.date: 03/30/2017
helpviewer_keywords:
- Reliable session
ms.assetid: 86e914f2-060b-432b-bd17-333695317745
ms.openlocfilehash: c4e238cbc3b99209e88bb56c73097f25e56ccdfb
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814480"
---
# <a name="ws-reliable-session"></a>WS 可靠工作階段
這個範例會示範可靠工作階段的使用方式。 可靠工作階段會支援可信賴傳訊和工作階段。 可信賴傳訊失敗時會重試通訊，而且允許指定傳遞保證，例如訊息依序到達。 工作階段會保持呼叫之間的用戶端狀態。 此範例會實作維持用戶端狀態的工作階段，並且指定依序傳遞保證。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsReliableSession`  
  
 此樣本根據[開始使用](../../../../docs/framework/wcf/samples/getting-started-sample.md)以實作計算機服務。 可靠工作階段的功能已在用戶端和服務的應用程式組態檔中啟用和設定。  
  
 在這個範例中，服務會由網際網路資訊服務 (IIS) 裝載，而用戶端是主控台應用程式 (.exe)。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
 這個範例會使用 `wsHttpBinding`。 用戶端和服務的組態檔中都會指定繫結。 在端點項目的 `binding` 屬性中會指定繫結類型，如下列範例組態所示。  
  
```xml  
<endpoint address=""  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"   
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 端點包含參考名為 "Binding1." 之繫結組態的 `bindingConfiguration` 屬性。 繫結組態會啟用可靠工作階段藉由設定`enabled`的屬性[ \<reliableSession >](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md)到`true`。 已排序工作階段之傳遞保證的控制方式，是將已排序的屬性設定為 `true` 或 `false`。 預設為 `true`。  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding name="Binding1">  
            <reliableSession enabled="true" />  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 服務實作類別會將 <xref:System.ServiceModel.InstanceContextMode.PerSession> 執行個體實作成維護每個用戶端的不同類別執行個體，如下列範例程式碼所示。  

```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)] public class CalculatorService : ICalculator  
{  
    ...  
}  
```
  
 當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。 在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  使用下列命令安裝 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0。  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
3.  若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
4.  若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  

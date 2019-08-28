---
title: WSHttpBinding
ms.date: 03/30/2017
helpviewer_keywords:
- WS Profile binding
ms.assetid: 22d85b19-0135-4141-9179-a0e9c343ad73
ms.openlocfilehash: 7751e40762a99711302681f28a88d451087e4980
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044501"
---
# <a name="wshttpbinding"></a>WSHttpBinding
這個範例會示範如何使用 Windows Communication Foundation (WCF) 來執行一般服務和一般用戶端。 這個範例是由用戶端主控台程式 (client.exe) 和網際網路資訊服務 (IIS) 所裝載的服務程式庫所組成。 服務會實作定義要求-回覆通訊模式的合約。 合約是由 `ICalculator` 介面所定義，這個介面會公開數學運算作業 (加、減、乘、除)。 用戶端會對指定的數學運算作業提出同步要求，服務則會以結果回覆。 您可以在主控台視窗中看到用戶端活動。  
  
> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> 如果此目錄不存在, 請移至[.NET Framework 4 的 Windows Communication Foundation (wcf) 和 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780), 以下載所有 Windows Communication Foundation (wcf) [!INCLUDE[wf1](../../../../includes/wf1-md.md)]和範例。 此範例位於下列目錄。  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsHttp`  
  
> [!NOTE]
> 此範例的安裝程序與建置指示位於本主題的結尾。  
  
 這個範例會`ICalculator` [ \<使用 wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)來公開合約。 這個繫結的組態已展開於 Web.config 檔中。  
  
```xml
<bindings>  
  <wsHttpBinding>  
    <!--The following is the expanded configuration section for a-->  
    <!--WSHttpBinding. Each property is configured with the default-->   
    <!--value. See the ReliableSession, TransactionFlow, -->  
    <!--TransportSecurity, and MessageSecurity samples in the WS -->  
    <!--directory to learn how to configure these features. -->  
    <binding name="Binding1"  
              bypassProxyOnLocal="false"   
              transactionFlow="false"   
              hostNameComparisonMode="StrongWildcard"  
              maxBufferPoolSize="524288"   
              maxReceivedMessageSize="65536"  
              messageEncoding="Text"   
              textEncoding="utf-8"   
              useDefaultWebProxy="true"  
              allowCookies="false">  
      <reliableSession ordered="true"   
                       inactivityTimeout="00:10:00"  
                       enabled="false" />  
      <security mode="Message">  
        <message clientCredentialType="Windows"   
                 negotiateServiceCredential="true"  
                 algorithmSuite="Default"   
                 establishSecurityContext="true" />  
      </security>  
    </binding>  
  </wsHttpBinding>  
</bindings>  
```  
  
 在基底 `binding` 項目上，`maxReceivedMessageSize` 值可以讓您設定傳入訊息的大小上限 (以位元組為單位)。 `hostNameComparisonMode` 值可以讓您設定當分離訊息信號至服務時，是否要考量主機名稱。 `messageEncoding` 值可以讓您設定訊息是要使用 Text 編碼或 MTOM 編碼。 `textEncoding` 值可以讓您設定訊息的字元編碼。 `bypassProxyOnLocal` 值可以讓您設定本機通訊是否要使用 HTTP Proxy。 `transactionFlow` 值會設定是否流動目前的異動 (如果作業已設定為異動流程)。  
  
 在[reliableSession > 元素上, 啟用的布林值會設定是否啟用可靠會話。 \< ](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) `ordered` 值會設定是否保留訊息順序。 `inactivityTimeout` 值會設定工作階段在發生錯誤前能夠閒置的時間長度。  
  
 在 [ [ \<安全性](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)] `mode` > 上, 值會設定應該使用的安全性模式。 在此範例中, 會使用訊息安全性, 這就是為什麼[ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) [ \<會在安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)內部指定訊息 >。  
  
 當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。 在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 使用下列命令安裝 ASP.NET 4.0。  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. 請確定您已[針對 Windows Communication Foundation 範例執行一次安裝程式](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
3. 若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
4. 若要在單一或跨電腦設定中執行範例, 請遵循執行[Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的指示。  

---
title: WS 傳輸安全性
ms.date: 03/30/2017
ms.assetid: 33a20358-5e1b-458a-a6a9-15753bc7b99b
author: BrucePerlerMS
ms.openlocfilehash: 99f8e038657a620de56d1d759a95bbbdf93b1ed4
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48029134"
---
# <a name="ws-transport-security"></a>WS 傳輸安全性
這個範例會示範搭配 <xref:System.ServiceModel.WSHttpBinding> 繫結來使用 SSL 傳輸安全性。 根據預設，`wsHttpBinding` 繫結會提供 HTTP 通訊。 當針對傳輸安全性設定時，此繫結會支援 HTTPS 通訊。 此樣本根據[開始使用](../../../../docs/framework/wcf/samples/getting-started-sample.md)以實作計算機服務。 `wsHttpBinding` 會指定並設定在用戶端和服務的應用程式組態檔中。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsTransportSecurity`  
  
 程式碼範例中的是相同[開始使用](../../../../docs/framework/wcf/samples/getting-started-sample.md)服務。 您必須建立一個憑證並使用 [Web 伺服器憑證精靈] 指派憑證，再建置及執行範例。 組態檔設定中的端點定義與繫結定義會啟用 `Transport` 安全性模式，如同下列用戶端的範例組態所示。  
  
```xml  
<system.serviceModel>  
  
    <client>  
      <!-- this endpoint has an https: address -->  
      <endpoint address="https://localhost/servicemodelsamples/service.svc" binding="wsHttpBinding" bindingConfiguration="Binding1" contract="Microsoft.Samples.TransportSecurity.ICalculator"/>  
    </client>  
  
    <bindings>  
      <wsHttpBinding>  
        <!-- configure wsHttpbinding with Transport security mode  
                   and clientCredentialType as None -->  
        <binding name="Binding1">  
          <security mode="Transport">  
            <transport clientCredentialType="None"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
  
  </system.serviceModel>  
```  
  
 指定的位址會使用 https:// 配置。 繫結組態會將安全性模式設定為 `Transport`。 相同的安全性模式必須指定在服務的 Web.config 檔中。  
  
 當您嘗試存取 https 時，因為此範例中使用的憑證是使用 Makecert.exe 所建立的測試憑證，會顯示安全性警示： 位址，例如 https://localhost/servicemodelsamples/service.svc ，從您的瀏覽器。 若要讓 Windows Communication Foundation (WCF) 用戶端，才能使用測試憑證中的位置，已新增一些額外的程式碼用戶端以隱藏安全性警示。 使用實際執行憑證時，不需要這個程式碼及伴隨的類別。  

```csharp
// This code is required only for test certificates like those created by Makecert.exe.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
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
  
3.  請確定您已執行[Internet Information Services (IIS) 伺服器憑證安裝指示](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md)。  
  
4.  若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
5.  若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
## <a name="see-also"></a>另請參閱

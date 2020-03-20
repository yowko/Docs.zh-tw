---
title: WS 傳輸安全性
ms.date: 03/30/2017
ms.assetid: 33a20358-5e1b-458a-a6a9-15753bc7b99b
ms.openlocfilehash: 221bf2e0d304e93242bb5fea6854c1c9bb72aec2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143456"
---
# <a name="ws-transport-security"></a>WS 傳輸安全性
這個範例會示範搭配 <xref:System.ServiceModel.WSHttpBinding> 繫結來使用 SSL 傳輸安全性。 根據預設，`wsHttpBinding` 繫結會提供 HTTP 通訊。 當針對傳輸安全性設定時，此繫結會支援 HTTPS 通訊。 此示例基於實現計算機服務的[入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)。 `wsHttpBinding` 會指定並設定在用戶端和服務的應用程式組態檔中。  
  
> [!NOTE]
> 此範例的安裝程序與建置指示位於本主題的結尾。  
  
> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> 如果此目錄不存在，請轉到[Windows 通信基礎 （WCF） 和 Windows 工作流基礎 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基礎 （WCF） 和示例。 此範例位於下列目錄。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsTransportSecurity`  
  
 示例中的程式碼與[入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)服務的代碼相同。 您必須建立一個憑證並使用 [Web 伺服器憑證精靈] 指派憑證，再建置及執行範例。 組態檔設定中的端點定義與繫結定義會啟用 `Transport` 安全性模式，如同下列用戶端的範例組態所示。  
  
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
  
 由於此示例中使用的證書是使用 Makecert.exe 創建的測試憑證，因此當您嘗試從瀏覽器訪問 HTTPs： 位址（如https://localhost/servicemodelsamples/service.svc）時，會顯示安全警報。 為了允許 Windows 通信基礎 （WCF） 用戶端使用就地使用測試憑證，已經向用戶端添加了一些附加代碼以禁止安全警報。 使用實際執行憑證時，不需要這個程式碼及伴隨的類別。  

```csharp
// This code is required only for test certificates like those created by Makecert.exe.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```

 當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。 在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 使用以下命令安裝ASP.NET 4.0。  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. 確保已為 Windows[通信基礎示例執行一次性設置過程](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
3. 確保您已執行[互聯網資訊服務 （IIS） 伺服器憑證安裝說明](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md)。  
  
4. 若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
5. 要在單機或跨電腦配置中運行示例，請按照[運行 Windows 通信基礎示例中的](../../../../docs/framework/wcf/samples/running-the-samples.md)說明操作。  

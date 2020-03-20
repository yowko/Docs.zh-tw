---
title: 使用訊息認證的 WS 傳輸
ms.date: 03/30/2017
ms.assetid: 0d092f3a-b309-439b-920b-66d8f46a0e3c
ms.openlocfilehash: 076d4490f6edc6efa8eeb50ae8baa23d5c4e369a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183137"
---
# <a name="ws-transport-with-message-credential"></a>使用訊息認證的 WS 傳輸
這個範例會示範結合訊息中傳遞的用戶端認證來使用 SSL 傳輸安全性。 這個範例會使用 `wsHttpBinding` 繫結。  
  
 根據預設，`wsHttpBinding` 繫結會提供 HTTP 通訊。 當針對傳輸安全性設定時，此繫結會支援 HTTPS 通訊。 HTTPS 會保護在網路上傳輸之訊息的機密性與完整性。 但是，可以用來驗證服務之用戶端的驗證機制集合會受限於 HTTPS 傳輸所支援的機制。 Windows 通信基礎 （WCF）`TransportWithMessageCredential`提供一種安全模式，旨在克服此限制。 如果是設定這種安全性模式，傳輸安全性就會用來提供所傳輸訊息的機密性與完整性，以及用來執行服務驗證。 但是，用戶端身份驗證是通過將用戶端憑據直接放入消息來執行的。 這允許您使用用戶端身份驗證的消息安全模式支援的任何憑據類型，同時保持傳輸安全模式的性能優勢。  
  
 在這個範例中，`UserName` 認證類型會用來驗證服務的用戶端。  
  
 此示例基於實現計算機服務的[入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)。 `wsHttpBinding` 繫結會指定並設定在用戶端和服務的應用程式組態檔中。  
  
> [!NOTE]
> 此範例的安裝程序與建置指示位於本主題的結尾。  
  
 示例中的程式碼與[入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)服務的代碼幾乎相同。 服務合約則另外提供一項作業 - `GetCallerIdentity`。 這個作業會將呼叫者身分識別名稱傳回呼叫者。  

```csharp
public string GetCallerIdentity()  
{  
    // Use ServiceSecurityContext.WindowsIdentity to get the name of the caller.  
    return ServiceSecurityContext.Current.WindowsIdentity.Name;  
}  
```

 您必須建立一個憑證並使用 [Web 伺服器憑證精靈] 指派憑證，再建置及執行範例。 組態檔設定中的端點定義與繫結定義會啟用 `TransportWithMessageCredential` 安全性模式，如同下列用戶端的範例組態所示。  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint name=""  
              address="https://localhost/servicemodelsamples/service.svc"
              binding="wsHttpBinding"
              bindingConfiguration="Binding1"
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!--   
        This configuration defines the security mode as TransportWithMessageCredential.  
        and the clientCredentialType as UserName.  
        -->  
      <binding name="Binding1">  
        <security mode ="TransportWithMessageCredential">  
          <message clientCredentialType="UserName" />  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 指定的位址會使用 https:// 配置。 繫結組態會將安全性模式設定為 `TransportWithMessageCredential`。 相同的安全性模式必須指定在服務的 Web.config 檔中。  
  
 由於此示例中使用的證書是使用 Makecert.exe 創建的測試憑證，因此當您嘗試從瀏覽器訪問 HTTPs： 位址（如`https://localhost/servicemodelsamples/service.svc`）時，會顯示安全警報。 為了允許 WCF 用戶端在原位上使用測試憑證，已經向用戶端添加了一些附加代碼以禁止安全警報。 使用實際執行憑證時，不需要這個程式碼及伴隨的類別。  

```csharp
// WARNING: This code is only needed for test certificates such as those created by makecert. It is
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```
  
 當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。 在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。  
  
```console  
Username authentication required.  
Provide a valid machine or domain account. [domain\\user]  
   Enter username:
YourDomainName\YourAccountName  
   Enter password:
********  
YourDomainName\YourAccountName  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 確保已為 Windows[通信基礎示例執行一次性設置過程](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2. 確保您已執行[互聯網資訊服務 （IIS） 伺服器憑證安裝說明](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md)。  
  
3. 若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
4. 要在單機或跨電腦配置中運行示例，請按照[運行 Windows 通信基礎示例中的](../../../../docs/framework/wcf/samples/running-the-samples.md)說明操作。  

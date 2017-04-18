---
title: "HTTPS 上的自訂繫結可靠工作階段 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 16aaa80d-3ffe-47c4-8b16-ec65c4d25f8d
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# HTTPS 上的自訂繫結可靠工作階段
這個範例示範透過可靠工作階段來使用 SSL 傳輸安全性。可靠工作階段會實作 WS\-Reliable Messaging 通訊協定。您可以經由在可靠工作階段上撰寫 WS\-Security 來建立安全可靠工作階段。但有時候，您可以改成選擇搭配 SSL 來使用 HTTP 傳輸安全性。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\ReliableSessionOverHttps`  
  
## 範例詳細資料  
 SSL 會確定封包本身的安全性。值得注意的是，這種作法不同於使用 WS\-Secure Conversation 來保護可靠工作階段。  
  
 若要在 HTTPS 上使用可靠工作階段，您必須建立自訂繫結。這個範例是以實作計算機服務的[使用者入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)為基礎。使用可靠工作階段繫結項目與 [\<httpsTransport\>](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md)，便可建立自訂繫結。下列組態是使用自訂繫結。  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service   
          name="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- use base address provided by host -->  
        <endpoint address=""  
                  binding="customBinding"  
                  bindingConfiguration="reliableSessionOverHttps"   
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is exposed as http://localhost/servicemodelsamples/service.svc/mex-->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange"/>  
      </service>  
    </services>  
  
    <bindings>  
      <customBinding>  
        <binding name="reliableSessionOverHttps">  
          <reliableSession />  
          <httpsTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="true" />  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
  
</configuration>  
```  
  
 本範例中的程式碼與[使用者入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)服務中的程式碼相同。您必須建立一個憑證並使用 \[Web 伺服器憑證精靈\] 指派憑證，再建置及執行範例。組態檔設定中的端點定義與繫結定義會啟用自訂繫結，如同下列用戶端的範例組態所示。  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
  
    <client>  
      <!-- this endpoint has an https: address -->  
      <endpoint name=""  
                address="https://localhost/servicemodelsamples/service.svc"   
                binding="customBinding"   
                bindingConfiguration="reliableSessionOverHttps"   
                contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </client>  
  
      <bindings>  
        <customBinding>  
          <binding name="reliableSessionOverHttps">  
            <reliableSession />  
            <httpsTransport />  
          </binding>  
        </customBinding>        
    </bindings>  
  
  </system.serviceModel>  
  
</configuration>  
  
```  
  
 指定的位址會使用 https:\/\/ 配置。  
  
 因為本範例中所使用的憑證是使用 Makecert.exe 所建立的測試憑證，所以當您嘗試從瀏覽器存取 https: 位址時 \(例如 https:\/\/localhost\/servicemodelsamples\/service.svc\)，會顯示安全性警示。若要允許 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 用戶端適當地使用測試憑證，就必須在用戶端新增某些其他程式碼以便隱藏安全性警示。使用實際執行憑證時，不需要這個程式碼及伴隨的類別。  
  
```  
// This code is required only for test certificates like those created by Makecert.exe.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
  
```  
  
 當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
#### 若要安裝、建立及執行範例  
  
1.  使用下列命令安裝 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0。  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
  
    ```  
  
2.  請確定您已執行 [Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
3.  請確定您已執行 [網際網路資訊服務 \(IIS\) 伺服器憑證安裝指示](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md)。  
  
4.  若要建置方案的 C\# 或 Visual Basic .NET 版本，請遵循[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
5.  若要在單一或跨電腦的組態中執行本範例，請遵循[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的指示。  
  
## 請參閱
---
title: "自訂繫結可靠工作階段"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c5fcd409-246f-4f3e-b3f1-629506ca4c04
caps.latest.revision: "23"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9737adfe300eaaeab75b4b071b4ed49fda4499c0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="custom-binding-reliable-session"></a>自訂繫結可靠工作階段
自訂繫結由經過排序的獨立繫結項目清單所定義。 此範例示範如何使用各種傳輸與訊息編碼項目設定自訂繫結，特別是啟用可靠工作階段。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\ReliableSession`  
  
## <a name="sample-details"></a>範例詳細資料  
 可靠的工作階段會提供可靠傳訊和工作階段功能。 可靠的傳訊失敗時會重試通訊，而且允許指定傳遞保證，例如訊息依序到達。 工作階段會保持呼叫之間的用戶端狀態。 此範例會實作維持用戶端狀態的工作階段，並且指定依序傳遞保證。 範例根據[入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)，用來實作計算機服務。 可靠工作階段的功能已在用戶端和服務的應用程式組態檔中啟用和設定。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
 繫結項目的順序很重要定義自訂繫結，因為每個表示通道堆疊中的圖層中 (請參閱[自訂繫結](../../../../docs/framework/wcf/extending/custom-bindings.md))。  
  
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
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  使用下列命令安裝 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0：  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
3.  若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
4.  若要在單一或跨電腦組態中執行範例時，請依照中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
    > [!IMPORTANT]
    >  當用戶端執行跨電腦組態中時，請務必取代"localhost"，在這兩`address`屬性[\<端點 >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)項目和`clientBaseAddress`屬性[\<compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md)具有適當的電腦，如下列範例所示的名稱。  
  
    ```xml  
    <endpoint name = ""  
    address="http://service_machine_name/servicemodelsamples/service.svc"  
    ... />  
    <compositeDuplex clientBaseAddress="http://client_machine_name:8000/myClient/" />  
    ```  
  
## <a name="see-also"></a>另請參閱

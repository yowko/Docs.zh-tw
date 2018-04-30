---
title: 匿名用戶端的傳輸安全性
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 056653a5-384e-4a02-ae3c-1b0157d2ccb4
caps.latest.revision: 14
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 2b52a32db1f1ac02f9204198a4cda5d4cb157486
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2018
---
# <a name="transport-security-with-an-anonymous-client"></a>匿名用戶端的傳輸安全性
這個 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 案例會使用傳輸安全性 (HTTPS) 來確保機密性和完整性。 伺服器必須使用安全通訊端層 (SSL) 憑證進行驗證，而且用戶端必須信任該伺服器的憑證。 此用戶端不會透過任何機制進行驗證，因此屬於匿名。  
  
 範例應用程式，請參閱[WS 傳輸安全性](../../../../docs/framework/wcf/samples/ws-transport-security.md)。 如需有關傳輸安全性的詳細資訊，請參閱[傳輸安全性概觀](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)。  
  
 如需使用憑證與服務的詳細資訊，請參閱[使用憑證](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)和[How to： 使用 SSL 憑證設定連接埠](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)。  
  
 ![搭配匿名用戶端使用傳輸安全性](../../../../docs/framework/wcf/feature-details/media/8fa2e931-0cfb-4aaa-9272-91d652b85d8d.gif "8fa2e931-0cfb-4aaa-9272-91d652b85d8d")  
  
|特性|描述|  
|--------------------|-----------------|  
|安全性模式|Transport|  
|互通性|與現有的 Web 服務和用戶端|  
|驗證 (伺服器)<br /><br /> 驗證 (用戶端)|[是]<br /><br /> 應用程式層 ([!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 不支援)|  
|完整性|是|  
|機密性|是|  
|Transport|HTTPS|  
|繫結|<<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>|  
  
## <a name="service"></a>服務  
 下列程式碼和組態要獨立執行。 執行下列任一步驟：  
  
-   使用不含組態的程式碼建立獨立服務。  
  
-   使用提供的組態建立服務，但不要定義任何端點。  
  
### <a name="code"></a>程式碼  
 下列程式碼會示範如何建立會使用傳輸安全性的端點：  
  
 [!code-csharp[c_SecurityScenarios#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#5)]
 [!code-vb[c_SecurityScenarios#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#5)]  
  
### <a name="configuration"></a>組態  
 下列程式碼會使用組態設定相同端點。 此用戶端不會透過任何機制進行驗證，因此屬於匿名。  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"   
                  binding="wsHttpBinding"  
                  bindingConfiguration="WSHttpBinding_ICalculator"   
                  name="SecuredByTransportEndpoint"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator">  
          <security mode="Transport">  
            <transport clientCredentialType="None" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a>用戶端  
 下列程式碼和組態要獨立執行。 執行下列任一步驟：  
  
-   使用此程式碼 (和用戶端程式碼) 建立獨立用戶端。  
  
-   建立未定義任何端點位址的用戶端， 然後改用可接受組態名稱當做引數的用戶端建構函式。 例如：  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a>程式碼  
 [!code-csharp[c_SecurityScenarios#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#6)]
 [!code-vb[c_SecurityScenarios#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#6)]  
  
### <a name="configuration"></a>組態  
 可以使用下列組態來取代程式碼，進行設定服務。  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Transport">  
            <transport clientCredentialType="None" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="https://machineName/Calculator"   
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"   
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱  
 [安全性概觀](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [WS 傳輸安全性](../../../../docs/framework/wcf/samples/ws-transport-security.md)  
 [傳輸安全性概觀](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 [Windows Server App Fabric 的安全性模型](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)

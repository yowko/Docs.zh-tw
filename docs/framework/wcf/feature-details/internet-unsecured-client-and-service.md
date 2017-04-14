---
title: "沒有安全保障的網際網路用戶端與服務 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 97a10d79-3e7d-4bd1-9a99-fd9807fd70bc
caps.latest.revision: 17
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 17
---
# 沒有安全保障的網際網路用戶端與服務
下圖顯示公開、不安全的 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 用戶端與服務範例。  
  
 ![不安全的網際網路用戶端和服務情節](../../../../docs/framework/wcf/feature-details/media/publicunsecured.gif "publicUnsecured")  
  
|特性|說明|  
|--------|--------|  
|安全性模式|無|  
|傳輸|HTTP|  
|繫結|程式碼的 <xref:System.ServiceModel.BasicHttpBinding>，或組態中的 [\<basicHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) 項目。|  
|互通性|使用現有的 Web 服務用戶端和服務|  
|驗證|無|  
|完整性|無|  
|機密性|無|  
  
## 服務  
 下列程式碼和組態要獨立執行。執行下列其中一項：  
  
-   使用不含組態的程式碼建立獨立服務。  
  
-   使用提供的組態建立服務，但不要定義任何端點。  
  
### 程式碼  
 下列程式碼顯示如何建立無安全性的端點。根據預設值，<xref:System.ServiceModel.BasicHttpBinding> 的安全性模式設定為 <xref:System.ServiceModel.BasicHttpSecurityMode>。  
  
 [!code-csharp[C_UnsecuredService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#1)]
 [!code-vb[C_UnsecuredService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#1)]  
  
### 服務組態  
 下列程式碼會使用組態設定相同端點。  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration="" name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"   
                  binding="basicHttpBinding"  
                  bindingConfiguration="Basic_Unsecured"   
                  name="BasicHttp_ICalculator"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <basicHttpBinding>  
        <binding name="Basic_Unsecured" />  
      </basicHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## 用戶端  
 下列程式碼和組態要獨立執行。執行下列其中一項：  
  
-   使用此程式碼 \(和用戶端程式碼\) 建立獨立用戶端。  
  
-   建立未定義任何端點位址的用戶端，然後改用可接受組態名稱當做引數的用戶端建構函式。例如：  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### 程式碼  
 下列程式碼顯示使用不安全端點的基本 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端。  
  
 [!code-csharp[C_UnsecuredClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#1)]
 [!code-vb[C_UnsecuredClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#1)]  
  
### 用戶端組態  
 下列程式碼會設定用戶端。  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <basicHttpBinding>  
        <binding name="BasicHttpBinding_ICalculator" >  
          <security mode="None">  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://localhost/Calculator/Unsecured"  
          binding="basicHttpBinding"   
          bindingConfiguration="BasicHttpBinding_ICalculator"  
          contract="ICalculator"   
          name="BasicHttpBinding_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## 請參閱  
 [常見的安全性案例](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)   
 [安全性概觀](../../../../docs/framework/wcf/feature-details/security-overview.md)   
 [Windows Server AppFabric 的資訊安全模型](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
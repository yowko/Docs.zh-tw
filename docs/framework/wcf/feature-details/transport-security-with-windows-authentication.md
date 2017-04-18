---
title: "Windows 驗證的傳輸安全性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 96dd26e2-46e7-4de0-9a29-4fcb05bf187b
caps.latest.revision: 17
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 17
---
# Windows 驗證的傳輸安全性
下列情節顯示 Windows 安全性所保護的 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 用戶端與服務。[!INCLUDE[crabout](../../../../includes/crabout-md.md)]程式設計的詳細資訊，請參閱 [HOW TO：使用 Windows 認證來確保服務安全](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md)。  
  
 內部網路 Web 服務顯示人力資源資訊。用戶端為 Windows Form 應用程式。應用程式部署於由 Kerberos 控制站負責網域安全的網域內。  
  
 ![使用 Windows 驗證的傳輸安全性](../../../../docs/framework/wcf/feature-details/media/securedbywindows.gif "SecuredByWindows")  
  
|特性|描述|  
|--------|--------|  
|安全性模式|傳輸|  
|互通性|僅限 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]|  
|驗證 \(伺服器\)<br /><br /> 驗證 \(用戶端\)|是 \(使用 Windows 整合式驗證\)<br /><br /> 是 \(使用 Windows 整合式驗證\)|  
|完整性|是|  
|機密性|是|  
|傳輸|NET.TCP|  
|繫結|<xref:System.ServiceModel.NetTcpBinding>|  
  
## 服務  
 下列程式碼和組態要獨立執行。執行下列其中一項：  
  
-   使用不含組態的程式碼建立獨立服務。  
  
-   使用提供的組態建立服務，但不要定義任何端點。  
  
### 程式碼  
 下列程式碼顯示如何建立使用 Windows 安全性的服務端點。  
  
 [!code-csharp[C_SecurityScenarios#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#3)]
 [!code-vb[C_SecurityScenarios#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#3)]  
  
### 組態  
 可使用以下組態來取代程式碼設定服務端點。  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration="" name="ServiceModel.Calculator">  
        <endpoint address="net.tcp://localhost:8008/Calculator"   
                  binding="netTcpBinding"  
          bindingConfiguration="WindowsClientOverTcp"   
                  name="WindowsClientOverTcp"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="WindowsClientOverTcp">  
          <security mode="Transport">  
            <transport clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
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
 下列程式碼會建立用戶端。繫結會設定為使用傳輸模式安全性，採用 TCP 傳輸，並將用戶端認證類型設為 Windows。  
  
 [!code-csharp[C_SecurityScenarios#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#4)]
 [!code-vb[C_SecurityScenarios#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#4)]  
  
### 組態  
 可使用以下組態來取代程式碼建立用戶端。  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <netTcpBinding>  
        <binding name="NetTcpBinding_ICalculator" >  
          <security mode="Transport">  
            <transport clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client>  
      <endpoint address="net.tcp://localhost:8008/Calculator"   
                binding="netTcpBinding"            
                bindingConfiguration="NetTcpBinding_ICalculator"   
                contract="ICalculator"  
                name="NetTcpBinding_ICalculator">  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## 請參閱  
 [安全性概觀](../../../../docs/framework/wcf/feature-details/security-overview.md)   
 [HOW TO：使用 Windows 認證來確保服務安全](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md)   
 [Windows Server AppFabric 的資訊安全模型](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
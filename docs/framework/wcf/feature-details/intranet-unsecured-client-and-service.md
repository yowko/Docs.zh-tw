---
title: "沒有安全保障的內部網路用戶端與服務 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f450f5d4-3547-47ec-9320-2809e6a12634
caps.latest.revision: 20
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 20
---
# 沒有安全保障的內部網路用戶端與服務
下圖說明為了在安全私人網路上提供資訊給 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式而開發的簡單 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務。  因為資料重要性低、預期網路本質上是安全的，或者安全性已由 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 基礎結構的下一層提供，所以不需要安全性。  
  
 ![內部網路不安全的用戶端和服務情節](../../../../docs/framework/wcf/feature-details/media/unsecuredwebservice.gif "UnsecuredWebService")  
  
|特性|描述|  
|--------|--------|  
|安全性模式|無|  
|Transport|TCP|  
|繫結|<xref:System.ServiceModel.NetTcpBinding>|  
|互通性|僅限 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]|  
|驗證|無|  
|完整性|無|  
|機密性|無|  
  
## 服務  
 下列程式碼和組態要獨立執行。  執行下列任一步驟：  
  
-   使用不含組態的程式碼建立獨立服務。  
  
-   使用提供的組態建立服務，但不要定義任何端點。  
  
### 程式碼  
 下列程式碼會示範如何建立無安全性的端點：  
  
 [!code-csharp[C_UnsecuredService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#2)]
 [!code-vb[C_UnsecuredService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#2)]  
  
### 組態  
 下列程式碼會設定使用組態的相同端點：  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration=""   
               name="ServiceModel.Calculator">  
        <endpoint address="net.tcp://localhost:8008/Calculator"   
                  binding="netTcpBinding"  
                  bindingConfiguration="tcp_Unsecured"   
                  name="netTcp_ICalculator"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="tcp_Unsecured">  
          <security mode="None" />  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## 用戶端  
 下列程式碼和組態要獨立執行。  執行下列任一步驟：  
  
-   使用此程式碼 \(和用戶端程式碼\) 建立獨立用戶端。  
  
-   建立未定義任何端點位址的用戶端，  然後改用可接受組態名稱當做引數的用戶端建構函式。  例如：  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### 程式碼  
 下列程式碼示範使用 TCP 通訊協定來存取不安全端點的基本 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端。  
  
 [!code-csharp[C_UnsecuredClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#2)]
 [!code-vb[C_UnsecuredClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#2)]  
  
### 組態  
 下列組態程式碼會套用至用戶端：  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <netTcpBinding>  
        <binding name="NetTcpBinding_ICalculator" >  
          <security mode="None">  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client>  
      <endpoint address="net.tcp://machineName:8008/Calculator "  
                binding="netTcpBinding"   
                bindingConfiguration="NetTcpBinding_ICalculator"  
                contract="ICalculator"   
                name="NetTcpBinding_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## 請參閱  
 <xref:System.ServiceModel.NetTcpBinding>   
 [安全性概觀](../../../../docs/framework/wcf/feature-details/security-overview.md)   
 [Windows Server App Fabric 的資訊安全模型](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
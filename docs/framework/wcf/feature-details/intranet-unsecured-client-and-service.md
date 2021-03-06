---
title: 沒有安全保障的內部網路用戶端與服務
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f450f5d4-3547-47ec-9320-2809e6a12634
ms.openlocfilehash: f9cd297b479a07f2330eabbaaf81605a3874ec25
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96257217"
---
# <a name="intranet-unsecured-client-and-service"></a>沒有安全保障的內部網路用戶端與服務

下圖說明一個簡單 Windows Communication Foundation (WCF) 服務，其開發目的是要將安全私人網路的資訊提供給 WCF 應用程式。 不需要安全性，因為資料的重要性很低、網路預期會是安全的，或是由 WCF 基礎結構底下的層級提供安全性。  
  
 ![內部網路不安全的用戶端和服務案例。](./media/intranet-unsecured-client-and-service/unsecured-web-client-service.gif)  
  
|特性|描述|  
|--------------------|-----------------|  
|安全性模式|無|  
|傳輸|TCP|  
|繫結|<xref:System.ServiceModel.NetTcpBinding>|  
|互通性|僅限 WCF|  
|驗證|無|  
|完整性|無|  
|機密性|無|  
  
## <a name="service"></a>服務  

 下列程式碼和組態要獨立執行。 請執行下列其中一項：  
  
- 使用不含組態的程式碼建立獨立服務。  
  
- 使用提供的組態建立服務，但不要定義任何端點。  
  
### <a name="code"></a>程式碼  

 下列程式碼會示範如何建立無安全性的端點：  
  
 [!code-csharp[C_UnsecuredService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#2)]
 [!code-vb[C_UnsecuredService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#2)]  
  
### <a name="configuration"></a>設定  

 下列程式碼會設定使用組態的相同端點：  
  
```xml  
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
  
## <a name="client"></a>用戶端  

 下列程式碼和組態要獨立執行。 請執行下列其中一項：  
  
- 使用此程式碼 (和用戶端程式碼) 建立獨立用戶端。  
  
- 建立未定義任何端點位址的用戶端， 然後改用可接受組態名稱當做引數的用戶端建構函式。 例如：  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a>程式碼  

 下列程式碼顯示使用 TCP 通訊協定來存取不安全端點的基本 WCF 用戶端。  
  
 [!code-csharp[C_UnsecuredClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#2)]
 [!code-vb[C_UnsecuredClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#2)]  
  
### <a name="configuration"></a>設定  

 下列組態程式碼會套用至用戶端：  
  
```xml  
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
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.NetTcpBinding>
- [安全性概觀](security-overview.md)
- [Windows Server AppFabric 的資訊安全模型](/previous-versions/appfabric/ee677202(v=azure.10))

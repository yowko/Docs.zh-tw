---
title: WCF 服務的簡化組態
ms.date: 03/30/2017
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
ms.openlocfilehash: 80e2ac83ec0e07176d6afe6d34c63fb4d8e836d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33502260"
---
# <a name="simplified-configuration-for-wcf-services"></a>WCF 服務的簡化組態
這個範例示範如何實作與設定一般服務和用戶端會使用 Windows Communication Foundation (WCF)。 這個範例是所有其他基本技術範例的基礎。  
  
 公開端點以便與服務進行通訊的這個服務會在 [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] 中使用簡化的組態。 在 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] 之前，端點通常是在組態檔 (Web.config) 中定義的，如下列範例組態程式碼所示。  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright ©) Microsoft Corporation.  All Rights Reserved. -->  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service name="Microsoft.Samples.GettingStarted.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <endpoint address="" binding="basicHttpBinding" contract="ICalculator"/>  
        <endpoint address="mex" binding="mexHttpBinding" contract="IMetadataExchange"/>  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 在 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] 中，`<service>` 項目是選用的。 當服務沒有定義任何端點時，每個基底位址的端點和實作的合約都會加入到服務中。 基底位址會附加到合約名稱以判斷端點，而繫結則取決於位址配置。 下列程式碼範例示範簡化的組態檔。 在設定，可以存取的服務在http://localhost/servicemodelsamples/service.svc在同一部電腦上的用戶端。 為了讓遠端電腦上的用戶端存取服務，這時必須指定完整網域名稱，而不要指定 localhost。 根據預設，此服務不會公開任何中繼資料。 因此，服務會開啟 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 行為。  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright © Microsoft Corporation.  All Rights Reserved. -->  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要建置此方案，請依照中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。  
  
3.  遵循下列步驟執行範例：  
  
    1.  以滑鼠右鍵按一下**服務**專案，然後選取**設定為啟始專案**，然後按下**Ctrl + F5**。  
  
    2.  等待主控台輸出確認服務已啟動且在執行中。  
  
    3.  以滑鼠右鍵按一下**用戶端**專案，然後選取**設定為啟始專案**，然後按下**Ctrl + F5**。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a>另請參閱  
 [AppFabric 管理範例](http://go.microsoft.com/fwlink/?LinkId=193960)  
 [簡化設定](../../../../docs/framework/wcf/simplified-configuration.md)

---
title: WCF 服務的簡化組態
description: 瞭解如何使用 WCF 來執行和設定一般服務和用戶端。 服務會使用設定檔中指定的端點進行通訊。
ms.date: 03/30/2017
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
ms.openlocfilehash: 087618d603ea1c7df75ab5383f6c95b781dca847
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96290019"
---
# <a name="simplified-configuration-for-wcf-services"></a>WCF 服務的簡化組態

這個範例示範如何使用 Windows Communication Foundation (WCF) 來執行和設定一般服務和用戶端。 這個範例是所有其他基本技術範例的基礎。  
  
 這項服務會公開用來與服務進行通訊的端點，使用 .NET Framework 4 的簡化設定。 在 .NET Framework 4 之前，端點通常定義于設定檔中 ( # A0) ，如下列範例設定程式碼所示。  
  
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
  
 在 .NET Framework 4 中， `<service>` 元素是選擇性的。 當服務沒有定義任何端點時，每個基底位址的端點和實作的合約都會加入到服務中。 基底位址會附加到合約名稱以判斷端點，而繫結則取決於位址配置。 下列程式碼範例示範簡化的組態檔。 如同設定的，在 `http://localhost/servicemodelsamples/service.svc` 同一部電腦上的用戶端可以存取服務。 為了讓遠端電腦上的用戶端存取服務，這時必須指定完整網域名稱，而不要指定 localhost。 根據預設，此服務不會公開任何中繼資料。 因此，服務會開啟 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 行為。  
  
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
  
1. 確定您已 [針對 Windows Communication Foundation 範例執行一次性安裝程式](one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2. 若要建立方案，請依照 [建立 Windows Communication Foundation 範例](building-the-samples.md)中的指示進行。  
  
3. 遵循下列步驟執行範例：  
  
    1. 以滑鼠右鍵按一下 **服務** 專案，並選取 [ **設定為啟始專案**]，然後按 **Ctrl + F5**。  
  
    2. 等待主控台輸出確認服務已啟動且在執行中。  
  
    3. 以滑鼠右鍵按一下 **用戶端** 專案，並選取 [ **設定為啟始專案**]，然後按 **Ctrl + F5**。  
  
> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> 如果此目錄不存在，請移至 [Windows Communication Foundation (wcf) 並 Windows Workflow Foundation (適用于) 4 的 WF .NET Framework 範例](https://www.microsoft.com/download/details.aspx?id=21459) 下載所有 WINDOWS COMMUNICATION FOUNDATION 的 wcf (和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a>另請參閱

- [AppFabric 管理範例](/previous-versions/appfabric/ff383405(v=azure.10))
- [簡化的組態](../simplified-configuration.md)

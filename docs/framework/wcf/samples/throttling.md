---
title: "節流 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "服務行為, 節流範例"
  - "節流範例 [Windows Communication Foundation]"
ms.assetid: 40bb3582-8ae9-4410-96f0-6c515bfaf47c
caps.latest.revision: 18
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 18
---
# 節流
節流範例會示範節流控制項的用法。節流控制會限制同時呼叫、並行執行個體或工作階段的數目，以防止過度消耗資源。節流行為會指定於服務組態檔設定中。這個範例是以實作計算機服務的[使用者入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)為基礎。  
  
 在這個範例中，用戶端是主控台應用程式 \(.exe\)，而服務則是由網際網路資訊服務 \(IIS\) 所裝載。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
 服務組態檔會在[\<serviceThrottling\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicethrottling.md)中指定節流控制項，如下列範例組態所示。  
  
```  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceDebug includeExceptionDetailInFaults="False" />  
      <serviceMetadata httpGetEnabled="True"/>  
      <!-- Specify throttling behavior -->  
    <serviceThrottling maxConcurrentCalls="2"  
                       maxConcurrentInstances="10"/>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 當設定時，服務會將同時呼叫上限限制為 2，並行執行個體上限限制為 10。  
  
 為了示範節流，我們在服務方法上定義了睡眠時間，如下所示：  
  
```  
public double Add(double n1, double n2)  
{  
    System.Threading.Thread.Sleep(2000);  
    return n1 + n2;  
}  
  
```  
  
 當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。Add 和 Subtract 方法會同時執行，而 Multiply 和 Divide 方法會同時執行，如此證明了無法同時執行兩個以上的方法，並因此示範了節流。  
  
```  
  
Press <ENTER> to terminate client.  
Add(100,15.99)  
Subtract(145,76.54)  
Multiply(9,81.25)  
Divide(22,7)  
  
Add Result: 115.99  
Subtract Result: 68.46  
Multiply Result: 731.25  
Divide Result: 3.14285714285714  
  
Press any key to continue . . .  
```  
  
### 若要設定、建置及執行範例  
  
1.  請確定您已執行 [Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要建置方案的 C\# 或 Visual Basic .NET 版本，請遵循[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3.  若要在單一或跨機器的組態中執行本範例，請遵循[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的指示進行。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Throttling`  
  
## 請參閱
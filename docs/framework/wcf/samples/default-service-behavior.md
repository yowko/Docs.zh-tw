---
title: 預設服務行為
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, defaults
- Default Service Behavior Sample [Windows Communication Foundation]
ms.assetid: 442d4f71-c64e-4c62-816a-a66c38e7d3ec
ms.openlocfilehash: 8583c74f85d9638313db1779610c0f6dac9cfbe5
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43662002"
---
# <a name="default-service-behavior"></a>預設服務行為
這個範例會示範如何設定服務行為設定。 此樣本根據[快速入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)，它會實作`ICalculator`服務合約。 這個範例會使用 <xref:System.ServiceModel.ServiceBehaviorAttribute> 和 <xref:System.ServiceModel.OperationBehaviorAttribute> 屬性明確地定義服務行為與作業行為。 您可以在組態檔中設定行為，也可以在程式碼中以命令方式設定 (如這個範例所示)。  
  
 在這個範例中，用戶端是主控台應用程式 (.exe)，而服務則是由網際網路資訊服務 (IIS) 所裝載。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
 此服務類別會使用 <xref:System.ServiceModel.ServiceBehaviorAttribute> 和 <xref:System.ServiceModel.OperationBehaviorAttribute> 指定行為，如下列程式碼範例所示。 所有指定的值都是預設值。  
  
```  
[ServiceBehavior(  
    AutomaticSessionShutdown=true,  
    ConcurrencyMode=ConcurrencyMode.Single,  
    InstanceContextMode=InstanceContextMode.PerSession,  
    IncludeExceptionDetailInFaults=false,  
    UseSynchronizationContext=true,  
    ValidateMustUnderstand=true)]  
public class CalculatorService : ICalculator  
{  
    [OperationBehavior(  
        TransactionAutoComplete=true,  
        TransactionScopeRequired=false,  
        Impersonation=ImpersonationOption.NotAllowed)]  
    public double Add(double n1, double n2)  
    {  
        System.Threading.Thread.Sleep(1600);  
        return n1 + n2;  
    }  
    ...  
}  
```  
  
 服務行為是以 <xref:System.ServiceModel.ServiceBehaviorAttribute> 屬性指定。 下表會介紹其中一些行為。  
  
|服務行為|描述|  
|----------------------|-----------------|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.AutomaticSessionShutdown%2A>|在用戶端要求時自動關閉工作階段。|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>|指定每個服務執行個體的並行模式。|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>|指定執行個體內容模式。|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.UseSynchronizationContext%2A>|判定是否要使用所提供的同步化內容，如果有設定的話。 當您想要控制是否要在 Windows Form 應用程式中使用 `WindowsFormsSynchronizationContext` 時，便可使用這項功能。|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A>|判定一般未處理的執行例外狀況是否要轉換為 `Fault<string>`，並且當作錯誤訊息傳送。|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A>|指定異動的隔離等級。|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ValidateMustUnderstand%2A>|判斷未預期的訊息標頭是否會造成錯誤狀況。|  
  
 作業行為是以 <xref:System.ServiceModel.OperationBehaviorAttribute> 屬性所指定。 下表會介紹其中一些行為。  
  
|作業行為|描述|  
|------------------------|-----------------|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A>|判定服務作業完成是否會認可目前異動。|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>|判定服務作業是否會登記在用戶端流動的異動中。|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A>|判定服務作業是否會模擬呼叫者身分識別。|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A>|判定服務執行個體是否會在服務作業呼叫的開始與結束時回收。|  
  
 當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。 呼叫之間發生延遲是因為在服務作業中呼叫 `System.Threading.Thread.Sleep()`。 其他行為範例會更詳細說明這些行為。 在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3.  若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Default`  
  
## <a name="see-also"></a>另請參閱

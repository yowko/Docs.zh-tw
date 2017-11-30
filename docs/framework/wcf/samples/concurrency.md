---
title: "並行"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service behaviors, concurency sample
- Concurrency Sample [Windows Communication Foundation]
ms.assetid: f8dbdfb3-6858-4f95-abe3-3a1db7878926
caps.latest.revision: "32"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e0e6a0db5ee02f96582fe71414b620e1f78c40a1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="concurrency"></a>並行
並行範例會示範搭配 <xref:System.ServiceModel.ServiceBehaviorAttribute> 列舉使用 <xref:System.ServiceModel.ConcurrencyMode>，以控制服務的執行個體要循序處理或並行處理訊息。 範例根據[入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)，它會實作`ICalculator`服務合約。 這個範例會定義繼承自 `ICalculatorConcurrency` 的新合約 `ICalculator`，並提供兩個額外作業來檢查服務的並行狀態。 藉由改變並行設定，您可以在執行用戶端時觀察行為上的改變。  
  
 在這個範例中，用戶端是主控台應用程式 (.exe)，而服務則是由網際網路資訊服務 (IIS) 所裝載。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
 其中提供三種可用的並行模式：  
  
-   `Single`：每個服務執行個體都會一次處理一個訊息。 這是預設的並行模式。  
  
-   `Multiple`：每個服務執行個體都會並行處理多個訊息。 此服務實作必須是安全執行緒，才能使用這種並行模式。  
  
-   `Reentrant`：每個服務執行個體都會一次處理一個訊息，但是接受可重新進入 (Re-entrant) 的呼叫。 服務只有在對外呼叫時才會接受這些呼叫。示範 reentrant [ConcurrencyMode.Reentrant](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md)範例。  
  
 並存的使用與執行個體模式有關。 在 <xref:System.ServiceModel.InstanceContextMode.PerCall> 執行個體中，並行模式沒有任何相關，因為每個訊息都是由新的服務執行個體處理。 在 <xref:System.ServiceModel.InstanceContextMode.Single> 執行個體中，只有 <xref:System.ServiceModel.ConcurrencyMode.Single> 或 <xref:System.ServiceModel.ConcurrencyMode.Multiple>，並行模式才相關，這點會依單一執行個體是循序處理或並行處理訊息而定。 在 <xref:System.ServiceModel.InstanceContextMode.PerSession> 執行個體中，任何並行模式都可能相關。  
  
 此服務類別會指定具有 `[ServiceBehavior(ConcurrencyMode=<setting>)]` 屬性的並行行為，如下列程式碼範例所示。 藉由變更要標記為註解的程式碼行，您便可以體驗 `Single` 和 `Multiple` 並行模式。 請記得在變更並行模式後重建服務。  
  
```  
// Single allows a single message to be processed sequentially by each service instance.  
//[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, InstanceContextMode = InstanceContextMode.Single)]  
  
// Multiple allows concurrent processing of multiple messages by a service instance.  
// The service implementation should be thread-safe. This can be used to increase throughput.  
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple, InstanceContextMode = InstanceContextMode.Single)]  
  
// Uses Thread.Sleep to vary the execution time of each operation.  
public class CalculatorService : ICalculatorConcurrency  
{  
    int operationCount;  
  
    public double Add(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(180);  
        return n1 + n2;  
    }  
  
    public double Subtract(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(100);  
        return n1 - n2;  
    }  
  
    public double Multiply(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(150);  
        return n1 * n2;  
    }  
  
    public double Divide(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(120);  
        return n1 / n2;  
    }  
  
    public string GetConcurrencyMode()  
    {     
        // Return the ConcurrencyMode of the service.  
        ServiceHost host = (ServiceHost)OperationContext.Current.Host;  
        ServiceBehaviorAttribute behavior = host.Description.Behaviors.Find<ServiceBehaviorAttribute>();  
        return behavior.ConcurrencyMode.ToString();  
    }  
  
    public int GetOperationCount()  
    {     
        // Return the number of operations.  
        return operationCount;  
    }  
}  
```  
  
 此範例預設會搭配 <xref:System.ServiceModel.ConcurrencyMode.Multiple> 執行個體使用 <xref:System.ServiceModel.InstanceContextMode.Single> 並行。 用戶端程式碼已修改成使用非同步 Proxy。 這樣可以讓用戶端多次呼叫服務，而不用在每次呼叫之間等候回應。 您可以觀察服務並行模式之行為的差異。  
  
 當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。 這時會顯示用於執行服務的並行模式，同時呼叫每個作業，並接著顯示作業計數。 請注意，當並行模式為 `Multiple` 時，因為服務是同時處理多個訊息，所以結果的傳回順序會有別於作業的呼叫順序。 藉由將並行模式變更為 `Single`，因為服務會循序處理每個訊息，所以結果的傳回順序就會相同於作業的呼叫順序。 在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  如果您使用 Svcutil.exe 來產生 proxy 用戶端，請確定您包含`/async`選項。  
  
3.  若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
4.  若要在單一或跨電腦組態中執行範例時，請依照中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Concurrency`  
  
## <a name="see-also"></a>另請參閱

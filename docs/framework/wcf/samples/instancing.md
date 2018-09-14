---
title: 執行個體
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, instancing sample
- Instancing Sample [Windows Communication Foundation]
ms.assetid: c290fa54-f6ae-45a1-9186-d9504ebc6ee6
ms.openlocfilehash: 1d193b0cac56f365a4f0a294145369502754a1b1
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "44756804"
---
# <a name="instancing"></a>執行個體
執行個體範例會示範執行個體行為設定，此設定會控制如何建立可回應用戶端需求的服務類別執行個體。 此樣本根據[快速入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)，它會實作`ICalculator`服務合約。 這個範例會定義繼承自 `ICalculatorInstance` 的新合約 `ICalculator`。 由 `ICalculatorInstance` 指定的合約會提供三種額外作業以檢查服務執行個體的狀態。 藉由改變執行個體設定，您可以在執行用戶端時觀察行為上的改變。  
  
 在這個範例中，用戶端是主控台應用程式 (.exe)，而服務則是由網際網路資訊服務 (IIS) 所裝載。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
 以下為可用的執行個體模式：  
  
-   <xref:System.ServiceModel.InstanceContextMode.PerCall>：為每個用戶端要求建立新的服務執行個體。  
  
-   <xref:System.ServiceModel.InstanceContextMode.PerSession>：為每個新用戶端工作階段建立新執行個體，並在該工作階段之存留期進行維護 (需要支援工作階段的繫結)。  
  
-   <xref:System.ServiceModel.InstanceContextMode.Single>：服務類別的單一執行個體，負責處理應用程式之存留期時的所有用戶端要求。  
  
 此服務類別會指定具有 `[ServiceBehavior(InstanceContextMode=<setting>)]` 屬性的執行個體行為，如下列程式碼範例所示。 藉由將程式碼行標記為註解，您便可以觀察到每個執行個體模式的行為。 請記得在變更執行個體模式後重建服務。 這時並不需要在用戶端上指定任何與執行個體相關的設定。  
  
```  
// Enable one of the following instance modes to compare instancing behaviors.  
 [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
  
// PerCall creates a new instance for each operation.  
//[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerCall)]  
  
// Singleton creates a single instance for application lifetime.  
//[ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
public class CalculatorService : ICalculatorInstance  
{  
    static Object syncObject = new object();  
    static int instanceCount;  
    int instanceId;  
    int operationCount;  
  
    public CalculatorService()  
    {  
        lock (syncObject)  
        {  
            instanceCount++;  
            instanceId = instanceCount;  
        }  
    }  
  
    public double Add(double n1, double n2)  
    {  
        operationCount++;  
        return n1 + n2;  
    }  
  
    public double Subtract(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 - n2;  
    }  
  
    public double Multiply(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 * n2;  
    }  
  
    public double Divide(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 / n2;  
    }  
  
    public string GetInstanceContextMode()  
    {   // Return the InstanceContextMode of the service  
        ServiceHost host = (ServiceHost)OperationContext.Current.Host;  
        ServiceBehaviorAttribute behavior = host.Description.Behaviors.Find<ServiceBehaviorAttribute>();  
        return behavior.InstanceContextMode.ToString();  
    }  
  
    public int GetInstanceId()  
    {   // Return the id for this instance  
        return instanceId;  
    }  
  
    public int GetOperationCount()  
    {   // Return the number of ICalculator operations performed   
        // on this instance  
        lock (syncObject)  
        {  
            return operationCount;  
        }  
    }  
}  
  
static void Main()  
{  
    // Create a client.  
    CalculatorInstanceClient client = new CalculatorInstanceClient();  
    string instanceMode = client.GetInstanceContextMode();  
    Console.WriteLine("InstanceContextMode: {0}", instanceMode);  
    DoCalculations(client);  
  
    // Create a second client.  
    CalculatorInstanceClient client2 = new CalculatorInstanceClient();  
  
    DoCalculations(client2);  
  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
}  
```  
  
 當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。 服務正在執行的執行個體模式會顯示出來。 在完成每個作業後，會顯示執行個體識別碼與作業計數以反映執行個體模式的行為。 在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。  
  
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
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Instancing`  
  
## <a name="see-also"></a>另請參閱

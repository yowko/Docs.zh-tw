---
title: 單向
ms.date: 03/30/2017
ms.assetid: 74e3e03d-cd15-4191-a6a5-1efa2dcb9e73
ms.openlocfilehash: f392fad0461dab4dff6e5e4efe0070d7017a700b
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039048"
---
# <a name="one-way"></a>單向
這個範例示範具有單向服務作業的服務合約。 與雙向服務作業的情況不同，用戶端不會等候服務作業完成。 這個範例是以[消費者入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)為基礎, 並使用`wsHttpBinding`系結。 這個範例中的服務是自我裝載的主控台應用程式，您可以用來觀察接收和處理要求的服務。 用戶端也是主控台應用程式。  
  
> [!NOTE]
> 此範例的安裝程序與建置指示位於本主題的結尾。  
  
 若要建立單向服務合約，請定義服務合約、將 <xref:System.ServiceModel.OperationContractAttribute> 類別套用至每一項作業，然後將 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> 設定為 `true`，如下列範例程式碼所示：  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOneWayCalculator  
{  
    [OperationContract(IsOneWay=true)]  
    void Add(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Subtract(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Multiply(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Divide(double n1, double n2);  
}  
```  
  
 為了示範用戶端不等待服務作業完成的狀況，本範例中的服務程式碼實作了五秒鐘的延遲，如下列範例程式碼所示：  
  
```csharp
// This service class implements the service contract.  
// This code writes output to the console window.  
 [ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Multiple,  
    InstanceContextMode = InstanceContextMode.PerCall)]  
public class CalculatorService : IOneWayCalculator  
{  
    public void Add(double n1, double n2)  
    {  
        Console.WriteLine("Received Add({0},{1}) - sleeping", n1, n2);  
        System.Threading.Thread.Sleep(1000 * 5);  
        double result = n1 + n2;  
        Console.WriteLine("Processing Add({0},{1}) - result: {2}", n1, n2, result);  
    }  
    ...  
}  
```  
  
 當用戶端呼叫服務時，該呼叫會逕自傳回，而不等待服務作業完成。  
  
 當您執行範例時，用戶端與服務活動都會顯示在服務與用戶端主控台視窗中。 您可以查看來自用戶端的服務接收訊息。 請在每個主控台視窗中按下 ENTER，以關閉服務與用戶端。  
  
 用戶端會比服務先完成，表示用戶端不會等候單向服務作業完成。 用戶端輸出如下：  
  
```console  
Add(100,15.99)  
Subtract(145,76.54)  
Multiply(9,81.25)  
Divide(22,7)  
  
Press <ENTER> to terminate client.  
```  
  
 服務輸出如下：  
  
```console  
The service is ready.  
Press <ENTER> to terminate service.  
  
Received Add(100,15.99) - sleeping  
Received Subtract(145,76.54) - sleeping  
Received Multiply(9,81.25) - sleeping  
Received Divide(22,7) - sleeping  
Processing Add(100,15.99) - result: 115.99  
Processing Subtract(145,76.54) - result: 68.46  
Processing Multiply(9,81.25) - result: 731.25  
Processing Divide(22,7) - result: 3.14285714285714  
```  
  
> [!NOTE]
> 根據定義，HTTP 是一種要求/回應通訊協定；當要求提出時，就會傳回回應。 即便是在 HTTP 上公開的單向服務作業，也是如此。 呼叫作業時，服務會在服務作業執行以前傳回 202 的 HTTP 狀態碼。 這個狀態碼表示已接受要求進行處理，但是處理尚未完成。 呼叫此項作業的用戶端會封鎖，直到從服務收到 202 回應為止。 當使用設定為使用工作階段的繫結來傳送多則單向訊息時，這可能會產生某種未預期的行為。 根據預設，這個範例中使用的 `wsHttpBinding` 繫結會設定為使用工作階段，以便建立安全性內容。 在預設情況下，將保證工作階段中的訊息依照傳送的順序抵達。 因此，傳送工作階段中的第二則訊息時，就不會在第一則訊息處理完成之前加以處理。 因此，除非完成處理上一則的訊息，否則，用戶端將不會收到訊息的 202 回應。 所以用戶端會顯示為封鎖每次呼叫後續的作業。 為了避免這種行為，此範例將執行階段設定為同時分派訊息至不同執行個體以進行處理。 範例將 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> 設定為 `PerCall`，讓個別訊息可以分別由不同執行個體來處理。 <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> 會設定為 `Multiple`，以允許多個執行緒同時分派訊息。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 請確定您已[針對 Windows Communication Foundation 範例執行一次安裝程式](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2. 若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3. 若要在單一或跨電腦設定中執行範例, 請遵循執行[Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的指示。  
  
> [!NOTE]
> 請先執行服務，然後才執行用戶端；先關閉用戶端，再關閉服務。 這可以避免當用戶端因服務消失而無法正常關閉安全性工作階段時，所發生的用戶端例外狀況。  
  
> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> 如果此目錄不存在, 請移至[.NET Framework 4 的 Windows Communication Foundation (wcf) 和 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780), 以下載所有 Windows Communication Foundation (wcf) [!INCLUDE[wf1](../../../../includes/wf1-md.md)]和範例。 此範例位於下列目錄。  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Oneway`  

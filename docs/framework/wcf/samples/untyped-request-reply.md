---
title: 不具類型的要求-回覆
ms.date: 03/30/2017
ms.assetid: 0bf0f9d9-7caf-4d3d-8c9e-2d468cca16a5
ms.openlocfilehash: 2eb6a46d339c9277c1622c0cc16d057b186f1d79
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54612745"
---
# <a name="untyped-requestreply"></a>不具型別的要求/回覆
這個範例會示範如何定義使用 Message 類別的作業合約。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
 此樣本根據[開始使用](../../../../docs/framework/wcf/samples/getting-started-sample.md)。 此服務合約會定義將訊息類型當做引數接受並傳回訊息的作業。 此作業會收集所有必要資料來計算訊息本文的總和，然後將該總和當做傳回訊息中的本文加以傳送。  
  
```csharp
[OperationContract(Action = CalculatorService.RequestAction, ReplyAction = CalculatorService.ReplyAction)]  
Message ComputeSum(Message request);  
```  
  
 在進行此服務時，該作業會擷取輸入訊息中所傳遞之整數的陣列，然後計算出總和。 為了傳送回應訊息，此範例會建立包含適當的訊息版本和動作的新訊息，並將計算得到的總和當做本文加入至該訊息。 下列範例程式碼示範這項功能。  
  
```csharp
public Message ComputeSum(Message request)  
{  
    //The body of the message contains a list of numbers which will be   
    //read as a int[] using GetBody<T>  
    int result = 0;  
  
    int[] inputs = request.GetBody<int[]>();  
    foreach (int i in inputs)  
    {  
        result += i;  
    }  
  
    Message response = Message.CreateMessage(request.Version,   
                                      ReplyAction, result);  
    return response;  
}  
```  
  
 用戶端會使用產生的程式碼[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)建立遠端服務的 proxy。 為了傳送要求訊息，用戶端必須具備依基礎通道而定的訊息版本。 如此一來，它會建立範圍限定在其所建立之 Proxy 通道的新 <xref:System.ServiceModel.OperationContextScope>，而此新範圍會依據其 <xref:System.ServiceModel.OperationContext> 屬性中所填入之正確訊息版本來建立 `OutgoingMessageHeaders.MessageVersion`。 用戶端會將輸入陣列當做本文傳遞到要求訊息，然後叫用 Proxy 上的 `ComputeSum`。 接著，用戶端會藉由存取回覆訊息的 `GetBody<T>` 方法，擷取其所傳遞的輸入總和。 下列範例程式碼示範這項功能。  
  
```csharp
using (new OperationContextScope(client.InnerChannel))  
{  
    // Call the Sum service operation.  
    int[] values = { 1, 2, 3, 4, 5 };  
    Message request = Message.CreateMessage(  
        OperationContext.Current.OutgoingMessageHeaders.MessageVersion,   
        RequestAction, values);  
    Message reply = client.ComputeSum(request);  
    int response = reply.GetBody<int>();  
  
    Console.WriteLine("Sum of numbers passed (1,2,3,4,5) = {0}",   
                                                       response);  
}  
```  
  
 這個範例是 Web 主控的範例，所以只需要執行用戶端可執行檔。 下列是用戶端的輸出範例。  
  
```console  
Prompt>Client.exe  
Sum of numbers passed (1,2,3,4,5) = 15  
  
Press <ENTER> to terminate client.  
```  
  
 這個範例是 Web 主控的範例，所以請檢查步驟 3 提供的連結以得知如何建置與執行範例。  
  
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
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Untyped`  
  
## <a name="see-also"></a>另請參閱

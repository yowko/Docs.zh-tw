---
title: 預設訊息合約
ms.date: 03/30/2017
helpviewer_keywords:
- Message Contract
ms.assetid: 5a200b78-1a46-4104-b7fb-da6dbab33893
ms.openlocfilehash: 23ab534ef31773efc69b6a68e73ec30bde4f6e61
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43502655"
---
# <a name="default-message-contract"></a>預設訊息合約
預設訊息合約範例會示範一個服務，在這個服務中可以對服務作業來回傳遞自訂的使用者定義訊息。 此樣本根據[開始使用](../../../../docs/framework/wcf/samples/getting-started-sample.md)會實作計算機介面做為具類型的服務。 而不是加法、 減法、 乘法和除法中使用的個別服務作業[開始使用](../../../../docs/framework/wcf/samples/getting-started-sample.md)，此範例會傳遞包含運算元和運算子，並傳回的自訂訊息算術計算的結果。  
  
 用戶端是主控台程式 (.exe)，而服務程式庫 (.dll) 是由網際網路資訊服務 (IIS) 所裝載。 您可以在主控台視窗中看到用戶端活動。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
 在服務中，會定義單一服務作業，而這個作業會接受並傳回型別為 `MyMessage` 的自訂訊息。 雖然這個範例中的要求和回應訊息型別相同，但在必要時一定是不同的訊息合約。  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract(Action="http://test/MyMessage_action",  
                  ReplyAction="http://test/MyMessage_action")]  
    MyMessage Calculate(MyMessage request);  
}  
```  
  
 自訂訊息 `MyMessage` 是定義在以 <xref:System.ServiceModel.MessageContractAttribute>、<xref:System.ServiceModel.MessageHeaderAttribute> 和 <xref:System.ServiceModel.MessageBodyMemberAttribute> 屬性註解的類別中。 這個範例中只使用了第三個建構函式。 使用訊息合約可讓您完全控制 SOAP 訊息。 在這個範例中，會使用 <xref:System.ServiceModel.MessageHeaderAttribute> 屬性，將 `Operation` 放在 SOAP 標頭中。 因為運算元 `N1`、`N2` 和 `Result` 都套用了 <xref:System.ServiceModel.MessageBodyMemberAttribute> 屬性，所以會出現在 SOAP 本文中。  
  
```  
[MessageContract]  
public class MyMessage  
{  
    private string operation;  
    private double n1;  
    private double n2;  
    private double result;  
  
    //Constructor - create an empty message.  
  
    public MyMessage() {}  
  
    //Constructor - create a message and populate its members.  
  
    public MyMessage(double n1, double n2, string operation,   
                     double result)  
    {  
        this.n1 = n1;  
        this.n2 = n2;  
        this.operation = operation;  
        this.result = result;  
    }  
  
    //Constructor - create a message from another message.  
  
    public MyMessage(MyMessage message)  
    {  
        this.n1 = message.n1;  
        this.n2 = message.n2;  
        this.operation = message.operation;  
        this.result = message.result;  
    }  
  
    [MessageHeader]  
    public string Operation  
    {  
        get { return operation; }  
        set { operation = value; }  
    }  
  
    [MessageBodyMember]  
    public double N1  
    {  
        get { return n1; }  
        set { n1 = value; }  
    }  
  
    [MessageBodyMember]  
    public double N2  
    {  
        get { return n2; }  
        set { n2 = value; }  
    }  
  
    [MessageBodyMember]  
    public double Result  
    {  
        get { return result; }  
        set { result = value; }  
    }  
}  
```  
  
 實作類別包含 `Calculate` 服務作業的程式碼。 `CalculateService` 類別會從要求訊息中取得運算元和運算子，然後建立包含所要求之計算結果的回應訊息，如下列範例程式碼所示。  
  
```  
// Service class which implements the service contract.  
public class CalculatorService : ICalculator  
{  
    // Perform a calculation.  
  
    public MyMessage Calculate(MyMessage request)  
    {  
        MyMessage response = new MyMessage(request);  
        switch (request.Operation)  
        {  
            case "+":  
                response.Result = request.N1 + request.N2;  
                break;  
            case "-":  
                response.Result = request.N1 - request.N2;  
                break;  
            case "*":  
                response.Result = request.N1 * request.N2;  
                break;  
            case "/":  
                response.Result = request.N1 / request.N2;  
                break;  
            default:  
                response.Result = 0.0D;  
                break;  
        }  
        return response;  
    }  
}  
```  
  
 用戶端產生的用戶端程式碼經由[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)工具。 必要時，這個工具會自動在產生的用戶端程式碼中建立訊息合約類型。 您也可以指定 `/messageContract` 命令選項來強制產生訊息合約。  
  
```  
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" /o:client\generatedClient.cs http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 下列範例程式碼示範使用 `MyMessage` 訊息的用戶端。  
  
```  
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
// Perform addition using a typed message.  
  
MyMessage request = new MyMessage();  
request.N1 = 100D;  
request.N2 = 15.99D;  
request.Operation = "+";  
MyMessage response = ((ICalculator)client).Calculate(request);  
Console.WriteLine("Add({0},{1}) = {2}", request.N1, request.N2, response.Result);  
```  
  
 當您執行範例時，計算過程會顯示在用戶端主控台視窗中。 在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 此時，自訂的使用者定義訊息已在用戶端和服務作業之間傳遞。 訊息合約已定義將運算元和結果放在訊息本文中，而將運算子放在訊息標頭中。 您可以設定訊息記錄來觀察這個訊息結構。  
  
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
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Default`  
  
## <a name="see-also"></a>另請參閱

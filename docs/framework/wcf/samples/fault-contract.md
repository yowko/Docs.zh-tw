---
title: "錯誤合約 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b31b140e-dc3b-408b-b3c7-10b6fe769725
caps.latest.revision: 16
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 16
---
# 錯誤合約
錯誤合約範例會示範如何在服務與用戶端之間傳達錯誤資訊。  此範例是以[使用者入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)為基礎，並在服務新增一些額外程式碼，以便將內部例外狀況轉換為錯誤。  用戶端會嘗試執行除數為零，以便強制在服務上造成錯誤狀況。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
 計算機合約已修改成包含 <xref:System.ServiceModel.FaultContractAttribute>，如下列範例程式碼所示。  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    int Add(int n1, int n2);  
    [OperationContract]  
    int Subtract(int n1, int n2);  
    [OperationContract]  
    int Multiply(int n1, int n2);  
    [OperationContract]  
    [FaultContract(typeof(MathFault))]  
    int Divide(int n1, int n2);  
}  
```  
  
 <xref:System.ServiceModel.FaultContractAttribute> 屬性表示 `Divide` 作業會傳回 `MathFault` 類型的錯誤。  錯誤可能是能夠序列化的任何類型。  在此範例中，`MathFault` 是資料合約，如下列所示：  
  
```  
[DataContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public class MathFault  
{      
    private string operation;  
    private string problemType;  
  
    [DataMember]  
    public string Operation  
    {  
        get { return operation; }  
        set { operation = value; }  
    }  
  
    [DataMember]          
    public string ProblemType  
    {  
        get { return problemType; }  
        set { problemType = value; }  
    }  
}  
  
```  
  
 當發生除數為零的例外狀況時，`Divide` 方法會擲回 <xref:System.ServiceModel.FaultException%601> 例外狀況，如下列範例程式碼所示。  這個例外狀況會造成傳送至用戶端的錯誤。  
  
```  
public int Divide(int n1, int n2)  
{  
    try  
    {  
        return n1 / n2;  
    }  
    catch (DivideByZeroException)  
    {  
        MathFault mf = new MathFault();  
        mf.operation = "division";  
        mf.problemType = "divide by zero";  
        throw new FaultException<MathFault>(mf);  
    }  
}  
```  
  
 此用戶端程式碼會藉由要求除數為零強制發生錯誤。  當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。  這個除數為零狀況將被報告為錯誤。  在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。  
  
```  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
FaultException<MathFault>: Math fault while doing division. Problem: divide by zero  
  
Press <ENTER> to terminate client.  
```  
  
 用戶端會藉由攔截適當的 `FaultException<MathFault>` 例外狀況來執行這項動作：  
  
```  
catch (FaultException<MathFault> e)  
{  
    Console.WriteLine("FaultException<MathFault>: Math fault while doing " + e.Detail.operation + ". Problem: " + e.Detail.problemType);  
    client.Abort();  
}  
```  
  
 根據預設，未預期之例外狀況的詳細資訊並不會傳送到用戶端，以避免服務實作的詳細資訊逸出服務的安全界限。  `FaultContract` 提供方法說明合約中的錯誤，並將某些例外狀況類型標記為適合傳輸至用戶端。  `FaultException<T>` 會提供將錯誤傳送至取用者的執行階段機制。  
  
 但是，在偵錯時檢視服務失敗的內部詳細資訊是很有用的。  若要關閉之前描述的安全行為，您可以指示在伺服器上的每個未處理例外狀況的詳細資訊是否應該要包含在傳送至用戶端的錯誤中。  這是透過將 <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> 設定為 `true` 所完成的。  您可以透過程式碼或組態來設定它，如下列範例所示。  
  
```  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="True" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 此外，必須透過將組態檔中的服務 `behaviorConfiguration` 屬性設定為 “CalculatorServiceBehavior”，使行為與服務產生關聯。  
  
 為了攔截用戶端上的這類錯誤，此時必須攔截非泛型的 <xref:System.ServiceModel.FaultException>。  
  
 這個行為應該只用於偵錯用途，而絕對不可啟用於實際執行環境中。  
  
### 若要安裝、建置及執行範例  
  
1.  請確定您已執行 [Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要建置方案的 C\# 或 Visual Basic .NET 版本，請遵循[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3.  若要在單一或跨機器的組態中執行本範例，請遵循[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的指示進行。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。  請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。  此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Faults`  
  
## 請參閱
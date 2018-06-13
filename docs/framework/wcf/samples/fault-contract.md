---
title: 錯誤合約
ms.date: 03/30/2017
ms.assetid: b31b140e-dc3b-408b-b3c7-10b6fe769725
ms.openlocfilehash: 37b9d7e3ec2135d60215232fae114baef1b54f36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33504155"
---
# <a name="fault-contract"></a><span data-ttu-id="4d940-102">錯誤合約</span><span class="sxs-lookup"><span data-stu-id="4d940-102">Fault Contract</span></span>
<span data-ttu-id="4d940-103">錯誤合約範例會示範如何在服務與用戶端之間傳達錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="4d940-103">The Fault Contract sample demonstrates how to communicate error information from a service to a client.</span></span> <span data-ttu-id="4d940-104">範例根據[入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)，與其他程式碼加入至服務，以將內部例外狀況轉換為錯誤。</span><span class="sxs-lookup"><span data-stu-id="4d940-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), with some additional code added to the service to convert an internal exception to a fault.</span></span> <span data-ttu-id="4d940-105">用戶端會嘗試執行除數為零，以便強制在服務上造成錯誤狀況。</span><span class="sxs-lookup"><span data-stu-id="4d940-105">The client attempts to perform division by zero to force an error condition on the service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4d940-106">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="4d940-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="4d940-107">計算機合約已修改成包含 <xref:System.ServiceModel.FaultContractAttribute>，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="4d940-107">The calculator contract has been modified to include a <xref:System.ServiceModel.FaultContractAttribute> as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="4d940-108"><xref:System.ServiceModel.FaultContractAttribute> 屬性表示 `Divide` 作業會傳回 `MathFault` 類型的錯誤。</span><span class="sxs-lookup"><span data-stu-id="4d940-108">The <xref:System.ServiceModel.FaultContractAttribute> attribute indicates that the `Divide` operation may return a fault of type `MathFault`.</span></span> <span data-ttu-id="4d940-109">錯誤可能是能夠序列化的任何類型。</span><span class="sxs-lookup"><span data-stu-id="4d940-109">A fault can be of any type that can be serialized.</span></span> <span data-ttu-id="4d940-110">在此範例中，`MathFault` 是資料合約，如下列所示：</span><span class="sxs-lookup"><span data-stu-id="4d940-110">In this case, the `MathFault` is a data contract, as follows:</span></span>  
  
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
  
 <span data-ttu-id="4d940-111">當發生除數為零的例外狀況時，`Divide` 方法會擲回 <xref:System.ServiceModel.FaultException%601> 例外狀況，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="4d940-111">The `Divide` method throws a <xref:System.ServiceModel.FaultException%601> exception when a divide by zero exception occurs as shown in the following sample code.</span></span> <span data-ttu-id="4d940-112">這個例外狀況會造成傳送至用戶端的錯誤。</span><span class="sxs-lookup"><span data-stu-id="4d940-112">This exception results in a fault being sent to the client.</span></span>  
  
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
  
 <span data-ttu-id="4d940-113">此用戶端程式碼會藉由要求除數為零強制發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="4d940-113">The client code forces an error by requesting a division by zero.</span></span> <span data-ttu-id="4d940-114">當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="4d940-114">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="4d940-115">這個除數為零狀況將被報告為錯誤。</span><span class="sxs-lookup"><span data-stu-id="4d940-115">You see the division by zero being reported as a fault.</span></span> <span data-ttu-id="4d940-116">在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="4d940-116">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
FaultException<MathFault>: Math fault while doing division. Problem: divide by zero  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="4d940-117">用戶端會藉由攔截適當的 `FaultException<MathFault>` 例外狀況來執行這項動作：</span><span class="sxs-lookup"><span data-stu-id="4d940-117">The client does this by catching the appropriate `FaultException<MathFault>` exception:</span></span>  
  
```  
catch (FaultException<MathFault> e)  
{  
    Console.WriteLine("FaultException<MathFault>: Math fault while doing " + e.Detail.operation + ". Problem: " + e.Detail.problemType);  
    client.Abort();  
}  
```  
  
 <span data-ttu-id="4d940-118">根據預設，未預期之例外狀況的詳細資訊並不會傳送到用戶端，以避免服務實作的詳細資訊逸出服務的安全界限。</span><span class="sxs-lookup"><span data-stu-id="4d940-118">By default, the details of unexpected exceptions are not sent to the client to prevent details of the service implementation from escaping the secure boundary of the service.</span></span> <span data-ttu-id="4d940-119">`FaultContract` 提供方法說明合約中的錯誤，並將某些例外狀況類型標記為適合傳輸至用戶端。</span><span class="sxs-lookup"><span data-stu-id="4d940-119">`FaultContract` provides a way to describe faults in a contract and mark certain types of exceptions as appropriate for transmission to the client.</span></span> <span data-ttu-id="4d940-120">`FaultException<T>` 會提供將錯誤傳送至取用者的執行階段機制。</span><span class="sxs-lookup"><span data-stu-id="4d940-120">`FaultException<T>` provides the run-time mechanism for sending faults to consumers.</span></span>  
  
 <span data-ttu-id="4d940-121">但是，在偵錯時檢視服務失敗的內部詳細資訊是很有用的。</span><span class="sxs-lookup"><span data-stu-id="4d940-121">However, it is useful to see the internal details of a service failure when debugging.</span></span> <span data-ttu-id="4d940-122">若要關閉之前描述的安全行為，您可以指示在伺服器上的每個未處理例外狀況的詳細資訊是否應該要包含在傳送至用戶端的錯誤中。</span><span class="sxs-lookup"><span data-stu-id="4d940-122">To turn off the secure behavior previously described, you can indicate that the details of every unhandled exception on the server should be included in the fault that is sent to the client.</span></span> <span data-ttu-id="4d940-123">這是透過將 <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> 設定為 `true` 所完成的。</span><span class="sxs-lookup"><span data-stu-id="4d940-123">This is accomplished by setting <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> to `true`.</span></span> <span data-ttu-id="4d940-124">您可以透過程式碼或組態來設定它，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="4d940-124">You can either set it in code, or in configuration as shown in the following sample.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="True" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="4d940-125">此外，行為必須與相關聯的服務設定`behaviorConfiguration`"CalculatorServiceBehavior"組態檔案中的服務屬性。</span><span class="sxs-lookup"><span data-stu-id="4d940-125">Further, the behavior must be associated with the service by setting the `behaviorConfiguration` attribute of the service in the configuration file to "CalculatorServiceBehavior".</span></span>  
  
 <span data-ttu-id="4d940-126">為了攔截用戶端上的這類錯誤，此時必須攔截非泛型的 <xref:System.ServiceModel.FaultException>。</span><span class="sxs-lookup"><span data-stu-id="4d940-126">To catch such faults on the client, the non-generic <xref:System.ServiceModel.FaultException> must be caught.</span></span>  
  
 <span data-ttu-id="4d940-127">這個行為應該只用於偵錯用途，而絕對不可啟用於實際執行環境中。</span><span class="sxs-lookup"><span data-stu-id="4d940-127">This behavior should only be used for debugging purposes and should never be enabled in production.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4d940-128">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="4d940-128">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="4d940-129">請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="4d940-129">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="4d940-130">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="4d940-130">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="4d940-131">若要在單一或跨電腦組態中執行範例時，請依照中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="4d940-131">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4d940-132">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="4d940-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4d940-133">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="4d940-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4d940-134">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="4d940-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4d940-135">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="4d940-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Faults`  
  
## <a name="see-also"></a><span data-ttu-id="4d940-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d940-136">See Also</span></span>

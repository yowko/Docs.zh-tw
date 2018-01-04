---
title: "工作階段"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Sessions
ms.assetid: 36e1db50-008c-4b32-8d09-b56e790b8417
caps.latest.revision: "31"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 46994828124452d00ae74c30142dd62c52000b39
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="session"></a><span data-ttu-id="e12f1-102">工作階段</span><span class="sxs-lookup"><span data-stu-id="e12f1-102">Session</span></span>
<span data-ttu-id="e12f1-103">工作階段範例會示範如何實作需要工作階段的合約。</span><span class="sxs-lookup"><span data-stu-id="e12f1-103">The Session sample demonstrates how to implement a contract that requires a session.</span></span> <span data-ttu-id="e12f1-104">工作階段提供執行多個作業的內容。</span><span class="sxs-lookup"><span data-stu-id="e12f1-104">A session provides context for performing multiple operations.</span></span> <span data-ttu-id="e12f1-105">這可以讓服務將狀態與指定工作階段相關聯，如此一來後續作業就能夠使用之前作業的狀態。</span><span class="sxs-lookup"><span data-stu-id="e12f1-105">This allows a service to associate state with a given session, such that subsequent operations can use the state of a previous operation.</span></span> <span data-ttu-id="e12f1-106">這個範例根據[入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)，它會實作計算機服務。</span><span class="sxs-lookup"><span data-stu-id="e12f1-106">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements a calculator service.</span></span> <span data-ttu-id="e12f1-107">`ICalculator` 合約已修改成允許執行一組算數運算，並同時保留執行結果。</span><span class="sxs-lookup"><span data-stu-id="e12f1-107">The `ICalculator` contract has been modified to allow a set of arithmetic operations to be performed, while keeping a running result.</span></span> <span data-ttu-id="e12f1-108">`ICalculatorSession` 合約會定義這項功能。</span><span class="sxs-lookup"><span data-stu-id="e12f1-108">This functionality is defined by the `ICalculatorSession` contract.</span></span> <span data-ttu-id="e12f1-109">此服務會維護用戶端的狀態，因為在進行計算時已呼叫了多個服務作業。</span><span class="sxs-lookup"><span data-stu-id="e12f1-109">The service maintains the state for a client as multiple service operations are called to perform a calculation.</span></span> <span data-ttu-id="e12f1-110">用戶端會呼叫 `Result()` 以擷取目前的結果，並且呼叫 `Clear()` 將結果清除為零。</span><span class="sxs-lookup"><span data-stu-id="e12f1-110">The client can retrieve the current result by calling `Result()` and clear the result to zero by calling `Clear()`.</span></span>  
  
 <span data-ttu-id="e12f1-111">在這個範例中，用戶端是主控台應用程式 (.exe)，而服務則是由網際網路資訊服務 (IIS) 所裝載。</span><span class="sxs-lookup"><span data-stu-id="e12f1-111">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e12f1-112">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="e12f1-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="e12f1-113">將合約的 <xref:System.ServiceModel.SessionMode> 設定為 `Required`，可以確定當合約透過特定繫結公開時，該繫結能夠支援工作階段。</span><span class="sxs-lookup"><span data-stu-id="e12f1-113">Setting the <xref:System.ServiceModel.SessionMode> of the contract to `Required` ensures that when the contract is exposed over a particular binding, the binding supports sessions.</span></span> <span data-ttu-id="e12f1-114">如果繫結不支援工作階段，就會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e12f1-114">If the binding does not support sessions an exception is thrown.</span></span> <span data-ttu-id="e12f1-115">`ICalculatorSession` 介面已定義為可以呼叫一或多個作業以修改執行結果，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="e12f1-115">The `ICalculatorSession` interface is defined such that one or more operations can be called, which modifies a running result, as shown in the following sample code.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples", SessionMode=SessionMode.Required)]  
public interface ICalculatorSession  
{  
    [OperationContract(IsOneWay=true)]  
    void Clear();  
    [OperationContract(IsOneWay = true)]  
    void AddTo(double n);  
    [OperationContract(IsOneWay = true)]  
    void SubtractFrom(double n);  
    [OperationContract(IsOneWay = true)]  
    void MultiplyBy(double n);  
    [OperationContract(IsOneWay = true)]  
    void DivideBy(double n);  
    [OperationContract]  
    double Result();  
}  
```  
  
 <span data-ttu-id="e12f1-116">服務會使用 <xref:System.ServiceModel.InstanceContextMode> 的 <xref:System.ServiceModel.InstanceContextMode.PerSession>，將指定的服務執行個體內容繫結至每個傳入工作階段。</span><span class="sxs-lookup"><span data-stu-id="e12f1-116">The service uses a <xref:System.ServiceModel.InstanceContextMode> of <xref:System.ServiceModel.InstanceContextMode.PerSession> to bind a given service instance context to each incoming session.</span></span> <span data-ttu-id="e12f1-117">這樣服務便可在本機成員變數中維護每個工作階段的執行結果。</span><span class="sxs-lookup"><span data-stu-id="e12f1-117">This allows the service to maintain the running result for each session in a local member variable.</span></span>  
  
```  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
public class CalculatorService : ICalculatorSession  
{  
    double result = 0.0D;  
  
    public void Clear()  
    {  result = 0.0D; }  
  
    public void AddTo(double n)  
    {  result += n;   }  
  
    public void SubtractFrom(double n)  
    {  result -= n;   }  
  
    public void MultiplyBy(double n)  
    {  result *= n;   }  
  
    public void DivideBy(double n)  
    {  result /= n;   }  
  
    public double Result()  
    {  return result; }  
}  
```  
  
 <span data-ttu-id="e12f1-118">當您執行此範例時，用戶端會對伺服器提出幾個要求並要求結果，而該結果接著會顯示在用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="e12f1-118">When you run the sample, the client makes several requests to the server and requests the result, which it then displays in the client console window.</span></span> <span data-ttu-id="e12f1-119">在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="e12f1-119">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
(((0 + 100) - 50) * 17.65) / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e12f1-120">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="e12f1-120">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="e12f1-121">請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="e12f1-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="e12f1-122">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="e12f1-122">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="e12f1-123">若要在單一或跨電腦組態中執行範例時，請依照中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="e12f1-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e12f1-124">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="e12f1-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e12f1-125">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="e12f1-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e12f1-126">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="e12f1-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e12f1-127">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="e12f1-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Session`  
  
## <a name="see-also"></a><span data-ttu-id="e12f1-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="e12f1-128">See Also</span></span>

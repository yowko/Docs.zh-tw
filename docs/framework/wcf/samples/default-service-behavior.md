---
title: "預設服務行為"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service behaviors, defaults
- Default Service Behavior Sample [Windows Communication Foundation]
ms.assetid: 442d4f71-c64e-4c62-816a-a66c38e7d3ec
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d6b693c2030cd5da1aac49b9bb87d2eac3630627
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="default-service-behavior"></a><span data-ttu-id="f6895-102">預設服務行為</span><span class="sxs-lookup"><span data-stu-id="f6895-102">Default Service Behavior</span></span>
<span data-ttu-id="f6895-103">這個範例會示範如何設定服務行為設定。</span><span class="sxs-lookup"><span data-stu-id="f6895-103">This sample demonstrates how service behavior settings can be configured.</span></span> <span data-ttu-id="f6895-104">範例根據[入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)，它會實作`ICalculator`服務合約。</span><span class="sxs-lookup"><span data-stu-id="f6895-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="f6895-105">這個範例會使用 <xref:System.ServiceModel.ServiceBehaviorAttribute> 和 <xref:System.ServiceModel.OperationBehaviorAttribute> 屬性明確地定義服務行為與作業行為。</span><span class="sxs-lookup"><span data-stu-id="f6895-105">This sample explicitly defines service behaviors and operation behaviors using the <xref:System.ServiceModel.ServiceBehaviorAttribute> and <xref:System.ServiceModel.OperationBehaviorAttribute> attributes.</span></span> <span data-ttu-id="f6895-106">您可以在組態檔中設定行為，也可以在程式碼中以命令方式設定 (如這個範例所示)。</span><span class="sxs-lookup"><span data-stu-id="f6895-106">You can configure behaviors in configuration files or imperatively in code (as this sample demonstrates).</span></span>  
  
 <span data-ttu-id="f6895-107">在這個範例中，用戶端是主控台應用程式 (.exe)，而服務則是由網際網路資訊服務 (IIS) 所裝載。</span><span class="sxs-lookup"><span data-stu-id="f6895-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f6895-108">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="f6895-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="f6895-109">此服務類別會使用 <xref:System.ServiceModel.ServiceBehaviorAttribute> 和 <xref:System.ServiceModel.OperationBehaviorAttribute> 指定行為，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="f6895-109">The service class specifies behaviors with the <xref:System.ServiceModel.ServiceBehaviorAttribute> and the <xref:System.ServiceModel.OperationBehaviorAttribute> as shown in the following code sample.</span></span> <span data-ttu-id="f6895-110">所有指定的值都是預設值。</span><span class="sxs-lookup"><span data-stu-id="f6895-110">All values specified are the defaults.</span></span>  
  
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
  
 <span data-ttu-id="f6895-111">服務行為是以 <xref:System.ServiceModel.ServiceBehaviorAttribute> 屬性指定。</span><span class="sxs-lookup"><span data-stu-id="f6895-111">Service behaviors are specified with the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute.</span></span> <span data-ttu-id="f6895-112">下表會介紹其中一些行為。</span><span class="sxs-lookup"><span data-stu-id="f6895-112">The following table describes some of these behaviors.</span></span>  
  
|<span data-ttu-id="f6895-113">服務行為</span><span class="sxs-lookup"><span data-stu-id="f6895-113">Service behavior</span></span>|<span data-ttu-id="f6895-114">描述</span><span class="sxs-lookup"><span data-stu-id="f6895-114">Description</span></span>|  
|----------------------|-----------------|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.AutomaticSessionShutdown%2A>|<span data-ttu-id="f6895-115">在用戶端要求時自動關閉工作階段。</span><span class="sxs-lookup"><span data-stu-id="f6895-115">Automatically shuts down a session at the client's request.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>|<span data-ttu-id="f6895-116">指定每個服務執行個體的並行模式。</span><span class="sxs-lookup"><span data-stu-id="f6895-116">Specifies the concurrency mode for each service instance.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>|<span data-ttu-id="f6895-117">指定執行個體內容模式。</span><span class="sxs-lookup"><span data-stu-id="f6895-117">Specifies the instance context mode.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.UseSynchronizationContext%2A>|<span data-ttu-id="f6895-118">判定是否要使用所提供的同步化內容，如果有設定的話。</span><span class="sxs-lookup"><span data-stu-id="f6895-118">Determines whether to use the provided synchronization context, if one is set.</span></span> <span data-ttu-id="f6895-119">當您想要控制是否要在 Windows Form 應用程式中使用 `WindowsFormsSynchronizationContext` 時，便可使用這項功能。</span><span class="sxs-lookup"><span data-stu-id="f6895-119">Use this when you want to control whether to use a `WindowsFormsSynchronizationContext` in Windows Forms applications.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A>|<span data-ttu-id="f6895-120">判定一般未處理的執行例外狀況是否要轉換為 `Fault<string>`，並且當作錯誤訊息傳送。</span><span class="sxs-lookup"><span data-stu-id="f6895-120">Determines whether general unhandled execution exceptions are to be converted into a `Fault<string>` and sent as a fault message.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A>|<span data-ttu-id="f6895-121">指定異動的隔離等級。</span><span class="sxs-lookup"><span data-stu-id="f6895-121">Specifies the isolation level for transactions.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ValidateMustUnderstand%2A>|<span data-ttu-id="f6895-122">判斷未預期的訊息標頭是否會造成錯誤狀況。</span><span class="sxs-lookup"><span data-stu-id="f6895-122">Determines whether unexpected message headers cause an error condition.</span></span>|  
  
 <span data-ttu-id="f6895-123">作業行為是以 <xref:System.ServiceModel.OperationBehaviorAttribute> 屬性所指定。</span><span class="sxs-lookup"><span data-stu-id="f6895-123">Operation behaviors are specified by using the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span> <span data-ttu-id="f6895-124">下表會介紹其中一些行為。</span><span class="sxs-lookup"><span data-stu-id="f6895-124">The following table describes some of these behaviors.</span></span>  
  
|<span data-ttu-id="f6895-125">作業行為</span><span class="sxs-lookup"><span data-stu-id="f6895-125">Operation Behavior</span></span>|<span data-ttu-id="f6895-126">描述</span><span class="sxs-lookup"><span data-stu-id="f6895-126">Description</span></span>|  
|------------------------|-----------------|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A>|<span data-ttu-id="f6895-127">判定服務作業完成是否會認可目前異動。</span><span class="sxs-lookup"><span data-stu-id="f6895-127">Determines whether service operation completion commits the current transaction.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>|<span data-ttu-id="f6895-128">判定服務作業是否會登記在用戶端流動的異動中。</span><span class="sxs-lookup"><span data-stu-id="f6895-128">Determines whether the service operation enlists in a client-flowed transaction.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A>|<span data-ttu-id="f6895-129">判定服務作業是否會模擬呼叫者身分識別。</span><span class="sxs-lookup"><span data-stu-id="f6895-129">Determines whether the service operation impersonates the caller's identity.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A>|<span data-ttu-id="f6895-130">判定服務執行個體是否會在服務作業呼叫的開始與結束時回收。</span><span class="sxs-lookup"><span data-stu-id="f6895-130">Determines whether service instances are recycled at the start or end of the service operation call.</span></span>|  
  
 <span data-ttu-id="f6895-131">當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="f6895-131">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="f6895-132">呼叫之間發生延遲是因為在服務作業中呼叫 `System.Threading.Thread.Sleep()`。</span><span class="sxs-lookup"><span data-stu-id="f6895-132">The delay between the calls is the result of the calls to `System.Threading.Thread.Sleep()` made in the service operations.</span></span> <span data-ttu-id="f6895-133">其他行為範例會更詳細說明這些行為。</span><span class="sxs-lookup"><span data-stu-id="f6895-133">The rest of the behavior samples explain these behaviors in more detail.</span></span> <span data-ttu-id="f6895-134">在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="f6895-134">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f6895-135">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="f6895-135">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="f6895-136">請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="f6895-136">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="f6895-137">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="f6895-137">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="f6895-138">若要在單一或跨電腦組態中執行範例時，請依照中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="f6895-138">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f6895-139">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="f6895-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f6895-140">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="f6895-140">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f6895-141">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="f6895-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f6895-142">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="f6895-142">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Default`  
  
## <a name="see-also"></a><span data-ttu-id="f6895-143">請參閱</span><span class="sxs-lookup"><span data-stu-id="f6895-143">See Also</span></span>

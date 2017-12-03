---
title: "ASP.NET 相容性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8b51f1e-c096-4c42-ad99-0519887bbbc5
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2c8cf38e65bbc917720b1a1c5b604d81ca536c14
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="aspnet-compatibility"></a><span data-ttu-id="ac462-102">ASP.NET 相容性</span><span class="sxs-lookup"><span data-stu-id="ac462-102">ASP.NET Compatibility</span></span>
<span data-ttu-id="ac462-103">這個範例會示範如何在 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 中啟用 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 相容模式。</span><span class="sxs-lookup"><span data-stu-id="ac462-103">This sample demonstrates how to enable [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Compatibility mode in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="ac462-104">在 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 相容模式中執行的服務會完全參與 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 應用程式管線，並且會利用像是檔案/URL 授權、工作階段狀態，以及 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 類別等 <xref:System.Web.HttpContext> 功能。</span><span class="sxs-lookup"><span data-stu-id="ac462-104">Services running in [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Compatibility mode participate fully in the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application pipeline and can make use of [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] features such as file/URL authorization, session state, and the <xref:System.Web.HttpContext> class.</span></span> <span data-ttu-id="ac462-105"><xref:System.Web.HttpContext> 類別允許存取 Cookie、工作階段以及其他 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 功能。</span><span class="sxs-lookup"><span data-stu-id="ac462-105">The <xref:System.Web.HttpContext> class allows access to cookies, sessions, and other [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] features.</span></span> <span data-ttu-id="ac462-106">這個模式會要求這些繫結使用 HTTP 傳輸，而且服務本身必須以 IIS 裝載。</span><span class="sxs-lookup"><span data-stu-id="ac462-106">This mode requires that the bindings use the HTTP transport and the service itself must be hosted in IIS.</span></span>  
  
 <span data-ttu-id="ac462-107">在這個範例中，用戶端是主控台應用程式 (可執行檔)，而服務則是由網際網路資訊服務 (IIS) 裝載。</span><span class="sxs-lookup"><span data-stu-id="ac462-107">In this sample, the client is a console application (an executable) and the service is hosted in Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ac462-108">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="ac462-108">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ac462-109">這個範例需要 [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] 應用程式集區才能執行。</span><span class="sxs-lookup"><span data-stu-id="ac462-109">This sample requires a [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] application pool in order to run.</span></span> <span data-ttu-id="ac462-110">若要建立應用程式集區，或是修改預設的應用程式集區，請遵循下列步驟。</span><span class="sxs-lookup"><span data-stu-id="ac462-110">To create a new application pool, or to modify the default application pool, follow these steps.</span></span>  
>   
>  1.  <span data-ttu-id="ac462-111">開啟**控制台**。</span><span class="sxs-lookup"><span data-stu-id="ac462-111">Open **Control Panel**.</span></span>  <span data-ttu-id="ac462-112">開啟**系統管理工具**下方的小程式**系統及安全性**標題。</span><span class="sxs-lookup"><span data-stu-id="ac462-112">Open the **Administrative Tools** applet under the **System and Security** heading.</span></span> <span data-ttu-id="ac462-113">開啟**網際網路資訊服務 (IIS) 管理員**小程式。</span><span class="sxs-lookup"><span data-stu-id="ac462-113">Open the **Internet Information Services (IIS) Manager** applet.</span></span>  
> 2.  <span data-ttu-id="ac462-114">展開的 treeview**連線**窗格。</span><span class="sxs-lookup"><span data-stu-id="ac462-114">Expand the treeview in the **Connections** pane.</span></span> <span data-ttu-id="ac462-115">選取**應用程式集區**節點。</span><span class="sxs-lookup"><span data-stu-id="ac462-115">Select the **Application Pools** node.</span></span>  
> 3.  <span data-ttu-id="ac462-116">若要設定要使用的預設應用程式集區[!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]（這會導致與現有站台不相容問題），以滑鼠右鍵按一下**DefaultAppPool**清單項目，然後選取**基本設定...**.</span><span class="sxs-lookup"><span data-stu-id="ac462-116">To set the default application pool to use [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (which may cause incompatibility problems with existing sites), right-click the **DefaultAppPool** list item and select **Basic Settings…**.</span></span> <span data-ttu-id="ac462-117">設定**.Net Framework 版本**提取向**.Net Framework v4.0.30128** （或更新版本）。</span><span class="sxs-lookup"><span data-stu-id="ac462-117">Set the **.Net Framework Version** pull-down to **.Net Framework v4.0.30128** (or later).</span></span>  
> 4.  <span data-ttu-id="ac462-118">若要建立新的應用程式集區使用[!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]（以保留與其他應用程式相容性），以滑鼠右鍵按一下**應用程式集區**節點，然後選取**新增應用程式集區...**.</span><span class="sxs-lookup"><span data-stu-id="ac462-118">To create a new application pool that uses [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (to preserve compatibility for other applications), right-click the **Application Pools** node and select **Add Application Pool…**.</span></span> <span data-ttu-id="ac462-119">為新的應用程式集區，並設定**.Net Framework 版本**提取向**.Net Framework v4.0.30128** （或更新版本）。</span><span class="sxs-lookup"><span data-stu-id="ac462-119">Name the new application pool, and set the **.Net Framework Version** pull-down to **.Net Framework v4.0.30128** (or later).</span></span> <span data-ttu-id="ac462-120">下面執行安裝程式步驟之後，以滑鼠右鍵按一下**ServiceModelSamples**應用程式並選取**管理應用程式**，**進階設定...**.</span><span class="sxs-lookup"><span data-stu-id="ac462-120">After running the setup steps below, right-click the **ServiceModelSamples** application and select **Manage Application**, **Advanced Settings…**.</span></span> <span data-ttu-id="ac462-121">設定**應用程式集區**新的應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="ac462-121">Set the **Application Pool** to the new application pool.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ac462-122">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="ac462-122">The samples may already be installed on your computer.</span></span> <span data-ttu-id="ac462-123">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="ac462-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ac462-124">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="ac462-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ac462-125">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="ac462-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\ASPNetCompatibility`  
  
 <span data-ttu-id="ac462-126">這個範例根據[入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)，它會實作計算機服務。</span><span class="sxs-lookup"><span data-stu-id="ac462-126">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements a calculator service.</span></span> <span data-ttu-id="ac462-127">`ICalculator` 合約已修改成允許執行一組作業的 `ICalculatorSession` 合約，並同時保留執行結果。</span><span class="sxs-lookup"><span data-stu-id="ac462-127">The `ICalculator` contract has been modified as the `ICalculatorSession` contract to allow a set of operations to be performed, while keeping a running result.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculatorSession  
{  
    [OperationContract]  
    void Clear();  
    [OperationContract]  
    void AddTo(double n);  
    [OperationContract]  
    void SubtractFrom(double n);  
    [OperationContract]  
    void MultiplyBy(double n);  
    [OperationContract]  
    void DivideBy(double n);  
    [OperationContract]  
    double Result();  
}  
```  
  
 <span data-ttu-id="ac462-128">此服務會維護用戶端的狀態 (方法是使用該功能)，因為在進行計算時已呼叫了多個服務作業。</span><span class="sxs-lookup"><span data-stu-id="ac462-128">The service maintains state, using the feature, for each client as multiple service operations are called to perform a calculation.</span></span> <span data-ttu-id="ac462-129">用戶端會呼叫 `Result` 以擷取目前的結果，並且能夠呼叫 `Clear` 將結果清除為零。</span><span class="sxs-lookup"><span data-stu-id="ac462-129">The client can retrieve the current result by calling `Result` and can clear the result to zero by calling `Clear`.</span></span>  
  
 <span data-ttu-id="ac462-130">服務會使用 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 工作階段來儲存每個用戶端工作階段的結果。</span><span class="sxs-lookup"><span data-stu-id="ac462-130">The service uses the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] session to store the result for each client session.</span></span> <span data-ttu-id="ac462-131">這樣服務便可在跨多個服務呼叫時維護每個工作階段的執行結果。</span><span class="sxs-lookup"><span data-stu-id="ac462-131">This allows the service to maintain the running result for each client across multiple calls to the service.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]<span data-ttu-id="ac462-132"> 工作階段狀態與 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 工作階段是完全不同的項目。</span><span class="sxs-lookup"><span data-stu-id="ac462-132"> session state and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sessions are very different things.</span></span>  <span data-ttu-id="ac462-133">請參閱[工作階段](../../../../docs/framework/wcf/samples/session.md)如需詳細資訊[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]工作階段。</span><span class="sxs-lookup"><span data-stu-id="ac462-133">See the [Session](../../../../docs/framework/wcf/samples/session.md) for details on [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sessions.</span></span>  
  
 <span data-ttu-id="ac462-134">服務對 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 工作階段狀態有相當深的相依性，並且需要 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 相容性模式才能正確運作。</span><span class="sxs-lookup"><span data-stu-id="ac462-134">The service has an intimate dependency on [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] session state and requires [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] compatibility mode to function correctly.</span></span> <span data-ttu-id="ac462-135">這些需求會在套用 `AspNetCompatibilityRequirements` 屬性時以宣告方式表達。</span><span class="sxs-lookup"><span data-stu-id="ac462-135">These requirements are expressed declaratively by applying the `AspNetCompatibilityRequirements` attribute.</span></span>  
  
```  
[AspNetCompatibilityRequirements(RequirementsMode =  
                       AspNetCompatibilityRequirementsMode.Required)]  
public class CalculatorService : ICalculatorSession  
{  
    double Result  
    {  // store result in AspNet Session  
       get {  
          if (HttpContext.Current.Session["Result"] != null)  
             return (double)HttpContext.Current.Session["Result"];  
          return 0.0D;  
       }  
       set  
       {  
          HttpContext.Current.Session["Result"] = value;  
       }  
    }  
    public void Clear()  
    {  
        Result = 0.0D;  
    }  
    public void AddTo(double n)  
    {  
        Result += n;  
    }  
    public void SubtractFrom(double n)  
    {  
        Result -= n;  
    }  
    public void MultiplyBy(double n)  
    {  
        Result *= n;  
    }  
    public void DivideBy(double n)  
    {  
        Result /= n;  
    }  
    public double Result()  
    {  
        return Result;  
    }  
}  
```  
  
 <span data-ttu-id="ac462-136">當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="ac462-136">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="ac462-137">在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="ac462-137">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
0, + 100, - 50, * 17.65, / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ac462-138">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="ac462-138">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ac462-139">確認您已經執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="ac462-139">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="ac462-140">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="ac462-140">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="ac462-141">在建立方案後，執行 Setup.bat 以便在 [!INCLUDE[iisver](../../../../includes/iisver-md.md)] 中安裝 ServiceModelSamples 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ac462-141">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span></span> <span data-ttu-id="ac462-142">ServiceModelSamples 目錄現在應該會顯示為 [!INCLUDE[iisver](../../../../includes/iisver-md.md)] 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ac462-142">The ServiceModelSamples directory should now appear as an [!INCLUDE[iisver](../../../../includes/iisver-md.md)] Application.</span></span>  
  
4.  <span data-ttu-id="ac462-143">若要在單一或跨電腦組態中執行範例時，請依照中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="ac462-143">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac462-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac462-144">See Also</span></span>  
 [<span data-ttu-id="ac462-145">AppFabric 主控與持續性範例</span><span class="sxs-lookup"><span data-stu-id="ac462-145">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)

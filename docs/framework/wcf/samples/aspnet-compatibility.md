---
title: ASP.NET 相容性
ms.date: 03/30/2017
ms.assetid: c8b51f1e-c096-4c42-ad99-0519887bbbc5
ms.openlocfilehash: 01381dc579f5ae3eadd2f913a0e09d7d259794a1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62002660"
---
# <a name="aspnet-compatibility"></a><span data-ttu-id="2ae5d-102">ASP.NET 相容性</span><span class="sxs-lookup"><span data-stu-id="2ae5d-102">ASP.NET Compatibility</span></span>
<span data-ttu-id="2ae5d-103">此範例示範如何啟用 ASP.NET 相容性模式在 Windows Communication Foundation (WCF)。</span><span class="sxs-lookup"><span data-stu-id="2ae5d-103">This sample demonstrates how to enable ASP.NET Compatibility mode in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="2ae5d-104">在 ASP.NET 相容性模式會充分參與 ASP.NET 應用程式管線和可執行的服務使用的 ASP.NET 功能，例如檔案 /URL 授權、 工作階段狀態和<xref:System.Web.HttpContext>類別。</span><span class="sxs-lookup"><span data-stu-id="2ae5d-104">Services running in ASP.NET Compatibility mode participate fully in the ASP.NET application pipeline and can make use of ASP.NET features such as file/URL authorization, session state, and the <xref:System.Web.HttpContext> class.</span></span> <span data-ttu-id="2ae5d-105"><xref:System.Web.HttpContext>類別可讓您存取 cookie、 工作階段和其他 ASP.NET 功能。</span><span class="sxs-lookup"><span data-stu-id="2ae5d-105">The <xref:System.Web.HttpContext> class allows access to cookies, sessions, and other ASP.NET features.</span></span> <span data-ttu-id="2ae5d-106">這個模式會要求這些繫結使用 HTTP 傳輸，而且服務本身必須以 IIS 裝載。</span><span class="sxs-lookup"><span data-stu-id="2ae5d-106">This mode requires that the bindings use the HTTP transport and the service itself must be hosted in IIS.</span></span>  
  
 <span data-ttu-id="2ae5d-107">在這個範例中，用戶端是主控台應用程式 (可執行檔)，而服務則是由網際網路資訊服務 (IIS) 裝載。</span><span class="sxs-lookup"><span data-stu-id="2ae5d-107">In this sample, the client is a console application (an executable) and the service is hosted in Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2ae5d-108">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="2ae5d-108">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
<span data-ttu-id="2ae5d-109">這個範例需要 [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] 應用程式集區才能執行。</span><span class="sxs-lookup"><span data-stu-id="2ae5d-109">This sample requires a [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] application pool in order to run.</span></span> <span data-ttu-id="2ae5d-110">若要建立應用程式集區，或是修改預設的應用程式集區，請遵循下列步驟。</span><span class="sxs-lookup"><span data-stu-id="2ae5d-110">To create a new application pool, or to modify the default application pool, follow these steps.</span></span>  

1. <span data-ttu-id="2ae5d-111">開啟**控制台中**。</span><span class="sxs-lookup"><span data-stu-id="2ae5d-111">Open **Control Panel**.</span></span>  <span data-ttu-id="2ae5d-112">開啟**系統管理工具**下方的小程式**系統及安全性**標題。</span><span class="sxs-lookup"><span data-stu-id="2ae5d-112">Open the **Administrative Tools** applet under the **System and Security** heading.</span></span> <span data-ttu-id="2ae5d-113">開啟**Internet Information Services (IIS) 管理員**小程式。</span><span class="sxs-lookup"><span data-stu-id="2ae5d-113">Open the **Internet Information Services (IIS) Manager** applet.</span></span>  

2. <span data-ttu-id="2ae5d-114">展開在 treeview**連線**窗格。</span><span class="sxs-lookup"><span data-stu-id="2ae5d-114">Expand the treeview in the **Connections** pane.</span></span> <span data-ttu-id="2ae5d-115">選取 **應用程式集區**節點。</span><span class="sxs-lookup"><span data-stu-id="2ae5d-115">Select the **Application Pools** node.</span></span>  

3. <span data-ttu-id="2ae5d-116">若要設定要使用預設應用程式集區[!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]（其可能造成與現有的站台的不相容性問題），以滑鼠右鍵按一下**DefaultAppPool**清單項目，然後選取**基本設定...**.</span><span class="sxs-lookup"><span data-stu-id="2ae5d-116">To set the default application pool to use [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (which may cause incompatibility problems with existing sites), right-click the **DefaultAppPool** list item and select **Basic Settings…**.</span></span> <span data-ttu-id="2ae5d-117">設定 **.Net Framework 版本**提取-向下鍵即可 **.Net Framework v4.0.30128** （或更新版本）。</span><span class="sxs-lookup"><span data-stu-id="2ae5d-117">Set the **.Net Framework Version** pull-down to **.Net Framework v4.0.30128** (or later).</span></span>  

4. <span data-ttu-id="2ae5d-118">若要建立新的應用程式集區使用[!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]（以保留其他應用程式相容性），以滑鼠右鍵按一下**應用程式集區**節點，然後選取**新增應用程式集區...**.</span><span class="sxs-lookup"><span data-stu-id="2ae5d-118">To create a new application pool that uses [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (to preserve compatibility for other applications), right-click the **Application Pools** node and select **Add Application Pool…**.</span></span> <span data-ttu-id="2ae5d-119">命名新的應用程式集區，並設定 **.Net Framework 版本**提取-向下鍵即可 **.Net Framework v4.0.30128** （或更新版本）。</span><span class="sxs-lookup"><span data-stu-id="2ae5d-119">Name the new application pool, and set the **.Net Framework Version** pull-down to **.Net Framework v4.0.30128** (or later).</span></span> <span data-ttu-id="2ae5d-120">下列執行設定步驟之後，請以滑鼠右鍵按一下**ServiceModelSamples**應用程式，然後選取**管理應用程式**，**進階設定...**.</span><span class="sxs-lookup"><span data-stu-id="2ae5d-120">After running the setup steps below, right-click the **ServiceModelSamples** application and select **Manage Application**, **Advanced Settings…**.</span></span> <span data-ttu-id="2ae5d-121">設定**應用程式集區**新的應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="2ae5d-121">Set the **Application Pool** to the new application pool.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2ae5d-122">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="2ae5d-122">The samples may already be installed on your computer.</span></span> <span data-ttu-id="2ae5d-123">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="2ae5d-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2ae5d-124">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="2ae5d-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2ae5d-125">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="2ae5d-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\ASPNetCompatibility`  
  
 <span data-ttu-id="2ae5d-126">此樣本根據[開始使用](../../../../docs/framework/wcf/samples/getting-started-sample.md)，以實作計算機服務。</span><span class="sxs-lookup"><span data-stu-id="2ae5d-126">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements a calculator service.</span></span> <span data-ttu-id="2ae5d-127">`ICalculator` 合約已修改成允許執行一組作業的 `ICalculatorSession` 合約，並同時保留執行結果。</span><span class="sxs-lookup"><span data-stu-id="2ae5d-127">The `ICalculator` contract has been modified as the `ICalculatorSession` contract to allow a set of operations to be performed, while keeping a running result.</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="2ae5d-128">此服務會維護用戶端的狀態 (方法是使用該功能)，因為在進行計算時已呼叫了多個服務作業。</span><span class="sxs-lookup"><span data-stu-id="2ae5d-128">The service maintains state, using the feature, for each client as multiple service operations are called to perform a calculation.</span></span> <span data-ttu-id="2ae5d-129">用戶端會呼叫 `Result` 以擷取目前的結果，並且能夠呼叫 `Clear` 將結果清除為零。</span><span class="sxs-lookup"><span data-stu-id="2ae5d-129">The client can retrieve the current result by calling `Result` and can clear the result to zero by calling `Clear`.</span></span>  
  
 <span data-ttu-id="2ae5d-130">服務會使用 ASP.NET 工作階段，以儲存每個用戶端工作階段的結果。</span><span class="sxs-lookup"><span data-stu-id="2ae5d-130">The service uses the ASP.NET session to store the result for each client session.</span></span> <span data-ttu-id="2ae5d-131">這樣服務便可在跨多個服務呼叫時維護每個工作階段的執行結果。</span><span class="sxs-lookup"><span data-stu-id="2ae5d-131">This allows the service to maintain the running result for each client across multiple calls to the service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2ae5d-132">ASP.NET 工作階段狀態和 WCF 工作階段會非常不同的事物。</span><span class="sxs-lookup"><span data-stu-id="2ae5d-132">ASP.NET session state and WCF sessions are very different things.</span></span> <span data-ttu-id="2ae5d-133">請參閱[工作階段](../../../../docs/framework/wcf/samples/session.md)如需有關 WCF 工作階段。</span><span class="sxs-lookup"><span data-stu-id="2ae5d-133">See [Session](../../../../docs/framework/wcf/samples/session.md) for details on WCF sessions.</span></span>
  
 <span data-ttu-id="2ae5d-134">服務會在 ASP.NET 工作階段狀態有相當深的相依性，而且需要 ASP.NET 相容性模式，才能正確運作。</span><span class="sxs-lookup"><span data-stu-id="2ae5d-134">The service has an intimate dependency on ASP.NET session state and requires ASP.NET compatibility mode to function correctly.</span></span> <span data-ttu-id="2ae5d-135">這些需求會在套用 `AspNetCompatibilityRequirements` 屬性時以宣告方式表達。</span><span class="sxs-lookup"><span data-stu-id="2ae5d-135">These requirements are expressed declaratively by applying the `AspNetCompatibilityRequirements` attribute.</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="2ae5d-136">當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="2ae5d-136">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="2ae5d-137">在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="2ae5d-137">Press ENTER in the client window to shut down the client.</span></span>  
  
```console
0, + 100, - 50, * 17.65, / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2ae5d-138">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="2ae5d-138">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="2ae5d-139">確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="2ae5d-139">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="2ae5d-140">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="2ae5d-140">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="2ae5d-141">在建立方案後，執行 Setup.bat 以便在 [!INCLUDE[iisver](../../../../includes/iisver-md.md)] 中安裝 ServiceModelSamples 應用程式。</span><span class="sxs-lookup"><span data-stu-id="2ae5d-141">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span></span> <span data-ttu-id="2ae5d-142">ServiceModelSamples 目錄現在應該會顯示為 [!INCLUDE[iisver](../../../../includes/iisver-md.md)] 應用程式。</span><span class="sxs-lookup"><span data-stu-id="2ae5d-142">The ServiceModelSamples directory should now appear as an [!INCLUDE[iisver](../../../../includes/iisver-md.md)] Application.</span></span>  
  
4. <span data-ttu-id="2ae5d-143">若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="2ae5d-143">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ae5d-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ae5d-144">See also</span></span>

- [<span data-ttu-id="2ae5d-145">AppFabric 主控與持續性範例</span><span class="sxs-lookup"><span data-stu-id="2ae5d-145">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)

---
title: 使用內嵌程式碼的 IIS 裝載
ms.date: 03/30/2017
helpviewer_keywords:
- Web hosted service
- IIS Hosting Using Inline Code Sample [Windows Communication Foundation]
ms.assetid: 56fe3687-a34b-4661-8e30-b33770f413fa
ms.openlocfilehash: ebaf524997ae4ed50b28aec53507f843f028bc31
ms.sourcegitcommit: fd8d4587cc26e53f0e27e230d6e27d828ef4306b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2018
ms.locfileid: "49348973"
---
# <a name="iis-hosting-using-inline-code"></a><span data-ttu-id="8b8e5-102">使用內嵌程式碼的 IIS 裝載</span><span class="sxs-lookup"><span data-stu-id="8b8e5-102">IIS Hosting Using Inline Code</span></span>
<span data-ttu-id="8b8e5-103">這個範例會示範如何實作由網際網路資訊服務 (IIS) 裝載的服務，此時服務程式碼內嵌在 .svc 檔中並且視需要進行編譯。</span><span class="sxs-lookup"><span data-stu-id="8b8e5-103">This sample demonstrates how to implement a service hosted by Internet Information Services (IIS), where the service code is contained in-line in a .svc file and is compiled on demand.</span></span> <span data-ttu-id="8b8e5-104">服務程式碼也可以直接實作在位於應用程式之 \App_Code 目錄的原始程式碼檔中，或是編譯成部署在 \bin 中的組件。</span><span class="sxs-lookup"><span data-stu-id="8b8e5-104">Service code can also be implemented directly in source code files located in the application's \App_Code directory, or compiled into assembly deployed in \bin.</span></span> <span data-ttu-id="8b8e5-105">這個範例不會示範這些技術。</span><span class="sxs-lookup"><span data-stu-id="8b8e5-105">This sample does not demonstrate these techniques.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8b8e5-106">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="8b8e5-106">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8b8e5-107">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="8b8e5-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="8b8e5-108">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="8b8e5-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="8b8e5-109">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="8b8e5-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8b8e5-110">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="8b8e5-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\InlineCode`  
  
 <span data-ttu-id="8b8e5-111">此範例會示範將合約實作成定義要求-回覆通訊模式的一般服務。</span><span class="sxs-lookup"><span data-stu-id="8b8e5-111">The sample demonstrates a typical service that implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="8b8e5-112">該服務會裝載於 IIS，而且其服務程式碼會完整包含在 Service.svc 檔中。</span><span class="sxs-lookup"><span data-stu-id="8b8e5-112">The service is hosted in IIS and the service code is entirely contained in the Service.svc file.</span></span> <span data-ttu-id="8b8e5-113">該服務是由主機啟動，並且會根據傳送至服務之第一個訊息的需要進行編譯。</span><span class="sxs-lookup"><span data-stu-id="8b8e5-113">The service is host-activated and compiled on-demand by the first message sent to the service.</span></span> <span data-ttu-id="8b8e5-114">因此不需要先行編譯。</span><span class="sxs-lookup"><span data-stu-id="8b8e5-114">There is no pre-compilation necessary.</span></span> <span data-ttu-id="8b8e5-115">此服務會實作 `ICalculator` 合約，如下列程式碼中所定義：</span><span class="sxs-lookup"><span data-stu-id="8b8e5-115">The service implements an `ICalculator` contract as defined in the following code:</span></span>  
  
```csharp
// Define a service contract.  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
    public interface ICalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
    [OperationContract]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="8b8e5-116">服務實作會計算並傳回適當結果。</span><span class="sxs-lookup"><span data-stu-id="8b8e5-116">The service implementation calculates and returns the appropriate result.</span></span>  
  
```svc
<%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService" %>   
```
```csharp
// Service class that implements the service contract.  
public class CalculatorService : ICalculator  
{  
    public double Add(double n1, double n2)  
    {  
        return n1 + n2;  
    }  
    public double Subtract(double n1, double n2)  
    {  
        return n1 - n2;  
    }  
    public double Multiply(double n1, double n2)  
    {  
        return n1 * n2;  
    }  
    public double Divide(double n1, double n2)  
    {  
        return n1 / n2;  
    }  
}  
```  
  
 <span data-ttu-id="8b8e5-117">當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="8b8e5-117">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="8b8e5-118">在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="8b8e5-118">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8b8e5-119">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="8b8e5-119">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="8b8e5-120">請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="8b8e5-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="8b8e5-121">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="8b8e5-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="8b8e5-122">在建立方案後，執行 setup.bat 以便在 [!INCLUDE[iisver](../../../../includes/iisver-md.md)] 中安裝 ServiceModelSamples 應用程式。</span><span class="sxs-lookup"><span data-stu-id="8b8e5-122">After the solution has been built, run setup.bat to set up the ServiceModelSamples Application in [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span></span> <span data-ttu-id="8b8e5-123">ServiceModelSamples 目錄現在應該會顯示為 [!INCLUDE[iisver](../../../../includes/iisver-md.md)] 應用程式。</span><span class="sxs-lookup"><span data-stu-id="8b8e5-123">The ServiceModelSamples directory should now appear as an [!INCLUDE[iisver](../../../../includes/iisver-md.md)] Application.</span></span>  
  
4.  <span data-ttu-id="8b8e5-124">若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="8b8e5-124">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span> <span data-ttu-id="8b8e5-125">如需有關如何建立可呼叫此服務的用戶端應用程式的範例，請參閱[如何： 建立用戶端](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md)。</span><span class="sxs-lookup"><span data-stu-id="8b8e5-125">For an example on how to create a client application that can call this service, see [How to: Create a Client](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b8e5-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b8e5-126">See Also</span></span>  
 [<span data-ttu-id="8b8e5-127">AppFabric 主控與持續性範例</span><span class="sxs-lookup"><span data-stu-id="8b8e5-127">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)

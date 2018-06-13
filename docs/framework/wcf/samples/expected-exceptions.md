---
title: 預期的例外狀況
ms.date: 03/30/2017
ms.assetid: 299a6987-ae6b-43c6-987f-12b034b583ae
ms.openlocfilehash: 6c4af62e0870cdd670c46ead169033ff72902fc0
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33805820"
---
# <a name="expected-exceptions"></a><span data-ttu-id="e38a7-102">預期的例外狀況</span><span class="sxs-lookup"><span data-stu-id="e38a7-102">Expected Exceptions</span></span>
<span data-ttu-id="e38a7-103">此範例示範如何在使用型別用戶端時，攔截預期的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e38a7-103">This sample demonstrates how to catch expected exceptions when using a typed client.</span></span> <span data-ttu-id="e38a7-104">這個範例根據[入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)，用來實作計算機服務。</span><span class="sxs-lookup"><span data-stu-id="e38a7-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="e38a7-105">在這個範例中，用戶端是主控台應用程式 (.exe)，而服務則是由網際網路資訊服務 (IIS) 所裝載。</span><span class="sxs-lookup"><span data-stu-id="e38a7-105">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e38a7-106">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="e38a7-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="e38a7-107">此範例示範正確的程式必須處理的兩個預期例外狀況類型之捕捉與處理方式：`TimeoutException` 和 `CommunicationException`。</span><span class="sxs-lookup"><span data-stu-id="e38a7-107">This sample demonstrates catching and handling the two expected exception types that correct programs must handle: `TimeoutException` and `CommunicationException`.</span></span>  
  
 <span data-ttu-id="e38a7-108">從 Windows Communication Foundation (WCF) 用戶端上的通訊方法就會擲回的例外狀況會預期或未預期的。</span><span class="sxs-lookup"><span data-stu-id="e38a7-108">Exceptions that are thrown from communication methods on a Windows Communication Foundation (WCF) client are either expected or unexpected.</span></span> <span data-ttu-id="e38a7-109">未預期的例外狀況包含 `OutOfMemoryException` 之類的災難性失敗，以及像 `ArgumentNullException` 或 `InvalidOperationException` 之類的程式設計錯誤。</span><span class="sxs-lookup"><span data-stu-id="e38a7-109">Unexpected exceptions include catastrophic failures like `OutOfMemoryException` and programming errors like `ArgumentNullException` or `InvalidOperationException`.</span></span> <span data-ttu-id="e38a7-110">通常是沒有實用的方式來處理未預期的錯誤，因此通常不應該捕捉這些，當呼叫 WCF 用戶端通訊方法。</span><span class="sxs-lookup"><span data-stu-id="e38a7-110">Typically there is no useful way to handle unexpected errors, so typically you should not catch them when calling a WCF client communication method.</span></span>  
  
 <span data-ttu-id="e38a7-111">必須是由 WCF 用戶端上的通訊方法的例外狀況包含`TimeoutException`， `CommunicationException`，和任何衍生的類別`CommunicationException`。</span><span class="sxs-lookup"><span data-stu-id="e38a7-111">Expected exceptions from communication methods on a WCF client include `TimeoutException`, `CommunicationException`, and any derived class of `CommunicationException`.</span></span> <span data-ttu-id="e38a7-112">這些可以中止 WCF 用戶端並報告通訊失敗來妥善處理的通訊期間表示有問題。</span><span class="sxs-lookup"><span data-stu-id="e38a7-112">These indicate a problem during communication that can be safely handled by aborting the WCF client and reporting a communication failure.</span></span> <span data-ttu-id="e38a7-113">因為外部因素可能導致在任何應用程式中發生這些錯誤，正確的應用程式必須捕捉這些例外狀況，並在發生時加以復原。</span><span class="sxs-lookup"><span data-stu-id="e38a7-113">Because external factors can cause these errors in any application, correct applications must catch these exceptions and recover when they occur.</span></span>  
  
 <span data-ttu-id="e38a7-114">用戶端可以擲回的 `CommunicationException` 衍生類別有好幾種。</span><span class="sxs-lookup"><span data-stu-id="e38a7-114">There are several derived classes of `CommunicationException` that a client can throw.</span></span> <span data-ttu-id="e38a7-115">在某些情況中，應用程式也會捕捉當中的一些狀況以進行特殊處理，但同時讓其他狀況當成 `CommunicationException` 來處理。</span><span class="sxs-lookup"><span data-stu-id="e38a7-115">In some cases, applications also catch some of these to do special handling, but let the others be handled as a `CommunicationException`.</span></span> <span data-ttu-id="e38a7-116">首先您可以捕捉比較特別的例外狀況類型，然後在稍後的 catch 子句中捕捉 `CommunicationException` 來做同樣的處理。</span><span class="sxs-lookup"><span data-stu-id="e38a7-116">This can be accomplished by catching the more specific exception type first and then catching `CommunicationException` in a later catch-clause.</span></span>  
  
 <span data-ttu-id="e38a7-117">可呼叫用戶端通訊方法的程式碼必須捕捉 `TimeoutException` 和 `CommunicationException`。</span><span class="sxs-lookup"><span data-stu-id="e38a7-117">Code that calls a client communication method must catch the `TimeoutException` and `CommunicationException`.</span></span> <span data-ttu-id="e38a7-118">處理此類錯誤的一種方式，就是中止用戶端並報告通訊失敗。</span><span class="sxs-lookup"><span data-stu-id="e38a7-118">One way to handle such errors is to abort the client and report the communication failure.</span></span>  
  
```csharp   
try  
{  
    ...  
    double result = client.Add(value1, value2);  
    ...  
    client.Close();  
}  
catch (TimeoutException exception)  
{  
    Console.WriteLine("Got {0}", exception.GetType());  
    client.Abort();  
}  
catch (CommunicationException exception)  
{  
    Console.WriteLine("Got {0}", exception.GetType());  
    client.Abort();  
}  
```  
  
 <span data-ttu-id="e38a7-119">如果發生預期的例外狀況，日後用戶端可能還能使用，也可能無法使用。</span><span class="sxs-lookup"><span data-stu-id="e38a7-119">If an expected exception occurs, the client may or may not be usable afterwards.</span></span> <span data-ttu-id="e38a7-120">若要判斷用戶端是否仍可使用，請檢查 `State` 屬性是否設為 `CommunicationState`.Opened。</span><span class="sxs-lookup"><span data-stu-id="e38a7-120">To determine if the client is still usable, check that the `State` property is `CommunicationState`.Opened.</span></span> <span data-ttu-id="e38a7-121">如果仍為開啟狀態，表示仍可使用。</span><span class="sxs-lookup"><span data-stu-id="e38a7-121">If it is still opened, then it is still usable.</span></span> <span data-ttu-id="e38a7-122">否則，您應該中止用戶端，並釋放所有用戶端的參考。</span><span class="sxs-lookup"><span data-stu-id="e38a7-122">Otherwise you should abort the client and release all references to it.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="e38a7-123">您可以發現，具有工作階段的用戶端通常在發生例外狀況後無法繼續使用，而不具有工作階段的用戶端卻常常在發生例外狀況後還能使用。</span><span class="sxs-lookup"><span data-stu-id="e38a7-123">You may observe that clients that have a session are often no longer usable after an exception, and clients that do not have a session are often still usable after an exception.</span></span> <span data-ttu-id="e38a7-124">但是，這兩種情況並不必然發生，因此假如您想要在發生例外狀況後繼續使用用戶端，則您的應用程式應該檢查 `State` 屬性以確定用戶端仍為開啟狀態。</span><span class="sxs-lookup"><span data-stu-id="e38a7-124">However, neither of these is guaranteed, so if you want to try to continue using the client after an exception your application should check the `State` property to verify the client is still opened.</span></span>  
  
 <span data-ttu-id="e38a7-125">當您執行範例時，作業回應和例外狀況會顯示在用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="e38a7-125">When you run the sample, the operation responses and exceptions are displayed in the client console window.</span></span>  
  
 <span data-ttu-id="e38a7-126">用戶端處理序會執行兩個案例，每一個都會嘗試呼叫 `Add` 並接著呼叫 `Divide`。</span><span class="sxs-lookup"><span data-stu-id="e38a7-126">The client process runs two scenarios, each of which attempts to call `Add` followed by `Divide`.</span></span> <span data-ttu-id="e38a7-127">第一個案例會在呼叫 `Divide` 之前，先中止用戶端以便模擬網路問題。</span><span class="sxs-lookup"><span data-stu-id="e38a7-127">The first scenario simulates a network issue by aborting the client before making the call to `Divide`.</span></span> <span data-ttu-id="e38a7-128">第二個案例會將逾時值設為過短導致方法無法完成，以造成逾時情況。</span><span class="sxs-lookup"><span data-stu-id="e38a7-128">The second scenario causes a timeout condition by setting the timeout too short for the method to complete.</span></span> <span data-ttu-id="e38a7-129">從用戶端處理序產生的預期輸出如下：</span><span class="sxs-lookup"><span data-stu-id="e38a7-129">The expected output from the client process is:</span></span>  
  
```  
Add(100,15.99) = 115.99  
Simulated network problem occurs...  
Got System.ServiceModel.CommunicationObjectAbortedException  
Add(100,15.99) = 115.99  
Set timeout too short for method to complete...  
Got System.TimeoutException  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e38a7-130">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="e38a7-130">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="e38a7-131">請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="e38a7-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="e38a7-132">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="e38a7-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="e38a7-133">若要在單一或跨電腦組態中執行範例時，請依照中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="e38a7-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e38a7-134">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="e38a7-134">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e38a7-135">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="e38a7-135">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e38a7-136">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="e38a7-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e38a7-137">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="e38a7-137">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ExpectedExceptions`  
  
## <a name="see-also"></a><span data-ttu-id="e38a7-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e38a7-138">See Also</span></span>

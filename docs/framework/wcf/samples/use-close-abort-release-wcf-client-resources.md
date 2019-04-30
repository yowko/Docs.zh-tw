---
title: 使用關閉和中止發行 WCF 用戶端資源
description: Dispose 可以失敗，而且網路失敗時擲回例外狀況。 這可能導致不想要的行為。 相反地，使用關閉並釋放用戶端的資源，網路失敗時中止。
ms.date: 11/12/2018
ms.assetid: aff82a8d-933d-4bdc-b0c2-c2f7527204fb
ms.openlocfilehash: 58f828d9cd85806f5f04c349a7de18828ab5f6f2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62007569"
---
# <a name="close-and-abort-release-resources-safely-when-network-connections-have-dropped"></a><span data-ttu-id="e49d8-105">關閉和中止網路連線已卸除時，安全地釋放資源</span><span class="sxs-lookup"><span data-stu-id="e49d8-105">Close and Abort release resources safely when network connections have dropped</span></span>

<span data-ttu-id="e49d8-106">此範例示範如何使用`Close`和`Abort`方法，以清除資源，使用具類型的用戶端時。</span><span class="sxs-lookup"><span data-stu-id="e49d8-106">This sample demonstrates using the `Close` and `Abort` methods to clean up resources when using a typed client.</span></span> <span data-ttu-id="e49d8-107">`using`陳述式會不穩定的網路連線時，會導致例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e49d8-107">The `using` statement causes exceptions when the network connection is not robust.</span></span> <span data-ttu-id="e49d8-108">此樣本根據[開始使用](../../../../docs/framework/wcf/samples/getting-started-sample.md)以實作計算機服務。</span><span class="sxs-lookup"><span data-stu-id="e49d8-108">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="e49d8-109">在這個範例中，用戶端是主控台應用程式 (.exe)，而服務則是由網際網路資訊服務 (IIS) 所裝載。</span><span class="sxs-lookup"><span data-stu-id="e49d8-109">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>

> [!NOTE]
> <span data-ttu-id="e49d8-110">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="e49d8-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="e49d8-111">這個範例會說明兩個當 C# "using" 陳述式使用於具型別用戶端時發生的常見問題，並示範在例外狀況之後正確進行清除的程式碼。</span><span class="sxs-lookup"><span data-stu-id="e49d8-111">This sample shows two of the common problems that occur when using the C# "using" statement with typed clients, as well as code that correctly cleans up after exceptions.</span></span>

<span data-ttu-id="e49d8-112">C# "using" 陳述式會產生對 `Dispose`() 的呼叫。</span><span class="sxs-lookup"><span data-stu-id="e49d8-112">The C# "using" statement results in a call to `Dispose`().</span></span> <span data-ttu-id="e49d8-113">這就跟呼叫 `Close`() 一樣，可能會在發生網路錯誤時擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e49d8-113">This is the same as `Close`(), which may throw exceptions when a network error occurs.</span></span> <span data-ttu-id="e49d8-114">因為對 `Dispose`() 的呼叫會隱含地發生在 "using" 區塊的右邊大括號，所以撰寫和閱讀程式碼的人可能都不會注意到這個例外狀況來源。</span><span class="sxs-lookup"><span data-stu-id="e49d8-114">Because the call to `Dispose`() happens implicitly at the closing brace of the "using" block, this source of exceptions is likely to go unnoticed both by people writing the code and reading the code.</span></span> <span data-ttu-id="e49d8-115">這代表應用程式錯誤的潛在來源。</span><span class="sxs-lookup"><span data-stu-id="e49d8-115">This represents a potential source of application errors.</span></span>

<span data-ttu-id="e49d8-116">要在 `DemonstrateProblemUsingCanThrow` 方法中說明的第一個問題，是右大括號會擲回例外狀況，而且右大括號之後的程式碼不會執行：</span><span class="sxs-lookup"><span data-stu-id="e49d8-116">The first problem, illustrated in the `DemonstrateProblemUsingCanThrow` method, is that the closing brace throws an exception and the code after the closing brace does not execute:</span></span>

```csharp
using (CalculatorClient client = new CalculatorClient())
{
    ...
} // <-- this line might throw
Console.WriteLine("Hope this code wasn't important, because it might not happen.");
```

<span data-ttu-id="e49d8-117">即使在 using 區塊中沒有任何程式碼擲回例外狀況，或是已攔截到 using 區塊內的所有例外狀況，但 `Console.WriteLine` 可能仍然不執行，這是因為右大括號所隱含的 `Dispose`() 呼叫可能擲回了例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e49d8-117">Even if nothing inside the using block throws an exception or all exceptions inside the using block are caught, the `Console.WriteLine` might not happen because the implicit `Dispose`() call at the closing brace might throw an exception.</span></span>

<span data-ttu-id="e49d8-118">要在 `DemonstrateProblemUsingCanThrowAndMask` 方法中說明的第二個問題，則是右大括號的另一個會擲回例外狀況的隱含動作：</span><span class="sxs-lookup"><span data-stu-id="e49d8-118">The second problem, illustrated in the `DemonstrateProblemUsingCanThrowAndMask` method, is another implication of the closing brace throwing an exception:</span></span>

```csharp
using (CalculatorClient client = new CalculatorClient())
{
    ...
    throw new ApplicationException("Hope this exception was not important, because "+
                                   "it might be masked by the Close exception.");
} // <-- this line might throw an exception.
```

<span data-ttu-id="e49d8-119">因為 `Dispose`() 會在 "finally" 區塊內發生，如果 `ApplicationException`() 失敗，則永遠無法在 using 區塊之外見到 `Dispose`。</span><span class="sxs-lookup"><span data-stu-id="e49d8-119">Because the `Dispose`() occurs inside a "finally" block, the `ApplicationException` is never seen outside the using block if the `Dispose`() fails.</span></span> <span data-ttu-id="e49d8-120">如果區塊外面的程式碼必須知道 `ApplicationException` 何時發生，"using" 建構便可能因為遮罩了這個例外狀況而造成問題。</span><span class="sxs-lookup"><span data-stu-id="e49d8-120">If the code outside must know about when the `ApplicationException` occurs, the "using" construct may cause problems by masking this exception.</span></span>

<span data-ttu-id="e49d8-121">最後，範例會在 `DemonstrateCleanupWithExceptions` 中示範如何於例外狀況發生時正確清除。</span><span class="sxs-lookup"><span data-stu-id="e49d8-121">Finally, the sample demonstrates how to clean up correctly when exceptions occur in `DemonstrateCleanupWithExceptions`.</span></span> <span data-ttu-id="e49d8-122">這段程式碼會使用 try/catch 區塊，報告錯誤並呼叫 `Abort`。</span><span class="sxs-lookup"><span data-stu-id="e49d8-122">This uses a try/catch block to report errors and call `Abort`.</span></span> <span data-ttu-id="e49d8-123">請參閱[預期的例外狀況](../../../../docs/framework/wcf/samples/expected-exceptions.md)攔截例外狀況，從用戶端呼叫的更多詳細的範例。</span><span class="sxs-lookup"><span data-stu-id="e49d8-123">See the [Expected Exceptions](../../../../docs/framework/wcf/samples/expected-exceptions.md) sample for more details about catching exceptions from client calls.</span></span>

```csharp
try
{
    ...
    client.Close();
}
catch (CommunicationException e)
{
    ...
    client.Abort();
}
catch (TimeoutException e)
{
    ...
    client.Abort();
}
catch (Exception e)
{
    ...
    client.Abort();
    throw;
}
```

> [!NOTE]
> <span data-ttu-id="e49d8-124">使用陳述式和 ServiceHost:許多自我裝載的應用程式執行稍有多個裝載服務，，而 servicehost.close 則很少會擲回例外狀況，因此這類應用程式可以安全地使用 using 陳述式搭配 ServiceHost。</span><span class="sxs-lookup"><span data-stu-id="e49d8-124">The using statement and ServiceHost: Many self-hosting applications do little more than host a service, and ServiceHost.Close rarely throws an exception, so such applications can safely use the using statement with ServiceHost.</span></span> <span data-ttu-id="e49d8-125">但是要注意，ServiceHost.Close 可能擲回 `CommunicationException`，因此，如果應用程式會在關閉 ServiceHost 之後繼續執行，您應該避免使用 using 陳述式，而要遵循前述的模式。</span><span class="sxs-lookup"><span data-stu-id="e49d8-125">However, be aware that ServiceHost.Close can throw a `CommunicationException`, so if your application continues after closing the ServiceHost, you should avoid the using statement and follow the pattern previously given.</span></span>

<span data-ttu-id="e49d8-126">當您執行範例時，作業回應和例外狀況會顯示在用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="e49d8-126">When you run the sample, the operation responses and exceptions are displayed in the client console window.</span></span>

<span data-ttu-id="e49d8-127">用戶端處理序將執行三個案例，其中每一個都會嘗試呼叫 `Divide`。</span><span class="sxs-lookup"><span data-stu-id="e49d8-127">The client process runs three scenarios, each of which attempts to call `Divide`.</span></span> <span data-ttu-id="e49d8-128">第一個案例示範因 `Dispose`() 發生例外狀況而略過程式碼的情況。</span><span class="sxs-lookup"><span data-stu-id="e49d8-128">The first scenario demonstrates code being skipped because of an exception from `Dispose`().</span></span> <span data-ttu-id="e49d8-129">第二個案例示範因 `Dispose`() 發生例外狀況而遮罩了重要例外狀況的情況。</span><span class="sxs-lookup"><span data-stu-id="e49d8-129">The second scenario demonstrates an important exception being masked because of an exception from `Dispose`().</span></span> <span data-ttu-id="e49d8-130">第三個案例則示範進行正確清除。</span><span class="sxs-lookup"><span data-stu-id="e49d8-130">The third scenario demonstrates correct clean up.</span></span>

<span data-ttu-id="e49d8-131">從用戶端處理序產生的預期輸出如下：</span><span class="sxs-lookup"><span data-stu-id="e49d8-131">The expected output from the client process is:</span></span>

```
=
= Demonstrating problem:  closing brace of using statement can throw.
=
Got System.ServiceModel.CommunicationException from Divide.
Got System.ServiceModel.Security.MessageSecurityException
=
= Demonstrating problem:  closing brace of using statement can mask other Exceptions.
=
Got System.ServiceModel.CommunicationException from Divide.
Got System.ServiceModel.Security.MessageSecurityException
=
= Demonstrating cleanup with Exceptions.
=
Calling client.Add(0.0, 0.0);
        client.Add(0.0, 0.0); returned 0
Calling client.Divide(0.0, 0.0);
Got System.ServiceModel.CommunicationException from Divide.

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e49d8-132">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="e49d8-132">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="e49d8-133">請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="e49d8-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="e49d8-134">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="e49d8-134">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="e49d8-135">若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="e49d8-135">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e49d8-136">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="e49d8-136">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e49d8-137">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="e49d8-137">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="e49d8-138">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="e49d8-138">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e49d8-139">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="e49d8-139">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\UsingUsing`

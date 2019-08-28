---
title: ConcurrencyMode Reentrant
ms.date: 03/30/2017
ms.assetid: b2046c38-53d8-4a6c-a084-d6c7091d92b1
ms.openlocfilehash: c6bb73957da055e9d867fbcb78ce78acdb8d0b76
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040134"
---
# <a name="concurrencymode-reentrant"></a><span data-ttu-id="2e5f0-102">ConcurrencyMode Reentrant</span><span class="sxs-lookup"><span data-stu-id="2e5f0-102">ConcurrencyMode Reentrant</span></span>
<span data-ttu-id="2e5f0-103">這個範例示範在服務實作上使用 ConcurrencyMode.Reentrant 的必要性與隱含意義。</span><span class="sxs-lookup"><span data-stu-id="2e5f0-103">This sample demonstrates the necessity and implications of using ConcurrencyMode.Reentrant on a service implementation.</span></span> <span data-ttu-id="2e5f0-104">ConcurrencyMode.Reentrant 意指在指定的時間裡，服務 (或回呼) 只會處理一則訊息 (類似於 `ConcurencyMode.Single`)。</span><span class="sxs-lookup"><span data-stu-id="2e5f0-104">ConcurrencyMode.Reentrant implies that the service (or callback) processes only one message at a given time (analogous to `ConcurencyMode.Single`).</span></span> <span data-ttu-id="2e5f0-105">為確保執行緒安全, Windows Communication Foundation (WCF) 會鎖定`InstanceContext`處理訊息, 而不會處理任何其他訊息。</span><span class="sxs-lookup"><span data-stu-id="2e5f0-105">To ensure thread safety, Windows Communication Foundation (WCF) locks the `InstanceContext` processing a message so that no other messages can be processed.</span></span> <span data-ttu-id="2e5f0-106">在 Reentrant 模式的情況下，會在服務即將進行傳出呼叫之前解除鎖定 `InstanceContext` (因此允許進行後續呼叫，而這個呼叫可能是可重新進入 (Reentrant) 的，如範例中所示)，以便在下次進入服務時取得鎖定。</span><span class="sxs-lookup"><span data-stu-id="2e5f0-106">In case of Reentrant mode, the `InstanceContext` is unlocked just before the service makes an outgoing call thereby allowing the subsequent call, (which can be reentrant as demonstrated in the sample) to get the lock next time it comes in to the service.</span></span> <span data-ttu-id="2e5f0-107">為方便示範行為，範例會顯示用戶端與服務如何使用雙工合約相互傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="2e5f0-107">To demonstrate the behavior, the sample shows how a client and service can send messages between each other using a duplex contract.</span></span>  
  
 <span data-ttu-id="2e5f0-108">所定義的合約是一份雙工合約，其中包含服務所實作的 `Ping` 方法，以及用戶端所實作的 `Pong` 回呼方法。</span><span class="sxs-lookup"><span data-stu-id="2e5f0-108">The contract defined is a duplex contract with the `Ping` method being implemented by the service and the callback method `Pong` being implemented by the client.</span></span> <span data-ttu-id="2e5f0-109">用戶端會使用滴答計數來叫用伺服器的 `Ping` 方法，從而啟始呼叫。</span><span class="sxs-lookup"><span data-stu-id="2e5f0-109">A client invokes the server's `Ping` method with a tick count thereby initiating the call.</span></span> <span data-ttu-id="2e5f0-110">服務則會確認滴答計數不等於 0，再叫用回呼方法 `Pong`，並同時遞減滴答計數。</span><span class="sxs-lookup"><span data-stu-id="2e5f0-110">The service checks whether the tick count is not equal to 0 and then invokes the callbacks `Pong` method while decrementing the tick count.</span></span> <span data-ttu-id="2e5f0-111">其做法如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="2e5f0-111">This is done by the following code in the sample.</span></span>  
  
```csharp
public void Ping(int ticks)  
{  
     Console.WriteLine("Ping: Ticks = " + ticks);  
     //Keep pinging back and forth till Ticks reaches 0.  
     if (ticks != 0)  
     {  
         OperationContext.Current.GetCallbackChannel<IPingPongCallback>().Pong((ticks - 1));  
     }  
}  
```  
  
 此回呼之 `Pong` 實作的邏輯與 `Ping` 實作的相同。 也就是，它會確認滴答計數不為零，然後在回呼通道 (在本例中，是先前用來傳送原始 `Ping` 訊息的通道) 上叫用 `Ping` 方法，並將滴答計數遞減 1。 一旦滴答計數到達 0，方法就會將所有回覆傳回 (從而將其包裝解開) 至啟始呼叫之用戶端所發出的第一項呼叫。 <span data-ttu-id="2e5f0-115">其做法如下列回呼實作所示。</span><span class="sxs-lookup"><span data-stu-id="2e5f0-115">This is shown in the callback implementation.</span></span>  
  
```csharp
public void Pong(int ticks)  
{  
    Console.WriteLine("Pong: Ticks = " + ticks);  
    if (ticks != 0)  
    {  
        //Retrieve the Callback  Channel (in this case the Channel which was used to send the  
        //original message) and make an outgoing call until ticks reaches 0.  
        IPingPong channel = OperationContext.Current.GetCallbackChannel<IPingPong>();  
        channel.Ping((ticks - 1));  
    }  
}  
```  
  
 `Ping` 和 `Pong` 方法都屬於要求/回覆模式，意即在 `Ping` 的呼叫傳回之前，對於 `CallbackChannel<T>.Pong()` 的第一項呼叫將不會傳回。 在用戶端上，`Pong` 方法要等到它所進行的下一個 `Ping` 呼叫傳回時，才會傳回。 <span data-ttu-id="2e5f0-118">因為回呼和服務都必須進行傳出的要求/回覆呼叫，才能回覆暫止要求，所以必須將這兩個實作標記為 ConcurrencyMode.Reentrant 行為。</span><span class="sxs-lookup"><span data-stu-id="2e5f0-118">Because both the callback and the service must make outgoing request/reply calls before they can reply for the pending request, both the implementations must be marked with the ConcurrencyMode.Reentrant behavior.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2e5f0-119">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="2e5f0-119">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="2e5f0-120">請確定您已[針對 Windows Communication Foundation 範例執行一次安裝程式](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="2e5f0-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="2e5f0-121">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="2e5f0-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="2e5f0-122">若要在單一或跨電腦設定中執行範例, 請遵循執行[Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="2e5f0-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="2e5f0-123">示範</span><span class="sxs-lookup"><span data-stu-id="2e5f0-123">Demonstrates</span></span>  
 <span data-ttu-id="2e5f0-124">若要執行範例，請建置用戶端和伺服器專案，</span><span class="sxs-lookup"><span data-stu-id="2e5f0-124">To run the sample, build the client and server projects.</span></span> <span data-ttu-id="2e5f0-125">然後開啟兩個命令視窗, 並將目錄變更\<為範例 > \CS\Service\bin\debug \<和範例 > \CS\Client\bin\debug 目錄。</span><span class="sxs-lookup"><span data-stu-id="2e5f0-125">Then open two command windows and change the directories to the \<sample>\CS\Service\bin\debug and \<sample>\CS\Client\bin\debug directories.</span></span> <span data-ttu-id="2e5f0-126">然後藉由輸入`service.exe`來啟動服務, 然後使用當做輸入引數傳遞的初始值來叫用 Client .exe。</span><span class="sxs-lookup"><span data-stu-id="2e5f0-126">Then start the service by typing `service.exe` and then invoke the Client.exe with the initial value of ticks passed as an input argument.</span></span> <span data-ttu-id="2e5f0-127">10 次滴答計數的範例輸出如下所示。</span><span class="sxs-lookup"><span data-stu-id="2e5f0-127">A sample output for 10 ticks is shown.</span></span>  
  
```console  
Prompt>Service.exe  
ServiceHost Started. Press Enter to terminate service.  
Ping: Ticks = 10  
Ping: Ticks = 8  
Ping: Ticks = 6  
Ping: Ticks = 4  
Ping: Ticks = 2  
Ping: Ticks = 0  
  
Prompt>Client.exe 10  
Pong: Ticks = 9  
Pong: Ticks = 7  
Pong: Ticks = 5  
Pong: Ticks = 3  
Pong: Ticks = 1  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="2e5f0-128">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="2e5f0-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2e5f0-129">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="2e5f0-129">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="2e5f0-130">如果此目錄不存在, 請移至[.NET Framework 4 的 Windows Communication Foundation (wcf) 和 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780), 以下載所有 Windows Communication Foundation (wcf) [!INCLUDE[wf1](../../../../includes/wf1-md.md)]和範例。</span><span class="sxs-lookup"><span data-stu-id="2e5f0-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2e5f0-131">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="2e5f0-131">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Reentrant`  

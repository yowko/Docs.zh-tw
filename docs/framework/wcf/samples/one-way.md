---
title: 單向
ms.date: 03/30/2017
ms.assetid: 74e3e03d-cd15-4191-a6a5-1efa2dcb9e73
ms.openlocfilehash: e82034a79610ea7956b3ef07508295578461de1b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008029"
---
# <a name="one-way"></a><span data-ttu-id="00f18-102">單向</span><span class="sxs-lookup"><span data-stu-id="00f18-102">One-Way</span></span>
<span data-ttu-id="00f18-103">這個範例示範具有單向服務作業的服務合約。</span><span class="sxs-lookup"><span data-stu-id="00f18-103">This sample demonstrates a service contact with one-way service operations.</span></span> <span data-ttu-id="00f18-104">與雙向服務作業的情況不同，用戶端不會等候服務作業完成。</span><span class="sxs-lookup"><span data-stu-id="00f18-104">The client does not wait for service operations to complete as is the case with two-way service operations.</span></span> <span data-ttu-id="00f18-105">此樣本根據[快速入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)，並使用`wsHttpBinding`繫結。</span><span class="sxs-lookup"><span data-stu-id="00f18-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and uses the `wsHttpBinding` binding.</span></span> <span data-ttu-id="00f18-106">這個範例中的服務是自我裝載的主控台應用程式，您可以用來觀察接收和處理要求的服務。</span><span class="sxs-lookup"><span data-stu-id="00f18-106">The service in this sample is a self-hosted console application to enable you to observe the service that receives and processes requests.</span></span> <span data-ttu-id="00f18-107">用戶端也是主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="00f18-107">The client is also a console application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="00f18-108">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="00f18-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="00f18-109">若要建立單向服務合約，請定義服務合約、將 <xref:System.ServiceModel.OperationContractAttribute> 類別套用至每一項作業，然後將 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> 設定為 `true`，如下列範例程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="00f18-109">To create a one-way service contract, define your service contract, apply the <xref:System.ServiceModel.OperationContractAttribute> class to each operation, and set <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> to `true` as shown in the following sample code:</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOneWayCalculator  
{  
    [OperationContract(IsOneWay=true)]  
    void Add(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Subtract(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Multiply(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Divide(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="00f18-110">為了示範用戶端不等待服務作業完成的狀況，本範例中的服務程式碼實作了五秒鐘的延遲，如下列範例程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="00f18-110">To demonstrate that the client does not wait for the service operations to complete, the service code in this sample implements a five-second delay, as shown in the following sample code:</span></span>  
  
```csharp
// This service class implements the service contract.  
// This code writes output to the console window.  
 [ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Multiple,  
    InstanceContextMode = InstanceContextMode.PerCall)]  
public class CalculatorService : IOneWayCalculator  
{  
    public void Add(double n1, double n2)  
    {  
        Console.WriteLine("Received Add({0},{1}) - sleeping", n1, n2);  
        System.Threading.Thread.Sleep(1000 * 5);  
        double result = n1 + n2;  
        Console.WriteLine("Processing Add({0},{1}) - result: {2}", n1, n2, result);  
    }  
    ...  
}  
```  
  
 <span data-ttu-id="00f18-111">當用戶端呼叫服務時，該呼叫會逕自傳回，而不等待服務作業完成。</span><span class="sxs-lookup"><span data-stu-id="00f18-111">When the client calls the service, the call returns without waiting for the service operation to complete.</span></span>  
  
 <span data-ttu-id="00f18-112">當您執行範例時，用戶端與服務活動都會顯示在服務與用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="00f18-112">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="00f18-113">您可以查看來自用戶端的服務接收訊息。</span><span class="sxs-lookup"><span data-stu-id="00f18-113">You can see the service receive messages from the client.</span></span> <span data-ttu-id="00f18-114">請在每個主控台視窗中按下 ENTER，以關閉服務與用戶端。</span><span class="sxs-lookup"><span data-stu-id="00f18-114">Press ENTER in each console window to shut down both the service and the client.</span></span>  
  
 <span data-ttu-id="00f18-115">用戶端會比服務先完成，表示用戶端不會等候單向服務作業完成。</span><span class="sxs-lookup"><span data-stu-id="00f18-115">The client finishes ahead of the service, demonstrating that a client does not wait for one-way service operations to complete.</span></span> <span data-ttu-id="00f18-116">用戶端輸出如下：</span><span class="sxs-lookup"><span data-stu-id="00f18-116">The client output is as follows:</span></span>  
  
```console  
Add(100,15.99)  
Subtract(145,76.54)  
Multiply(9,81.25)  
Divide(22,7)  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="00f18-117">服務輸出如下：</span><span class="sxs-lookup"><span data-stu-id="00f18-117">The following service output is shown:</span></span>  
  
```console  
The service is ready.  
Press <ENTER> to terminate service.  
  
Received Add(100,15.99) - sleeping  
Received Subtract(145,76.54) - sleeping  
Received Multiply(9,81.25) - sleeping  
Received Divide(22,7) - sleeping  
Processing Add(100,15.99) - result: 115.99  
Processing Subtract(145,76.54) - result: 68.46  
Processing Multiply(9,81.25) - result: 731.25  
Processing Divide(22,7) - result: 3.14285714285714  
```  
  
> [!NOTE]
>  <span data-ttu-id="00f18-118">根據定義，HTTP 是一種要求/回應通訊協定；當要求提出時，就會傳回回應。</span><span class="sxs-lookup"><span data-stu-id="00f18-118">HTTP is, by definition, a request/response protocol; when a request is made, a response is returned.</span></span> <span data-ttu-id="00f18-119">即便是在 HTTP 上公開的單向服務作業，也是如此。</span><span class="sxs-lookup"><span data-stu-id="00f18-119">This is true even for a one-way service operation that is exposed over HTTP.</span></span> <span data-ttu-id="00f18-120">呼叫作業時，服務會在服務作業執行以前傳回 202 的 HTTP 狀態碼。</span><span class="sxs-lookup"><span data-stu-id="00f18-120">When the operation is called, the service returns an HTTP status code of 202 before the service operation has executed.</span></span> <span data-ttu-id="00f18-121">這個狀態碼表示已接受要求進行處理，但是處理尚未完成。</span><span class="sxs-lookup"><span data-stu-id="00f18-121">This status code means that the request has been accepted for processing, but the processing has not yet been completed.</span></span> <span data-ttu-id="00f18-122">呼叫此項作業的用戶端會封鎖，直到從服務收到 202 回應為止。</span><span class="sxs-lookup"><span data-stu-id="00f18-122">The client that called the operation blocks until it receives the 202 response from the service.</span></span> <span data-ttu-id="00f18-123">當使用設定為使用工作階段的繫結來傳送多則單向訊息時，這可能會產生某種未預期的行為。</span><span class="sxs-lookup"><span data-stu-id="00f18-123">This can cause some unexpected behavior when multiple one-way messages are sent using a binding that is configured to use sessions.</span></span> <span data-ttu-id="00f18-124">根據預設，這個範例中使用的 `wsHttpBinding` 繫結會設定為使用工作階段，以便建立安全性內容。</span><span class="sxs-lookup"><span data-stu-id="00f18-124">The `wsHttpBinding` binding used in this sample is configured to use sessions by default to establish a security context.</span></span> <span data-ttu-id="00f18-125">在預設情況下，將保證工作階段中的訊息依照傳送的順序抵達。</span><span class="sxs-lookup"><span data-stu-id="00f18-125">By default, messages in a session are guaranteed to arrive in the order in which they are sent.</span></span> <span data-ttu-id="00f18-126">因此，傳送工作階段中的第二則訊息時，就不會在第一則訊息處理完成之前加以處理。</span><span class="sxs-lookup"><span data-stu-id="00f18-126">Because of this, when the second message in a session is sent, it is not processed until the first message has been processed.</span></span> <span data-ttu-id="00f18-127">因此，除非完成處理上一則的訊息，否則，用戶端將不會收到訊息的 202 回應。</span><span class="sxs-lookup"><span data-stu-id="00f18-127">The result of this is that the client does not receive the 202 response for a message until the processing of the previous message has been completed.</span></span> <span data-ttu-id="00f18-128">所以用戶端會顯示為封鎖每次呼叫後續的作業。</span><span class="sxs-lookup"><span data-stu-id="00f18-128">The client therefore appears to block on each subsequent operation call.</span></span> <span data-ttu-id="00f18-129">為了避免這種行為，此範例將執行階段設定為同時分派訊息至不同執行個體以進行處理。</span><span class="sxs-lookup"><span data-stu-id="00f18-129">To avoid this behavior, this sample configures the runtime to dispatch messages concurrently to distinct instances for processing.</span></span> <span data-ttu-id="00f18-130">範例將 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> 設定為 `PerCall`，讓個別訊息可以分別由不同執行個體來處理。</span><span class="sxs-lookup"><span data-stu-id="00f18-130">The sample sets <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> to `PerCall` so that each message can be processed by a different instance.</span></span> <span data-ttu-id="00f18-131"><xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> 會設定為 `Multiple`，以允許多個執行緒同時分派訊息。</span><span class="sxs-lookup"><span data-stu-id="00f18-131"><xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to `Multiple` to allow more than one thread to dispatch messages at a time.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="00f18-132">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="00f18-132">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="00f18-133">請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="00f18-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="00f18-134">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="00f18-134">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="00f18-135">若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="00f18-135">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="00f18-136">請先執行服務，然後才執行用戶端；先關閉用戶端，再關閉服務。</span><span class="sxs-lookup"><span data-stu-id="00f18-136">Run the service before you run the client and shut down the client before shutting down the service.</span></span> <span data-ttu-id="00f18-137">這可以避免當用戶端因服務消失而無法正常關閉安全性工作階段時，所發生的用戶端例外狀況。</span><span class="sxs-lookup"><span data-stu-id="00f18-137">This avoids a client exception when the client cannot close the security session cleanly because the service is gone.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="00f18-138">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="00f18-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="00f18-139">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="00f18-139">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="00f18-140">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="00f18-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="00f18-141">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="00f18-141">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Oneway`  

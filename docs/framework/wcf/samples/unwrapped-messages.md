---
title: 未包裝的訊息
ms.date: 03/30/2017
ms.assetid: 019657bd-1f9b-4315-ad74-eaa4e7551ff6
ms.openlocfilehash: 161f38e474534d5a0e522817c4bd64925bb4cac6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "59976751"
---
# <a name="unwrapped-messages"></a><span data-ttu-id="6d148-102">未包裝的訊息</span><span class="sxs-lookup"><span data-stu-id="6d148-102">Unwrapped Messages</span></span>
<span data-ttu-id="6d148-103">此範例示範未包裝的訊息。</span><span class="sxs-lookup"><span data-stu-id="6d148-103">This sample demonstrates unwrapped messages.</span></span> <span data-ttu-id="6d148-104">根據預設，訊息本文會格式化，以便包裝服務作業的參數。</span><span class="sxs-lookup"><span data-stu-id="6d148-104">By default, the message body is formatted such that the parameters to a service operation are wrapped.</span></span> <span data-ttu-id="6d148-105">下列範例說明對包裝模式中對 `Add` 服務的 `ICalculator` 要求訊息。</span><span class="sxs-lookup"><span data-stu-id="6d148-105">The following sample shows an `Add` request message to the `ICalculator` service in wrapped mode.</span></span>  
  
```xml  
<s:Envelope   
    xmlns:s="http://www.w3.org/2003/05/soap-envelope"  
    xmlns:a="http://schemas.xmlsoap.org/ws/2005/08/addressing">  
    <s:Header>  
        …  
    </s:Header>  
    <s:Body>  
      <Add xmlns="http://Microsoft.ServiceModel.Samples">  
        <n1>100</n1>  
        <n2>15.99</n2>  
      </Add>  
    </s:Body>  
</s:Envelope>  
```  
  
 <span data-ttu-id="6d148-106">訊息本文中的 `<Add>` 項目會包裝 `n1` 和 `n2` 參數。</span><span class="sxs-lookup"><span data-stu-id="6d148-106">The `<Add>` element in the message body wraps the `n1` and `n2` parameters.</span></span> <span data-ttu-id="6d148-107">相反地，下列範例說明未包裝模式中的對等訊息。</span><span class="sxs-lookup"><span data-stu-id="6d148-107">In contrast, the following sample shows the equivalent message in the unwrapped mode.</span></span>  
  
```xml  
<s:Envelope   
    xmlns:s="http://www.w3.org/2003/05/soap-envelope"   
    xmlns:a="http://schemas.xmlsoap.org/ws/2005/08/addressing">  
    <s:Header>  
        ….  
    </s:Header>  
    <s:Body>  
      <n1 xmlns="http://Microsoft.ServiceModel.Samples">100</n1>  
      <n2 xmlns="http://Microsoft.ServiceModel.Samples">15.99</n2>  
    </s:Body>  
  </s:Envelope>  
</MessageLogTraceRecord>  
```  
  
 <span data-ttu-id="6d148-108">未包裝的訊息不會包裝在包含項目中的 `n1` 和 `n2` 參數，它們是 SOAP 本文項目的直接子系。</span><span class="sxs-lookup"><span data-stu-id="6d148-108">The unwrapped message does not wrap the `n1` and `n2` parameters in a containing element, they are direct children of the soap body element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6d148-109">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="6d148-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="6d148-110">在此範例中，未包裝訊息的建立方式是將 <xref:System.ServiceModel.MessageContractAttribute> 套用至服務作業參數型別和傳回值型別，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="6d148-110">In this sample, an unwrapped message is created by applying the <xref:System.ServiceModel.MessageContractAttribute> to the service operation parameter type and return value type as shown in the following sample code.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    ResponseMessage Add(RequestMessage request);  
    [OperationContract]  
    ResponseMessage Subtract(RequestMessage request);  
    [OperationContract]  
    ResponseMessage Multiply(RequestMessage request);  
    [OperationContract]  
    ResponseMessage Divide(RequestMessage request);  
}  
  
//setting IsWrapped to false means the n1 and n2  
//members will be direct children of the soap body element  
[MessageContract(IsWrapped = false)]  
public class RequestMessage  
{  
    [MessageBodyMember]  
    private double n1;  
    [MessageBodyMember]  
    private double n2;  
    //…  
}  
  
//setting IsWrapped to false means the result  
//member will be a direct child of the soap body element  
[MessageContract(IsWrapped = false)]  
public class ResponseMessage  
{  
    [MessageBodyMember]  
    private double result;  
    //…  
}  
```  
  
 <span data-ttu-id="6d148-111">為了可讓您看到正在傳送和接收的訊息，此範例使用追蹤。</span><span class="sxs-lookup"><span data-stu-id="6d148-111">To allow you to see the messages being sent and received, this sample uses tracing.</span></span> <span data-ttu-id="6d148-112">此外，<xref:System.ServiceModel.WSHttpBinding> 已設定為不帶安全性，可減少其記錄的訊息數量。</span><span class="sxs-lookup"><span data-stu-id="6d148-112">In addition, the <xref:System.ServiceModel.WSHttpBinding> has been configured without security, to reduce the number of messages it logs.</span></span>  
  
 <span data-ttu-id="6d148-113">產生的追蹤記錄檔 (c:\logs\Message.log) 可以使用檢視[Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="6d148-113">The resulting trace log (c:\logs\Message.log) can be viewed by using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="6d148-114">若要檢視訊息內容，請選取**訊息**左和右窗格的 [服務追蹤檢視器] 工具中。</span><span class="sxs-lookup"><span data-stu-id="6d148-114">To view message contents, select **Messages** in both the left and the right panes of the Service Trace Viewer tool.</span></span> <span data-ttu-id="6d148-115">此範例中的追蹤記錄是設定為產生至 C:\LOGS 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="6d148-115">Trace logs in this sample are configured to be generated into the C:\LOGS folder.</span></span> <span data-ttu-id="6d148-116">請先建立這個資料夾，然後再執行範例並給予使用者這個目錄的網路服務寫入權限。</span><span class="sxs-lookup"><span data-stu-id="6d148-116">Create this folder before running the sample and give the user Network Service write permissions for this directory.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6d148-117">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="6d148-117">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="6d148-118">請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="6d148-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="6d148-119">建立用於記錄訊息的 C:\LOGS 目錄。</span><span class="sxs-lookup"><span data-stu-id="6d148-119">Create a C:\LOGS directory for logging messages.</span></span> <span data-ttu-id="6d148-120">給予使用者這個目錄的網路服務寫入權限。</span><span class="sxs-lookup"><span data-stu-id="6d148-120">Give the user Network Service write permissions for this directory.</span></span>  
  
3. <span data-ttu-id="6d148-121">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="6d148-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="6d148-122">若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="6d148-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6d148-123">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="6d148-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6d148-124">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="6d148-124">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6d148-125">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="6d148-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6d148-126">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="6d148-126">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Unwrapped`  

---
title: "預設訊息合約"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Message Contract
ms.assetid: 5a200b78-1a46-4104-b7fb-da6dbab33893
caps.latest.revision: "35"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 407fa758c6564c3b7a5a8573acef1b6e181399d2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="default-message-contract"></a><span data-ttu-id="1e3ad-102">預設訊息合約</span><span class="sxs-lookup"><span data-stu-id="1e3ad-102">Default Message Contract</span></span>
<span data-ttu-id="1e3ad-103">預設訊息合約範例會示範一個服務，在這個服務中可以對服務作業來回傳遞自訂的使用者定義訊息。</span><span class="sxs-lookup"><span data-stu-id="1e3ad-103">The Default Message Contract sample demonstrates a service where a custom user-defined message is passed to and from service operations.</span></span> <span data-ttu-id="1e3ad-104">這個範例根據[入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)，用來實作計算機介面，以具型別的服務。</span><span class="sxs-lookup"><span data-stu-id="1e3ad-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator interface as a typed service.</span></span> <span data-ttu-id="1e3ad-105">而不是個別服務作業的加法、 減法、 乘法和除法用於[入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)，此範例會傳遞包含運算元和運算子，並傳回的自訂訊息算術運算的結果。</span><span class="sxs-lookup"><span data-stu-id="1e3ad-105">Instead of the individual service operations for addition, subtraction, multiplication, and division used in the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), this sample passes a custom message that contains both the operands and the operator, and returns the result of the arithmetic calculation.</span></span>  
  
 <span data-ttu-id="1e3ad-106">用戶端是主控台程式 (.exe)，而服務程式庫 (.dll) 是由網際網路資訊服務 (IIS) 所裝載。</span><span class="sxs-lookup"><span data-stu-id="1e3ad-106">The client is a console program (.exe) and the service library (.dll) is hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="1e3ad-107">您可以在主控台視窗中看到用戶端活動。</span><span class="sxs-lookup"><span data-stu-id="1e3ad-107">Client activity is visible in the console window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1e3ad-108">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="1e3ad-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="1e3ad-109">在服務中，會定義單一服務作業，而這個作業會接受並傳回型別為 `MyMessage` 的自訂訊息。</span><span class="sxs-lookup"><span data-stu-id="1e3ad-109">In the service, a single service operation is defined that accepts and returns custom messages of type `MyMessage`.</span></span> <span data-ttu-id="1e3ad-110">雖然這個範例中的要求和回應訊息型別相同，但在必要時一定是不同的訊息合約。</span><span class="sxs-lookup"><span data-stu-id="1e3ad-110">Although in this sample the request and response messages are of the same type, they could of course be different message contracts if necessary.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract(Action="http://test/MyMessage_action",  
                  ReplyAction="http://test/MyMessage_action")]  
    MyMessage Calculate(MyMessage request);  
}  
```  
  
 <span data-ttu-id="1e3ad-111">自訂訊息 `MyMessage` 是定義在以 <xref:System.ServiceModel.MessageContractAttribute>、<xref:System.ServiceModel.MessageHeaderAttribute> 和 <xref:System.ServiceModel.MessageBodyMemberAttribute> 屬性註解的類別中。</span><span class="sxs-lookup"><span data-stu-id="1e3ad-111">The custom message `MyMessage` is defined in a class annotated with <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes.</span></span> <span data-ttu-id="1e3ad-112">這個範例中只使用了第三個建構函式。</span><span class="sxs-lookup"><span data-stu-id="1e3ad-112">Only the third constructor is used in this sample.</span></span> <span data-ttu-id="1e3ad-113">使用訊息合約可讓您完全控制 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="1e3ad-113">Using message contracts allows you to exercise full control over the SOAP message.</span></span> <span data-ttu-id="1e3ad-114">在這個範例中，會使用 <xref:System.ServiceModel.MessageHeaderAttribute> 屬性，將 `Operation` 放在 SOAP 標頭中。</span><span class="sxs-lookup"><span data-stu-id="1e3ad-114">In this sample, the <xref:System.ServiceModel.MessageHeaderAttribute> attribute is used to put `Operation` in a SOAP header.</span></span> <span data-ttu-id="1e3ad-115">因為運算元 `N1`、`N2` 和 `Result` 都套用了 <xref:System.ServiceModel.MessageBodyMemberAttribute> 屬性，所以會出現在 SOAP 本文中。</span><span class="sxs-lookup"><span data-stu-id="1e3ad-115">The operands `N1`, `N2` and the `Result` appear within the SOAP body because they have the <xref:System.ServiceModel.MessageBodyMemberAttribute> attribute applied.</span></span>  
  
```  
[MessageContract]  
public class MyMessage  
{  
    private string operation;  
    private double n1;  
    private double n2;  
    private double result;  
  
    //Constructor - create an empty message.  
  
    public MyMessage() {}  
  
    //Constructor - create a message and populate its members.  
  
    public MyMessage(double n1, double n2, string operation,   
                     double result)  
    {  
        this.n1 = n1;  
        this.n2 = n2;  
        this.operation = operation;  
        this.result = result;  
    }  
  
    //Constructor - create a message from another message.  
  
    public MyMessage(MyMessage message)  
    {  
        this.n1 = message.n1;  
        this.n2 = message.n2;  
        this.operation = message.operation;  
        this.result = message.result;  
    }  
  
    [MessageHeader]  
    public string Operation  
    {  
        get { return operation; }  
        set { operation = value; }  
    }  
  
    [MessageBodyMember]  
    public double N1  
    {  
        get { return n1; }  
        set { n1 = value; }  
    }  
  
    [MessageBodyMember]  
    public double N2  
    {  
        get { return n2; }  
        set { n2 = value; }  
    }  
  
    [MessageBodyMember]  
    public double Result  
    {  
        get { return result; }  
        set { result = value; }  
    }  
}  
```  
  
 <span data-ttu-id="1e3ad-116">實作類別包含 `Calculate` 服務作業的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1e3ad-116">The implementation class contains the code for the `Calculate` service operation.</span></span> <span data-ttu-id="1e3ad-117">`CalculateService` 類別會從要求訊息中取得運算元和運算子，然後建立包含所要求之計算結果的回應訊息，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="1e3ad-117">The `CalculateService` class obtains the operands and operator from the request message and creates a response message that contains the result of the requested calculation, as shown in the following sample code.</span></span>  
  
```  
// Service class which implements the service contract.  
public class CalculatorService : ICalculator  
{  
    // Perform a calculation.  
  
    public MyMessage Calculate(MyMessage request)  
    {  
        MyMessage response = new MyMessage(request);  
        switch (request.Operation)  
        {  
            case "+":  
                response.Result = request.N1 + request.N2;  
                break;  
            case "-":  
                response.Result = request.N1 - request.N2;  
                break;  
            case "*":  
                response.Result = request.N1 * request.N2;  
                break;  
            case "/":  
                response.Result = request.N1 / request.N2;  
                break;  
            default:  
                response.Result = 0.0D;  
                break;  
        }  
        return response;  
    }  
}  
```  
  
 <span data-ttu-id="1e3ad-118">用戶端產生的用戶端程式碼以建立[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)工具。</span><span class="sxs-lookup"><span data-stu-id="1e3ad-118">The generated client code for the client was created with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool.</span></span> <span data-ttu-id="1e3ad-119">必要時，這個工具會自動在產生的用戶端程式碼中建立訊息合約類型。</span><span class="sxs-lookup"><span data-stu-id="1e3ad-119">The tool automatically creates message contract types in the generated client code if necessary.</span></span> <span data-ttu-id="1e3ad-120">您也可以指定 `/messageContract` 命令選項來強制產生訊息合約。</span><span class="sxs-lookup"><span data-stu-id="1e3ad-120">The `/messageContract` command option may be specified to force the generation of message contracts.</span></span>  
  
```  
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" /o:client\generatedClient.cs http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="1e3ad-121">下列範例程式碼示範使用 `MyMessage` 訊息的用戶端。</span><span class="sxs-lookup"><span data-stu-id="1e3ad-121">The following sample code demonstrates the client using the `MyMessage` message.</span></span>  
  
```  
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
// Perform addition using a typed message.  
  
MyMessage request = new MyMessage();  
request.N1 = 100D;  
request.N2 = 15.99D;  
request.Operation = "+";  
MyMessage response = ((ICalculator)client).Calculate(request);  
Console.WriteLine("Add({0},{1}) = {2}", request.N1, request.N2, response.Result);  
```  
  
 <span data-ttu-id="1e3ad-122">當您執行範例時，計算過程會顯示在用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="1e3ad-122">When you run the sample, the calculations are displayed in the client console window.</span></span> <span data-ttu-id="1e3ad-123">在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="1e3ad-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="1e3ad-124">此時，自訂的使用者定義訊息已在用戶端和服務作業之間傳遞。</span><span class="sxs-lookup"><span data-stu-id="1e3ad-124">At this point, custom user-defined messages have passed between the client and the service operation.</span></span> <span data-ttu-id="1e3ad-125">訊息合約已定義將運算元和結果放在訊息本文中，而將運算子放在訊息標頭中。</span><span class="sxs-lookup"><span data-stu-id="1e3ad-125">The message contract defined that the operands and results were in the message body and that the operator was in a message header.</span></span> <span data-ttu-id="1e3ad-126">您可以設定訊息記錄來觀察這個訊息結構。</span><span class="sxs-lookup"><span data-stu-id="1e3ad-126">Message logging can be configured to observe this message structure.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1e3ad-127">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="1e3ad-127">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="1e3ad-128">請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="1e3ad-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="1e3ad-129">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="1e3ad-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="1e3ad-130">若要在單一或跨電腦組態中執行範例時，請依照中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="1e3ad-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1e3ad-131">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="1e3ad-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1e3ad-132">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="1e3ad-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1e3ad-133">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="1e3ad-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1e3ad-134">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="1e3ad-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Default`  
  
## <a name="see-also"></a><span data-ttu-id="1e3ad-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e3ad-135">See Also</span></span>

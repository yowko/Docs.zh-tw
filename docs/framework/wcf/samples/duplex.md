---
title: 雙工
ms.date: 03/30/2017
helpviewer_keywords:
- Duplex Service Contract
ms.assetid: bc5de6b6-1a63-42a3-919a-67d21bae24e0
ms.openlocfilehash: c132b49c3d1ff1cd72c7a02f66ad4bf6d2d65d1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33506642"
---
# <a name="duplex"></a><span data-ttu-id="b2cad-102">雙工</span><span class="sxs-lookup"><span data-stu-id="b2cad-102">Duplex</span></span>
<span data-ttu-id="b2cad-103">雙工範例示範如何定義和實作雙工合約。</span><span class="sxs-lookup"><span data-stu-id="b2cad-103">The Duplex sample demonstrates how to define and implement a duplex contract.</span></span> <span data-ttu-id="b2cad-104">用戶端建立與服務的工作階段，並提供服務所需的通道以供服務將訊息傳回用戶端，這個程序即是所謂的雙工通訊。</span><span class="sxs-lookup"><span data-stu-id="b2cad-104">Duplex communication occurs when a client establishes a session with a service and gives the service a channel on which the service can send messages back to the client.</span></span> <span data-ttu-id="b2cad-105">這個範例根據[入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="b2cad-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="b2cad-106">雙工合約被定義為一對介面，其中的主要介面從用戶端到服務，回呼介面從服務到用戶端。</span><span class="sxs-lookup"><span data-stu-id="b2cad-106">A duplex contract is defined as a pair of interfaces—a primary interface from the client to the service and a callback interface from the service to the client.</span></span> <span data-ttu-id="b2cad-107">在此範例中，`ICalculatorDuplex` 介面允許用戶端執行數學運算，透過工作階段執行結果。</span><span class="sxs-lookup"><span data-stu-id="b2cad-107">In this sample, the `ICalculatorDuplex` interface allows the client to perform math operations, calculating the result over a session.</span></span> <span data-ttu-id="b2cad-108">服務傳回 `ICalculatorDuplexCallback` 介面上的結果。</span><span class="sxs-lookup"><span data-stu-id="b2cad-108">The service returns results on the `ICalculatorDuplexCallback` interface.</span></span> <span data-ttu-id="b2cad-109">雙工合約需要一個工作階段，因為必須建立內容，將用戶端與服務之間傳送的訊息關聯在一起。</span><span class="sxs-lookup"><span data-stu-id="b2cad-109">A duplex contract requires a session, because a context must be established to correlate the set of messages being sent between the client and the service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2cad-110">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="b2cad-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="b2cad-111">在這個範例中，用戶端是主控台應用程式 (.exe)，而服務則是由網際網路資訊服務 (IIS) 所裝載。</span><span class="sxs-lookup"><span data-stu-id="b2cad-111">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="b2cad-112">雙工合約的定義如下：</span><span class="sxs-lookup"><span data-stu-id="b2cad-112">The duplex contract is defined as follows:</span></span>  
  
```  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples", SessionMode=SessionMode.Required,  
                 CallbackContract=typeof(ICalculatorDuplexCallback))]  
public interface ICalculatorDuplex  
{  
    [OperationContract(IsOneWay = true)]  
    void Clear();  
    [OperationContract(IsOneWay = true)]  
    void AddTo(double n);  
    [OperationContract(IsOneWay = true)]  
    void SubtractFrom(double n);  
    [OperationContract(IsOneWay = true)]  
    void MultiplyBy(double n);  
    [OperationContract(IsOneWay = true)]  
    void DivideBy(double n);  
}  
  
public interface ICalculatorDuplexCallback  
{  
    [OperationContract(IsOneWay = true)]  
    void Result(double result);  
    [OperationContract(IsOneWay = true)]  
    void Equation(string eqn);  
}  
```  
  
 <span data-ttu-id="b2cad-113">`CalculatorService` 類別會實作主要的 `ICalculatorDuplex` 介面。</span><span class="sxs-lookup"><span data-stu-id="b2cad-113">The `CalculatorService` class implements the primary `ICalculatorDuplex` interface.</span></span> <span data-ttu-id="b2cad-114">服務會使用 <xref:System.ServiceModel.InstanceContextMode.PerSession> 執行個體模式維持各工作階段的結果。</span><span class="sxs-lookup"><span data-stu-id="b2cad-114">The service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the result for each session.</span></span> <span data-ttu-id="b2cad-115">而名為 `Callback` 的私用屬性用於存取用戶端的回呼通道。</span><span class="sxs-lookup"><span data-stu-id="b2cad-115">A private property named `Callback` is used to access the callback channel to the client.</span></span> <span data-ttu-id="b2cad-116">服務會使用回呼，以透過回呼介面將訊息傳回用戶端。</span><span class="sxs-lookup"><span data-stu-id="b2cad-116">The service uses the callback for sending messages back to the client through the callback interface.</span></span>  
  
```  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]  
public class CalculatorService : ICalculatorDuplex  
{  
    double result = 0.0D;  
    string equation;  
  
    public CalculatorService()  
    {  
        equation = result.ToString();  
    }  
  
    public void Clear()  
    {  
        Callback.Equation(equation + " = " + result.ToString());  
        equation = result.ToString();  
    }  
  
    public void AddTo(double n)  
    {  
        result += n;  
        equation += " + " + n.ToString();  
        Callback.Result(result);  
    }  
    ...  
    ICalculatorDuplexCallback Callback  
    {  
        get  
        {  
            return OperationContext.Current.GetCallbackChannel<ICalculatorDuplexCallback>();  
        }  
    }  
}  
```  
  
 <span data-ttu-id="b2cad-117">用戶端必須提供實作雙工合約回呼介面的類別，用於接收來自服務的訊息。</span><span class="sxs-lookup"><span data-stu-id="b2cad-117">The client must provide a class that implements the callback interface of the duplex contract, for receiving messages from the service.</span></span> <span data-ttu-id="b2cad-118">在範例中，定義 `CallbackHandler` 類別以實作 `ICalculatorDuplexCallback` 介面。</span><span class="sxs-lookup"><span data-stu-id="b2cad-118">In the sample, a `CallbackHandler` class is defined to implement the `ICalculatorDuplexCallback` interface.</span></span>  
  
```  
public class CallbackHandler : ICalculatorDuplexCallback  
{  
   public void Result(double result)  
   {  
      Console.WriteLine("Result({0})", result);  
   }  
  
   public void Equation(string equation)  
   {  
      Console.WriteLine("Equation({0}", equation);  
   }  
}  
```  
  
 <span data-ttu-id="b2cad-119">針對雙工合約所產生的 Proxy，會要求在建構時提供 <xref:System.ServiceModel.InstanceContext>。</span><span class="sxs-lookup"><span data-stu-id="b2cad-119">The proxy that is generated for a duplex contract requires a <xref:System.ServiceModel.InstanceContext> to be provided upon construction.</span></span> <span data-ttu-id="b2cad-120">這個 <xref:System.ServiceModel.InstanceContext> 會用來做為站台，讓物件實作回呼介面並處理服務傳回的訊息。</span><span class="sxs-lookup"><span data-stu-id="b2cad-120">This <xref:System.ServiceModel.InstanceContext> is used as the site for an object that implements the callback interface and handles messages that are sent back from the service.</span></span> <span data-ttu-id="b2cad-121"><xref:System.ServiceModel.InstanceContext> 是以 `CallbackHandler` 類別的執行個體所建構。</span><span class="sxs-lookup"><span data-stu-id="b2cad-121">An <xref:System.ServiceModel.InstanceContext> is constructed with an instance of the `CallbackHandler` class.</span></span> <span data-ttu-id="b2cad-122">這個物件會處理回呼介面上，從服務傳回至用戶端的訊息。</span><span class="sxs-lookup"><span data-stu-id="b2cad-122">This object handles messages sent from the service to the client on the callback interface.</span></span>  
  
```  
// Construct InstanceContext to handle messages on callback interface.  
InstanceContext instanceContext = new InstanceContext(new CallbackHandler());  
  
// Create a client.  
CalculatorDuplexClient client = new CalculatorDuplexClient(instanceContext);  
  
Console.WriteLine("Press <ENTER> to terminate client once the output is displayed.");  
Console.WriteLine();  
  
// Call the AddTo service operation.  
double value = 100.00D;  
client.AddTo(value);  
  
// Call the SubtractFrom service operation.  
value = 50.00D;  
client.SubtractFrom(value);  
  
// Call the MultiplyBy service operation.  
value = 17.65D;  
client.MultiplyBy(value);  
  
// Call the DivideBy service operation.  
value = 2.00D;  
client.DivideBy(value);  
  
// Complete equation.  
client.Clear();  
  
Console.ReadLine();  
  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
```  
  
 <span data-ttu-id="b2cad-123">組態已經過修改，以提供同時支援工作階段通訊和雙工通訊的繫結。</span><span class="sxs-lookup"><span data-stu-id="b2cad-123">The configuration has been modified to provide a binding that supports both session communication and duplex communication.</span></span> <span data-ttu-id="b2cad-124">`wsDualHttpBinding` 支援工作階段通訊，並且藉由提供雙重 HTTP 連接 (一個方向一個連接) 允許雙工通訊。</span><span class="sxs-lookup"><span data-stu-id="b2cad-124">The `wsDualHttpBinding` supports session communication and allows duplex communication by providing dual HTTP connections, one for each direction.</span></span> <span data-ttu-id="b2cad-125">在服務上，組態中的唯一差異是所使用的繫結。</span><span class="sxs-lookup"><span data-stu-id="b2cad-125">On the service, the only difference in configuration is the binding that is used.</span></span> <span data-ttu-id="b2cad-126">在用戶端上，您必須設定伺服器可用來連接用戶端的位址，如下面的範例組態中所示。</span><span class="sxs-lookup"><span data-stu-id="b2cad-126">On the client, you must configure an address that the server can use to connect to the client as shown in the following sample configuration.</span></span>  
  
```xml  
<client>  
  <endpoint name=""  
            address="http://localhost/servicemodelsamples/service.svc"   
            binding="wsDualHttpBinding"   
            bindingConfiguration="DuplexBinding"   
            contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex" />  
</client>  
  
<bindings>  
  <!-- Configure a binding that support duplex communication. -->  
  <wsDualHttpBinding>  
    <binding name="DuplexBinding"   
             clientBaseAddress="http://localhost:8000/myClient/">  
    </binding>  
  </wsDualHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="b2cad-127">執行範例時，您會看到傳回用戶端的訊息，該用戶端位於從服務傳送出的回呼介面上。</span><span class="sxs-lookup"><span data-stu-id="b2cad-127">When you run the sample, you see the messages that are returned to the client on the callback interface that is sent from the service.</span></span> <span data-ttu-id="b2cad-128">顯示每個中繼結果，接著顯示在完成所有操作時的整個方程式。</span><span class="sxs-lookup"><span data-stu-id="b2cad-128">Each intermediate result is displayed, followed by the entire equation upon the completion of all operations.</span></span> <span data-ttu-id="b2cad-129">按 ENTER 鍵關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="b2cad-129">Press ENTER to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b2cad-130">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="b2cad-130">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="b2cad-131">請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="b2cad-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="b2cad-132">若要建置方案的 C#、 c + + 或 Visual BASIC.NET 版本，請依照中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="b2cad-132">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="b2cad-133">若要在單一或跨電腦組態中執行範例時，請依照中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="b2cad-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="b2cad-134">當用戶端執行跨電腦組態中時，請務必取代"localhost"，在這兩`address`屬性[端點](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017)項目和`clientBaseAddress`屬性[ \<繫結 >](../../../../docs/framework/misc/binding.md)元素[ \<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)適當電腦名稱，如下列所示的項目：</span><span class="sxs-lookup"><span data-stu-id="b2cad-134">When running the client in a cross-machine configuration, be sure to replace "localhost" in both the `address` attribute of the [endpoint](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) element and the `clientBaseAddress` attribute of the [\<binding>](../../../../docs/framework/misc/binding.md) element of the [\<wsDualHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md) element with the name of the appropriate machine, as shown in the following:</span></span>  
  
    ```xml  
    <client>  
    <endpoint name = ""  
    address="http://service_machine_name/servicemodelsamples/service.svc"  
    ... />  
    </client>  
    ...  
    <wsDualHttpBinding>  
    <binding name="DuplexBinding" clientBaseAddress="http://client_machine_name:8000/myClient/">  
    </binding>  
    </wsDualHttpBinding>  
    ```  
  
> [!IMPORTANT]
>  <span data-ttu-id="b2cad-135">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="b2cad-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b2cad-136">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="b2cad-136">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b2cad-137">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="b2cad-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b2cad-138">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="b2cad-138">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Duplex`  
  
## <a name="see-also"></a><span data-ttu-id="b2cad-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2cad-139">See Also</span></span>

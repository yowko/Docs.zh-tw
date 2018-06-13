---
title: 傳輸：自訂跨 UDP 異動範例
ms.date: 03/30/2017
ms.assetid: 6cebf975-41bd-443e-9540-fd2463c3eb23
ms.openlocfilehash: 911331d5f5120f33a6c442a1eb4b2be2c8269a0e
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33806142"
---
# <a name="transport-custom-transactions-over-udp-sample"></a><span data-ttu-id="84f5b-102">傳輸：自訂跨 UDP 異動範例</span><span class="sxs-lookup"><span data-stu-id="84f5b-102">Transport: Custom Transactions over UDP Sample</span></span>
<span data-ttu-id="84f5b-103">這個範例根據[傳輸： UDP](../../../../docs/framework/wcf/samples/transport-udp.md)範例 Windows Communication Foundation (WCF) 中[傳輸擴充性](../../../../docs/framework/wcf/samples/transport-extensibility.md)。</span><span class="sxs-lookup"><span data-stu-id="84f5b-103">This sample is based on the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample in the Windows Communication Foundation (WCF)[Transport Extensibility](../../../../docs/framework/wcf/samples/transport-extensibility.md).</span></span> <span data-ttu-id="84f5b-104">它會延伸 UDP 傳輸範例以支援自訂交易流程，並示範 <xref:System.ServiceModel.Channels.TransactionMessageProperty> 屬性的使用方式。</span><span class="sxs-lookup"><span data-stu-id="84f5b-104">It extends the UDP Transport sample to support custom transaction flow and demonstrates the use of the <xref:System.ServiceModel.Channels.TransactionMessageProperty> property.</span></span>  
  
## <a name="code-changes-in-the-udp-transport-sample"></a><span data-ttu-id="84f5b-105">變更 UDP 傳輸範例中的程式碼</span><span class="sxs-lookup"><span data-stu-id="84f5b-105">Code Changes in the UDP Transport Sample</span></span>  
 <span data-ttu-id="84f5b-106">為了示範交易流程，此範例變更了服務合約，讓 `ICalculatorContract` 可以要求 `CalculatorService.Add()` 的交易範圍。</span><span class="sxs-lookup"><span data-stu-id="84f5b-106">To demonstrate transaction flow, the sample changes the service contract for `ICalculatorContract` to require a transaction scope for `CalculatorService.Add()`.</span></span> <span data-ttu-id="84f5b-107">範例還另外將 `System.Guid` 參數新增至 `Add` 作業的合約。</span><span class="sxs-lookup"><span data-stu-id="84f5b-107">The sample also adds an extra `System.Guid` parameter to the contract of the `Add` operation.</span></span> <span data-ttu-id="84f5b-108">這個參數是用來將用戶端異動識別碼傳遞給服務。</span><span class="sxs-lookup"><span data-stu-id="84f5b-108">This parameter is used to pass the identifier of the client transaction to the service.</span></span>  
  
```  
class CalculatorService : IDatagramContract, ICalculatorContract  
{  
    [OperationBehavior(TransactionScopeRequired=true)]  
    public int Add(int x, int y, Guid clientTransactionId)  
    {  
        if(Transaction.Current.TransactionInformation.DistributedIdentifier == clientTransactionId)  
    {  
        Console.WriteLine("The client transaction has flowed to the service");  
    }  
    else  
    {  
     Console.WriteLine("The client transaction has NOT flowed to the service");  
    }  
  
    Console.WriteLine("   adding {0} + {1}", x, y);              
    return (x + y);  
    }  
  
    [...]  
}  
```  
  
 <span data-ttu-id="84f5b-109">[傳輸： UDP](../../../../docs/framework/wcf/samples/transport-udp.md)範例會使用 UDP 封包在用戶端與服務之間傳遞訊息。</span><span class="sxs-lookup"><span data-stu-id="84f5b-109">The [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample uses UDP packets to pass messages between a client and a service.</span></span> <span data-ttu-id="84f5b-110">[傳輸： 自訂傳輸範例](../../../../docs/framework/wcf/samples/transport-custom-transactions-over-udp-sample.md)使用相同的機制來傳輸訊息，但當流動異動，它會插入至 UDP 封包，以及編碼的訊息。</span><span class="sxs-lookup"><span data-stu-id="84f5b-110">The [Transport: Custom Transport Sample](../../../../docs/framework/wcf/samples/transport-custom-transactions-over-udp-sample.md) uses the same mechanism to transport messages, but when a transaction is flowed, it is inserted into the UDP packet along with the encoded message.</span></span>  
  
```  
byte[] txmsgBuffer =                TransactionMessageBuffer.WriteTransactionMessageBuffer(txPropToken, messageBuffer);  
  
int bytesSent = this.socket.SendTo(txmsgBuffer, 0, txmsgBuffer.Length, SocketFlags.None, this.remoteEndPoint);  
```  
  
 <span data-ttu-id="84f5b-111">`TransactionMessageBuffer.WriteTransactionMessageBuffer` 是 Helper 方法，其中包含的新功能可以將目前交易的傳播權杖與訊息實體 (Entity) 合併，再將它放在緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="84f5b-111">`TransactionMessageBuffer.WriteTransactionMessageBuffer` is a helper method that contains new functionality to merge the propagation token for the current transaction with the message entity and place it into a buffer.</span></span>  
  
 <span data-ttu-id="84f5b-112">自訂交易流程傳輸而言，用戶端的實作必須知道何種服務作業需要異動流程，並且將這項資訊傳遞至 WCF。</span><span class="sxs-lookup"><span data-stu-id="84f5b-112">For custom transaction flow transport, the client implementation must know what service operations require transaction flow and to pass this information to WCF.</span></span> <span data-ttu-id="84f5b-113">其中也必須有可以用來傳輸使用者異動至傳輸層的機制。</span><span class="sxs-lookup"><span data-stu-id="84f5b-113">There should also be a mechanism for transmitting the user transaction to the transport layer.</span></span> <span data-ttu-id="84f5b-114">這個範例會使用 「 WCF 訊息偵測器 」 來取得這項資訊。</span><span class="sxs-lookup"><span data-stu-id="84f5b-114">This sample uses "WCF message inspectors" to obtain this information.</span></span> <span data-ttu-id="84f5b-115">此處實作的用戶端訊息偵測器稱為 `TransactionFlowInspector`，它會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="84f5b-115">The client message inspector implemented here, which is called `TransactionFlowInspector`, performs the following tasks:</span></span>  
  
-   <span data-ttu-id="84f5b-116">判斷交易是否必須針對指定的訊息動作流動 (這會在 `IsTxFlowRequiredForThisOperation()` 中進行)。</span><span class="sxs-lookup"><span data-stu-id="84f5b-116">Determines whether a transaction must be flowed for a given message action (this takes place in `IsTxFlowRequiredForThisOperation()`).</span></span>  
  
-   <span data-ttu-id="84f5b-117">在需要流動交易時，使用 `TransactionFlowProperty` 將目前環境交易附加至訊息 (這會在 `BeforeSendRequest()` 中完成)。</span><span class="sxs-lookup"><span data-stu-id="84f5b-117">Attaches the current ambient transaction to the message using `TransactionFlowProperty`, if a transaction is required to be flowed (this is done in `BeforeSendRequest()`).</span></span>  
  
```  
public class TransactionFlowInspector : IClientMessageInspector  
{  
   void IClientMessageInspector.AfterReceiveReply(ref           System.ServiceModel.Channels.Message reply, object correlationState)  
  {  
  }  
  
   public object BeforeSendRequest(ref System.ServiceModel.Channels.Message request, System.ServiceModel.IClientChannel channel)  
   {  
       // obtain the tx propagation token  
       byte[] propToken = null;             
       if (Transaction.Current != null && IsTxFlowRequiredForThisOperation(request.Headers.Action))  
       {  
           try  
           {  
               propToken = TransactionInterop.GetTransmitterPropagationToken(Transaction.Current);  
           }  
           catch (TransactionException e)  
           {  
              throw new CommunicationException("TransactionInterop.GetTransmitterPropagationToken failed.", e);  
           }  
       }  
  
      // set the propToken on the message in a TransactionFlowProperty  
       TransactionFlowProperty.Set(propToken, request);  
  
       return null;              
    }  
  }  
  
  static bool IsTxFlowRequiredForThisOperation(String action)  
 {  
       // In general, this should contain logic to identify which operations (actions)      require transaction flow.  
      [...]  
 }  
}  
```  
  
 <span data-ttu-id="84f5b-118">`TransactionFlowInspector` 本身是使用自訂行為 (`TransactionFlowBehavior`) 傳遞給架構。</span><span class="sxs-lookup"><span data-stu-id="84f5b-118">The `TransactionFlowInspector` itself is passed to the framework using a custom behavior: the `TransactionFlowBehavior`.</span></span>  
  
```  
public class TransactionFlowBehavior : IEndpointBehavior  
{  
       public void AddBindingParameters(ServiceEndpoint endpoint,            System.ServiceModel.Channels.BindingParameterCollection bindingParameters)  
      {  
      }  
  
       public void ApplyClientBehavior(ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.ClientRuntime clientRuntime)  
      {  
            TransactionFlowInspector inspector = new TransactionFlowInspector();  
            clientRuntime.MessageInspectors.Add(inspector);  
      }  
  
      public void ApplyDispatchBehavior(ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.EndpointDispatcher endpointDispatcher)  
     {  
     }  
  
      public void Validate(ServiceEndpoint endpoint)  
      {  
      }  
}  
```  
  
 <span data-ttu-id="84f5b-119">備妥前述機制之後，使用者程式碼會在呼叫服務作業之前建立 `TransactionScope`。</span><span class="sxs-lookup"><span data-stu-id="84f5b-119">With the preceding mechanism in place, the user code creates a `TransactionScope` before calling the service operation.</span></span> <span data-ttu-id="84f5b-120">如果需要讓異動流動至服務作業，訊息偵測器可以確保異動傳遞給傳輸。</span><span class="sxs-lookup"><span data-stu-id="84f5b-120">The message inspector ensures that the transaction is passed to the transport in case it is required to be flowed to the service operation.</span></span>  
  
```  
CalculatorContractClient calculatorClient = new CalculatorContractClient("SampleProfileUdpBinding_ICalculatorContract");  
calculatorClient.Endpoint.Behaviors.Add(new TransactionFlowBehavior());               
  
try  
{  
       for (int i = 0; i < 5; ++i)  
      {  
              // call the 'Add' service operation under a transaction scope  
             using (TransactionScope ts = new TransactionScope())  
             {  
        [...]  
        Console.WriteLine(calculatorClient.Add(i, i * 2));  
         }  
      }               
       calculatorClient.Close();  
}  
catch (TimeoutException)  
{  
    calculatorClient.Abort();  
}  
catch (CommunicationException)  
{  
    calculatorClient.Abort();  
}  
catch (Exception)  
{  
    calculatorClient.Abort();  
    throw;  
}  
```  
  
 <span data-ttu-id="84f5b-121">從用戶端收到 UDP 封包時，服務會將它還原序列化，以擷取訊息及可能的異動。</span><span class="sxs-lookup"><span data-stu-id="84f5b-121">Upon receiving a UDP packet from the client, the service deserializes it to extract the message and possibly a transaction.</span></span>  
  
```  
count = listenSocket.EndReceiveFrom(result, ref dummy);  
  
// read the transaction and message                       TransactionMessageBuffer.ReadTransactionMessageBuffer(buffer, count, out transaction, out msg);  
```  
  
 <span data-ttu-id="84f5b-122">`TransactionMessageBuffer.ReadTransactionMessageBuffer()` 是 Helper 方法，它會反轉 `TransactionMessageBuffer.WriteTransactionMessageBuffer()` 所執行的序列化 (Serialization) 程序。</span><span class="sxs-lookup"><span data-stu-id="84f5b-122">`TransactionMessageBuffer.ReadTransactionMessageBuffer()` is the helper method that reverses the serialization process performed by `TransactionMessageBuffer.WriteTransactionMessageBuffer()`.</span></span>  
  
 <span data-ttu-id="84f5b-123">如果有交易流入，就會將它附加至 `TransactionMessageProperty` 中的訊息。</span><span class="sxs-lookup"><span data-stu-id="84f5b-123">If a transaction was flowed in, it is appended to the message in the `TransactionMessageProperty`.</span></span>  
  
```  
message = MessageEncoderFactory.Encoder.ReadMessage(msg, bufferManager);  
  
if (transaction != null)  
{  
       TransactionMessageProperty.Set(transaction, message);  
}  
```  
  
 <span data-ttu-id="84f5b-124">這可以確保發送器在分派階段收到交易，且在呼叫訊息所定址的服務作業時使用此交易。</span><span class="sxs-lookup"><span data-stu-id="84f5b-124">This ensures that the dispatcher picks up the transaction at dispatch time and uses it when calling the service operation addressed by the message.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="84f5b-125">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="84f5b-125">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="84f5b-126">若要建置此方案，請依照中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="84f5b-126">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="84f5b-127">目前的範例應類似於[傳輸： UDP](../../../../docs/framework/wcf/samples/transport-udp.md)範例。</span><span class="sxs-lookup"><span data-stu-id="84f5b-127">The current sample should be run similarly to the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span> <span data-ttu-id="84f5b-128">若要執行，請使用 UdpTestService.exe 啟動服務。</span><span class="sxs-lookup"><span data-stu-id="84f5b-128">To run it, start the service with UdpTestService.exe.</span></span> <span data-ttu-id="84f5b-129">如果您是執行 [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)]，則必須使用更高的權限來啟動服務。</span><span class="sxs-lookup"><span data-stu-id="84f5b-129">If you are running [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], you must start the service with elevated privileges.</span></span> <span data-ttu-id="84f5b-130">若要這樣做，請以滑鼠右鍵按一下 UdpTestService.exe 中的[!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)]按一下**系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="84f5b-130">To do so, right-click UdpTestService.exe in [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] and click **Run as administrator**.</span></span>  
  
3.  <span data-ttu-id="84f5b-131">此程序產生以下輸出。</span><span class="sxs-lookup"><span data-stu-id="84f5b-131">This produces the following output.</span></span>  
  
    ```  
    Testing Udp From Code.  
    Service is started from code...  
    Press <ENTER> to terminate the service and start service from config...  
    ```  
  
4.  <span data-ttu-id="84f5b-132">此時，您可以執行 UdpTestClient.exe 以啟動用戶端。</span><span class="sxs-lookup"><span data-stu-id="84f5b-132">At this time, you can start the client by running UdpTestClient.exe.</span></span> <span data-ttu-id="84f5b-133">用戶端所產生的輸出如下所示。</span><span class="sxs-lookup"><span data-stu-id="84f5b-133">The output produced by the client is as follows.</span></span>  
  
    ```  
    0  
    3  
    6  
    9  
    12  
    Press <ENTER> to complete test.  
    ```  
  
5.  <span data-ttu-id="84f5b-134">服務輸出如下。</span><span class="sxs-lookup"><span data-stu-id="84f5b-134">The service output is as follows.</span></span>  
  
    ```  
    Hello, world!  
    Hello, world!  
    Hello, world!  
    Hello, world!  
    Hello, world!  
    The client transaction has flowed to the service  
       adding 0 + 0  
    The client transaction has flowed to the service  
       adding 1 + 2  
    The client transaction has flowed to the service  
       adding 2 + 4  
    The client transaction has flowed to the service  
       adding 3 + 6  
    The client transaction has flowed to the service  
       adding 4 + 8  
    ```  
  
6.  <span data-ttu-id="84f5b-135">如果服務應用程式可以找到與用戶端傳送的交易識別碼 (在 `The client transaction has flowed to the service` 作業的 `clientTransactionId` 參數中傳送) 相符的服務交易識別碼，就會顯示`CalculatorService.Add()`訊息。</span><span class="sxs-lookup"><span data-stu-id="84f5b-135">The service application displays the message `The client transaction has flowed to the service` if it can match the transaction identifier sent by the client, in the `clientTransactionId` parameter of the `CalculatorService.Add()` operation, to the identifier of the service transaction.</span></span> <span data-ttu-id="84f5b-136">只有在用戶端異動已流至服務時，才能取得相符的異動識別項。</span><span class="sxs-lookup"><span data-stu-id="84f5b-136">A match is obtained only if the client transaction has flowed to the service.</span></span>  
  
7.  <span data-ttu-id="84f5b-137">若要使用組態來對已發行的端點執行用戶端應用程式，請在服務應用程式視窗上按下 ENTER，然後再執行測試用戶端一次。</span><span class="sxs-lookup"><span data-stu-id="84f5b-137">To run the client application against endpoints published using configuration, press ENTER on the service application window and then run the test client again.</span></span> <span data-ttu-id="84f5b-138">您應該會在服務上看見下列輸出。</span><span class="sxs-lookup"><span data-stu-id="84f5b-138">You should see the following output on the service.</span></span>  
  
    ```  
    Testing Udp From Config.  
    Service is started from config...  
    Press <ENTER> to terminate the service and exit...  
    ```  
  
8.  <span data-ttu-id="84f5b-139">現在，針對服務執行用戶端，就會產生跟前面相似的輸出。</span><span class="sxs-lookup"><span data-stu-id="84f5b-139">Running the client against the service now produces similar output as before.</span></span>  
  
9. <span data-ttu-id="84f5b-140">若要使用 Svcutil.exe 重新產生用戶端程式碼和組態，請啟動服務應用程式，然後從範例的根目錄執行下列 Svcutil.exe 命令。</span><span class="sxs-lookup"><span data-stu-id="84f5b-140">To regenerate the client code and configuration using Svcutil.exe, start the service application and then run the following Svcutil.exe command from the root directory of the sample.</span></span>  
  
    ```  
    svcutil http://localhost:8000/udpsample/ /reference:UdpTranport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
    ```  
  
10. <span data-ttu-id="84f5b-141">請注意，Svcutil.exe 不會為 `sampleProfileUdpBinding` 產生繫結延伸組態，您必須以手動方式新增。</span><span class="sxs-lookup"><span data-stu-id="84f5b-141">Note that Svcutil.exe does not generate the binding extension configuration for the `sampleProfileUdpBinding`; you must add it manually.</span></span>  
  
    ```xml  
    <configuration>  
        <system.serviceModel>      
            …  
            <extensions>  
                <!-- This was added manually because svcutil.exe does not add this extension to the file -->  
                <bindingExtensions>  
                    <add name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport" />  
                </bindingExtensions>  
            </extensions>  
        </system.serviceModel>  
    </configuration>  
    ```  
  
> [!IMPORTANT]
>  <span data-ttu-id="84f5b-142">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="84f5b-142">The samples may already be installed on your machine.</span></span> <span data-ttu-id="84f5b-143">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="84f5b-143">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="84f5b-144">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="84f5b-144">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="84f5b-145">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="84f5b-145">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transactions\TransactionMessagePropertyUDPTransport`  
  
## <a name="see-also"></a><span data-ttu-id="84f5b-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84f5b-146">See Also</span></span>  
 [<span data-ttu-id="84f5b-147">傳輸：UDP</span><span class="sxs-lookup"><span data-stu-id="84f5b-147">Transport: UDP</span></span>](../../../../docs/framework/wcf/samples/transport-udp.md)

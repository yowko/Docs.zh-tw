---
title: 自訂繫結傳輸和編碼
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c0b353d-79ee-4e61-b348-be49ad0e9a16
ms.openlocfilehash: ee15fd37390f8bf4ca3bc287f9a3dbd5f8ebd935
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2018
ms.locfileid: "44508630"
---
# <a name="custom-binding-transport-and-encoding"></a><span data-ttu-id="6f801-102">自訂繫結傳輸和編碼</span><span class="sxs-lookup"><span data-stu-id="6f801-102">Custom Binding Transport and Encoding</span></span>
<span data-ttu-id="6f801-103">自訂繫結由經過排序的獨立繫結項目清單所定義。</span><span class="sxs-lookup"><span data-stu-id="6f801-103">A custom binding is defined by an ordered list of discrete binding elements.</span></span> <span data-ttu-id="6f801-104">這個範例會示範如何使用各種傳輸與訊息編碼項目來設定自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="6f801-104">This sample demonstrates how to configure a custom binding with various transport and message encoding elements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6f801-105">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="6f801-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="6f801-106">此樣本根據[自我裝載](../../../../docs/framework/wcf/samples/self-host.md)，而且已設定三個端點，以支援 HTTP、 TCP 和 NamedPipe 傳輸自訂繫結的修改。</span><span class="sxs-lookup"><span data-stu-id="6f801-106">This sample is based on the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md), and has been modified to configure three endpoints to support HTTP, TCP, and NamedPipe transports with custom bindings.</span></span> <span data-ttu-id="6f801-107">用戶端組態已採用類似方式加以修改，因此用戶端程式碼已變更成與這三個端點中的每個端點進行通訊。</span><span class="sxs-lookup"><span data-stu-id="6f801-107">The client configuration was similarly modified, and the client code changed to communicate with each of the three endpoints.</span></span>  
  
 <span data-ttu-id="6f801-108">此範例會示範如何設定支援特定傳輸與訊息編碼的自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="6f801-108">The sample demonstrates a how to configure a custom binding that supports a particular transport and message encoding.</span></span> <span data-ttu-id="6f801-109">這是設定 `binding` 項目的傳輸與訊息編碼完成的。</span><span class="sxs-lookup"><span data-stu-id="6f801-109">This is accomplished by configuring a transport and a message encoding for the `binding` element.</span></span> <span data-ttu-id="6f801-110">繫結項目的順序很重要定義自訂繫結，因為每個都代表通道堆疊中的圖層 (請參閱[自訂繫結](../../../../docs/framework/wcf/extending/custom-bindings.md))。</span><span class="sxs-lookup"><span data-stu-id="6f801-110">The ordering of binding elements is important in defining a custom binding, because each represents a layer in the channel stack (see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span></span> <span data-ttu-id="6f801-111">這個範例會設定三個自訂繫結：使用文字編碼的 HTTP 傳輸、使用文字編碼的 TCP 傳輸，以及使用二進位編碼的 NamedPipe 傳輸。</span><span class="sxs-lookup"><span data-stu-id="6f801-111">This sample configures three custom bindings: an HTTP transport with text encoding, a TCP transport with text encoding, and a NamedPipe transport with a binary encoding.</span></span>  
  
 <span data-ttu-id="6f801-112">服務組態會定義如下所示的自訂繫結：</span><span class="sxs-lookup"><span data-stu-id="6f801-112">The service configuration defines the custom bindings as follows:</span></span>  
  
```xml  
<bindings>  
    <customBinding>  
        <binding name="HttpBinding" >  
            <textMessageEncoding   
                messageVersion="Soap12Addressing10"/>  
            <httpTransport />  
        </binding>  
        <binding name="TcpBinding" >  
            <textMessageEncoding />  
            <tcpTransport />  
        </binding>  
        <binding name="NamedPipeBinding" >  
            <binaryMessageEncoding />  
            <namedPipeTransport />  
        </binding>  
    </customBinding>  
</bindings>  
```  
  
 <span data-ttu-id="6f801-113">當您執行範例時，作業要求和回應都會顯示在服務與用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="6f801-113">When you run the sample, the operation requests and responses are displayed in both the service and client console window.</span></span> <span data-ttu-id="6f801-114">用戶端會與這三個端點個別進行通訊，步驟是先存取 HTTP，接著存取 TCP，最後再存取 NamedPipe。</span><span class="sxs-lookup"><span data-stu-id="6f801-114">The client communicates with each of the three endpoints, accessing first HTTP, then TCP, and finally NamedPipe.</span></span> <span data-ttu-id="6f801-115">在每個主控台視窗中按下 ENTER 鍵，即可關閉服務與用戶端。</span><span class="sxs-lookup"><span data-stu-id="6f801-115">Press ENTER in each console window to shut down the service and client.</span></span>  
  
 <span data-ttu-id="6f801-116">`namedPipeTransport` 繫結不支援電腦對電腦的作業。</span><span class="sxs-lookup"><span data-stu-id="6f801-116">The `namedPipeTransport` binding does not support machine-to-machine operations.</span></span> <span data-ttu-id="6f801-117">這個繫結只用於相同電腦上的通訊。</span><span class="sxs-lookup"><span data-stu-id="6f801-117">It is used only for communication on the same machine.</span></span> <span data-ttu-id="6f801-118">因此，如果是在跨電腦案例中執行此範例，請將用戶端程式碼檔中的下列程式碼行標記為註解：</span><span class="sxs-lookup"><span data-stu-id="6f801-118">Therefore, when running the sample in a cross-machine scenario, comment out the following lines in the client code file:</span></span>  
  
```csharp  
CalculatorClient client = new CalculatorClient("default");  
Console.WriteLine("Communicate with named pipe endpoint.");  
// Call operations.  
DoCalculations(client);  
//Closing the client gracefully closes the connection and cleans up resources  
client.Close();  
```  
  
```vb  
Dim client As New CalculatorClient("default")  
Console.WriteLine("Communicate with named pipe endpoint.")  
' call operations  
DoCalculations(client)  
'Closing the client gracefully closes the connection and cleans up resources  
client.Close()  
```  
  
> [!NOTE]
>  <span data-ttu-id="6f801-119">如果您使用 Svcutil.exe 重新產生這個範例的組態，請務必修改用戶端組態中的端點名稱，以符合用戶端程式碼。</span><span class="sxs-lookup"><span data-stu-id="6f801-119">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6f801-120">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="6f801-120">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="6f801-121">請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="6f801-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="6f801-122">若要建置方案的 C#、 c + + 或 Visual Basic.NET 版本，請依照下列中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="6f801-122">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="6f801-123">若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="6f801-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6f801-124">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="6f801-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6f801-125">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="6f801-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6f801-126">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="6f801-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6f801-127">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="6f801-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\Transport`  
  
## <a name="see-also"></a><span data-ttu-id="6f801-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f801-128">See Also</span></span>

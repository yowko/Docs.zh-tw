---
title: WS 雙重 Http
ms.date: 03/30/2017
ms.assetid: 9997eba5-29ec-48db-86f3-fa77b241fb1a
ms.openlocfilehash: 03cc5a2359c6430c04c6afb09f161b397fcb1afa
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038482"
---
# <a name="ws-dual-http"></a><span data-ttu-id="de208-102">WS 雙重 Http</span><span class="sxs-lookup"><span data-stu-id="de208-102">WS Dual Http</span></span>

<span data-ttu-id="de208-103">雙重 Http 範例會示範如何設定 `WSDualHttpBinding` 繫結。</span><span class="sxs-lookup"><span data-stu-id="de208-103">The Dual Http sample demonstrates how to configure the `WSDualHttpBinding` binding.</span></span> <span data-ttu-id="de208-104">這個範例是由用戶端主控台程式 (.exe) 和網際網路資訊服務 (IIS) 所裝載的服務程式庫 (.dll) 所組成。</span><span class="sxs-lookup"><span data-stu-id="de208-104">This sample consists of a client console program (.exe) and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="de208-105">服務會實作雙工合約。</span><span class="sxs-lookup"><span data-stu-id="de208-105">The service implements a duplex contract.</span></span> <span data-ttu-id="de208-106">合約是由 `ICalculatorDuplex` 介面所定義，這個介面會公開數學運算作業 (加、減、乘、除)。</span><span class="sxs-lookup"><span data-stu-id="de208-106">The contract is defined by the `ICalculatorDuplex` interface, which exposes math operations (Add, Subtract, Multiply, and Divide).</span></span> <span data-ttu-id="de208-107">在此範例中，`ICalculatorDuplex` 介面允許用戶端執行數學運算，計算整個工作階段的執行結果。</span><span class="sxs-lookup"><span data-stu-id="de208-107">In this sample, the `ICalculatorDuplex` interface allows the client to perform math operations, calculating a running result over the session.</span></span> <span data-ttu-id="de208-108">服務會獨立地傳回 `ICalculatorDuplexCallback` 介面上的結果。</span><span class="sxs-lookup"><span data-stu-id="de208-108">Independently, the service returns results on the `ICalculatorDuplexCallback` interface.</span></span> <span data-ttu-id="de208-109">雙工合約需要一個工作階段，因為必須建立內容，將用戶端與服務之間傳送的訊息關聯在一起。</span><span class="sxs-lookup"><span data-stu-id="de208-109">A duplex contract requires a session, because a context must be established to correlate the set of messages being sent between client and service.</span></span> <span data-ttu-id="de208-110">`WSDualHttpBinding` 繫結支援雙工通訊。</span><span class="sxs-lookup"><span data-stu-id="de208-110">The `WSDualHttpBinding` binding supports duplex communication.</span></span>

> [!NOTE]
> <span data-ttu-id="de208-111">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="de208-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="de208-112">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="de208-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="de208-113">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="de208-113">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="de208-114">如果此目錄不存在, 請移至[.NET Framework 4 的 Windows Communication Foundation (wcf) 和 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780), 以下載所有 Windows Communication Foundation (wcf) [!INCLUDE[wf1](../../../../includes/wf1-md.md)]和範例。</span><span class="sxs-lookup"><span data-stu-id="de208-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="de208-115">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="de208-115">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\DualHttp`

<span data-ttu-id="de208-116">若要設定使用 `WSDualHttpBinding` 的服務端點，請在端點組態中指定此繫結，如下所示。</span><span class="sxs-lookup"><span data-stu-id="de208-116">To configure a service endpoint with the `WSDualHttpBinding`, specify the binding in the endpoint configuration as shown.</span></span>

```xml
<endpoint address=""
         binding="wsDualHttpBinding"
         contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex" />
```

<span data-ttu-id="de208-117">在用戶端上，您必須設定伺服器可用來連接用戶端的位址，如下面的範例組態中所示。</span><span class="sxs-lookup"><span data-stu-id="de208-117">On the client, you must configure an address that the server can use to connect to the client as shown in the following sample configuration.</span></span>

```xml
<system.serviceModel>
  <client>
    <endpoint address=
         "http://localhost/servicemodelsamples/service.svc"
         binding="wsDualHttpBinding"
         bindingConfiguration="Binding1"
         contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex" />
  </client>

  <bindings>
    <!-- Configure a WSDualHttpBinding that supports duplex -->
    <!-- communication. -->
    <wsDualHttpBinding>
      <binding name="Binding1"
               clientBaseAddress="http://localhost:8000/myClient/"
               useDefaultWebProxy="true"
               bypassProxyOnLocal="false">
      </binding>
    </wsDualHttpBinding>
  </bindings>
</system.serviceModel>
```

<span data-ttu-id="de208-118">當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="de208-118">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="de208-119">在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="de208-119">Press ENTER in the client window to shut down the client.</span></span>

```
Press <ENTER> to terminate client once the output is displayed.

Result(100)
Result(50)
Result(882.5)
Result(441.25)
Equation(0 + 100 - 50 * 17.65 / 2 = 441.25)
```

<span data-ttu-id="de208-120">當執行範例時，您會看到訊息在回呼服務所傳送的介面時傳回到用戶端。</span><span class="sxs-lookup"><span data-stu-id="de208-120">When you run the sample, you see the messages returned to the client on the callback interface sent from the service.</span></span> <span data-ttu-id="de208-121">完成所有作業時，每個中繼結果都會顯示，並接著顯示整個方程式。</span><span class="sxs-lookup"><span data-stu-id="de208-121">Each intermediate result is displayed, followed by the entire equation upon completion of all operations.</span></span> <span data-ttu-id="de208-122">按 ENTER 鍵關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="de208-122">Press ENTER to shut down the client.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="de208-123">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="de208-123">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="de208-124">使用下列命令安裝 ASP.NET 4.0。</span><span class="sxs-lookup"><span data-stu-id="de208-124">Install ASP.NET 4.0 using the following command.</span></span>

    ```
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="de208-125">請確定您已[針對 Windows Communication Foundation 範例執行一次安裝程式](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="de208-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="de208-126">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="de208-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="de208-127">若要在單一或跨電腦設定中執行範例, 請遵循執行[Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="de208-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="de208-128">在跨電腦設定中執行用戶端時, 請務必在[ \< \<用戶端 >](../../configure-apps/file-schema/wcf/endpoint-of-client.md)專案的端點`address` > 屬性和`clientBaseAddress`的屬性 (attribute [ )中取代localhost。使用\<](../../../../docs/framework/misc/binding.md)適當電腦的名稱系結[ \<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)專案的 > 元素, 如下所示:</span><span class="sxs-lookup"><span data-stu-id="de208-128">When running the client in a cross-machine configuration, be sure to replace localhost in both the `address` attribute of the [\<endpoint> of \<client>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) element and the `clientBaseAddress` attribute of the [\<binding>](../../../../docs/framework/misc/binding.md) element of the [\<wsDualHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md) element with the name of the appropriate machine, as shown:</span></span>

    ```xml
    <client>
        <endpoint name = ""
          address=
         "http://service_machine_name/servicemodelsamples/service.svc"
        />
    </client>
    ...
    <wsDualHttpBinding>
        <binding name="DuplexBinding" clientBaseAddress=
            "http://client_machine_name:8000/myClient/">
        </binding>
    </wsDualHttpBinding>
    ```

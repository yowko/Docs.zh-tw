---
title: WSHttpBinding
ms.date: 03/30/2017
helpviewer_keywords:
- WS Profile binding
ms.assetid: 22d85b19-0135-4141-9179-a0e9c343ad73
ms.openlocfilehash: 6eccaaaa3ad941b16690afeecef618cdfb9040a1
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43512027"
---
# <a name="wshttpbinding"></a><span data-ttu-id="dee3a-102">WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="dee3a-102">WSHttpBinding</span></span>
<span data-ttu-id="dee3a-103">此範例示範如何實作一般服務與一般用戶端使用 Windows Communication Foundation (WCF)。</span><span class="sxs-lookup"><span data-stu-id="dee3a-103">This sample demonstrates how to implement a typical service and a typical client using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="dee3a-104">這個範例是由用戶端主控台程式 (client.exe) 和網際網路資訊服務 (IIS) 所裝載的服務程式庫所組成。</span><span class="sxs-lookup"><span data-stu-id="dee3a-104">This sample consists of a client console program (client.exe) and a service library hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="dee3a-105">服務會實作定義要求-回覆通訊模式的合約。</span><span class="sxs-lookup"><span data-stu-id="dee3a-105">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="dee3a-106">合約是由 `ICalculator` 介面所定義，這個介面會公開數學運算作業 (加、減、乘、除)。</span><span class="sxs-lookup"><span data-stu-id="dee3a-106">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="dee3a-107">用戶端會對指定的數學運算作業提出同步要求，服務則會以結果回覆。</span><span class="sxs-lookup"><span data-stu-id="dee3a-107">The client makes synchronous requests to a given math operation and the service replies with the result.</span></span> <span data-ttu-id="dee3a-108">您可以在主控台視窗中看到用戶端活動。</span><span class="sxs-lookup"><span data-stu-id="dee3a-108">Client activity is visible in the console window.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="dee3a-109">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="dee3a-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="dee3a-110">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="dee3a-110">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="dee3a-111">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="dee3a-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="dee3a-112">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="dee3a-112">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsHttp`  
  
> [!NOTE]
>  <span data-ttu-id="dee3a-113">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="dee3a-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="dee3a-114">此範例會公開`ICalculator`合約使用[ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="dee3a-114">This sample exposes the `ICalculator` contract using the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="dee3a-115">這個繫結的組態已展開於 Web.config 檔中。</span><span class="sxs-lookup"><span data-stu-id="dee3a-115">The configuration of this binding has been expanded in the Web.config file.</span></span>  
  
```xml
<bindings>  
  <wsHttpBinding>  
    <!--The following is the expanded configuration section for a-->  
    <!--WSHttpBinding. Each property is configured with the default-->   
    <!--value. See the ReliableSession, TransactionFlow, -->  
    <!--TransportSecurity, and MessageSecurity samples in the WS -->  
    <!--directory to learn how to configure these features. -->  
    <binding name="Binding1"  
              bypassProxyOnLocal="false"   
              transactionFlow="false"   
              hostNameComparisonMode="StrongWildcard"  
              maxBufferPoolSize="524288"   
              maxReceivedMessageSize="65536"  
              messageEncoding="Text"   
              textEncoding="utf-8"   
              useDefaultWebProxy="true"  
              allowCookies="false">  
      <reliableSession ordered="true"   
                       inactivityTimeout="00:10:00"  
                       enabled="false" />  
      <security mode="Message">  
        <message clientCredentialType="Windows"   
                 negotiateServiceCredential="true"  
                 algorithmSuite="Default"   
                 establishSecurityContext="true" />  
      </security>  
    </binding>  
  </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="dee3a-116">在基底 `binding` 項目上，`maxReceivedMessageSize` 值可以讓您設定傳入訊息的大小上限 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="dee3a-116">On the base `binding` element, the `maxReceivedMessageSize` value lets you configure the maximum size of an incoming message (in bytes).</span></span> <span data-ttu-id="dee3a-117">`hostNameComparisonMode` 值可以讓您設定當分離訊息信號至服務時，是否要考量主機名稱。</span><span class="sxs-lookup"><span data-stu-id="dee3a-117">The `hostNameComparisonMode` value lets you configure whether the hostname is considered when de-multiplexing messages to the service.</span></span> <span data-ttu-id="dee3a-118">`messageEncoding` 值可以讓您設定訊息是要使用 Text 編碼或 MTOM 編碼。</span><span class="sxs-lookup"><span data-stu-id="dee3a-118">The `messageEncoding` value lets you configure whether to use Text or MTOM encoding for messages.</span></span> <span data-ttu-id="dee3a-119">`textEncoding` 值可以讓您設定訊息的字元編碼。</span><span class="sxs-lookup"><span data-stu-id="dee3a-119">The `textEncoding` value lets you configure the character encoding for messages.</span></span> <span data-ttu-id="dee3a-120">`bypassProxyOnLocal` 值可以讓您設定本機通訊是否要使用 HTTP Proxy。</span><span class="sxs-lookup"><span data-stu-id="dee3a-120">The `bypassProxyOnLocal` value lets you configure whether to use an HTTP proxy for local communication.</span></span> <span data-ttu-id="dee3a-121">`transactionFlow` 值會設定是否流動目前的交易 (如果作業已設定為交易流程)。</span><span class="sxs-lookup"><span data-stu-id="dee3a-121">The `transactionFlow` value configures whether the current transaction is flowed (if an operation is configured for transaction flow).</span></span>  
  
 <span data-ttu-id="dee3a-122">在  [ \<reliableSession >](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md)項目，啟用的布林值會設定是否啟用可靠工作階段。</span><span class="sxs-lookup"><span data-stu-id="dee3a-122">On the [\<reliableSession>](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) element, the enabled Boolean value configures whether reliable sessions are enabled.</span></span> <span data-ttu-id="dee3a-123">`ordered` 值會設定是否保留訊息順序。</span><span class="sxs-lookup"><span data-stu-id="dee3a-123">The `ordered` value configures whether message ordering is preserved.</span></span> <span data-ttu-id="dee3a-124">`inactivityTimeout` 值會設定工作階段在發生錯誤前能夠閒置的時間長度。</span><span class="sxs-lookup"><span data-stu-id="dee3a-124">The `inactivityTimeout` value configures how long a session can be idle before being faulted.</span></span>  
  
 <span data-ttu-id="dee3a-125">在  [\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)，則`mode`值會設定應該使用哪一種安全性模式。</span><span class="sxs-lookup"><span data-stu-id="dee3a-125">On the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md), the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="dee3a-126">在此範例中，使用訊息安全性時，這就是為什麼[\<訊息 >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md)內部指定[\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="dee3a-126">In this sample, messages security is being used, which is why the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) is specified inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="dee3a-127">當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="dee3a-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="dee3a-128">在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="dee3a-128">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="dee3a-129">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="dee3a-129">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="dee3a-130">使用下列命令安裝 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0。</span><span class="sxs-lookup"><span data-stu-id="dee3a-130">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="dee3a-131">請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="dee3a-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="dee3a-132">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="dee3a-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="dee3a-133">若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="dee3a-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dee3a-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dee3a-134">See Also</span></span>

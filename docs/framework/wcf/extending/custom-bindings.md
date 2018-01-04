---
title: "自訂繫結"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, endpoints
- Windows Communication Foundation, configuration
ms.assetid: 58532b6d-4eea-4a4f-854f-a1c8c842564d
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d51e6e5b72deea417b7313d88a4d58610b401244
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="custom-bindings"></a><span data-ttu-id="59a5d-102">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="59a5d-102">Custom Bindings</span></span>
<span data-ttu-id="59a5d-103">當系統提供的其中一個繫結不符合服務的需求時，您可以使用 <xref:System.ServiceModel.Channels.CustomBinding> 類別。</span><span class="sxs-lookup"><span data-stu-id="59a5d-103">You can use the <xref:System.ServiceModel.Channels.CustomBinding> class when one of the system-provided bindings does not meet the requirements of your service.</span></span> <span data-ttu-id="59a5d-104">所有繫結都是根據已排序的繫結項目組所建構。</span><span class="sxs-lookup"><span data-stu-id="59a5d-104">All bindings are constructed from an ordered set of binding elements.</span></span> <span data-ttu-id="59a5d-105">自訂的繫結可以從系統提供的繫結項目建置，或是可以包含使用者定義的自訂繫結項目。</span><span class="sxs-lookup"><span data-stu-id="59a5d-105">Custom bindings can be built from a set of system-provided binding elements or can include user-defined custom binding elements.</span></span> <span data-ttu-id="59a5d-106">例如，您可以使用自訂繫結項目，以便在服務端點使用新的傳輸或編碼器。</span><span class="sxs-lookup"><span data-stu-id="59a5d-106">You can use custom binding elements, for example, to enable the use of new transports or encoders at a service endpoint.</span></span> <span data-ttu-id="59a5d-107">如需實用範例，請參閱[自訂繫結範例](http://msdn.microsoft.com/en-us/657e8143-beb0-472d-9cfe-ed1a19c2ab08)。</span><span class="sxs-lookup"><span data-stu-id="59a5d-107">For working examples, see [Custom Binding Samples](http://msdn.microsoft.com/en-us/657e8143-beb0-472d-9cfe-ed1a19c2ab08).</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="59a5d-108">[ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)。</span><span class="sxs-lookup"><span data-stu-id="59a5d-108"> [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
## <a name="construction-of-a-custom-binding"></a><span data-ttu-id="59a5d-109">建構自訂繫結</span><span class="sxs-lookup"><span data-stu-id="59a5d-109">Construction of a Custom Binding</span></span>  
 <span data-ttu-id="59a5d-110">在建構自訂繫結時，會使用依特定順序堆疊的繫結項目集合中的 <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> 建構函式：</span><span class="sxs-lookup"><span data-stu-id="59a5d-110">A custom binding is constructed using the <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> constructor from a collection of binding elements that are "stacked" in a specific order:</span></span>  
  
-   <span data-ttu-id="59a5d-111">在最上方為允許流動交易的選擇性 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> 類別。</span><span class="sxs-lookup"><span data-stu-id="59a5d-111">At the top is an optional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> class that allows flowing transactions.</span></span>  
  
-   <span data-ttu-id="59a5d-112">接下來是選擇性 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> 類別，它會提供 WS-ReliableMessaging 規格中所定義的工作階段和排序機制。</span><span class="sxs-lookup"><span data-stu-id="59a5d-112">Next is an optional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> class that provides a session and ordering mechanisms as defined in the WS-ReliableMessaging specification.</span></span> <span data-ttu-id="59a5d-113">工作階段可以跨 SOAP 和傳輸媒介。</span><span class="sxs-lookup"><span data-stu-id="59a5d-113">A session can cross SOAP and transport intermediaries.</span></span>  
  
-   <span data-ttu-id="59a5d-114">下一個是選擇性的 <xref:System.ServiceModel.Channels.SecurityBindingElement> 類別，它會提供如授權、驗證、保護和機密性等安全性功能。</span><span class="sxs-lookup"><span data-stu-id="59a5d-114">Next is an optional <xref:System.ServiceModel.Channels.SecurityBindingElement> class that provides security features such as authorization, authentication, protection, and confidentiality.</span></span>  
  
-   <span data-ttu-id="59a5d-115">下一個是選擇性的 <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> 類別，它可以與傳輸通訊協定進行雙向的雙工通訊，HTTP 之類的通訊協定原本並不支援雙工通訊。</span><span class="sxs-lookup"><span data-stu-id="59a5d-115">Next is an optional <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> class that provides the ability to have two way duplex communication with a transport protocol that does not support duplex communication natively, such as HTTP.</span></span>  
  
-   <span data-ttu-id="59a5d-116">下一個是選擇性的 <xref:System.ServiceModel.Channels.OneWayBindingElement> 類別，它提供單向通訊。</span><span class="sxs-lookup"><span data-stu-id="59a5d-116">Next is an optional <xref:System.ServiceModel.Channels.OneWayBindingElement>) class that provides one-way communication.</span></span>  
  
-   <span data-ttu-id="59a5d-117">下一個是選擇性的資料流安全性繫結項目，這個項目可以是下列其中一種。</span><span class="sxs-lookup"><span data-stu-id="59a5d-117">Next is an optional stream security binding element which can be one of the following.</span></span>  
  
    -   <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
-   <span data-ttu-id="59a5d-118">再來是必要的訊息編碼繫結項目。</span><span class="sxs-lookup"><span data-stu-id="59a5d-118">Next is a required message encoding binding element.</span></span> <span data-ttu-id="59a5d-119">您可以使用自己的訊息編碼器，或是三個訊息編碼繫結的其中一個：</span><span class="sxs-lookup"><span data-stu-id="59a5d-119">You can use your own message encoder or one of the three message encoding bindings:</span></span>  
  
    -   <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>  
  
 <span data-ttu-id="59a5d-120">最下方是必要的傳輸項目。</span><span class="sxs-lookup"><span data-stu-id="59a5d-120">At the bottom is a required transport element.</span></span> <span data-ttu-id="59a5d-121">您可以使用自己的傳輸，或是下列其中一個 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 提供的傳輸繫結項目：</span><span class="sxs-lookup"><span data-stu-id="59a5d-121">You can use your own transport or one of the following transport binding elements [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] provides:</span></span>  
  
-   <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.PeerTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>  
  
-   <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>  
  
-   <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
 <span data-ttu-id="59a5d-122">下表摘要列出每一層的選項。</span><span class="sxs-lookup"><span data-stu-id="59a5d-122">The following table summarizes the options for each layer.</span></span>  
  
|<span data-ttu-id="59a5d-123">圖層</span><span class="sxs-lookup"><span data-stu-id="59a5d-123">Layer</span></span>|<span data-ttu-id="59a5d-124">選項</span><span class="sxs-lookup"><span data-stu-id="59a5d-124">Options</span></span>|<span data-ttu-id="59a5d-125">必要</span><span class="sxs-lookup"><span data-stu-id="59a5d-125">Required</span></span>|  
|-----------|-------------|--------------|  
|<span data-ttu-id="59a5d-126">異動</span><span class="sxs-lookup"><span data-stu-id="59a5d-126">Transactions</span></span>|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|<span data-ttu-id="59a5d-127">否</span><span class="sxs-lookup"><span data-stu-id="59a5d-127">No</span></span>|  
|<span data-ttu-id="59a5d-128">可靠性</span><span class="sxs-lookup"><span data-stu-id="59a5d-128">Reliability</span></span>|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|<span data-ttu-id="59a5d-129">否</span><span class="sxs-lookup"><span data-stu-id="59a5d-129">No</span></span>|  
|<span data-ttu-id="59a5d-130">安全性</span><span class="sxs-lookup"><span data-stu-id="59a5d-130">Security</span></span>|<xref:System.ServiceModel.Channels.SecurityBindingElement>|<span data-ttu-id="59a5d-131">否</span><span class="sxs-lookup"><span data-stu-id="59a5d-131">No</span></span>|  
|<span data-ttu-id="59a5d-132">編碼</span><span class="sxs-lookup"><span data-stu-id="59a5d-132">Encoding</span></span>|<span data-ttu-id="59a5d-133">文字、二進位、訊息傳輸最佳化機制 (MTOM)、自訂</span><span class="sxs-lookup"><span data-stu-id="59a5d-133">Text, binary, Message Transmission Optimization Mechanism (MTOM), custom</span></span>|<span data-ttu-id="59a5d-134">[是]</span><span class="sxs-lookup"><span data-stu-id="59a5d-134">Yes</span></span>|  
|<span data-ttu-id="59a5d-135">Transport</span><span class="sxs-lookup"><span data-stu-id="59a5d-135">Transport</span></span>|<span data-ttu-id="59a5d-136">TCP、HTTP、HTTPS、具名管道 (也稱為 IPC)、對等式 (P2P)、訊息佇列 (也稱為 MSMQ)、自訂</span><span class="sxs-lookup"><span data-stu-id="59a5d-136">TCP, HTTP, HTTPS, named pipes (also known as IPC), Peer-to-Peer (P2P), Message Queuing (also known as MSMQ), Custom</span></span>|<span data-ttu-id="59a5d-137">[是]</span><span class="sxs-lookup"><span data-stu-id="59a5d-137">Yes</span></span>|  
  
 <span data-ttu-id="59a5d-138">此外，您也可以定義自己的繫結項目，並將其插入上述任何定義層之間。</span><span class="sxs-lookup"><span data-stu-id="59a5d-138">In addition, you can define your own binding elements and insert them between any of the preceding defined layers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59a5d-139">請參閱</span><span class="sxs-lookup"><span data-stu-id="59a5d-139">See Also</span></span>  
 [<span data-ttu-id="59a5d-140">建立端點概觀</span><span class="sxs-lookup"><span data-stu-id="59a5d-140">Endpoint Creation Overview</span></span>](../../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [<span data-ttu-id="59a5d-141">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="59a5d-141">Using Bindings to Configure Services and Clients</span></span>](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="59a5d-142">系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="59a5d-142">System-Provided Bindings</span></span>](../../../../docs/framework/wcf/system-provided-bindings.md)  
 [<span data-ttu-id="59a5d-143">如何：自訂系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="59a5d-143">How to: Customize a System-Provided Binding</span></span>](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)  
 [<span data-ttu-id="59a5d-144">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="59a5d-144">\<customBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="59a5d-145">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="59a5d-145">Custom Binding</span></span>](../../../../docs/framework/wcf/samples/custom-binding.md)

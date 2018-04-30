---
title: 使用繫結來設定服務和用戶端
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- bindings [WCF], using
ms.assetid: c39479c3-0766-4a17-ba4c-97a74607f392
caps.latest.revision: 33
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 68c8c2c93ce29147247c332848025fd931bf7854
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2018
---
# <a name="using-bindings-to-configure-services-and-clients"></a><span data-ttu-id="e47f6-102">使用繫結來設定服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="e47f6-102">Using Bindings to Configure Services and Clients</span></span>
<span data-ttu-id="e47f6-103">繫結是指定連接端點所需要之通訊詳細資料的物件。</span><span class="sxs-lookup"><span data-stu-id="e47f6-103">Bindings are objects that specify the communication details required to connect to an endpoint.</span></span> <span data-ttu-id="e47f6-104">更明確的說，繫結包含藉由定義傳輸、網路格式 (訊息編碼) 的細節，用於建立用戶端或服務執行階段的組態資訊，以及用於個別端點或用戶端通道的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="e47f6-104">More specifically, bindings contain configuration information that is used to create the client or service runtime by defining the specifics of transports, wire-formats (message encoding), and protocols to use for the respective endpoint or client channel.</span></span> <span data-ttu-id="e47f6-105">如果要建立可以運作的 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 服務，服務中每個端點都需要繫結。</span><span class="sxs-lookup"><span data-stu-id="e47f6-105">To create a functioning [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service, each endpoint in the service requires a binding.</span></span> <span data-ttu-id="e47f6-106">本主題將說明什麼是繫結、如何定義繫結，以及如何為端點指定特定繫結。</span><span class="sxs-lookup"><span data-stu-id="e47f6-106">This topic explains what bindings are, how they are defined, and how a particular binding is specified for an endpoint.</span></span>  
  
## <a name="what-a-binding-defines"></a><span data-ttu-id="e47f6-107">繫結所定義的內容</span><span class="sxs-lookup"><span data-stu-id="e47f6-107">What a Binding Defines</span></span>  
 <span data-ttu-id="e47f6-108">繫結中的資訊可能很基本，也可能很複雜。</span><span class="sxs-lookup"><span data-stu-id="e47f6-108">The information in a binding can be very basic or very complex.</span></span> <span data-ttu-id="e47f6-109">最基本的繫結只會指定連線至端點時必須使用的傳輸通訊協定 (例如 HTTP)。</span><span class="sxs-lookup"><span data-stu-id="e47f6-109">The most basic binding specifies only the transport protocol (such as HTTP) that must be used to connect to the endpoint.</span></span> <span data-ttu-id="e47f6-110">說的更簡單一點，繫結中所含有關如何連線至端點的資訊，屬於下表其中一種類別。</span><span class="sxs-lookup"><span data-stu-id="e47f6-110">More generally, the information a binding contains about how to connect to an endpoint falls into one of the categories in the following table.</span></span>  
  
 <span data-ttu-id="e47f6-111">通訊協定</span><span class="sxs-lookup"><span data-stu-id="e47f6-111">Protocols</span></span>  
 <span data-ttu-id="e47f6-112">判斷使用的安全性機制，是可靠的傳訊能力或交易內容流量設定。</span><span class="sxs-lookup"><span data-stu-id="e47f6-112">Determines the security mechanism being used, either reliable messaging capability or transaction context flow settings.</span></span>  
  
 <span data-ttu-id="e47f6-113">Transport</span><span class="sxs-lookup"><span data-stu-id="e47f6-113">Transport</span></span>  
 <span data-ttu-id="e47f6-114">判斷要使用的基礎傳輸通訊協定 (例如，TCP 或 HTTP)。</span><span class="sxs-lookup"><span data-stu-id="e47f6-114">Determines the underlying transport protocol to use (for example, TCP or HTTP).</span></span>  
  
 <span data-ttu-id="e47f6-115">編碼</span><span class="sxs-lookup"><span data-stu-id="e47f6-115">Encoding</span></span>  
 <span data-ttu-id="e47f6-116">判斷訊息編碼，例如 text/XML、二進位或 Message Transmission Optimization Mechanism (MTOM)，它會決定在網路上如何將訊息表示為位元組資料流。</span><span class="sxs-lookup"><span data-stu-id="e47f6-116">Determines the message encoding, for example, text/XML, binary, or Message Transmission Optimization Mechanism (MTOM), which determines how messages are represented as byte streams on the wire.</span></span>  
  
## <a name="system-provided-bindings"></a><span data-ttu-id="e47f6-117">系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="e47f6-117">System-Provided Bindings</span></span>  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="e47f6-118"> 包括一組系統提供的繫結，設計來涵蓋大部分的應用程式需求和案例。</span><span class="sxs-lookup"><span data-stu-id="e47f6-118"> includes a set of system-provided bindings that are designed to cover most application requirements and scenarios.</span></span> <span data-ttu-id="e47f6-119">下列類別則表示系統提供之繫結的一些範例：</span><span class="sxs-lookup"><span data-stu-id="e47f6-119">The following classes represent some examples of system-provided bindings:</span></span>  
  
-   <span data-ttu-id="e47f6-120"><xref:System.ServiceModel.BasicHttpBinding>：一種 HTTP 通訊協定繫結，適用於連線至 Web 服務，並符合 WS-I Basic Profile 1.1 規格 (例如，以 ASP.NET Web 服務 [ASMX] 為基礎的服務)。</span><span class="sxs-lookup"><span data-stu-id="e47f6-120"><xref:System.ServiceModel.BasicHttpBinding>: An HTTP protocol binding suitable for connecting to Web services that conforms to the WS-I Basic Profile 1.1 specification (for example, ASP.NET Web services [ASMX]-based services).</span></span>  
  
-   <span data-ttu-id="e47f6-121"><xref:System.ServiceModel.WSHttpBinding>：一種 HTTP 通訊協定繫結，適用於連線至符合 Web 服務規格通訊協定的端點。</span><span class="sxs-lookup"><span data-stu-id="e47f6-121"><xref:System.ServiceModel.WSHttpBinding>: An HTTP protocol binding suitable for connecting to endpoints that conform to the Web services specifications protocols.</span></span>  
  
-   <span data-ttu-id="e47f6-122"><xref:System.ServiceModel.NetNamedPipeBinding>：使用 .NET 二進位編碼和框架技術搭配 Windows 具名管道傳輸以連線至相同電腦上的其他 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 端點。</span><span class="sxs-lookup"><span data-stu-id="e47f6-122"><xref:System.ServiceModel.NetNamedPipeBinding>: Uses the .NET binary encoding and framing technologies in conjunction with the Windows named pipe transport to connect to other [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] endpoints on the same machine.</span></span>  
  
-   <span data-ttu-id="e47f6-123"><xref:System.ServiceModel.NetMsmqBinding>：使用 .NET 二進位編碼和框架技術搭配訊息佇列 (亦稱為 MSMQ)，以建立與其他 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 端點的佇列訊息連線。</span><span class="sxs-lookup"><span data-stu-id="e47f6-123"><xref:System.ServiceModel.NetMsmqBinding>: Uses the .NET binary encoding and framing technologies in conjunction with the Message Queuing (also known as MSMQ) to create queued message connections with other [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] endpoints.</span></span>  
  
 <span data-ttu-id="e47f6-124">如需完整的系統提供繫結，並說明，請參閱[之繫結](../../../docs/framework/wcf/system-provided-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="e47f6-124">For a complete list of system-provided bindings, with descriptions, see [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md).</span></span>  
  
## <a name="custom-bindings"></a><span data-ttu-id="e47f6-125">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="e47f6-125">Custom Bindings</span></span>  
 <span data-ttu-id="e47f6-126">如果系統提供的繫結集合沒有服務應用程式所需的正確功能組合，您可以建立 <xref:System.ServiceModel.Channels.CustomBinding> 繫結。</span><span class="sxs-lookup"><span data-stu-id="e47f6-126">If the system-provided binding collection does not have the correct combination of features that a service application requires, you can create a <xref:System.ServiceModel.Channels.CustomBinding> binding.</span></span> <span data-ttu-id="e47f6-127">如需有關的項目<xref:System.ServiceModel.Channels.CustomBinding>繫結，請參閱[ \<customBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)和[自訂繫結](../../../docs/framework/wcf/extending/custom-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="e47f6-127">For more information about the elements of a <xref:System.ServiceModel.Channels.CustomBinding> binding, see [\<customBinding>](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) and [Custom Bindings](../../../docs/framework/wcf/extending/custom-bindings.md).</span></span>  
  
## <a name="using-bindings"></a><span data-ttu-id="e47f6-128">使用繫結</span><span class="sxs-lookup"><span data-stu-id="e47f6-128">Using Bindings</span></span>  
 <span data-ttu-id="e47f6-129">使用繫結牽涉到兩個基本步驟：</span><span class="sxs-lookup"><span data-stu-id="e47f6-129">Using bindings entails two basic steps:</span></span>  
  
1.  <span data-ttu-id="e47f6-130">選取或定義繫結。</span><span class="sxs-lookup"><span data-stu-id="e47f6-130">Select or define a binding.</span></span> <span data-ttu-id="e47f6-131">最簡單的方法是選擇其中一個系統提供的繫結，並使用其預設值。</span><span class="sxs-lookup"><span data-stu-id="e47f6-131">The easiest method is to choose one of the system-provided bindings and use its default settings.</span></span> <span data-ttu-id="e47f6-132">也可以選擇系統提供的繫結，並重設其屬性值以符合您的需求。</span><span class="sxs-lookup"><span data-stu-id="e47f6-132">You can also choose a system-provided binding and reset its property values to suit your requirements.</span></span> <span data-ttu-id="e47f6-133">或者，您可以建立自訂繫結並依需要設定每個屬性。</span><span class="sxs-lookup"><span data-stu-id="e47f6-133">Alternatively, you can create a custom binding and set every property as required.</span></span>  
  
2.  <span data-ttu-id="e47f6-134">請建立使用這個繫結的端點。</span><span class="sxs-lookup"><span data-stu-id="e47f6-134">Create an endpoint that uses this binding.</span></span>  
  
## <a name="code-and-configuration"></a><span data-ttu-id="e47f6-135">程式碼和組態</span><span class="sxs-lookup"><span data-stu-id="e47f6-135">Code and Configuration</span></span>  
 <span data-ttu-id="e47f6-136">您可以透過程式碼或組態來定義或設定繫結。</span><span class="sxs-lookup"><span data-stu-id="e47f6-136">You can define or configure bindings through code or configuration.</span></span> <span data-ttu-id="e47f6-137">這兩種方法與所使用的繫結型別無關，例如，您是否使用系統提供的或 <xref:System.ServiceModel.Channels.CustomBinding> 繫結。</span><span class="sxs-lookup"><span data-stu-id="e47f6-137">These two approaches are independent of the type of binding used, for example, whether you are using a system-provided or a <xref:System.ServiceModel.Channels.CustomBinding> binding.</span></span> <span data-ttu-id="e47f6-138">一般來說，使用程式碼可讓您在編譯時完全控制繫結的定義。</span><span class="sxs-lookup"><span data-stu-id="e47f6-138">In general, using code gives you complete control over the definition of a binding when you compile.</span></span> <span data-ttu-id="e47f6-139">另一方面，使用組態可讓系統管理員或 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務或用戶端的使用者變更繫結的參數。</span><span class="sxs-lookup"><span data-stu-id="e47f6-139">Using configuration, on the other hand, allows a system administrator or the user of a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service or client to change the parameters of bindings.</span></span> <span data-ttu-id="e47f6-140">這種彈性常常是有需要的，因為沒有辦法可以預測要部署 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 應用程式的特定電腦需求和網路狀況。</span><span class="sxs-lookup"><span data-stu-id="e47f6-140">This flexibility is often desirable because there is no way to predict the specific machine requirements and network conditions into which a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] application is to be deployed.</span></span> <span data-ttu-id="e47f6-141">將繫結 (和位址) 資訊和程式碼分開可讓系統管理員變更繫結詳細資料，而不需要重新編譯或重新部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="e47f6-141">Separating the binding (and addressing) information from the code allows administrators to change the binding details without having to recompile or redeploy the application.</span></span> <span data-ttu-id="e47f6-142">請注意，如果繫結是以程式碼定義的，它會覆寫組態檔中任何以組態為基礎所做的定義。</span><span class="sxs-lookup"><span data-stu-id="e47f6-142">Note that if the binding is defined in code, it overwrites any configuration-based definitions made in the configuration file.</span></span> <span data-ttu-id="e47f6-143">如需這些方法的範例，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="e47f6-143">For examples of these approaches, see the following topics:</span></span>  
  
-   <span data-ttu-id="e47f6-144">[如何： 將 WCF 服務裝載於受管理的應用程式](../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)提供的範例程式碼中建立繫結。</span><span class="sxs-lookup"><span data-stu-id="e47f6-144">[How to: Host a WCF Service in a Managed Application](../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md) provides an example of creating a binding in code.</span></span>  
  
-   <span data-ttu-id="e47f6-145">[如何： 設定用戶端](../../../docs/framework/wcf/how-to-configure-a-basic-wcf-client.md)提供建立使用設定的用戶端的範例。</span><span class="sxs-lookup"><span data-stu-id="e47f6-145">[How to: Configure a Client](../../../docs/framework/wcf/how-to-configure-a-basic-wcf-client.md) provides an example of creating a client using configuration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e47f6-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e47f6-146">See Also</span></span>  
 [<span data-ttu-id="e47f6-147">建立端點概觀</span><span class="sxs-lookup"><span data-stu-id="e47f6-147">Endpoint Creation Overview</span></span>](../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [<span data-ttu-id="e47f6-148">如何：在設定中指定服務繫結</span><span class="sxs-lookup"><span data-stu-id="e47f6-148">How to: Specify a Service Binding in Configuration</span></span>](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)  
 [<span data-ttu-id="e47f6-149">如何：在程式碼中指定服務繫結</span><span class="sxs-lookup"><span data-stu-id="e47f6-149">How to: Specify a Service Binding in Code</span></span>](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-code.md)  
 [<span data-ttu-id="e47f6-150">如何：在設定中指定用戶端繫結</span><span class="sxs-lookup"><span data-stu-id="e47f6-150">How to: Specify a Client Binding in Configuration</span></span>](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md)  
 [<span data-ttu-id="e47f6-151">如何：在程式碼中指定用戶端繫結</span><span class="sxs-lookup"><span data-stu-id="e47f6-151">How to: Specify a Client Binding in Code</span></span>](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-code.md)

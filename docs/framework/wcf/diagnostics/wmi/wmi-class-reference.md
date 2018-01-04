---
title: "WMI 類別參考"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b95a51f5-8251-4619-ae05-7de88cb90f9a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0e221c8197b9713dd5f4e35114ada3c63f4978ef
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="wmi-class-reference"></a><span data-ttu-id="96de7-102">WMI 類別參考</span><span class="sxs-lookup"><span data-stu-id="96de7-102">WMI Class Reference</span></span>
<span data-ttu-id="96de7-103">本節將列出由 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] WMI 提供者公開的所有 WMI 類別。</span><span class="sxs-lookup"><span data-stu-id="96de7-103">This section lists all the WMI classes exposed by the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] WMI provider.</span></span>  
  
## <a name="accessing-wmi-instances"></a><span data-ttu-id="96de7-104">存取 WMI 執行個體</span><span class="sxs-lookup"><span data-stu-id="96de7-104">Accessing WMI Instances</span></span>  
 <span data-ttu-id="96de7-105">WMI 物件參考中列出的所有類別都無法直接產生，除了 Service、AppDomain、Contract、ServiceAppDomain、ServiceToEndpointAssociation 和 Endpoint。</span><span class="sxs-lookup"><span data-stu-id="96de7-105">All the classes listed in the WMI Object Reference cannot be directly instantiated, except for Service, AppDomain, Contract, ServiceAppDomain, ServiceToEndpointAssociation and Endpoint.</span></span> <span data-ttu-id="96de7-106">如果要存取其他執行個體，您可以存取先前所述最上層類別的屬性。</span><span class="sxs-lookup"><span data-stu-id="96de7-106">To access other instances, you can access the properties of the previously mentioned top level classes.</span></span> <span data-ttu-id="96de7-107">例如，您可以從 [端點執行個體] -> [繫結] -> [BindingElements] 來存取 TransportBindingElement 執行個體。</span><span class="sxs-lookup"><span data-stu-id="96de7-107">For example, you can access the TransportBindingElement instance from the Endpoint instance -> Binding -> BindingElements.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="96de7-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="96de7-108">In This Section</span></span>  
 [<span data-ttu-id="96de7-109">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="96de7-109">ActivityTransfer</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/activitytransfer.md)  
  
 [<span data-ttu-id="96de7-110">AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="96de7-110">AppDomainInfo</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/appdomaininfo.md)  
  
 [<span data-ttu-id="96de7-111">AspNetCompatibilityRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="96de7-111">AspNetCompatibilityRequirementsAttribute</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/aspnetcompatibilityrequirementsattribute.md)  
  
 [<span data-ttu-id="96de7-112">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="96de7-112">AsymmetricSecurityBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/asymmetricsecuritybindingelement.md)  
  
 <span data-ttu-id="96de7-113">「 行為類別 」</span><span class="sxs-lookup"><span data-stu-id="96de7-113">"Behavior class"</span></span>  
  
 [<span data-ttu-id="96de7-114">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="96de7-114">BinaryMessageEncodingBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/binarymessageencodingbindingelement.md)  
  
 [<span data-ttu-id="96de7-115">Binding</span><span class="sxs-lookup"><span data-stu-id="96de7-115">Binding</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/binding.md)  
  
 [<span data-ttu-id="96de7-116">BindingElement</span><span class="sxs-lookup"><span data-stu-id="96de7-116">BindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/bindingelement.md)  
  
 [<span data-ttu-id="96de7-117">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="96de7-117">CallbackBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/callbackbehavior.md)  
  
 [<span data-ttu-id="96de7-118">Channel 類別</span><span class="sxs-lookup"><span data-stu-id="96de7-118">Channel class</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/channel-class.md)  
  
 [<span data-ttu-id="96de7-119">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="96de7-119">ChannelPoolSettings</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/channelpoolsettings.md)  
  
 [<span data-ttu-id="96de7-120">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="96de7-120">ClientCredentials</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/clientcredentials.md)  
  
 [<span data-ttu-id="96de7-121">ClientViaBehavior</span><span class="sxs-lookup"><span data-stu-id="96de7-121">ClientViaBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md)  
  
 [<span data-ttu-id="96de7-122">CompositeDuplexBindingElement</span><span class="sxs-lookup"><span data-stu-id="96de7-122">CompositeDuplexBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/compositeduplexbindingelement.md)  
  
 [<span data-ttu-id="96de7-123">ConnectionOrientedTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="96de7-123">ConnectionOrientedTransportBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/connectionorientedtransportbindingelement.md)  
  
 [<span data-ttu-id="96de7-124">Contract</span><span class="sxs-lookup"><span data-stu-id="96de7-124">Contract</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/contract.md)  
  
 [<span data-ttu-id="96de7-125">CustomBindingElement</span><span class="sxs-lookup"><span data-stu-id="96de7-125">CustomBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/custombindingelement.md)  
  
 [<span data-ttu-id="96de7-126">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="96de7-126">DeliveryRequirementsAttribute</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/deliveryrequirementsattribute.md)  
  
 [<span data-ttu-id="96de7-127">Endpoint</span><span class="sxs-lookup"><span data-stu-id="96de7-127">Endpoint</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md)  
  
 [<span data-ttu-id="96de7-128">HttpsTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="96de7-128">HttpsTransportBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/httpstransportbindingelement.md)  
  
 [<span data-ttu-id="96de7-129">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="96de7-129">HttpTransportBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/httptransportbindingelement.md)  
  
 [<span data-ttu-id="96de7-130">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="96de7-130">LocalServiceSecuritySettings</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/localservicesecuritysettings.md)  
  
 [<span data-ttu-id="96de7-131">MatchAllEndpointBehavior</span><span class="sxs-lookup"><span data-stu-id="96de7-131">MatchAllEndpointBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/matchallendpointbehavior.md)  
  
 [<span data-ttu-id="96de7-132">MessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="96de7-132">MessageEncodingBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/messageencodingbindingelement.md)  
  
 [<span data-ttu-id="96de7-133">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="96de7-133">MsmqBindingElementBase</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/msmqbindingelementbase.md)  
  
 [<span data-ttu-id="96de7-134">MsmqIntegrationBindingElement</span><span class="sxs-lookup"><span data-stu-id="96de7-134">MsmqIntegrationBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/msmqintegrationbindingelement.md)  
  
 [<span data-ttu-id="96de7-135">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="96de7-135">MsmqTransportBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/msmqtransportbindingelement.md)  
  
 [<span data-ttu-id="96de7-136">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="96de7-136">MtomMessageEncodingBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/mtommessageencodingbindingelement.md)  
  
 [<span data-ttu-id="96de7-137">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="96de7-137">MustUnderstandBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/mustunderstandbehavior.md)  
  
 [<span data-ttu-id="96de7-138">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="96de7-138">NamedPipeConnectionPoolSettings</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/namedpipeconnectionpoolsettings.md)  
  
 [<span data-ttu-id="96de7-139">NamedPipeTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="96de7-139">NamedPipeTransportBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/namedpipetransportbindingelement.md)  
  
 [<span data-ttu-id="96de7-140">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="96de7-140">OneWayBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/onewaybindingelement.md)  
  
 <span data-ttu-id="96de7-141">「 作業類別 」</span><span class="sxs-lookup"><span data-stu-id="96de7-141">"Operation class"</span></span>  
  
 [<span data-ttu-id="96de7-142">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="96de7-142">OperationBehaviorAttribute</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/operationbehaviorattribute.md)  
  
 [<span data-ttu-id="96de7-143">PeerCustomResolverBindingElement</span><span class="sxs-lookup"><span data-stu-id="96de7-143">PeerCustomResolverBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/peercustomresolverbindingelement.md)  
  
 [<span data-ttu-id="96de7-144">PeerResolverBindingElement</span><span class="sxs-lookup"><span data-stu-id="96de7-144">PeerResolverBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/peerresolverbindingelement.md)  
  
 [<span data-ttu-id="96de7-145">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="96de7-145">PeerSecuritySettings</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/peersecuritysettings.md)  
  
 [<span data-ttu-id="96de7-146">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="96de7-146">PeerTransportBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/peertransportbindingelement.md)  
  
 [<span data-ttu-id="96de7-147">PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="96de7-147">PeerTransportSecuritySettings</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/peertransportsecuritysettings.md)  
  
 [<span data-ttu-id="96de7-148">PnrpPeerResolverBindingElement</span><span class="sxs-lookup"><span data-stu-id="96de7-148">PnrpPeerResolverBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/pnrppeerresolverbindingelement.md)  
  
 [<span data-ttu-id="96de7-149">PrivacyNoticeBindingElement</span><span class="sxs-lookup"><span data-stu-id="96de7-149">PrivacyNoticeBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/privacynoticebindingelement.md)  
  
 [<span data-ttu-id="96de7-150">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="96de7-150">ReliableSessionBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/reliablesessionbindingelement.md)  
  
 [<span data-ttu-id="96de7-151">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="96de7-151">SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/securitybindingelement.md)  
  
 [<span data-ttu-id="96de7-152">Service</span><span class="sxs-lookup"><span data-stu-id="96de7-152">Service</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/service.md)  
  
 [<span data-ttu-id="96de7-153">ServiceAppDomain</span><span class="sxs-lookup"><span data-stu-id="96de7-153">ServiceAppDomain</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/serviceappdomain.md)  
  
 [<span data-ttu-id="96de7-154">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="96de7-154">ServiceAuthorizationBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/serviceauthorizationbehavior.md)  
  
 [<span data-ttu-id="96de7-155">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="96de7-155">ServiceBehaviorAttribute</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/servicebehaviorattribute.md)  
  
 [<span data-ttu-id="96de7-156">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="96de7-156">ServiceCredentials</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/servicecredentials.md)  
  
 [<span data-ttu-id="96de7-157">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="96de7-157">ServiceDebugBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/servicedebugbehavior.md)  
  
 [<span data-ttu-id="96de7-158">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="96de7-158">ServiceMetadataBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/servicemetadatabehavior.md)  
  
 [<span data-ttu-id="96de7-159">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="96de7-159">ServiceSecurityAuditBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/servicesecurityauditbehavior.md)  
  
 [<span data-ttu-id="96de7-160">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="96de7-160">ServiceThrottlingBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/servicethrottlingbehavior.md)  
  
 [<span data-ttu-id="96de7-161">ServiceTimeoutsBehavior</span><span class="sxs-lookup"><span data-stu-id="96de7-161">ServiceTimeoutsBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/servicetimeoutsbehavior.md)  
  
 [<span data-ttu-id="96de7-162">ServiceToEndpointAssociation</span><span class="sxs-lookup"><span data-stu-id="96de7-162">ServiceToEndpointAssociation</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/servicetoendpointassociation.md)  
  
 [<span data-ttu-id="96de7-163">SslStreamSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="96de7-163">SslStreamSecurityBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/sslstreamsecuritybindingelement.md)  
  
 [<span data-ttu-id="96de7-164">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="96de7-164">SymmetricSecurityBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/symmetricsecuritybindingelement.md)  
  
 [<span data-ttu-id="96de7-165">SynchronousReceiveBehavior</span><span class="sxs-lookup"><span data-stu-id="96de7-165">SynchronousReceiveBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/synchronousreceivebehavior.md)  
  
 [<span data-ttu-id="96de7-166">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="96de7-166">TcpConnectionPoolSettings</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/tcpconnectionpoolsettings.md)  
  
 [<span data-ttu-id="96de7-167">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="96de7-167">TcpTransportBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/tcptransportbindingelement.md)  
  
 [<span data-ttu-id="96de7-168">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="96de7-168">TextMessageEncodingBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/textmessageencodingbindingelement.md)  
  
 [<span data-ttu-id="96de7-169">TraceListener</span><span class="sxs-lookup"><span data-stu-id="96de7-169">TraceListener</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/tracelistener.md)  
  
 [<span data-ttu-id="96de7-170">TraceListenerArgument</span><span class="sxs-lookup"><span data-stu-id="96de7-170">TraceListenerArgument</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/tracelistenerargument.md)  
  
 [<span data-ttu-id="96de7-171">TransactedBatchingBehavior</span><span class="sxs-lookup"><span data-stu-id="96de7-171">TransactedBatchingBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/transactedbatchingbehavior.md)  
  
 [<span data-ttu-id="96de7-172">TransactionFlowAttribute</span><span class="sxs-lookup"><span data-stu-id="96de7-172">TransactionFlowAttribute</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/transactionflowattribute.md)  
  
 [<span data-ttu-id="96de7-173">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="96de7-173">TransactionFlowBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/transactionflowbindingelement.md)  
  
 [<span data-ttu-id="96de7-174">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="96de7-174">TransportBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/transportbindingelement.md)  
  
 [<span data-ttu-id="96de7-175">TransportSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="96de7-175">TransportSecurityBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/transportsecuritybindingelement.md)  
  
 [<span data-ttu-id="96de7-176">UseManagedPresentationBindingElement</span><span class="sxs-lookup"><span data-stu-id="96de7-176">UseManagedPresentationBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/usemanagedpresentationbindingelement.md)  
  
 [<span data-ttu-id="96de7-177">WindowsStreamSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="96de7-177">WindowsStreamSecurityBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/windowsstreamsecuritybindingelement.md)  
  
 [<span data-ttu-id="96de7-178">WSAT_TraceEvent</span><span class="sxs-lookup"><span data-stu-id="96de7-178">WSAT_TraceEvent</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/wsat-traceevent.md)  
  
 [<span data-ttu-id="96de7-179">WSAT_TraceProvider</span><span class="sxs-lookup"><span data-stu-id="96de7-179">WSAT_TraceProvider</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/wsat-traceprovider.md)  
  
 [<span data-ttu-id="96de7-180">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="96de7-180">WSAT_TraceRecord</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/wsat-tracerecord.md)  
  
 [<span data-ttu-id="96de7-181">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="96de7-181">XmlDictionaryReaderQuotas</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/xmldictionaryreaderquotas.md)  
  
 [<span data-ttu-id="96de7-182">XmlSerializerOperationBehavior</span><span class="sxs-lookup"><span data-stu-id="96de7-182">XmlSerializerOperationBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/xmlserializeroperationbehavior.md)

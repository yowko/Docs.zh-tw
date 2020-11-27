---
title: WMI 類別參考
ms.date: 03/30/2017
ms.assetid: b95a51f5-8251-4619-ae05-7de88cb90f9a
ms.openlocfilehash: 9830fbf50e8df625e3d3077a66c66e0370204acb
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262251"
---
# <a name="wmi-class-reference"></a><span data-ttu-id="0315c-102">WMI 類別參考</span><span class="sxs-lookup"><span data-stu-id="0315c-102">WMI Class Reference</span></span>

<span data-ttu-id="0315c-103">本節列出 Windows Communication Foundation (WCF) WMI 提供者公開的所有 WMI 類別。</span><span class="sxs-lookup"><span data-stu-id="0315c-103">This section lists all the WMI classes exposed by the Windows Communication Foundation (WCF) WMI provider.</span></span>  
  
## <a name="accessing-wmi-instances"></a><span data-ttu-id="0315c-104">存取 WMI 執行個體</span><span class="sxs-lookup"><span data-stu-id="0315c-104">Accessing WMI Instances</span></span>  

 <span data-ttu-id="0315c-105">WMI 物件參考中列出的所有類別都無法直接產生，除了 Service、AppDomain、Contract、ServiceAppDomain、ServiceToEndpointAssociation 和 Endpoint。</span><span class="sxs-lookup"><span data-stu-id="0315c-105">All the classes listed in the WMI Object Reference cannot be directly instantiated, except for Service, AppDomain, Contract, ServiceAppDomain, ServiceToEndpointAssociation and Endpoint.</span></span> <span data-ttu-id="0315c-106">如果要存取其他執行個體，您可以存取先前所述最上層類別的屬性。</span><span class="sxs-lookup"><span data-stu-id="0315c-106">To access other instances, you can access the properties of the previously mentioned top level classes.</span></span> <span data-ttu-id="0315c-107">例如，您可以從端點實例存取 TransportBindingElement 實例-> 系結-> BindingElements。</span><span class="sxs-lookup"><span data-stu-id="0315c-107">For example, you can access the TransportBindingElement instance from the Endpoint instance -> Binding -> BindingElements.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0315c-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="0315c-108">In This Section</span></span>  

 [<span data-ttu-id="0315c-109">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="0315c-109">ActivityTransfer</span></span>](activitytransfer.md)  
  
 [<span data-ttu-id="0315c-110">AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="0315c-110">AppDomainInfo</span></span>](appdomaininfo.md)  
  
 [<span data-ttu-id="0315c-111">AspNetCompatibilityRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="0315c-111">AspNetCompatibilityRequirementsAttribute</span></span>](aspnetcompatibilityrequirementsattribute.md)  
  
 [<span data-ttu-id="0315c-112">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="0315c-112">AsymmetricSecurityBindingElement</span></span>](asymmetricsecuritybindingelement.md)  
  
 <span data-ttu-id="0315c-113">"行為類別"</span><span class="sxs-lookup"><span data-stu-id="0315c-113">"Behavior class"</span></span>  
  
 [<span data-ttu-id="0315c-114">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="0315c-114">BinaryMessageEncodingBindingElement</span></span>](binarymessageencodingbindingelement.md)  
  
 [<span data-ttu-id="0315c-115">繫結</span><span class="sxs-lookup"><span data-stu-id="0315c-115">Binding</span></span>](binding.md)  
  
 [<span data-ttu-id="0315c-116">BindingElement</span><span class="sxs-lookup"><span data-stu-id="0315c-116">BindingElement</span></span>](bindingelement.md)  
  
 [<span data-ttu-id="0315c-117">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="0315c-117">CallbackBehavior</span></span>](callbackbehavior.md)  
  
 [<span data-ttu-id="0315c-118">Channel 類別</span><span class="sxs-lookup"><span data-stu-id="0315c-118">Channel class</span></span>](channel-class.md)  
  
 [<span data-ttu-id="0315c-119">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="0315c-119">ChannelPoolSettings</span></span>](channelpoolsettings.md)  
  
 [<span data-ttu-id="0315c-120">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="0315c-120">ClientCredentials</span></span>](clientcredentials.md)  
  
 [<span data-ttu-id="0315c-121">ClientViaBehavior</span><span class="sxs-lookup"><span data-stu-id="0315c-121">ClientViaBehavior</span></span>](clientviabehavior.md)  
  
 [<span data-ttu-id="0315c-122">CompositeDuplexBindingElement</span><span class="sxs-lookup"><span data-stu-id="0315c-122">CompositeDuplexBindingElement</span></span>](compositeduplexbindingelement.md)  
  
 [<span data-ttu-id="0315c-123">ConnectionOrientedTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="0315c-123">ConnectionOrientedTransportBindingElement</span></span>](connectionorientedtransportbindingelement.md)  
  
 [<span data-ttu-id="0315c-124">合同</span><span class="sxs-lookup"><span data-stu-id="0315c-124">Contract</span></span>](contract.md)  
  
 [<span data-ttu-id="0315c-125">CustomBindingElement</span><span class="sxs-lookup"><span data-stu-id="0315c-125">CustomBindingElement</span></span>](custombindingelement.md)  
  
 [<span data-ttu-id="0315c-126">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="0315c-126">DeliveryRequirementsAttribute</span></span>](deliveryrequirementsattribute.md)  
  
 [<span data-ttu-id="0315c-127">端點</span><span class="sxs-lookup"><span data-stu-id="0315c-127">Endpoint</span></span>](endpoint.md)  
  
 [<span data-ttu-id="0315c-128">HttpsTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="0315c-128">HttpsTransportBindingElement</span></span>](httpstransportbindingelement.md)  
  
 [<span data-ttu-id="0315c-129">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="0315c-129">HttpTransportBindingElement</span></span>](httptransportbindingelement.md)  
  
 [<span data-ttu-id="0315c-130">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="0315c-130">LocalServiceSecuritySettings</span></span>](localservicesecuritysettings.md)  
  
 [<span data-ttu-id="0315c-131">MatchAllEndpointBehavior</span><span class="sxs-lookup"><span data-stu-id="0315c-131">MatchAllEndpointBehavior</span></span>](matchallendpointbehavior.md)  
  
 [<span data-ttu-id="0315c-132">MessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="0315c-132">MessageEncodingBindingElement</span></span>](messageencodingbindingelement.md)  
  
 [<span data-ttu-id="0315c-133">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="0315c-133">MsmqBindingElementBase</span></span>](msmqbindingelementbase.md)  
  
 [<span data-ttu-id="0315c-134">MsmqIntegrationBindingElement</span><span class="sxs-lookup"><span data-stu-id="0315c-134">MsmqIntegrationBindingElement</span></span>](msmqintegrationbindingelement.md)  
  
 [<span data-ttu-id="0315c-135">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="0315c-135">MsmqTransportBindingElement</span></span>](msmqtransportbindingelement.md)  
  
 [<span data-ttu-id="0315c-136">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="0315c-136">MtomMessageEncodingBindingElement</span></span>](mtommessageencodingbindingelement.md)  
  
 [<span data-ttu-id="0315c-137">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="0315c-137">MustUnderstandBehavior</span></span>](mustunderstandbehavior.md)  
  
 [<span data-ttu-id="0315c-138">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="0315c-138">NamedPipeConnectionPoolSettings</span></span>](namedpipeconnectionpoolsettings.md)  
  
 [<span data-ttu-id="0315c-139">NamedPipeTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="0315c-139">NamedPipeTransportBindingElement</span></span>](namedpipetransportbindingelement.md)  
  
 [<span data-ttu-id="0315c-140">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="0315c-140">OneWayBindingElement</span></span>](onewaybindingelement.md)  
  
 <span data-ttu-id="0315c-141">"Operation class"</span><span class="sxs-lookup"><span data-stu-id="0315c-141">"Operation class"</span></span>  
  
 [<span data-ttu-id="0315c-142">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="0315c-142">OperationBehaviorAttribute</span></span>](operationbehaviorattribute.md)  
  
 [<span data-ttu-id="0315c-143">PeerCustomResolverBindingElement</span><span class="sxs-lookup"><span data-stu-id="0315c-143">PeerCustomResolverBindingElement</span></span>](peercustomresolverbindingelement.md)  
  
 [<span data-ttu-id="0315c-144">PeerResolverBindingElement</span><span class="sxs-lookup"><span data-stu-id="0315c-144">PeerResolverBindingElement</span></span>](peerresolverbindingelement.md)  
  
 [<span data-ttu-id="0315c-145">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="0315c-145">PeerSecuritySettings</span></span>](peersecuritysettings.md)  
  
 [<span data-ttu-id="0315c-146">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="0315c-146">PeerTransportBindingElement</span></span>](peertransportbindingelement.md)  
  
 [<span data-ttu-id="0315c-147">PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="0315c-147">PeerTransportSecuritySettings</span></span>](peertransportsecuritysettings.md)  
  
 [<span data-ttu-id="0315c-148">PnrpPeerResolverBindingElement</span><span class="sxs-lookup"><span data-stu-id="0315c-148">PnrpPeerResolverBindingElement</span></span>](pnrppeerresolverbindingelement.md)  
  
 [<span data-ttu-id="0315c-149">PrivacyNoticeBindingElement</span><span class="sxs-lookup"><span data-stu-id="0315c-149">PrivacyNoticeBindingElement</span></span>](privacynoticebindingelement.md)  
  
 [<span data-ttu-id="0315c-150">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="0315c-150">ReliableSessionBindingElement</span></span>](reliablesessionbindingelement.md)  
  
 [<span data-ttu-id="0315c-151">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="0315c-151">SecurityBindingElement</span></span>](securitybindingelement.md)  
  
 [<span data-ttu-id="0315c-152">服務</span><span class="sxs-lookup"><span data-stu-id="0315c-152">Service</span></span>](service.md)  
  
 [<span data-ttu-id="0315c-153">ServiceAppDomain</span><span class="sxs-lookup"><span data-stu-id="0315c-153">ServiceAppDomain</span></span>](serviceappdomain.md)  
  
 [<span data-ttu-id="0315c-154">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="0315c-154">ServiceAuthorizationBehavior</span></span>](serviceauthorizationbehavior.md)  
  
 [<span data-ttu-id="0315c-155">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="0315c-155">ServiceBehaviorAttribute</span></span>](servicebehaviorattribute.md)  
  
 [<span data-ttu-id="0315c-156">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="0315c-156">ServiceCredentials</span></span>](servicecredentials.md)  
  
 [<span data-ttu-id="0315c-157">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="0315c-157">ServiceDebugBehavior</span></span>](servicedebugbehavior.md)  
  
 [<span data-ttu-id="0315c-158">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="0315c-158">ServiceMetadataBehavior</span></span>](servicemetadatabehavior.md)  
  
 [<span data-ttu-id="0315c-159">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="0315c-159">ServiceSecurityAuditBehavior</span></span>](servicesecurityauditbehavior.md)  
  
 [<span data-ttu-id="0315c-160">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="0315c-160">ServiceThrottlingBehavior</span></span>](servicethrottlingbehavior.md)  
  
 [<span data-ttu-id="0315c-161">ServiceTimeoutsBehavior</span><span class="sxs-lookup"><span data-stu-id="0315c-161">ServiceTimeoutsBehavior</span></span>](servicetimeoutsbehavior.md)  
  
 [<span data-ttu-id="0315c-162">ServiceToEndpointAssociation</span><span class="sxs-lookup"><span data-stu-id="0315c-162">ServiceToEndpointAssociation</span></span>](servicetoendpointassociation.md)  
  
 [<span data-ttu-id="0315c-163">SslStreamSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="0315c-163">SslStreamSecurityBindingElement</span></span>](sslstreamsecuritybindingelement.md)  
  
 [<span data-ttu-id="0315c-164">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="0315c-164">SymmetricSecurityBindingElement</span></span>](symmetricsecuritybindingelement.md)  
  
 [<span data-ttu-id="0315c-165">SynchronousReceiveBehavior</span><span class="sxs-lookup"><span data-stu-id="0315c-165">SynchronousReceiveBehavior</span></span>](synchronousreceivebehavior.md)  
  
 [<span data-ttu-id="0315c-166">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="0315c-166">TcpConnectionPoolSettings</span></span>](tcpconnectionpoolsettings.md)  
  
 [<span data-ttu-id="0315c-167">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="0315c-167">TcpTransportBindingElement</span></span>](tcptransportbindingelement.md)  
  
 [<span data-ttu-id="0315c-168">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="0315c-168">TextMessageEncodingBindingElement</span></span>](textmessageencodingbindingelement.md)  
  
 [<span data-ttu-id="0315c-169">TraceListener</span><span class="sxs-lookup"><span data-stu-id="0315c-169">TraceListener</span></span>](tracelistener.md)  
  
 [<span data-ttu-id="0315c-170">TraceListenerArgument</span><span class="sxs-lookup"><span data-stu-id="0315c-170">TraceListenerArgument</span></span>](tracelistenerargument.md)  
  
 [<span data-ttu-id="0315c-171">TransactedBatchingBehavior</span><span class="sxs-lookup"><span data-stu-id="0315c-171">TransactedBatchingBehavior</span></span>](transactedbatchingbehavior.md)  
  
 [<span data-ttu-id="0315c-172">TransactionFlowAttribute</span><span class="sxs-lookup"><span data-stu-id="0315c-172">TransactionFlowAttribute</span></span>](transactionflowattribute.md)  
  
 [<span data-ttu-id="0315c-173">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="0315c-173">TransactionFlowBindingElement</span></span>](transactionflowbindingelement.md)  
  
 [<span data-ttu-id="0315c-174">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="0315c-174">TransportBindingElement</span></span>](transportbindingelement.md)  
  
 [<span data-ttu-id="0315c-175">TransportSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="0315c-175">TransportSecurityBindingElement</span></span>](transportsecuritybindingelement.md)  
  
 [<span data-ttu-id="0315c-176">UseManagedPresentationBindingElement</span><span class="sxs-lookup"><span data-stu-id="0315c-176">UseManagedPresentationBindingElement</span></span>](usemanagedpresentationbindingelement.md)  
  
 [<span data-ttu-id="0315c-177">WindowsStreamSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="0315c-177">WindowsStreamSecurityBindingElement</span></span>](windowsstreamsecuritybindingelement.md)  
  
 [<span data-ttu-id="0315c-178">WSAT_TraceEvent</span><span class="sxs-lookup"><span data-stu-id="0315c-178">WSAT_TraceEvent</span></span>](wsat-traceevent.md)  
  
 [<span data-ttu-id="0315c-179">WSAT_TraceProvider</span><span class="sxs-lookup"><span data-stu-id="0315c-179">WSAT_TraceProvider</span></span>](wsat-traceprovider.md)  
  
 [<span data-ttu-id="0315c-180">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="0315c-180">WSAT_TraceRecord</span></span>](wsat-tracerecord.md)  
  
 [<span data-ttu-id="0315c-181">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="0315c-181">XmlDictionaryReaderQuotas</span></span>](xmldictionaryreaderquotas.md)  
  
 [<span data-ttu-id="0315c-182">XmlSerializerOperationBehavior</span><span class="sxs-lookup"><span data-stu-id="0315c-182">XmlSerializerOperationBehavior</span></span>](xmlserializeroperationbehavior.md)

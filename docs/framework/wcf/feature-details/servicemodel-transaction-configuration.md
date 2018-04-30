---
title: ServiceModel 異動組態
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
- transactions [WCF], ServiceModel configuration
ms.assetid: 5636067a-7fbd-4485-aaa2-8141c502acf3
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 96cf83be06949160cf3efa73344e4a7680d24e09
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2018
---
# <a name="servicemodel-transaction-configuration"></a><span data-ttu-id="3e279-102">ServiceModel 異動組態</span><span class="sxs-lookup"><span data-stu-id="3e279-102">ServiceModel Transaction Configuration</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="3e279-103"> 提供了三個屬性，可用於設定服務的交易：`transactionFlow`、`transactionProtocol` 和 `transactionTimeout`。</span><span class="sxs-lookup"><span data-stu-id="3e279-103"> provides three attributes for configuring transactions for a service: `transactionFlow`, `transactionProtocol`, and `transactionTimeout`.</span></span>  
  
## <a name="configuring-transactionflow"></a><span data-ttu-id="3e279-104">設定 transactionFlow</span><span class="sxs-lookup"><span data-stu-id="3e279-104">Configuring transactionFlow</span></span>  
 <span data-ttu-id="3e279-105">大部分所提供預先定義的繫結 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會包含 `transactionFlow` 和 `transactionProtocol` 屬性，因此您可以將繫結設定為接受使用特定交易流程通訊協定之特定端點的傳入交易。</span><span class="sxs-lookup"><span data-stu-id="3e279-105">Most of the predefined bindings [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides contain the `transactionFlow` and `transactionProtocol` attributes, so that you can configure the binding to accept incoming transactions for a specific endpoint using a specific transaction flow protocol.</span></span> <span data-ttu-id="3e279-106">此外，您可以使用 `transactionFlow` 元素及其 `transactionProtocol` 屬性來建置您自訂的繫結。</span><span class="sxs-lookup"><span data-stu-id="3e279-106">In addition, you can use the `transactionFlow` element and its `transactionProtocol` attribute to build your own custom binding.</span></span> <span data-ttu-id="3e279-107">如需有關設定組態項目，請參閱[\<繫結 >](../../../../docs/framework/misc/binding.md)和[WCF 組態結構描述](../../../../docs/framework/configure-apps/file-schema/wcf/index.md)。</span><span class="sxs-lookup"><span data-stu-id="3e279-107">For more information about setting the configuration elements, see [\<binding>](../../../../docs/framework/misc/binding.md) and [WCF Configuration Schema](../../../../docs/framework/configure-apps/file-schema/wcf/index.md).</span></span>  
  
 <span data-ttu-id="3e279-108">`transactionFlow` 屬性會指定是否要為使用繫結的服務端點啟用交易流程。</span><span class="sxs-lookup"><span data-stu-id="3e279-108">The `transactionFlow` attribute specifies whether transaction flow is enabled for service endpoints that use the binding.</span></span>  
  
## <a name="configuring-transactionprotocol"></a><span data-ttu-id="3e279-109">設定 transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="3e279-109">Configuring transactionProtocol</span></span>  
 <span data-ttu-id="3e279-110">`transactionProtocol` 屬性會指定交易通訊協定與使用繫結的服務端點一起使用。</span><span class="sxs-lookup"><span data-stu-id="3e279-110">The `transactionProtocol` attribute specifies the transaction protocol to use with service endpoints that use the binding.</span></span>  
  
 <span data-ttu-id="3e279-111">以下是組態區段的範例，其中設定了支援交易流程的指定繫結，以及使用 WS-AtomicTransaction 通訊協定的範例。</span><span class="sxs-lookup"><span data-stu-id="3e279-111">The following is an example of a configuration section that configures the specified binding to support transaction flow, as well as a use the WS-AtomicTransaction protocol.</span></span>  
  
```xml  
<netNamedPipeBinding>  
   <binding name="test"  
      closeTimeout="00:00:10"  
      openTimeout="00:00:20"   
      receiveTimeout="00:00:30"  
      sendTimeout="00:00:40"  
      transactionFlow="true"  
      transactionProtocol="WSAtomicTransactionOctober2004"  
      hostNameComparisonMode="WeakWildcard"  
      maxBufferSize="1001"  
      maxConnections="123"   
      maxReceivedMessageSize="1000">  
   </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="configuring-transactiontimeout"></a><span data-ttu-id="3e279-112">設定 transactionTimeout</span><span class="sxs-lookup"><span data-stu-id="3e279-112">Configuring transactionTimeout</span></span>  
 <span data-ttu-id="3e279-113">您可以在組態檔的 `transactionTimeout` 項目內為您的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務設定 `behavior` 屬性。</span><span class="sxs-lookup"><span data-stu-id="3e279-113">You can configure the `transactionTimeout` attribute for your [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service in the `behavior` element of the configuration file.</span></span> <span data-ttu-id="3e279-114">下列程式碼會示範如何執行此項作業。</span><span class="sxs-lookup"><span data-stu-id="3e279-114">The following code demonstrates how to do this.</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>  
         <behavior name="NewBehavior" transactionTimeout="00:01:00" /> <!-- 1 minute timeout -->  
      </behaviors>  
   </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="3e279-115">`transactionTimeout` 屬性會指定在服務所建立之新交易必須完成的時間週期。</span><span class="sxs-lookup"><span data-stu-id="3e279-115">The `transactionTimeout` attribute specifies the time period within which a new transaction created at the service must complete.</span></span> <span data-ttu-id="3e279-116">這個屬性可當做任何建立新交易之作業的 <xref:System.Transactions.TransactionScope> 逾時使用，若套用了 <xref:System.ServiceModel.OperationBehaviorAttribute>，則 <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> 屬性會設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="3e279-116">It is used as the <xref:System.Transactions.TransactionScope> time-out for any operation that establishes a new transaction, and if <xref:System.ServiceModel.OperationBehaviorAttribute> is applied, the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property is set to `true`.</span></span>  
  
 <span data-ttu-id="3e279-117">逾時會指定從建立交易到完成兩階段交易認可通訊協定中的階段 1 的時間範圍。</span><span class="sxs-lookup"><span data-stu-id="3e279-117">The time-out specifies the duration of time from the creation of the transaction to the completion of phase 1 in the two-phase commit protocol.</span></span>  
  
 <span data-ttu-id="3e279-118">如果在 `service` 組態區段中設定這個屬性，您至少應該以 <xref:System.ServiceModel.OperationBehaviorAttribute> 套用一個對應服務的方法，其中 <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="3e279-118">If this attribute is set within a `service` configuration section, you should apply at least one method of the corresponding service with <xref:System.ServiceModel.OperationBehaviorAttribute>, in which the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property is set to `true`.</span></span>  
  
 <span data-ttu-id="3e279-119">請注意，所使用的逾時值會是這個 `transactionTimeout` 組態設定和任何 <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> 屬性間的較小值。</span><span class="sxs-lookup"><span data-stu-id="3e279-119">Note that the time-out value used is the smaller value between this `transactionTimeout` configuration setting and any <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e279-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e279-120">See Also</span></span>  
 [<span data-ttu-id="3e279-121">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="3e279-121">\<binding></span></span>](../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="3e279-122">WCF 組態結構描述</span><span class="sxs-lookup"><span data-stu-id="3e279-122">WCF Configuration Schema</span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/index.md)

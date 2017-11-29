---
title: '&lt;transactionFlow&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8c40b3a79567ccc1ca5a83631253d3ff6ead0f84
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="lttransactionflowgt"></a><span data-ttu-id="c02c1-102">&lt;transactionFlow&gt;</span><span class="sxs-lookup"><span data-stu-id="c02c1-102">&lt;transactionFlow&gt;</span></span>
<span data-ttu-id="c02c1-103">指定自訂繫結的交易流程支援。</span><span class="sxs-lookup"><span data-stu-id="c02c1-103">Specifies transaction flow support for the custom binding.</span></span>  
  
 <span data-ttu-id="c02c1-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="c02c1-104">\<system.serviceModel></span></span>  
<span data-ttu-id="c02c1-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="c02c1-105">\<bindings></span></span>  
<span data-ttu-id="c02c1-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="c02c1-106">\<customBinding></span></span>  
<span data-ttu-id="c02c1-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="c02c1-107">\<binding></span></span>  
<span data-ttu-id="c02c1-108">\<transactionFlow ></span><span class="sxs-lookup"><span data-stu-id="c02c1-108">\<transactionFlow></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c02c1-109">語法</span><span class="sxs-lookup"><span data-stu-id="c02c1-109">Syntax</span></span>  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c02c1-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c02c1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c02c1-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c02c1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c02c1-112">屬性</span><span class="sxs-lookup"><span data-stu-id="c02c1-112">Attributes</span></span>  
  
|<span data-ttu-id="c02c1-113">屬性</span><span class="sxs-lookup"><span data-stu-id="c02c1-113">Attribute</span></span>|<span data-ttu-id="c02c1-114">描述</span><span class="sxs-lookup"><span data-stu-id="c02c1-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c02c1-115">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="c02c1-115">transactionProtocol</span></span>|<span data-ttu-id="c02c1-116">指定要使用的交易通訊協定。</span><span class="sxs-lookup"><span data-stu-id="c02c1-116">Specifies the transaction protocol to be used.</span></span> <span data-ttu-id="c02c1-117">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="c02c1-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="c02c1-118">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="c02c1-118">-   OleTransactions</span></span><br /><span data-ttu-id="c02c1-119">-WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="c02c1-119">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="c02c1-120">預設值為 OleTransactions。</span><span class="sxs-lookup"><span data-stu-id="c02c1-120">The default is OleTransactions.</span></span><br /><br /> <span data-ttu-id="c02c1-121">此屬性的型別為 <xref:System.ServiceModel.TransactionProtocol>。</span><span class="sxs-lookup"><span data-stu-id="c02c1-121">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c02c1-122">子元素</span><span class="sxs-lookup"><span data-stu-id="c02c1-122">Child Elements</span></span>  
 <span data-ttu-id="c02c1-123">無。</span><span class="sxs-lookup"><span data-stu-id="c02c1-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c02c1-124">父項目</span><span class="sxs-lookup"><span data-stu-id="c02c1-124">Parent Elements</span></span>  
  
|<span data-ttu-id="c02c1-125">項目</span><span class="sxs-lookup"><span data-stu-id="c02c1-125">Element</span></span>|<span data-ttu-id="c02c1-126">說明</span><span class="sxs-lookup"><span data-stu-id="c02c1-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c02c1-127">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="c02c1-127">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="c02c1-128">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="c02c1-128">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c02c1-129">備註</span><span class="sxs-lookup"><span data-stu-id="c02c1-129">Remarks</span></span>  
 <span data-ttu-id="c02c1-130">這個項目可以讓您啟用或停用端點繫結設定的傳入交易流程，以及指定傳入交易的所需通訊協定格式。</span><span class="sxs-lookup"><span data-stu-id="c02c1-130">This element allows you to enable or disable incoming transaction flow in an endpoint’s binding settings, as well as to specify the desired protocol format for incoming transactions.</span></span> <span data-ttu-id="c02c1-131">如需有關如何使用這個組態項目的詳細資訊，請參閱[ServiceModel 異動組態](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md)和[啟用交易流程](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)。</span><span class="sxs-lookup"><span data-stu-id="c02c1-131">For more information on using this configuration element, see [ServiceModel Transaction Configuration](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md) and [Enabling Transaction Flow](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="c02c1-132">當使用 `OleTransactions` 通訊協定在端點之間流動交易時，如果目的端點嘗試使用任何 `OleTransactions` 以外的通訊協定再次流動時，交易逾時可能會遺失。</span><span class="sxs-lookup"><span data-stu-id="c02c1-132">When using the `OleTransactions` protocol to flow transactions from endpoint to endpoint, the transaction timeout can be lost if the destination endpoint attempts to flow again using any protocol other than `OleTransactions`.</span></span> <span data-ttu-id="c02c1-133">這會導致 OleTransactions 躍點後的所有下層節點比預期的時間更晚發生逾時。</span><span class="sxs-lookup"><span data-stu-id="c02c1-133">This can cause all down-level nodes after the OleTransactions hop to timeout later than expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c02c1-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c02c1-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TransactionFlowElement>  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="c02c1-135">ServiceModel 異動組態</span><span class="sxs-lookup"><span data-stu-id="c02c1-135">ServiceModel Transaction Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md)  
 [<span data-ttu-id="c02c1-136">啟用交易流程</span><span class="sxs-lookup"><span data-stu-id="c02c1-136">Enabling Transaction Flow</span></span>](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)  
 [<span data-ttu-id="c02c1-137">繫結</span><span class="sxs-lookup"><span data-stu-id="c02c1-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="c02c1-138">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="c02c1-138">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="c02c1-139">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="c02c1-139">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="c02c1-140">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="c02c1-140">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)

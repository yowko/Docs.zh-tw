---
title: '&lt;transactionFlow&gt;'
ms.date: 03/30/2017
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
ms.openlocfilehash: d8597a71a9b7afadba7565290085f491052e04d6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54622114"
---
# <a name="lttransactionflowgt"></a><span data-ttu-id="8ca83-102">&lt;transactionFlow&gt;</span><span class="sxs-lookup"><span data-stu-id="8ca83-102">&lt;transactionFlow&gt;</span></span>
<span data-ttu-id="8ca83-103">指定自訂繫結程序的異動流程支援。</span><span class="sxs-lookup"><span data-stu-id="8ca83-103">Specifies transaction flow support for the custom binding.</span></span>  
  
 <span data-ttu-id="8ca83-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="8ca83-104">\<system.serviceModel></span></span>  
<span data-ttu-id="8ca83-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="8ca83-105">\<bindings></span></span>  
<span data-ttu-id="8ca83-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="8ca83-106">\<customBinding></span></span>  
<span data-ttu-id="8ca83-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="8ca83-107">\<binding></span></span>  
<span data-ttu-id="8ca83-108">\<transactionFlow></span><span class="sxs-lookup"><span data-stu-id="8ca83-108">\<transactionFlow></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ca83-109">語法</span><span class="sxs-lookup"><span data-stu-id="8ca83-109">Syntax</span></span>  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8ca83-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8ca83-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8ca83-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="8ca83-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8ca83-112">屬性</span><span class="sxs-lookup"><span data-stu-id="8ca83-112">Attributes</span></span>  
  
|<span data-ttu-id="8ca83-113">屬性</span><span class="sxs-lookup"><span data-stu-id="8ca83-113">Attribute</span></span>|<span data-ttu-id="8ca83-114">描述</span><span class="sxs-lookup"><span data-stu-id="8ca83-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8ca83-115">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="8ca83-115">transactionProtocol</span></span>|<span data-ttu-id="8ca83-116">指定要使用的交易通訊協定。</span><span class="sxs-lookup"><span data-stu-id="8ca83-116">Specifies the transaction protocol to be used.</span></span> <span data-ttu-id="8ca83-117">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="8ca83-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="8ca83-118">-   OleTransactions</span><span class="sxs-lookup"><span data-stu-id="8ca83-118">-   OleTransactions</span></span><br /><span data-ttu-id="8ca83-119">-   WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="8ca83-119">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="8ca83-120">預設值為 OleTransactions。</span><span class="sxs-lookup"><span data-stu-id="8ca83-120">The default is OleTransactions.</span></span><br /><br /> <span data-ttu-id="8ca83-121">此屬性的型別為 <xref:System.ServiceModel.TransactionProtocol>。</span><span class="sxs-lookup"><span data-stu-id="8ca83-121">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8ca83-122">子元素</span><span class="sxs-lookup"><span data-stu-id="8ca83-122">Child Elements</span></span>  
 <span data-ttu-id="8ca83-123">無。</span><span class="sxs-lookup"><span data-stu-id="8ca83-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8ca83-124">父項目</span><span class="sxs-lookup"><span data-stu-id="8ca83-124">Parent Elements</span></span>  
  
|<span data-ttu-id="8ca83-125">項目</span><span class="sxs-lookup"><span data-stu-id="8ca83-125">Element</span></span>|<span data-ttu-id="8ca83-126">描述</span><span class="sxs-lookup"><span data-stu-id="8ca83-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8ca83-127">\<binding></span><span class="sxs-lookup"><span data-stu-id="8ca83-127">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="8ca83-128">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="8ca83-128">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ca83-129">備註</span><span class="sxs-lookup"><span data-stu-id="8ca83-129">Remarks</span></span>  
 <span data-ttu-id="8ca83-130">這個項目可以讓您啟用或停用端點繫結程序設定的傳入異動流程，以及指定傳入異動的所需通訊協定格式。</span><span class="sxs-lookup"><span data-stu-id="8ca83-130">This element allows you to enable or disable incoming transaction flow in an endpoint’s binding settings, as well as to specify the desired protocol format for incoming transactions.</span></span> <span data-ttu-id="8ca83-131">如需有關使用這個組態項的詳細資訊，請參閱[ServiceModel 異動組態](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md)並[啟用交易流程](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)。</span><span class="sxs-lookup"><span data-stu-id="8ca83-131">For more information on using this configuration element, see [ServiceModel Transaction Configuration](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md) and [Enabling Transaction Flow](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="8ca83-132">當使用 `OleTransactions` 通訊協定在端點之間流動異動時，如果目的端點嘗試使用任何 `OleTransactions` 以外的通訊協定再次流動時，異動逾時可能會遺失。</span><span class="sxs-lookup"><span data-stu-id="8ca83-132">When using the `OleTransactions` protocol to flow transactions from endpoint to endpoint, the transaction timeout can be lost if the destination endpoint attempts to flow again using any protocol other than `OleTransactions`.</span></span> <span data-ttu-id="8ca83-133">這會導致 OleTransactions 躍點後的所有下層節點比預期的時間更晚發生逾時。</span><span class="sxs-lookup"><span data-stu-id="8ca83-133">This can cause all down-level nodes after the OleTransactions hop to timeout later than expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ca83-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ca83-134">See also</span></span>
- <xref:System.ServiceModel.Configuration.TransactionFlowElement>
- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="8ca83-135">ServiceModel 異動組態</span><span class="sxs-lookup"><span data-stu-id="8ca83-135">ServiceModel Transaction Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md)
- [<span data-ttu-id="8ca83-136">啟用異動流程</span><span class="sxs-lookup"><span data-stu-id="8ca83-136">Enabling Transaction Flow</span></span>](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)
- [<span data-ttu-id="8ca83-137">繫結</span><span class="sxs-lookup"><span data-stu-id="8ca83-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="8ca83-138">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="8ca83-138">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="8ca83-139">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="8ca83-139">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="8ca83-140">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="8ca83-140">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)

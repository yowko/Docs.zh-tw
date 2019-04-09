---
title: <transactionFlow>
ms.date: 03/30/2017
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
ms.openlocfilehash: 626ae03d622221ab3e956bd03898b6cc30482c98
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59179149"
---
# <a name="transactionflow"></a><span data-ttu-id="e2ac4-101">\<transactionFlow></span><span class="sxs-lookup"><span data-stu-id="e2ac4-101">\<transactionFlow></span></span>
<span data-ttu-id="e2ac4-102">指定自訂繫結的交易流程支援。</span><span class="sxs-lookup"><span data-stu-id="e2ac4-102">Specifies transaction flow support for the custom binding.</span></span>  
  
 <span data-ttu-id="e2ac4-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e2ac4-103">\<system.serviceModel></span></span>  
<span data-ttu-id="e2ac4-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="e2ac4-104">\<bindings></span></span>  
<span data-ttu-id="e2ac4-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="e2ac4-105">\<customBinding></span></span>  
<span data-ttu-id="e2ac4-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="e2ac4-106">\<binding></span></span>  
<span data-ttu-id="e2ac4-107">\<transactionFlow></span><span class="sxs-lookup"><span data-stu-id="e2ac4-107">\<transactionFlow></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2ac4-108">語法</span><span class="sxs-lookup"><span data-stu-id="e2ac4-108">Syntax</span></span>  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e2ac4-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e2ac4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e2ac4-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e2ac4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e2ac4-111">屬性</span><span class="sxs-lookup"><span data-stu-id="e2ac4-111">Attributes</span></span>  
  
|<span data-ttu-id="e2ac4-112">屬性</span><span class="sxs-lookup"><span data-stu-id="e2ac4-112">Attribute</span></span>|<span data-ttu-id="e2ac4-113">描述</span><span class="sxs-lookup"><span data-stu-id="e2ac4-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e2ac4-114">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="e2ac4-114">transactionProtocol</span></span>|<span data-ttu-id="e2ac4-115">指定要使用的異動通訊協定。</span><span class="sxs-lookup"><span data-stu-id="e2ac4-115">Specifies the transaction protocol to be used.</span></span> <span data-ttu-id="e2ac4-116">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="e2ac4-116">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e2ac4-117">-   OleTransactions</span><span class="sxs-lookup"><span data-stu-id="e2ac4-117">-   OleTransactions</span></span><br /><span data-ttu-id="e2ac4-118">-   WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="e2ac4-118">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="e2ac4-119">預設值為 OleTransactions。</span><span class="sxs-lookup"><span data-stu-id="e2ac4-119">The default is OleTransactions.</span></span><br /><br /> <span data-ttu-id="e2ac4-120">此屬性的型別為 <xref:System.ServiceModel.TransactionProtocol>。</span><span class="sxs-lookup"><span data-stu-id="e2ac4-120">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e2ac4-121">子元素</span><span class="sxs-lookup"><span data-stu-id="e2ac4-121">Child Elements</span></span>  
 <span data-ttu-id="e2ac4-122">無。</span><span class="sxs-lookup"><span data-stu-id="e2ac4-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e2ac4-123">父項目</span><span class="sxs-lookup"><span data-stu-id="e2ac4-123">Parent Elements</span></span>  
  
|<span data-ttu-id="e2ac4-124">項目</span><span class="sxs-lookup"><span data-stu-id="e2ac4-124">Element</span></span>|<span data-ttu-id="e2ac4-125">描述</span><span class="sxs-lookup"><span data-stu-id="e2ac4-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e2ac4-126">\<binding></span><span class="sxs-lookup"><span data-stu-id="e2ac4-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="e2ac4-127">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="e2ac4-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2ac4-128">備註</span><span class="sxs-lookup"><span data-stu-id="e2ac4-128">Remarks</span></span>  
 <span data-ttu-id="e2ac4-129">這個項目可以讓您啟用或停用端點繫結設定的傳入交易流程，以及指定傳入交易的所需通訊協定格式。</span><span class="sxs-lookup"><span data-stu-id="e2ac4-129">This element allows you to enable or disable incoming transaction flow in an endpoint’s binding settings, as well as to specify the desired protocol format for incoming transactions.</span></span> <span data-ttu-id="e2ac4-130">如需有關使用這個組態項的詳細資訊，請參閱[ServiceModel 異動組態](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md)並[啟用交易流程](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)。</span><span class="sxs-lookup"><span data-stu-id="e2ac4-130">For more information on using this configuration element, see [ServiceModel Transaction Configuration](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md) and [Enabling Transaction Flow](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="e2ac4-131">當使用 `OleTransactions` 通訊協定在端點之間流動交易時，如果目的端點嘗試使用任何 `OleTransactions` 以外的通訊協定再次流動時，交易逾時可能會遺失。</span><span class="sxs-lookup"><span data-stu-id="e2ac4-131">When using the `OleTransactions` protocol to flow transactions from endpoint to endpoint, the transaction timeout can be lost if the destination endpoint attempts to flow again using any protocol other than `OleTransactions`.</span></span> <span data-ttu-id="e2ac4-132">這會導致 OleTransactions 躍點後的所有下層節點比預期的時間更晚發生逾時。</span><span class="sxs-lookup"><span data-stu-id="e2ac4-132">This can cause all down-level nodes after the OleTransactions hop to timeout later than expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2ac4-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2ac4-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactionFlowElement>
- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="e2ac4-134">ServiceModel 交易組態</span><span class="sxs-lookup"><span data-stu-id="e2ac4-134">ServiceModel Transaction Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md)
- [<span data-ttu-id="e2ac4-135">啟用交易流程</span><span class="sxs-lookup"><span data-stu-id="e2ac4-135">Enabling Transaction Flow</span></span>](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)
- [<span data-ttu-id="e2ac4-136">繫結</span><span class="sxs-lookup"><span data-stu-id="e2ac4-136">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="e2ac4-137">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="e2ac4-137">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="e2ac4-138">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="e2ac4-138">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="e2ac4-139">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="e2ac4-139">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)

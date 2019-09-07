---
title: <transactionFlow>
ms.date: 03/30/2017
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
ms.openlocfilehash: 8247dd62f4dda853487fe52f00f8f548b627c075
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399402"
---
# <a name="transactionflow"></a><span data-ttu-id="06dd5-101">\<transactionFlow></span><span class="sxs-lookup"><span data-stu-id="06dd5-101">\<transactionFlow></span></span>
<span data-ttu-id="06dd5-102">指定自訂繫結的交易流程支援。</span><span class="sxs-lookup"><span data-stu-id="06dd5-102">Specifies transaction flow support for the custom binding.</span></span>  
  
<span data-ttu-id="06dd5-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="06dd5-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="06dd5-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="06dd5-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="06dd5-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<系結 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="06dd5-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="06dd5-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="06dd5-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="06dd5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<系結 >** </span><span class="sxs-lookup"><span data-stu-id="06dd5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="06dd5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<transactionFlow >**</span><span class="sxs-lookup"><span data-stu-id="06dd5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transactionFlow>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06dd5-109">語法</span><span class="sxs-lookup"><span data-stu-id="06dd5-109">Syntax</span></span>  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="06dd5-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="06dd5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="06dd5-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="06dd5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="06dd5-112">屬性</span><span class="sxs-lookup"><span data-stu-id="06dd5-112">Attributes</span></span>  
  
|<span data-ttu-id="06dd5-113">屬性</span><span class="sxs-lookup"><span data-stu-id="06dd5-113">Attribute</span></span>|<span data-ttu-id="06dd5-114">說明</span><span class="sxs-lookup"><span data-stu-id="06dd5-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="06dd5-115">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="06dd5-115">transactionProtocol</span></span>|<span data-ttu-id="06dd5-116">指定要使用的異動通訊協定。</span><span class="sxs-lookup"><span data-stu-id="06dd5-116">Specifies the transaction protocol to be used.</span></span> <span data-ttu-id="06dd5-117">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="06dd5-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="06dd5-118">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="06dd5-118">-   OleTransactions</span></span><br /><span data-ttu-id="06dd5-119">-   WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="06dd5-119">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="06dd5-120">預設值為 OleTransactions。</span><span class="sxs-lookup"><span data-stu-id="06dd5-120">The default is OleTransactions.</span></span><br /><br /> <span data-ttu-id="06dd5-121">此屬性的型別為 <xref:System.ServiceModel.TransactionProtocol>。</span><span class="sxs-lookup"><span data-stu-id="06dd5-121">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="06dd5-122">子元素</span><span class="sxs-lookup"><span data-stu-id="06dd5-122">Child Elements</span></span>  
 <span data-ttu-id="06dd5-123">無。</span><span class="sxs-lookup"><span data-stu-id="06dd5-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="06dd5-124">父項目</span><span class="sxs-lookup"><span data-stu-id="06dd5-124">Parent Elements</span></span>  
  
|<span data-ttu-id="06dd5-125">項目</span><span class="sxs-lookup"><span data-stu-id="06dd5-125">Element</span></span>|<span data-ttu-id="06dd5-126">說明</span><span class="sxs-lookup"><span data-stu-id="06dd5-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="06dd5-127">\<binding></span><span class="sxs-lookup"><span data-stu-id="06dd5-127">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="06dd5-128">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="06dd5-128">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06dd5-129">備註</span><span class="sxs-lookup"><span data-stu-id="06dd5-129">Remarks</span></span>  
 <span data-ttu-id="06dd5-130">這個項目可以讓您啟用或停用端點繫結設定的傳入交易流程，以及指定傳入交易的所需通訊協定格式。</span><span class="sxs-lookup"><span data-stu-id="06dd5-130">This element allows you to enable or disable incoming transaction flow in an endpoint’s binding settings, as well as to specify the desired protocol format for incoming transactions.</span></span> <span data-ttu-id="06dd5-131">如需使用此設定元素的詳細資訊，請參閱[配置交易](../../../wcf/feature-details/servicemodel-transaction-configuration.md)設定和[啟用交易流程](../../../wcf/feature-details/enabling-transaction-flow.md)。</span><span class="sxs-lookup"><span data-stu-id="06dd5-131">For more information on using this configuration element, see [ServiceModel Transaction Configuration](../../../wcf/feature-details/servicemodel-transaction-configuration.md) and [Enabling Transaction Flow](../../../wcf/feature-details/enabling-transaction-flow.md).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="06dd5-132">當使用 `OleTransactions` 通訊協定在端點之間流動交易時，如果目的端點嘗試使用任何 `OleTransactions` 以外的通訊協定再次流動時，交易逾時可能會遺失。</span><span class="sxs-lookup"><span data-stu-id="06dd5-132">When using the `OleTransactions` protocol to flow transactions from endpoint to endpoint, the transaction timeout can be lost if the destination endpoint attempts to flow again using any protocol other than `OleTransactions`.</span></span> <span data-ttu-id="06dd5-133">這會導致 OleTransactions 躍點後的所有下層節點比預期的時間更晚發生逾時。</span><span class="sxs-lookup"><span data-stu-id="06dd5-133">This can cause all down-level nodes after the OleTransactions hop to timeout later than expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06dd5-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06dd5-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactionFlowElement>
- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="06dd5-135">ServiceModel 異動組態</span><span class="sxs-lookup"><span data-stu-id="06dd5-135">ServiceModel Transaction Configuration</span></span>](../../../wcf/feature-details/servicemodel-transaction-configuration.md)
- [<span data-ttu-id="06dd5-136">啟用異動流程</span><span class="sxs-lookup"><span data-stu-id="06dd5-136">Enabling Transaction Flow</span></span>](../../../wcf/feature-details/enabling-transaction-flow.md)
- [<span data-ttu-id="06dd5-137">繫結</span><span class="sxs-lookup"><span data-stu-id="06dd5-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="06dd5-138">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="06dd5-138">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="06dd5-139">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="06dd5-139">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="06dd5-140">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="06dd5-140">\<customBinding></span></span>](custombinding.md)

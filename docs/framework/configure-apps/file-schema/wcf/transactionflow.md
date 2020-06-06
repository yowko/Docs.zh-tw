---
title: <transactionFlow>
ms.date: 03/30/2017
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
ms.openlocfilehash: f5bcd142fb2b032ea179bcbba68fee53b98d2d77
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736311"
---
# \<transactionFlow>
<span data-ttu-id="d7dea-101">指定自訂繫結的交易流程支援。</span><span class="sxs-lookup"><span data-stu-id="d7dea-101">Specifies transaction flow support for the custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transactionFlow>**  
  
## <a name="syntax"></a><span data-ttu-id="d7dea-102">語法</span><span class="sxs-lookup"><span data-stu-id="d7dea-102">Syntax</span></span>  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d7dea-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d7dea-103">Attributes and Elements</span></span>  
 <span data-ttu-id="d7dea-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d7dea-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d7dea-105">屬性</span><span class="sxs-lookup"><span data-stu-id="d7dea-105">Attributes</span></span>  
  
|<span data-ttu-id="d7dea-106">屬性</span><span class="sxs-lookup"><span data-stu-id="d7dea-106">Attribute</span></span>|<span data-ttu-id="d7dea-107">描述</span><span class="sxs-lookup"><span data-stu-id="d7dea-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d7dea-108">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="d7dea-108">transactionProtocol</span></span>|<span data-ttu-id="d7dea-109">指定要使用的異動通訊協定。</span><span class="sxs-lookup"><span data-stu-id="d7dea-109">Specifies the transaction protocol to be used.</span></span> <span data-ttu-id="d7dea-110">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="d7dea-110">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="d7dea-111">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="d7dea-111">-   OleTransactions</span></span><br /><span data-ttu-id="d7dea-112">-WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="d7dea-112">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="d7dea-113">預設值為 OleTransactions。</span><span class="sxs-lookup"><span data-stu-id="d7dea-113">The default is OleTransactions.</span></span><br /><br /> <span data-ttu-id="d7dea-114">此屬性的型別為 <xref:System.ServiceModel.TransactionProtocol>。</span><span class="sxs-lookup"><span data-stu-id="d7dea-114">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d7dea-115">子元素</span><span class="sxs-lookup"><span data-stu-id="d7dea-115">Child Elements</span></span>  
 <span data-ttu-id="d7dea-116">無。</span><span class="sxs-lookup"><span data-stu-id="d7dea-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d7dea-117">父項目</span><span class="sxs-lookup"><span data-stu-id="d7dea-117">Parent Elements</span></span>  
  
|<span data-ttu-id="d7dea-118">元素</span><span class="sxs-lookup"><span data-stu-id="d7dea-118">Element</span></span>|<span data-ttu-id="d7dea-119">描述</span><span class="sxs-lookup"><span data-stu-id="d7dea-119">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="d7dea-120">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="d7dea-120">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7dea-121">備註</span><span class="sxs-lookup"><span data-stu-id="d7dea-121">Remarks</span></span>  
 <span data-ttu-id="d7dea-122">這個項目可以讓您啟用或停用端點繫結設定的傳入交易流程，以及指定傳入交易的所需通訊協定格式。</span><span class="sxs-lookup"><span data-stu-id="d7dea-122">This element allows you to enable or disable incoming transaction flow in an endpoint’s binding settings, as well as to specify the desired protocol format for incoming transactions.</span></span> <span data-ttu-id="d7dea-123">如需使用此設定元素的詳細資訊，請參閱[配置交易](../../../wcf/feature-details/servicemodel-transaction-configuration.md)設定和[啟用交易流程](../../../wcf/feature-details/enabling-transaction-flow.md)。</span><span class="sxs-lookup"><span data-stu-id="d7dea-123">For more information on using this configuration element, see [ServiceModel Transaction Configuration](../../../wcf/feature-details/servicemodel-transaction-configuration.md) and [Enabling Transaction Flow](../../../wcf/feature-details/enabling-transaction-flow.md).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="d7dea-124">當使用 `OleTransactions` 通訊協定在端點之間流動交易時，如果目的端點嘗試使用任何 `OleTransactions` 以外的通訊協定再次流動時，交易逾時可能會遺失。</span><span class="sxs-lookup"><span data-stu-id="d7dea-124">When using the `OleTransactions` protocol to flow transactions from endpoint to endpoint, the transaction timeout can be lost if the destination endpoint attempts to flow again using any protocol other than `OleTransactions`.</span></span> <span data-ttu-id="d7dea-125">這會導致 OleTransactions 躍點後的所有下層節點比預期的時間更晚發生逾時。</span><span class="sxs-lookup"><span data-stu-id="d7dea-125">This can cause all down-level nodes after the OleTransactions hop to timeout later than expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7dea-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7dea-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactionFlowElement>
- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="d7dea-127">ServiceModel 異動組態</span><span class="sxs-lookup"><span data-stu-id="d7dea-127">ServiceModel Transaction Configuration</span></span>](../../../wcf/feature-details/servicemodel-transaction-configuration.md)
- [<span data-ttu-id="d7dea-128">啟用交易流程</span><span class="sxs-lookup"><span data-stu-id="d7dea-128">Enabling Transaction Flow</span></span>](../../../wcf/feature-details/enabling-transaction-flow.md)
- [<span data-ttu-id="d7dea-129">繫結</span><span class="sxs-lookup"><span data-stu-id="d7dea-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d7dea-130">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="d7dea-130">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="d7dea-131">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="d7dea-131">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)

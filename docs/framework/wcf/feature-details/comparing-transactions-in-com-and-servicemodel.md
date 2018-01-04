---
title: "比較 COM+ 與 ServiceModel 的異動"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e493bcdd-b91a-4486-853f-83dbcd1931b7
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 87e3df31060a9c71e0b2868aa34373bca221fa79
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="comparing-transactions-in-com-and-servicemodel"></a><span data-ttu-id="f76c2-102">比較 COM+ 與 ServiceModel 的異動</span><span class="sxs-lookup"><span data-stu-id="f76c2-102">Comparing Transactions in COM+ and ServiceModel</span></span>
<span data-ttu-id="f76c2-103">這個主題會討論如何使用 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 命名空間提供的 <xref:System.ServiceModel> 屬性，來模擬交易 COM+ 服務的行為。</span><span class="sxs-lookup"><span data-stu-id="f76c2-103">This topic discusses how to simulate the behavior of a transactional COM+ service using the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] attributes the <xref:System.ServiceModel> namespace provides.</span></span>  
  
## <a name="emulating-com-using-servicemodel-attributes"></a><span data-ttu-id="f76c2-104">使用 ServiceModel 屬性模擬 COM+</span><span class="sxs-lookup"><span data-stu-id="f76c2-104">Emulating COM+ Using ServiceModel Attributes</span></span>  
 <span data-ttu-id="f76c2-105">下列表格會比較用來建立 <xref:System.EnterpriseServices.TransactionOption> 交易的 `EnterpriseServices` 列舉，以及如何與 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 命名空間提供的 <xref:System.ServiceModel> 屬性產生關聯。</span><span class="sxs-lookup"><span data-stu-id="f76c2-105">The following table compares the <xref:System.EnterpriseServices.TransactionOption> enumeration used to create an `EnterpriseServices` transaction and how they correlate to the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] attributes the <xref:System.ServiceModel> namespace provides.</span></span>  
  
|<span data-ttu-id="f76c2-106">COM+ 屬性</span><span class="sxs-lookup"><span data-stu-id="f76c2-106">COM+ attribute</span></span>|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f76c2-107"> 屬性</span><span class="sxs-lookup"><span data-stu-id="f76c2-107"> attributes</span></span>|  
|---------------------|------------------------------------------------------------------------|  
|<span data-ttu-id="f76c2-108">RequiresNew</span><span class="sxs-lookup"><span data-stu-id="f76c2-108">RequiresNew</span></span>|<span data-ttu-id="f76c2-109"><xref:System.ServiceModel.TransactionFlowAttribute> 設定為 <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>。</span><span class="sxs-lookup"><span data-stu-id="f76c2-109"><xref:System.ServiceModel.TransactionFlowAttribute> is set to <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>.</span></span><br /><br /> <span data-ttu-id="f76c2-110"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> 為 `true`。</span><span class="sxs-lookup"><span data-stu-id="f76c2-110"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> is `true`.</span></span><br /><br /> <span data-ttu-id="f76c2-111">繫結項目中的 `TransactionFlow` 屬性為 `false`。</span><span class="sxs-lookup"><span data-stu-id="f76c2-111">The `TransactionFlow` attribute in the binding element is `false`.</span></span>|  
|<span data-ttu-id="f76c2-112">必要項</span><span class="sxs-lookup"><span data-stu-id="f76c2-112">Required</span></span>|<span data-ttu-id="f76c2-113"><xref:System.ServiceModel.TransactionFlowAttribute> 設定為 <xref:System.ServiceModel.TransactionFlowOption.Allowed>。</span><span class="sxs-lookup"><span data-stu-id="f76c2-113"><xref:System.ServiceModel.TransactionFlowAttribute> is set to <xref:System.ServiceModel.TransactionFlowOption.Allowed>.</span></span><br /><br /> <span data-ttu-id="f76c2-114"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> 為 `true`。</span><span class="sxs-lookup"><span data-stu-id="f76c2-114"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> is `true`.</span></span><br /><br /> <span data-ttu-id="f76c2-115">繫結項目中的 `TransactionFlow` 屬性為 `true`。</span><span class="sxs-lookup"><span data-stu-id="f76c2-115">The `TransactionFlow` attribute in the binding element is `true`.</span></span>|  
|<span data-ttu-id="f76c2-116">支援</span><span class="sxs-lookup"><span data-stu-id="f76c2-116">Supported</span></span>|<span data-ttu-id="f76c2-117">沒有直接的對等項目。</span><span class="sxs-lookup"><span data-stu-id="f76c2-117">There is no direct equivalent.</span></span> <span data-ttu-id="f76c2-118">一般來說，您應該採用對 `Required` 所指定的行為。</span><span class="sxs-lookup"><span data-stu-id="f76c2-118">In general, you should adopt the behavior specified for `Required` instead.</span></span>|  
|<span data-ttu-id="f76c2-119">NotSupported</span><span class="sxs-lookup"><span data-stu-id="f76c2-119">NotSupported</span></span>|<span data-ttu-id="f76c2-120"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> 為 `false`。</span><span class="sxs-lookup"><span data-stu-id="f76c2-120"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> is `false`.</span></span><br /><br /> <span data-ttu-id="f76c2-121">繫結項目中的 `TransactionFlow` 屬性為 `false`。</span><span class="sxs-lookup"><span data-stu-id="f76c2-121">The `TransactionFlow` attribute in the binding element is `false`.</span></span>|  
|<span data-ttu-id="f76c2-122">已停用</span><span class="sxs-lookup"><span data-stu-id="f76c2-122">Disabled</span></span>|<span data-ttu-id="f76c2-123">沒有直接的對等項目。</span><span class="sxs-lookup"><span data-stu-id="f76c2-123">There is no direct equivalent.</span></span> <span data-ttu-id="f76c2-124">一般來說，您應該採用對 `NotSupported` 所指定的行為。</span><span class="sxs-lookup"><span data-stu-id="f76c2-124">In general, you should adopt the behavior specified for `NotSupported` instead.</span></span>|

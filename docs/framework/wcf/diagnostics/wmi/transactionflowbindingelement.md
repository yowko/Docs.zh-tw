---
title: TransactionFlowBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0b073efc47ccc1708bf4c58153b1001a21eee25f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="transactionflowbindingelement"></a><span data-ttu-id="098a7-102">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="098a7-102">TransactionFlowBindingElement</span></span>
<span data-ttu-id="098a7-103">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="098a7-103">TransactionFlowBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="098a7-104">語法</span><span class="sxs-lookup"><span data-stu-id="098a7-104">Syntax</span></span>  
  
```  
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="098a7-105">方法</span><span class="sxs-lookup"><span data-stu-id="098a7-105">Methods</span></span>  
 <span data-ttu-id="098a7-106">TransactionFlowBindingElement 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="098a7-106">The TransactionFlowBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="098a7-107">屬性</span><span class="sxs-lookup"><span data-stu-id="098a7-107">Properties</span></span>  
 <span data-ttu-id="098a7-108">TransactionFlowBindingElement 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="098a7-108">The TransactionFlowBindingElement class has the following properties:</span></span>  
  
### <a name="issuedtokens"></a><span data-ttu-id="098a7-109">IssuedTokens</span><span class="sxs-lookup"><span data-stu-id="098a7-109">IssuedTokens</span></span>  
 <span data-ttu-id="098a7-110">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="098a7-110">Data type: string</span></span>  
  
 <span data-ttu-id="098a7-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="098a7-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="098a7-112">指定所發行安全性權杖標頭 (WS-Trust 的 IssuedTokens) 的需求。</span><span class="sxs-lookup"><span data-stu-id="098a7-112">Specifies the requirement for an issued security tokens header (IssuedTokens from WS-Trust).</span></span>  
  
### <a name="transactionprotocol"></a><span data-ttu-id="098a7-113">TransactionProtocol</span><span class="sxs-lookup"><span data-stu-id="098a7-113">TransactionProtocol</span></span>  
 <span data-ttu-id="098a7-114">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="098a7-114">Data type: string</span></span>  
  
 <span data-ttu-id="098a7-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="098a7-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="098a7-116">服務用來使交易流動的交易通訊協定。</span><span class="sxs-lookup"><span data-stu-id="098a7-116">The transactions protocol used by the service to flow transactions.</span></span>  
  
### <a name="transactions"></a><span data-ttu-id="098a7-117">異動</span><span class="sxs-lookup"><span data-stu-id="098a7-117">Transactions</span></span>  
 <span data-ttu-id="098a7-118">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="098a7-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="098a7-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="098a7-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="098a7-120">代表是否支援傳入異動。</span><span class="sxs-lookup"><span data-stu-id="098a7-120">Indicates whether the incoming transaction is supported.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="098a7-121">需求</span><span class="sxs-lookup"><span data-stu-id="098a7-121">Requirements</span></span>  
  
|<span data-ttu-id="098a7-122">MOF</span><span class="sxs-lookup"><span data-stu-id="098a7-122">MOF</span></span>|<span data-ttu-id="098a7-123">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="098a7-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="098a7-124">命名空間</span><span class="sxs-lookup"><span data-stu-id="098a7-124">Namespace</span></span>|<span data-ttu-id="098a7-125">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="098a7-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="098a7-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="098a7-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>

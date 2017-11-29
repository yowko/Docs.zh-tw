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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4c65eb1689d1411cb9083967b9a29c946b7568b7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="transactionflowbindingelement"></a><span data-ttu-id="6c422-102">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="6c422-102">TransactionFlowBindingElement</span></span>
<span data-ttu-id="6c422-103">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="6c422-103">TransactionFlowBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c422-104">語法</span><span class="sxs-lookup"><span data-stu-id="6c422-104">Syntax</span></span>  
  
```  
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="6c422-105">方法</span><span class="sxs-lookup"><span data-stu-id="6c422-105">Methods</span></span>  
 <span data-ttu-id="6c422-106">TransactionFlowBindingElement 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="6c422-106">The TransactionFlowBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="6c422-107">屬性</span><span class="sxs-lookup"><span data-stu-id="6c422-107">Properties</span></span>  
 <span data-ttu-id="6c422-108">TransactionFlowBindingElement 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="6c422-108">The TransactionFlowBindingElement class has the following properties:</span></span>  
  
### <a name="issuedtokens"></a><span data-ttu-id="6c422-109">IssuedTokens</span><span class="sxs-lookup"><span data-stu-id="6c422-109">IssuedTokens</span></span>  
 <span data-ttu-id="6c422-110">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="6c422-110">Data type: string</span></span>  
  
 <span data-ttu-id="6c422-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="6c422-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6c422-112">指定所發行安全性權杖標頭 (WS-Trust 的 IssuedTokens) 的需求。</span><span class="sxs-lookup"><span data-stu-id="6c422-112">Specifies the requirement for an issued security tokens header (IssuedTokens from WS-Trust).</span></span>  
  
### <a name="transactionprotocol"></a><span data-ttu-id="6c422-113">TransactionProtocol</span><span class="sxs-lookup"><span data-stu-id="6c422-113">TransactionProtocol</span></span>  
 <span data-ttu-id="6c422-114">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="6c422-114">Data type: string</span></span>  
  
 <span data-ttu-id="6c422-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="6c422-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6c422-116">服務用來使交易流動的交易通訊協定。</span><span class="sxs-lookup"><span data-stu-id="6c422-116">The transactions protocol used by the service to flow transactions.</span></span>  
  
### <a name="transactions"></a><span data-ttu-id="6c422-117">異動</span><span class="sxs-lookup"><span data-stu-id="6c422-117">Transactions</span></span>  
 <span data-ttu-id="6c422-118">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="6c422-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="6c422-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="6c422-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6c422-120">代表是否支援傳入交易。</span><span class="sxs-lookup"><span data-stu-id="6c422-120">Indicates whether the incoming transaction is supported.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c422-121">需求</span><span class="sxs-lookup"><span data-stu-id="6c422-121">Requirements</span></span>  
  
|<span data-ttu-id="6c422-122">MOF</span><span class="sxs-lookup"><span data-stu-id="6c422-122">MOF</span></span>|<span data-ttu-id="6c422-123">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="6c422-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="6c422-124">命名空間</span><span class="sxs-lookup"><span data-stu-id="6c422-124">Namespace</span></span>|<span data-ttu-id="6c422-125">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="6c422-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6c422-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c422-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>

---
title: OperationBehaviorAttribute
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8c9b0755-9e83-411f-bdcb-61a586022797
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fd01c5c4d37f5c0ec5673dc9aa4a47cb8affbc29
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="operationbehaviorattribute"></a><span data-ttu-id="310e3-102">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="310e3-102">OperationBehaviorAttribute</span></span>
<span data-ttu-id="310e3-103">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="310e3-103">OperationBehaviorAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="310e3-104">語法</span><span class="sxs-lookup"><span data-stu-id="310e3-104">Syntax</span></span>  
  
```  
class OperationBehaviorAttribute : Behavior  
{  
  boolean AutoDisposeParameters;  
  string Impersonation;  
  string ReleaseInstanceMode;  
  boolean TransactionAutoComplete;  
  boolean TransactionScopeRequired;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="310e3-105">方法</span><span class="sxs-lookup"><span data-stu-id="310e3-105">Methods</span></span>  
 <span data-ttu-id="310e3-106">OperationBehaviorAttribute 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="310e3-106">The OperationBehaviorAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="310e3-107">屬性</span><span class="sxs-lookup"><span data-stu-id="310e3-107">Properties</span></span>  
 <span data-ttu-id="310e3-108">OperationBehaviorAttribute 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="310e3-108">The OperationBehaviorAttribute class has the following properties:</span></span>  
  
### <a name="autodisposeparameters"></a><span data-ttu-id="310e3-109">AutoDisposeParameters</span><span class="sxs-lookup"><span data-stu-id="310e3-109">AutoDisposeParameters</span></span>  
 <span data-ttu-id="310e3-110">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="310e3-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="310e3-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="310e3-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="310e3-112">參數自動處置功能的狀態。</span><span class="sxs-lookup"><span data-stu-id="310e3-112">The state of the auto-dispose feature for parameters.</span></span>  
  
### <a name="impersonation"></a><span data-ttu-id="310e3-113">模擬</span><span class="sxs-lookup"><span data-stu-id="310e3-113">Impersonation</span></span>  
 <span data-ttu-id="310e3-114">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="310e3-114">Data type: string</span></span>  
  
 <span data-ttu-id="310e3-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="310e3-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="310e3-116">表示作業支援的呼叫端模擬等級。</span><span class="sxs-lookup"><span data-stu-id="310e3-116">Indicates the level of caller impersonation that the operation supports.</span></span>  
  
### <a name="releaseinstancemode"></a><span data-ttu-id="310e3-117">ReleaseInstanceMode</span><span class="sxs-lookup"><span data-stu-id="310e3-117">ReleaseInstanceMode</span></span>  
 <span data-ttu-id="310e3-118">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="310e3-118">Data type: string</span></span>  
  
 <span data-ttu-id="310e3-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="310e3-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="310e3-120">表示在作業引動過程當中要回收物件的時機。</span><span class="sxs-lookup"><span data-stu-id="310e3-120">Indicates when in the course of an operation invocation to recycle the object.</span></span>  
  
### <a name="transactionautocomplete"></a><span data-ttu-id="310e3-121">TransactionAutoComplete</span><span class="sxs-lookup"><span data-stu-id="310e3-121">TransactionAutoComplete</span></span>  
 <span data-ttu-id="310e3-122">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="310e3-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="310e3-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="310e3-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="310e3-124">表示未發生未處理的例外狀況時是否要自動認可目前的交易。</span><span class="sxs-lookup"><span data-stu-id="310e3-124">Indicates whether to automatically commit the current transaction if no unhandled exceptions occur.</span></span>  
  
### <a name="transactionscoperequired"></a><span data-ttu-id="310e3-125">TransactionScopeRequired</span><span class="sxs-lookup"><span data-stu-id="310e3-125">TransactionScopeRequired</span></span>  
 <span data-ttu-id="310e3-126">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="310e3-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="310e3-127">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="310e3-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="310e3-128">表示作業是否需要交易。</span><span class="sxs-lookup"><span data-stu-id="310e3-128">Indicates whether the operation requires a transaction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="310e3-129">需求</span><span class="sxs-lookup"><span data-stu-id="310e3-129">Requirements</span></span>  
  
|<span data-ttu-id="310e3-130">MOF</span><span class="sxs-lookup"><span data-stu-id="310e3-130">MOF</span></span>|<span data-ttu-id="310e3-131">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="310e3-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="310e3-132">命名空間</span><span class="sxs-lookup"><span data-stu-id="310e3-132">Namespace</span></span>|<span data-ttu-id="310e3-133">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="310e3-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="310e3-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="310e3-134">See Also</span></span>  
 <xref:System.ServiceModel.OperationBehaviorAttribute>

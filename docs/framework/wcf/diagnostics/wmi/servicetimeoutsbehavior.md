---
title: ServiceTimeoutsBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4412525d-a3cc-4eae-b3e8-a50ce766d09d
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a65104a6fe76c22fca308091cc02e9496912129c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="servicetimeoutsbehavior"></a><span data-ttu-id="58b6b-102">ServiceTimeoutsBehavior</span><span class="sxs-lookup"><span data-stu-id="58b6b-102">ServiceTimeoutsBehavior</span></span>
<span data-ttu-id="58b6b-103">ServiceTimeoutsBehavior</span><span class="sxs-lookup"><span data-stu-id="58b6b-103">ServiceTimeoutsBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58b6b-104">語法</span><span class="sxs-lookup"><span data-stu-id="58b6b-104">Syntax</span></span>  
  
```  
class ServiceTimeoutsBehavior : Behavior  
{  
  datetime TransactionTimeout;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="58b6b-105">方法</span><span class="sxs-lookup"><span data-stu-id="58b6b-105">Methods</span></span>  
 <span data-ttu-id="58b6b-106">ServiceTimeoutsBehavior 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="58b6b-106">The ServiceTimeoutsBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="58b6b-107">屬性</span><span class="sxs-lookup"><span data-stu-id="58b6b-107">Properties</span></span>  
 <span data-ttu-id="58b6b-108">ServiceTimeoutsBehavior 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="58b6b-108">The ServiceTimeoutsBehavior class has the following property:</span></span>  
  
### <a name="transactiontimeout"></a><span data-ttu-id="58b6b-109">TransactionTimeout</span><span class="sxs-lookup"><span data-stu-id="58b6b-109">TransactionTimeout</span></span>  
 <span data-ttu-id="58b6b-110">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="58b6b-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="58b6b-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="58b6b-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="58b6b-112">交易必須完成的期間。</span><span class="sxs-lookup"><span data-stu-id="58b6b-112">The period within which a transaction must complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58b6b-113">需求</span><span class="sxs-lookup"><span data-stu-id="58b6b-113">Requirements</span></span>  
  
|<span data-ttu-id="58b6b-114">MOF</span><span class="sxs-lookup"><span data-stu-id="58b6b-114">MOF</span></span>|<span data-ttu-id="58b6b-115">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="58b6b-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="58b6b-116">命名空間</span><span class="sxs-lookup"><span data-stu-id="58b6b-116">Namespace</span></span>|<span data-ttu-id="58b6b-117">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="58b6b-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="58b6b-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58b6b-118">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>

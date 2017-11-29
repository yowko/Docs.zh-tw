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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d4b597dbdd8dfea1cab35c717f416d91677c5987
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="servicetimeoutsbehavior"></a><span data-ttu-id="4ad56-102">ServiceTimeoutsBehavior</span><span class="sxs-lookup"><span data-stu-id="4ad56-102">ServiceTimeoutsBehavior</span></span>
<span data-ttu-id="4ad56-103">ServiceTimeoutsBehavior</span><span class="sxs-lookup"><span data-stu-id="4ad56-103">ServiceTimeoutsBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ad56-104">語法</span><span class="sxs-lookup"><span data-stu-id="4ad56-104">Syntax</span></span>  
  
```  
class ServiceTimeoutsBehavior : Behavior  
{  
  datetime TransactionTimeout;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="4ad56-105">方法</span><span class="sxs-lookup"><span data-stu-id="4ad56-105">Methods</span></span>  
 <span data-ttu-id="4ad56-106">ServiceTimeoutsBehavior 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="4ad56-106">The ServiceTimeoutsBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4ad56-107">屬性</span><span class="sxs-lookup"><span data-stu-id="4ad56-107">Properties</span></span>  
 <span data-ttu-id="4ad56-108">ServiceTimeoutsBehavior 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="4ad56-108">The ServiceTimeoutsBehavior class has the following property:</span></span>  
  
### <a name="transactiontimeout"></a><span data-ttu-id="4ad56-109">TransactionTimeout</span><span class="sxs-lookup"><span data-stu-id="4ad56-109">TransactionTimeout</span></span>  
 <span data-ttu-id="4ad56-110">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="4ad56-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="4ad56-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="4ad56-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4ad56-112">交易必須完成的期間。</span><span class="sxs-lookup"><span data-stu-id="4ad56-112">The period within which a transaction must complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ad56-113">需求</span><span class="sxs-lookup"><span data-stu-id="4ad56-113">Requirements</span></span>  
  
|<span data-ttu-id="4ad56-114">MOF</span><span class="sxs-lookup"><span data-stu-id="4ad56-114">MOF</span></span>|<span data-ttu-id="4ad56-115">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="4ad56-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4ad56-116">命名空間</span><span class="sxs-lookup"><span data-stu-id="4ad56-116">Namespace</span></span>|<span data-ttu-id="4ad56-117">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="4ad56-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4ad56-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ad56-118">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>

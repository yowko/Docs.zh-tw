---
title: "StackOverflowType 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StackOverflowType
api_location: mscoree.dll
api_type: COM
f1_keywords: StackOverflowType
helpviewer_keywords: StackOverflowType enumeration [.NET Framework hosting]
ms.assetid: dab648ad-972b-479c-b129-b4c1dcbd932e
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a04db61a16aeae24476fb0b191a3d2dc89743dee
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="stackoverflowtype-enumeration"></a><span data-ttu-id="0d04b-102">StackOverflowType 列舉</span><span class="sxs-lookup"><span data-stu-id="0d04b-102">StackOverflowType Enumeration</span></span>
<span data-ttu-id="0d04b-103">包含值，表示造成堆疊溢位事件的根本原因。</span><span class="sxs-lookup"><span data-stu-id="0d04b-103">Contains values that indicate the underlying cause of a stack overflow event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d04b-104">語法</span><span class="sxs-lookup"><span data-stu-id="0d04b-104">Syntax</span></span>  
  
```  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a><span data-ttu-id="0d04b-105">成員</span><span class="sxs-lookup"><span data-stu-id="0d04b-105">Members</span></span>  
  
|<span data-ttu-id="0d04b-106">成員</span><span class="sxs-lookup"><span data-stu-id="0d04b-106">Member</span></span>|<span data-ttu-id="0d04b-107">描述</span><span class="sxs-lookup"><span data-stu-id="0d04b-107">Description</span></span>|  
|------------|-----------------|  
|`SO_ClrEngine`|<span data-ttu-id="0d04b-108">堆疊溢位是由執行引擎所造成的。</span><span class="sxs-lookup"><span data-stu-id="0d04b-108">The stack overflow was caused by the execution engine.</span></span>|  
|`SO_Managed`|<span data-ttu-id="0d04b-109">堆疊溢位所造成的 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="0d04b-109">The stack overflow was caused by managed code.</span></span>|  
|`SO_Other`|<span data-ttu-id="0d04b-110">堆疊溢位是 unmanaged 程式碼所造成。</span><span class="sxs-lookup"><span data-stu-id="0d04b-110">The stack overflow was caused by unmanaged code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d04b-111">備註</span><span class="sxs-lookup"><span data-stu-id="0d04b-111">Remarks</span></span>  
 <span data-ttu-id="0d04b-112">這項資訊透過呼叫傳遞至主機[iactiononclrevent:: Onevent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="0d04b-112">This information is passed to the host through a call to the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d04b-113">需求</span><span class="sxs-lookup"><span data-stu-id="0d04b-113">Requirements</span></span>  
 <span data-ttu-id="0d04b-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0d04b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d04b-115">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0d04b-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0d04b-116">**程式庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0d04b-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0d04b-117">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d04b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d04b-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="0d04b-118">See Also</span></span>  
 [<span data-ttu-id="0d04b-119">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="0d04b-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

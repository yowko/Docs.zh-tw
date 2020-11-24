---
title: EContextType 列舉
ms.date: 03/30/2017
api_name:
- EContextType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EContextType
helpviewer_keywords:
- EContextType enumeration [.NET Framework hosting]
ms.assetid: 92b926a9-b87e-408a-9036-df7b752c9492
topic_type:
- apiref
ms.openlocfilehash: c6d1ace12bd07fa1f14c8570eca1f950a5c22be9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686328"
---
# <a name="econtexttype-enumeration"></a><span data-ttu-id="7a3c9-102">EContextType 列舉</span><span class="sxs-lookup"><span data-stu-id="7a3c9-102">EContextType Enumeration</span></span>

<span data-ttu-id="7a3c9-103">描述目前執行中線程的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="7a3c9-103">Describes the security context of the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a3c9-104">語法</span><span class="sxs-lookup"><span data-stu-id="7a3c9-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eCurrentContext    = 0x00,  
    eRestrictedContext = 0x01  
} EContextType;  
```  
  
## <a name="members"></a><span data-ttu-id="7a3c9-105">成員</span><span class="sxs-lookup"><span data-stu-id="7a3c9-105">Members</span></span>  
  
|<span data-ttu-id="7a3c9-106">member</span><span class="sxs-lookup"><span data-stu-id="7a3c9-106">Member</span></span>|<span data-ttu-id="7a3c9-107">描述</span><span class="sxs-lookup"><span data-stu-id="7a3c9-107">Description</span></span>|  
|------------|-----------------|  
|`eCurrentContext`|<span data-ttu-id="7a3c9-108">指出 common language runtime (CLR) 呼叫 [IHostSecurityManager：： GetSecurityCoNtext](ihostsecuritymanager-getsecuritycontext-method.md) 方法，或呼叫 [IHostSecurityManager：： SetSecurityCoNtext](ihostsecuritymanager-setsecuritycontext-method.md) 方法時，clr 所要求的內容在目前線程上的內容。</span><span class="sxs-lookup"><span data-stu-id="7a3c9-108">Indicates the context on the current thread at the time the common language runtime (CLR) calls the [IHostSecurityManager::GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md) method, or the context requested by the CLR in a call to the [IHostSecurityManager::SetSecurityContext](ihostsecuritymanager-setsecuritycontext-method.md) method.</span></span>|  
|`eRestrictedContext`|<span data-ttu-id="7a3c9-109">指出主機具有較低許可權的內容，例如垃圾收集行程，或類別或模組的函式。</span><span class="sxs-lookup"><span data-stu-id="7a3c9-109">Indicates a context over which the host has lower privileges, such as the garbage collector, or class or module constructors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7a3c9-110">備註</span><span class="sxs-lookup"><span data-stu-id="7a3c9-110">Remarks</span></span>  

 <span data-ttu-id="7a3c9-111">CLR 會 `EContextType` 在呼叫和方法時，將其中一個值作為參數值 `IHostSecurityManager::GetSecurityContext` 提供 `IHostSecurityManager::SetSecurityContext` 。</span><span class="sxs-lookup"><span data-stu-id="7a3c9-111">The CLR supplies one of the `EContextType` values as a parameter value in calls to the `IHostSecurityManager::GetSecurityContext` and `IHostSecurityManager::SetSecurityContext` methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a3c9-112">需求</span><span class="sxs-lookup"><span data-stu-id="7a3c9-112">Requirements</span></span>  

 <span data-ttu-id="7a3c9-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7a3c9-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a3c9-114">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="7a3c9-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7a3c9-115">連結 **庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7a3c9-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7a3c9-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a3c9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a3c9-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a3c9-117">See also</span></span>

- [<span data-ttu-id="7a3c9-118">IHostSecurityContext 介面</span><span class="sxs-lookup"><span data-stu-id="7a3c9-118">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="7a3c9-119">IHostSecurityManager 介面</span><span class="sxs-lookup"><span data-stu-id="7a3c9-119">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="7a3c9-120">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="7a3c9-120">Hosting Enumerations</span></span>](hosting-enumerations.md)

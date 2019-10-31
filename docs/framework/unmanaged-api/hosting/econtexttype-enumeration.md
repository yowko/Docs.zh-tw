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
ms.openlocfilehash: 5e82f542bdc364a52fc558e582134a7d8d554ec3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131150"
---
# <a name="econtexttype-enumeration"></a><span data-ttu-id="37fe0-102">EContextType 列舉</span><span class="sxs-lookup"><span data-stu-id="37fe0-102">EContextType Enumeration</span></span>
<span data-ttu-id="37fe0-103">描述目前執行中線程的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="37fe0-103">Describes the security context of the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37fe0-104">語法</span><span class="sxs-lookup"><span data-stu-id="37fe0-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eCurrentContext    = 0x00,  
    eRestrictedContext = 0x01  
} EContextType;  
```  
  
## <a name="members"></a><span data-ttu-id="37fe0-105">Members</span><span class="sxs-lookup"><span data-stu-id="37fe0-105">Members</span></span>  
  
|<span data-ttu-id="37fe0-106">成員</span><span class="sxs-lookup"><span data-stu-id="37fe0-106">Member</span></span>|<span data-ttu-id="37fe0-107">描述</span><span class="sxs-lookup"><span data-stu-id="37fe0-107">Description</span></span>|  
|------------|-----------------|  
|`eCurrentContext`|<span data-ttu-id="37fe0-108">指出當 common language runtime （CLR）呼叫[IHostSecurityManager：： GetSecurityCoNtext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)方法時，或 clr 要求的內容呼叫[IHostSecurityManager：： SetSecurityCoNtext 時，目前線程上的內容](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="37fe0-108">Indicates the context on the current thread at the time the common language runtime (CLR) calls the [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md) method, or the context requested by the CLR in a call to the [IHostSecurityManager::SetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md) method.</span></span>|  
|`eRestrictedContext`|<span data-ttu-id="37fe0-109">表示主機具有較低許可權的內容，例如垃圾收集行程或類別或模組的處理常式。</span><span class="sxs-lookup"><span data-stu-id="37fe0-109">Indicates a context over which the host has lower privileges, such as the garbage collector, or class or module constructors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37fe0-110">備註</span><span class="sxs-lookup"><span data-stu-id="37fe0-110">Remarks</span></span>  
 <span data-ttu-id="37fe0-111">CLR 會在呼叫 `IHostSecurityManager::GetSecurityContext` 和 `IHostSecurityManager::SetSecurityContext` 方法時，提供其中一個 `EContextType` 值做為參數值。</span><span class="sxs-lookup"><span data-stu-id="37fe0-111">The CLR supplies one of the `EContextType` values as a parameter value in calls to the `IHostSecurityManager::GetSecurityContext` and `IHostSecurityManager::SetSecurityContext` methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37fe0-112">需求</span><span class="sxs-lookup"><span data-stu-id="37fe0-112">Requirements</span></span>  
 <span data-ttu-id="37fe0-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="37fe0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37fe0-114">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="37fe0-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="37fe0-115">連結**庫：** Mscoree.dll .dll</span><span class="sxs-lookup"><span data-stu-id="37fe0-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="37fe0-116">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37fe0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37fe0-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="37fe0-117">See also</span></span>

- [<span data-ttu-id="37fe0-118">IHostSecurityContext 介面</span><span class="sxs-lookup"><span data-stu-id="37fe0-118">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="37fe0-119">IHostSecurityManager 介面</span><span class="sxs-lookup"><span data-stu-id="37fe0-119">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="37fe0-120">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="37fe0-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

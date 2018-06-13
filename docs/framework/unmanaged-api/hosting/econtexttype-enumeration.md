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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a261d9164e8714531eab1fe9fc8148304e6d5bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432878"
---
# <a name="econtexttype-enumeration"></a><span data-ttu-id="4f17c-102">EContextType 列舉</span><span class="sxs-lookup"><span data-stu-id="4f17c-102">EContextType Enumeration</span></span>
<span data-ttu-id="4f17c-103">描述目前執行中執行緒的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="4f17c-103">Describes the security context of the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f17c-104">語法</span><span class="sxs-lookup"><span data-stu-id="4f17c-104">Syntax</span></span>  
  
```  
typedef enum {  
    eCurrentContext    = 0x00,  
    eRestrictedContext = 0x01  
} EContextType;  
```  
  
## <a name="members"></a><span data-ttu-id="4f17c-105">成員</span><span class="sxs-lookup"><span data-stu-id="4f17c-105">Members</span></span>  
  
|<span data-ttu-id="4f17c-106">成員</span><span class="sxs-lookup"><span data-stu-id="4f17c-106">Member</span></span>|<span data-ttu-id="4f17c-107">描述</span><span class="sxs-lookup"><span data-stu-id="4f17c-107">Description</span></span>|  
|------------|-----------------|  
|`eCurrentContext`|<span data-ttu-id="4f17c-108">指出目前的執行緒上的內容時，common language runtime (CLR) 呼叫[ihostsecuritymanager:: Getsecuritycontext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)方法或呼叫中的 CLR 所要求的內容[Ihostsecuritymanager:: Setsecuritycontext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="4f17c-108">Indicates the context on the current thread at the time the common language runtime (CLR) calls the [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md) method, or the context requested by the CLR in a call to the [IHostSecurityManager::SetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md) method.</span></span>|  
|`eRestrictedContext`|<span data-ttu-id="4f17c-109">指出哪些主機具有較低權限，例如記憶體回收行程或類別或模組的建構函式的內容。</span><span class="sxs-lookup"><span data-stu-id="4f17c-109">Indicates a context over which the host has lower privileges, such as the garbage collector, or class or module constructors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f17c-110">備註</span><span class="sxs-lookup"><span data-stu-id="4f17c-110">Remarks</span></span>  
 <span data-ttu-id="4f17c-111">CLR 提供的其中一個`EContextType`值做為參數值，在呼叫`IHostSecurityManager::GetSecurityContext`和`IHostSecurityManager::SetSecurityContext`方法。</span><span class="sxs-lookup"><span data-stu-id="4f17c-111">The CLR supplies one of the `EContextType` values as a parameter value in calls to the `IHostSecurityManager::GetSecurityContext` and `IHostSecurityManager::SetSecurityContext` methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f17c-112">需求</span><span class="sxs-lookup"><span data-stu-id="4f17c-112">Requirements</span></span>  
 <span data-ttu-id="4f17c-113">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4f17c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f17c-114">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4f17c-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4f17c-115">**程式庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4f17c-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4f17c-116">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f17c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f17c-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f17c-117">See Also</span></span>  
 [<span data-ttu-id="4f17c-118">IHostSecurityContext 介面</span><span class="sxs-lookup"><span data-stu-id="4f17c-118">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="4f17c-119">IHostSecurityManager 介面</span><span class="sxs-lookup"><span data-stu-id="4f17c-119">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 [<span data-ttu-id="4f17c-120">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="4f17c-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

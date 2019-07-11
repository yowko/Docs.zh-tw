---
title: EClrFailure 列舉
ms.date: 03/30/2017
api_name:
- EClrFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrFailure
helpviewer_keywords:
- EClrFailure enumeration [.NET Framework hosting]
ms.assetid: 37b95cce-9bfb-4ecf-a00b-33dcba782c67
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5f3e39d94996f14f1ae6593b9adaa5db3ef674c5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769661"
---
# <a name="eclrfailure-enumeration"></a><span data-ttu-id="f7bd0-102">EClrFailure 列舉</span><span class="sxs-lookup"><span data-stu-id="f7bd0-102">EClrFailure Enumeration</span></span>
<span data-ttu-id="f7bd0-103">描述的主機可以設定的原則動作失敗。</span><span class="sxs-lookup"><span data-stu-id="f7bd0-103">Describes the set of failures for which a host can set policy actions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7bd0-104">語法</span><span class="sxs-lookup"><span data-stu-id="f7bd0-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    FAIL_NonCriticalResource,  
    FAIL_CriticalResource,  
    FAIL_FatalRuntime,  
    FAIL_OrphanedLock  
    FAIL_StackOverflow  
    FAIL_AccessViolation  
    FAIL_CodeContract  
} EClrFailure;  
```  
  
## <a name="members"></a><span data-ttu-id="f7bd0-105">成員</span><span class="sxs-lookup"><span data-stu-id="f7bd0-105">Members</span></span>  
  
|<span data-ttu-id="f7bd0-106">成員</span><span class="sxs-lookup"><span data-stu-id="f7bd0-106">Member</span></span>|<span data-ttu-id="f7bd0-107">描述</span><span class="sxs-lookup"><span data-stu-id="f7bd0-107">Description</span></span>|  
|------------|-----------------|  
|`FAIL_NonCriticalResource`|<span data-ttu-id="f7bd0-108">嘗試配置的資源 （例如執行緒、 記憶體、 區塊或鎖定） 期間發生非關鍵的程式碼區域中的失敗。</span><span class="sxs-lookup"><span data-stu-id="f7bd0-108">A failure occurred during an attempt to allocate a resource (such as a thread, a block of memory, or a lock) in a non-critical region of code.</span></span>|  
|`FAIL_CriticalResource`|<span data-ttu-id="f7bd0-109">在關鍵區域的程式碼中，嘗試配置的資源 （例如執行緒、 記憶體、 區塊或鎖定） 期間發生失敗。</span><span class="sxs-lookup"><span data-stu-id="f7bd0-109">A failure occurred during an attempt to allocate a resource (such as a thread, a block of memory, or a lock) in a critical region of code.</span></span>|  
|`FAIL_FatalRuntime`|<span data-ttu-id="f7bd0-110">Common language runtime (CLR) 已不再能夠執行程序中的 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="f7bd0-110">The common language runtime (CLR) is no longer able to run managed code in the process.</span></span> <span data-ttu-id="f7bd0-111">從此以後，任何裝載的函式的呼叫會傳回 HOST_E_CLRNOTAVAILABLE HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="f7bd0-111">Henceforth, calls to any hosting functions return an HRESULT value of HOST_E_CLRNOTAVAILABLE.</span></span>|  
|`FAIL_OrphanedLock`|<span data-ttu-id="f7bd0-112">執行緒無法釋放鎖定時<xref:System.AppDomain>物件。</span><span class="sxs-lookup"><span data-stu-id="f7bd0-112">A thread has failed to release a lock upon returning from an <xref:System.AppDomain> object.</span></span> <span data-ttu-id="f7bd0-113">主應用程式無法設定此失敗會造成執行緒中止。</span><span class="sxs-lookup"><span data-stu-id="f7bd0-113">The host cannot set this failure to cause a thread to abort.</span></span>|  
|`FAIL_StackOverflow`|<span data-ttu-id="f7bd0-114">發生堆疊溢位。</span><span class="sxs-lookup"><span data-stu-id="f7bd0-114">A stack overflow has occurred.</span></span>|  
|`FAIL_AccessViolation`|<span data-ttu-id="f7bd0-115">嘗試讀取或寫入受保護的記憶體。</span><span class="sxs-lookup"><span data-stu-id="f7bd0-115">An attempt was made to read or write protected memory.</span></span> <span data-ttu-id="f7bd0-116">不支援在.NET Framework 4。</span><span class="sxs-lookup"><span data-stu-id="f7bd0-116">Not supported in the .NET Framework 4.</span></span>|  
|`FAIL_CodeContract`|<span data-ttu-id="f7bd0-117">程式碼合約失敗。</span><span class="sxs-lookup"><span data-stu-id="f7bd0-117">A code contract failure occurred.</span></span> <span data-ttu-id="f7bd0-118">請參閱[程式碼合約](../../../../docs/framework/debug-trace-profile/code-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="f7bd0-118">See [Code Contracts](../../../../docs/framework/debug-trace-profile/code-contracts.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7bd0-119">備註</span><span class="sxs-lookup"><span data-stu-id="f7bd0-119">Remarks</span></span>  
 <span data-ttu-id="f7bd0-120">請參閱[iclrpolicymanager:: Setactiononfailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)方法，取得一份[EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)主應用程式可用來指定原則動作失敗狀況的值。</span><span class="sxs-lookup"><span data-stu-id="f7bd0-120">See the [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) method for a list of [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values the host can use to specify the policy actions for failure conditions.</span></span> <span data-ttu-id="f7bd0-121">程式碼的重大和非關鍵區域的相關資訊，請參閱[EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="f7bd0-121">For more information about critical and non-critical regions of code, see [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7bd0-122">需求</span><span class="sxs-lookup"><span data-stu-id="f7bd0-122">Requirements</span></span>  
 <span data-ttu-id="f7bd0-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f7bd0-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7bd0-124">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f7bd0-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f7bd0-125">**LIBRARY:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f7bd0-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f7bd0-126">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7bd0-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7bd0-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7bd0-127">See also</span></span>

- [<span data-ttu-id="f7bd0-128">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="f7bd0-128">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="f7bd0-129">SetActionOnFailure 方法</span><span class="sxs-lookup"><span data-stu-id="f7bd0-129">SetActionOnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)
- [<span data-ttu-id="f7bd0-130">IHostPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="f7bd0-130">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [<span data-ttu-id="f7bd0-131">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="f7bd0-131">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

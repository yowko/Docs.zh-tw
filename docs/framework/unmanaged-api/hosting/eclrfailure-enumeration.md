---
title: "EClrFailure 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EClrFailure
api_location: mscoree.dll
api_type: COM
f1_keywords: EClrFailure
helpviewer_keywords: EClrFailure enumeration [.NET Framework hosting]
ms.assetid: 37b95cce-9bfb-4ecf-a00b-33dcba782c67
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e25a5378349dd476321765bb085db958e29670e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="eclrfailure-enumeration"></a><span data-ttu-id="96459-102">EClrFailure 列舉</span><span class="sxs-lookup"><span data-stu-id="96459-102">EClrFailure Enumeration</span></span>
<span data-ttu-id="96459-103">描述的主機可以設定原則動作失敗。</span><span class="sxs-lookup"><span data-stu-id="96459-103">Describes the set of failures for which a host can set policy actions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96459-104">語法</span><span class="sxs-lookup"><span data-stu-id="96459-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="96459-105">成員</span><span class="sxs-lookup"><span data-stu-id="96459-105">Members</span></span>  
  
|<span data-ttu-id="96459-106">成員</span><span class="sxs-lookup"><span data-stu-id="96459-106">Member</span></span>|<span data-ttu-id="96459-107">描述</span><span class="sxs-lookup"><span data-stu-id="96459-107">Description</span></span>|  
|------------|-----------------|  
|`FAIL_NonCriticalResource`|<span data-ttu-id="96459-108">嘗試配置的資源 （例如執行緒、 記憶體區塊或鎖定） 期間發生非關鍵的程式碼區域中的失敗。</span><span class="sxs-lookup"><span data-stu-id="96459-108">A failure occurred during an attempt to allocate a resource (such as a thread, a block of memory, or a lock) in a non-critical region of code.</span></span>|  
|`FAIL_CriticalResource`|<span data-ttu-id="96459-109">關鍵程式碼區域中，嘗試配置的資源 （例如執行緒、 記憶體區塊或鎖定） 期間發生失敗。</span><span class="sxs-lookup"><span data-stu-id="96459-109">A failure occurred during an attempt to allocate a resource (such as a thread, a block of memory, or a lock) in a critical region of code.</span></span>|  
|`FAIL_FatalRuntime`|<span data-ttu-id="96459-110">Common language runtime (CLR) 已不再能夠以 managed 程式碼執行處理程序。</span><span class="sxs-lookup"><span data-stu-id="96459-110">The common language runtime (CLR) is no longer able to run managed code in the process.</span></span> <span data-ttu-id="96459-111">從此以後，用於裝載函式的呼叫傳回 HOST_E_CLRNOTAVAILABLE 的 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="96459-111">Henceforth, calls to any hosting functions return an HRESULT value of HOST_E_CLRNOTAVAILABLE.</span></span>|  
|`FAIL_OrphanedLock`|<span data-ttu-id="96459-112">執行緒無法釋放鎖定時<xref:System.AppDomain>物件。</span><span class="sxs-lookup"><span data-stu-id="96459-112">A thread has failed to release a lock upon returning from an <xref:System.AppDomain> object.</span></span> <span data-ttu-id="96459-113">主機無法設定此失敗會導致中止的執行緒。</span><span class="sxs-lookup"><span data-stu-id="96459-113">The host cannot set this failure to cause a thread to abort.</span></span>|  
|`FAIL_StackOverflow`|<span data-ttu-id="96459-114">發生堆疊溢位。</span><span class="sxs-lookup"><span data-stu-id="96459-114">A stack overflow has occurred.</span></span>|  
|`FAIL_AccessViolation`|<span data-ttu-id="96459-115">嘗試讀取或寫入受保護的記憶體。</span><span class="sxs-lookup"><span data-stu-id="96459-115">An attempt was made to read or write protected memory.</span></span> <span data-ttu-id="96459-116">不支援[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="96459-116">Not supported in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>|  
|`FAIL_CodeContract`|<span data-ttu-id="96459-117">程式碼合約失敗。</span><span class="sxs-lookup"><span data-stu-id="96459-117">A code contract failure occurred.</span></span> <span data-ttu-id="96459-118">請參閱[程式碼合約](../../../../docs/framework/debug-trace-profile/code-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="96459-118">See [Code Contracts](../../../../docs/framework/debug-trace-profile/code-contracts.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96459-119">備註</span><span class="sxs-lookup"><span data-stu-id="96459-119">Remarks</span></span>  
 <span data-ttu-id="96459-120">請參閱[iclrpolicymanager:: Setactiononfailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)方法取得一份[EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)主應用程式可用來指定原則動作失敗狀況的值。</span><span class="sxs-lookup"><span data-stu-id="96459-120">See the [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) method for a list of [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values the host can use to specify the policy actions for failure conditions.</span></span> <span data-ttu-id="96459-121">程式碼的重大和非關鍵區域的相關資訊，請參閱[EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="96459-121">For more information about critical and non-critical regions of code, see [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96459-122">需求</span><span class="sxs-lookup"><span data-stu-id="96459-122">Requirements</span></span>  
 <span data-ttu-id="96459-123">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="96459-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96459-124">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="96459-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="96459-125">**程式庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="96459-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="96459-126">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96459-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96459-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="96459-127">See Also</span></span>  
 [<span data-ttu-id="96459-128">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="96459-128">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="96459-129">SetActionOnFailure 方法</span><span class="sxs-lookup"><span data-stu-id="96459-129">SetActionOnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)  
 [<span data-ttu-id="96459-130">IHostPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="96459-130">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [<span data-ttu-id="96459-131">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="96459-131">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

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
ms.openlocfilehash: d2794b53ed17640413928b3af0d1ed3656e25f22
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675759"
---
# <a name="eclrfailure-enumeration"></a><span data-ttu-id="ada25-102">EClrFailure 列舉</span><span class="sxs-lookup"><span data-stu-id="ada25-102">EClrFailure Enumeration</span></span>

<span data-ttu-id="ada25-103">描述主機可以設定原則動作的失敗集。</span><span class="sxs-lookup"><span data-stu-id="ada25-103">Describes the set of failures for which a host can set policy actions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ada25-104">語法</span><span class="sxs-lookup"><span data-stu-id="ada25-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="ada25-105">成員</span><span class="sxs-lookup"><span data-stu-id="ada25-105">Members</span></span>  
  
|<span data-ttu-id="ada25-106">member</span><span class="sxs-lookup"><span data-stu-id="ada25-106">Member</span></span>|<span data-ttu-id="ada25-107">描述</span><span class="sxs-lookup"><span data-stu-id="ada25-107">Description</span></span>|  
|------------|-----------------|  
|`FAIL_NonCriticalResource`|<span data-ttu-id="ada25-108">嘗試在非關鍵性的程式碼區域中配置資源 (（例如執行緒、記憶體區塊或鎖定) ）時發生失敗。</span><span class="sxs-lookup"><span data-stu-id="ada25-108">A failure occurred during an attempt to allocate a resource (such as a thread, a block of memory, or a lock) in a non-critical region of code.</span></span>|  
|`FAIL_CriticalResource`|<span data-ttu-id="ada25-109">嘗試在程式碼的關鍵區域中配置資源 (（例如執行緒、記憶體區塊或鎖定) ）時發生失敗。</span><span class="sxs-lookup"><span data-stu-id="ada25-109">A failure occurred during an attempt to allocate a resource (such as a thread, a block of memory, or a lock) in a critical region of code.</span></span>|  
|`FAIL_FatalRuntime`|<span data-ttu-id="ada25-110">Common language runtime (CLR) 不再能夠在進程中執行 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="ada25-110">The common language runtime (CLR) is no longer able to run managed code in the process.</span></span> <span data-ttu-id="ada25-111">因而需要，對任何裝載函數的呼叫都會傳回 HOST_E_CLRNOTAVAILABLE 的 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="ada25-111">Henceforth, calls to any hosting functions return an HRESULT value of HOST_E_CLRNOTAVAILABLE.</span></span>|  
|`FAIL_OrphanedLock`|<span data-ttu-id="ada25-112">執行緒無法在從物件傳回時解除鎖定 <xref:System.AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="ada25-112">A thread has failed to release a lock upon returning from an <xref:System.AppDomain> object.</span></span> <span data-ttu-id="ada25-113">主機無法設定此失敗，導致執行緒中止。</span><span class="sxs-lookup"><span data-stu-id="ada25-113">The host cannot set this failure to cause a thread to abort.</span></span>|  
|`FAIL_StackOverflow`|<span data-ttu-id="ada25-114">發生堆疊溢位。</span><span class="sxs-lookup"><span data-stu-id="ada25-114">A stack overflow has occurred.</span></span>|  
|`FAIL_AccessViolation`|<span data-ttu-id="ada25-115">嘗試讀取或寫入受保護的記憶體。</span><span class="sxs-lookup"><span data-stu-id="ada25-115">An attempt was made to read or write protected memory.</span></span> <span data-ttu-id="ada25-116">.NET Framework 4 不支援。</span><span class="sxs-lookup"><span data-stu-id="ada25-116">Not supported in the .NET Framework 4.</span></span>|  
|`FAIL_CodeContract`|<span data-ttu-id="ada25-117">發生程式碼合約失敗。</span><span class="sxs-lookup"><span data-stu-id="ada25-117">A code contract failure occurred.</span></span> <span data-ttu-id="ada25-118">請參閱程式 [代碼合約](../../debug-trace-profile/code-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="ada25-118">See [Code Contracts](../../debug-trace-profile/code-contracts.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ada25-119">備註</span><span class="sxs-lookup"><span data-stu-id="ada25-119">Remarks</span></span>  

 <span data-ttu-id="ada25-120">請參閱 [ICLRPolicyManager：： SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) 方法，以取得可供主機用來指定失敗狀況之原則動作的 [EPolicyAction](epolicyaction-enumeration.md) 值清單。</span><span class="sxs-lookup"><span data-stu-id="ada25-120">See the [ICLRPolicyManager::SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) method for a list of [EPolicyAction](epolicyaction-enumeration.md) values the host can use to specify the policy actions for failure conditions.</span></span> <span data-ttu-id="ada25-121">如需程式碼的關鍵和非關鍵區域的詳細資訊，請參閱 [EClrOperation](eclroperation-enumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="ada25-121">For more information about critical and non-critical regions of code, see [EClrOperation](eclroperation-enumeration.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ada25-122">需求</span><span class="sxs-lookup"><span data-stu-id="ada25-122">Requirements</span></span>  

 <span data-ttu-id="ada25-123">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ada25-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ada25-124">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="ada25-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ada25-125">連結 **庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ada25-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ada25-126">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ada25-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ada25-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ada25-127">See also</span></span>

- [<span data-ttu-id="ada25-128">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="ada25-128">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="ada25-129">SetActionOnFailure 方法</span><span class="sxs-lookup"><span data-stu-id="ada25-129">SetActionOnFailure Method</span></span>](iclrpolicymanager-setactiononfailure-method.md)
- [<span data-ttu-id="ada25-130">IHostPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="ada25-130">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
- [<span data-ttu-id="ada25-131">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="ada25-131">Hosting Enumerations</span></span>](hosting-enumerations.md)

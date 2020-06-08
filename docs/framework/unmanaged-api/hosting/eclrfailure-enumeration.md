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
ms.openlocfilehash: fa2b5052a1d569487f0c6c72699ff9ab571beefc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504390"
---
# <a name="eclrfailure-enumeration"></a><span data-ttu-id="bcc1c-102">EClrFailure 列舉</span><span class="sxs-lookup"><span data-stu-id="bcc1c-102">EClrFailure Enumeration</span></span>
<span data-ttu-id="bcc1c-103">描述主機可以設定原則動作的失敗集。</span><span class="sxs-lookup"><span data-stu-id="bcc1c-103">Describes the set of failures for which a host can set policy actions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcc1c-104">語法</span><span class="sxs-lookup"><span data-stu-id="bcc1c-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="bcc1c-105">成員</span><span class="sxs-lookup"><span data-stu-id="bcc1c-105">Members</span></span>  
  
|<span data-ttu-id="bcc1c-106">成員</span><span class="sxs-lookup"><span data-stu-id="bcc1c-106">Member</span></span>|<span data-ttu-id="bcc1c-107">說明</span><span class="sxs-lookup"><span data-stu-id="bcc1c-107">Description</span></span>|  
|------------|-----------------|  
|`FAIL_NonCriticalResource`|<span data-ttu-id="bcc1c-108">嘗試在不重要的程式碼區域中配置資源（例如執行緒、記憶體區塊或鎖定）時發生失敗。</span><span class="sxs-lookup"><span data-stu-id="bcc1c-108">A failure occurred during an attempt to allocate a resource (such as a thread, a block of memory, or a lock) in a non-critical region of code.</span></span>|  
|`FAIL_CriticalResource`|<span data-ttu-id="bcc1c-109">嘗試在程式碼的關鍵區域中配置資源（例如執行緒、記憶體區塊或鎖定）時發生失敗。</span><span class="sxs-lookup"><span data-stu-id="bcc1c-109">A failure occurred during an attempt to allocate a resource (such as a thread, a block of memory, or a lock) in a critical region of code.</span></span>|  
|`FAIL_FatalRuntime`|<span data-ttu-id="bcc1c-110">Common language runtime （CLR）不再能夠在進程中執行 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="bcc1c-110">The common language runtime (CLR) is no longer able to run managed code in the process.</span></span> <span data-ttu-id="bcc1c-111">因而需要，對任何裝載函數的呼叫都會傳回 HRESULT 值 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="bcc1c-111">Henceforth, calls to any hosting functions return an HRESULT value of HOST_E_CLRNOTAVAILABLE.</span></span>|  
|`FAIL_OrphanedLock`|<span data-ttu-id="bcc1c-112">執行緒無法在從物件傳回時釋放鎖定 <xref:System.AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="bcc1c-112">A thread has failed to release a lock upon returning from an <xref:System.AppDomain> object.</span></span> <span data-ttu-id="bcc1c-113">主機無法設定此失敗，導致執行緒中止。</span><span class="sxs-lookup"><span data-stu-id="bcc1c-113">The host cannot set this failure to cause a thread to abort.</span></span>|  
|`FAIL_StackOverflow`|<span data-ttu-id="bcc1c-114">發生堆疊溢位。</span><span class="sxs-lookup"><span data-stu-id="bcc1c-114">A stack overflow has occurred.</span></span>|  
|`FAIL_AccessViolation`|<span data-ttu-id="bcc1c-115">嘗試讀取或寫入受保護的記憶體。</span><span class="sxs-lookup"><span data-stu-id="bcc1c-115">An attempt was made to read or write protected memory.</span></span> <span data-ttu-id="bcc1c-116">在 .NET Framework 4 中不支援。</span><span class="sxs-lookup"><span data-stu-id="bcc1c-116">Not supported in the .NET Framework 4.</span></span>|  
|`FAIL_CodeContract`|<span data-ttu-id="bcc1c-117">發生程式碼合約失敗。</span><span class="sxs-lookup"><span data-stu-id="bcc1c-117">A code contract failure occurred.</span></span> <span data-ttu-id="bcc1c-118">請參閱程式[代碼合約](../../debug-trace-profile/code-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="bcc1c-118">See [Code Contracts](../../debug-trace-profile/code-contracts.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bcc1c-119">備註</span><span class="sxs-lookup"><span data-stu-id="bcc1c-119">Remarks</span></span>  
 <span data-ttu-id="bcc1c-120">請參閱[ICLRPolicyManager：： SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md)方法，以取得可供主機用來指定失敗狀況之原則動作的[EPolicyAction](epolicyaction-enumeration.md)值清單。</span><span class="sxs-lookup"><span data-stu-id="bcc1c-120">See the [ICLRPolicyManager::SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) method for a list of [EPolicyAction](epolicyaction-enumeration.md) values the host can use to specify the policy actions for failure conditions.</span></span> <span data-ttu-id="bcc1c-121">如需程式碼重要和非關鍵區域的詳細資訊，請參閱[EClrOperation](eclroperation-enumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="bcc1c-121">For more information about critical and non-critical regions of code, see [EClrOperation](eclroperation-enumeration.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bcc1c-122">規格需求</span><span class="sxs-lookup"><span data-stu-id="bcc1c-122">Requirements</span></span>  
 <span data-ttu-id="bcc1c-123">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bcc1c-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bcc1c-124">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="bcc1c-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bcc1c-125">連結**庫：** Mscoree.dll .dll</span><span class="sxs-lookup"><span data-stu-id="bcc1c-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bcc1c-126">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bcc1c-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcc1c-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bcc1c-127">See also</span></span>

- [<span data-ttu-id="bcc1c-128">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="bcc1c-128">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="bcc1c-129">SetActionOnFailure 方法</span><span class="sxs-lookup"><span data-stu-id="bcc1c-129">SetActionOnFailure Method</span></span>](iclrpolicymanager-setactiononfailure-method.md)
- [<span data-ttu-id="bcc1c-130">IHostPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="bcc1c-130">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
- [<span data-ttu-id="bcc1c-131">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="bcc1c-131">Hosting Enumerations</span></span>](hosting-enumerations.md)

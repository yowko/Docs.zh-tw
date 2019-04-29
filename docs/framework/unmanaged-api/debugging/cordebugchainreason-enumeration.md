---
title: CorDebugChainReason 列舉
ms.date: 03/30/2017
api_name:
- CorDebugChainReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugChainReason
helpviewer_keywords:
- CorDebugChainReason enumeration [.NET Framework debugging]
ms.assetid: c915da51-50b2-41df-841a-2b971f4d0975
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cac790ebbf25ee3095db293ba90612be37fff9b9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61609226"
---
# <a name="cordebugchainreason-enumeration"></a><span data-ttu-id="77dc0-102">CorDebugChainReason 列舉</span><span class="sxs-lookup"><span data-stu-id="77dc0-102">CorDebugChainReason Enumeration</span></span>
<span data-ttu-id="77dc0-103">指出呼叫鏈結初始化的原因。</span><span class="sxs-lookup"><span data-stu-id="77dc0-103">Indicates the reason or reasons for the initiation of a call chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77dc0-104">語法</span><span class="sxs-lookup"><span data-stu-id="77dc0-104">Syntax</span></span>  
  
```  
typedef enum CorDebugChainReason {  
    CHAIN_NONE              = 0x000,  
    CHAIN_CLASS_INIT        = 0x001,  
    CHAIN_EXCEPTION_FILTER  = 0x002,  
    CHAIN_SECURITY          = 0x004,  
    CHAIN_CONTEXT_POLICY    = 0x008,  
    CHAIN_INTERCEPTION      = 0x010,  
    CHAIN_PROCESS_START     = 0x020,  
    CHAIN_THREAD_START      = 0x040,  
    CHAIN_ENTER_MANAGED     = 0x080,  
    CHAIN_ENTER_UNMANAGED   = 0x100,  
    CHAIN_DEBUGGER_EVAL     = 0x200,  
    CHAIN_CONTEXT_SWITCH    = 0x400,  
    CHAIN_FUNC_EVAL         = 0x800  
} CorDebugChainReason;  
```  
  
## <a name="members"></a><span data-ttu-id="77dc0-105">成員</span><span class="sxs-lookup"><span data-stu-id="77dc0-105">Members</span></span>  
  
|<span data-ttu-id="77dc0-106">成員</span><span class="sxs-lookup"><span data-stu-id="77dc0-106">Member</span></span>|<span data-ttu-id="77dc0-107">描述</span><span class="sxs-lookup"><span data-stu-id="77dc0-107">Description</span></span>|  
|------------|-----------------|  
|`CHAIN_NONE`|<span data-ttu-id="77dc0-108">未起始任何呼叫鏈結。</span><span class="sxs-lookup"><span data-stu-id="77dc0-108">No call chain has been initiated.</span></span>|  
|`CHAIN_CLASS_INIT`|<span data-ttu-id="77dc0-109">鏈結是由建構函式所起始。</span><span class="sxs-lookup"><span data-stu-id="77dc0-109">The chain was initiated by a constructor.</span></span>|  
|`CHAIN_EXCEPTION_FILTER`|<span data-ttu-id="77dc0-110">鏈結是由例外狀況篩選條件所起始。</span><span class="sxs-lookup"><span data-stu-id="77dc0-110">The chain was initiated by an exception filter.</span></span>|  
|`CHAIN_SECURITY`|<span data-ttu-id="77dc0-111">鏈結是由強制執行安全性的程式碼所起始。</span><span class="sxs-lookup"><span data-stu-id="77dc0-111">The chain was initiated by code that enforces security.</span></span>|  
|`CHAIN_CONTEXT_POLICY`|<span data-ttu-id="77dc0-112">鏈結是由內容原則所起始。</span><span class="sxs-lookup"><span data-stu-id="77dc0-112">The chain was initiated by a context policy.</span></span>|  
|`CHAIN_INTERCEPTION`|<span data-ttu-id="77dc0-113">未使用。</span><span class="sxs-lookup"><span data-stu-id="77dc0-113">Not used.</span></span>|  
|`CHAIN_PROCESS_START`|<span data-ttu-id="77dc0-114">未使用。</span><span class="sxs-lookup"><span data-stu-id="77dc0-114">Not used.</span></span>|  
|`CHAIN_THREAD_START`|<span data-ttu-id="77dc0-115">鏈結是由執行緒執行開始所起始。</span><span class="sxs-lookup"><span data-stu-id="77dc0-115">The chain was initiated by the start of a thread execution.</span></span>|  
|`CHAIN_ENTER_MANAGED`|<span data-ttu-id="77dc0-116">鏈結是由進入 Managed 程式碼的項目所起始。</span><span class="sxs-lookup"><span data-stu-id="77dc0-116">The chain was initiated by entry into managed code.</span></span>|  
|`CHAIN_ENTER_UNMANAGED`|<span data-ttu-id="77dc0-117">鏈結是由進入 Unmanaged 程式碼的項目所起始。</span><span class="sxs-lookup"><span data-stu-id="77dc0-117">The chain was initiated by entry into unmanaged code.</span></span>|  
|`CHAIN_DEBUGGER_EVAL`|<span data-ttu-id="77dc0-118">未使用。</span><span class="sxs-lookup"><span data-stu-id="77dc0-118">Not used.</span></span>|  
|`CHAIN_CONTEXT_SWITCH`|<span data-ttu-id="77dc0-119">未使用。</span><span class="sxs-lookup"><span data-stu-id="77dc0-119">Not used.</span></span>|  
|`CHAIN_FUNC_EVAL`|<span data-ttu-id="77dc0-120">鏈結是由函式評估所起始。</span><span class="sxs-lookup"><span data-stu-id="77dc0-120">The chain was initiated by a function evaluation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77dc0-121">備註</span><span class="sxs-lookup"><span data-stu-id="77dc0-121">Remarks</span></span>  
 <span data-ttu-id="77dc0-122">使用[icordebugchain:: Getreason](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md)方法來確定呼叫鏈結的起始原因。</span><span class="sxs-lookup"><span data-stu-id="77dc0-122">Use the [ICorDebugChain::GetReason](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md) method to ascertain the reasons for the initiation of a call chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77dc0-123">需求</span><span class="sxs-lookup"><span data-stu-id="77dc0-123">Requirements</span></span>  
 <span data-ttu-id="77dc0-124">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="77dc0-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77dc0-125">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="77dc0-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="77dc0-126">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="77dc0-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77dc0-127">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77dc0-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77dc0-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77dc0-128">See also</span></span>

- [<span data-ttu-id="77dc0-129">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="77dc0-129">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

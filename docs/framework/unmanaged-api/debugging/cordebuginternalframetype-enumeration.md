---
title: CorDebugInternalFrameType 列舉
ms.date: 03/30/2017
api_name:
- CorDebugInternalFrameType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugInternalFrameType
helpviewer_keywords:
- CorDebugInternalFrameType enumeration [.NET Framework debugging]
ms.assetid: e4412dc2-c338-4cfb-94d8-f682095dd2b1
topic_type:
- apiref
ms.openlocfilehash: 1c94e03aa088d8f48eb7f7a418cebd0492319513
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696592"
---
# <a name="cordebuginternalframetype-enumeration"></a><span data-ttu-id="938ff-102">CorDebugInternalFrameType 列舉</span><span class="sxs-lookup"><span data-stu-id="938ff-102">CorDebugInternalFrameType Enumeration</span></span>

<span data-ttu-id="938ff-103">識別堆疊框架的類型。</span><span class="sxs-lookup"><span data-stu-id="938ff-103">Identifies the type of stack frame.</span></span> <span data-ttu-id="938ff-104">此列舉是由 [ICorDebugInternalFrame：： GetFrameType](icordebuginternalframe-getframetype-method.md) 方法所使用。</span><span class="sxs-lookup"><span data-stu-id="938ff-104">This enumeration is used by the [ICorDebugInternalFrame::GetFrameType](icordebuginternalframe-getframetype-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="938ff-105">語法</span><span class="sxs-lookup"><span data-stu-id="938ff-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugInternalFrameType {  
  
    STUBFRAME_NONE                 = 0x00000000,  
    STUBFRAME_M2U                  = 0x00000001,  
    STUBFRAME_U2M                  = 0x00000002,  
    STUBFRAME_APPDOMAIN_TRANSITION = 0x00000003,  
    STUBFRAME_LIGHTWEIGHT_FUNCTION = 0x00000004,  
    STUBFRAME_FUNC_EVAL            = 0x00000005,  
    STUBFRAME_INTERNALCALL         = 0x00000006,  
    STUBFRAME_CLASS_INIT           = 0x00000007,  
    STUBFRAME_EXCEPTION            = 0x00000008,  
    STUBFRAME_SECURITY             = 0x00000009,  
    STUBFRAME_JIT_COMPILATION     = 0x0000000a,  
} CorDebugInternalFrameType;  
```  
  
## <a name="members"></a><span data-ttu-id="938ff-106">成員</span><span class="sxs-lookup"><span data-stu-id="938ff-106">Members</span></span>  
  
|<span data-ttu-id="938ff-107">member</span><span class="sxs-lookup"><span data-stu-id="938ff-107">Member</span></span>|<span data-ttu-id="938ff-108">描述</span><span class="sxs-lookup"><span data-stu-id="938ff-108">Description</span></span>|  
|------------|-----------------|  
|`STUBFRAME_NONE`|<span data-ttu-id="938ff-109">null 值。</span><span class="sxs-lookup"><span data-stu-id="938ff-109">A null value.</span></span> <span data-ttu-id="938ff-110">`ICorDebugInternalFrame::GetFrameType`方法永遠不會傳回此值。</span><span class="sxs-lookup"><span data-stu-id="938ff-110">The `ICorDebugInternalFrame::GetFrameType` method never returns this value.</span></span>|  
|`STUBFRAME_M2U`|<span data-ttu-id="938ff-111">受管理的非受控存根框架。</span><span class="sxs-lookup"><span data-stu-id="938ff-111">A managed-to-unmanaged stub frame.</span></span>|  
|`STUBFRAME_U2M`|<span data-ttu-id="938ff-112">未受管理的存根框架。</span><span class="sxs-lookup"><span data-stu-id="938ff-112">An unmanaged-to-managed stub frame.</span></span>|  
|`STUBFRAME_APPDOMAIN_TRANSITION`|<span data-ttu-id="938ff-113">應用程式域之間的轉換。</span><span class="sxs-lookup"><span data-stu-id="938ff-113">A transition between application domains.</span></span>|  
|`STUBFRAME_LIGHTWEIGHT_FUNCTION`|<span data-ttu-id="938ff-114">輕量方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="938ff-114">A lightweight method call.</span></span>|  
|`STUBFRAME_FUNC_EVAL`|<span data-ttu-id="938ff-115">函數評估的開始。</span><span class="sxs-lookup"><span data-stu-id="938ff-115">The start of function evaluation.</span></span>|  
|`STUBFRAME_INTERNALCALL`|<span data-ttu-id="938ff-116">Common language runtime 的內部呼叫。</span><span class="sxs-lookup"><span data-stu-id="938ff-116">An internal call into the common language runtime.</span></span>|  
|`STUBFRAME_CLASS_INIT`|<span data-ttu-id="938ff-117">類別初始化的開始。</span><span class="sxs-lookup"><span data-stu-id="938ff-117">The start of a class initialization.</span></span>|  
|`STUBFRAME_EXCEPTION`|<span data-ttu-id="938ff-118">擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="938ff-118">An exception that is thrown.</span></span>|  
|`STUBFRAME_SECURITY`|<span data-ttu-id="938ff-119">用於代碼啟用安全性的框架。</span><span class="sxs-lookup"><span data-stu-id="938ff-119">A frame used for code access security.</span></span>|  
|`STUBFRAME_JIT_COMPILATION`|<span data-ttu-id="938ff-120">執行時間會以 JIT 方式編譯方法。</span><span class="sxs-lookup"><span data-stu-id="938ff-120">The runtime is JIT-compiling a method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="938ff-121">需求</span><span class="sxs-lookup"><span data-stu-id="938ff-121">Requirements</span></span>  

 <span data-ttu-id="938ff-122">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="938ff-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="938ff-123">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="938ff-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="938ff-124">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="938ff-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="938ff-125">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="938ff-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="938ff-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="938ff-126">See also</span></span>

- [<span data-ttu-id="938ff-127">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="938ff-127">Debugging Enumerations</span></span>](debugging-enumerations.md)

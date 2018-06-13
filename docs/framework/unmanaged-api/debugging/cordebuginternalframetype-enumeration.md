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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49b42a7fc54af56149b602b337e4a6c853c270cd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406353"
---
# <a name="cordebuginternalframetype-enumeration"></a><span data-ttu-id="00552-102">CorDebugInternalFrameType 列舉</span><span class="sxs-lookup"><span data-stu-id="00552-102">CorDebugInternalFrameType Enumeration</span></span>
<span data-ttu-id="00552-103">識別堆疊框架的類型。</span><span class="sxs-lookup"><span data-stu-id="00552-103">Identifies the type of stack frame.</span></span> <span data-ttu-id="00552-104">這個列舉型別由[icordebuginternalframe:: Getframetype](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="00552-104">This enumeration is used by the [ICorDebugInternalFrame::GetFrameType](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00552-105">語法</span><span class="sxs-lookup"><span data-stu-id="00552-105">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="00552-106">成員</span><span class="sxs-lookup"><span data-stu-id="00552-106">Members</span></span>  
  
|<span data-ttu-id="00552-107">成員</span><span class="sxs-lookup"><span data-stu-id="00552-107">Member</span></span>|<span data-ttu-id="00552-108">描述</span><span class="sxs-lookup"><span data-stu-id="00552-108">Description</span></span>|  
|------------|-----------------|  
|`STUBFRAME_NONE`|<span data-ttu-id="00552-109">null 值。</span><span class="sxs-lookup"><span data-stu-id="00552-109">A null value.</span></span> <span data-ttu-id="00552-110">`ICorDebugInternalFrame::GetFrameType`方法不會傳回此值。</span><span class="sxs-lookup"><span data-stu-id="00552-110">The `ICorDebugInternalFrame::GetFrameType` method never returns this value.</span></span>|  
|`STUBFRAME_M2U`|<span data-ttu-id="00552-111">管理至 unmanaged 的虛設常式的框架。</span><span class="sxs-lookup"><span data-stu-id="00552-111">A managed-to-unmanaged stub frame.</span></span>|  
|`STUBFRAME_U2M`|<span data-ttu-id="00552-112">Unmanaged--受管理的虛設常式的框架。</span><span class="sxs-lookup"><span data-stu-id="00552-112">An unmanaged-to-managed stub frame.</span></span>|  
|`STUBFRAME_APPDOMAIN_TRANSITION`|<span data-ttu-id="00552-113">應用程式定義域之間的轉換。</span><span class="sxs-lookup"><span data-stu-id="00552-113">A transition between application domains.</span></span>|  
|`STUBFRAME_LIGHTWEIGHT_FUNCTION`|<span data-ttu-id="00552-114">輕量級方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="00552-114">A lightweight method call.</span></span>|  
|`STUBFRAME_FUNC_EVAL`|<span data-ttu-id="00552-115">函式評估的開始。</span><span class="sxs-lookup"><span data-stu-id="00552-115">The start of function evaluation.</span></span>|  
|`STUBFRAME_INTERNALCALL`|<span data-ttu-id="00552-116">Common language runtime 內部呼叫。</span><span class="sxs-lookup"><span data-stu-id="00552-116">An internal call into the common language runtime.</span></span>|  
|`STUBFRAME_CLASS_INIT`|<span data-ttu-id="00552-117">類別初始設定開始。</span><span class="sxs-lookup"><span data-stu-id="00552-117">The start of a class initialization.</span></span>|  
|`STUBFRAME_EXCEPTION`|<span data-ttu-id="00552-118">就會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="00552-118">An exception that is thrown.</span></span>|  
|`STUBFRAME_SECURITY`|<span data-ttu-id="00552-119">使用程式碼存取安全性的框架。</span><span class="sxs-lookup"><span data-stu-id="00552-119">A frame used for code access security.</span></span>|  
|`STUBFRAME_JIT_COMPILATION`|<span data-ttu-id="00552-120">執行階段是 JIT 編譯方法。</span><span class="sxs-lookup"><span data-stu-id="00552-120">The runtime is JIT-compiling a method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="00552-121">需求</span><span class="sxs-lookup"><span data-stu-id="00552-121">Requirements</span></span>  
 <span data-ttu-id="00552-122">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="00552-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00552-123">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="00552-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="00552-124">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="00552-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00552-125">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00552-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00552-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00552-126">See Also</span></span>  
 [<span data-ttu-id="00552-127">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="00552-127">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

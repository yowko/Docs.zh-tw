---
title: ICorDebugProcess6::ProcessStateChanged 方法
ms.date: 03/30/2017
ms.assetid: fb6d30d9-54f3-462b-8ebf-ce0440791ad5
ms.openlocfilehash: 3927e57883ebe282b262cb03ececc3b2cd96fd46
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123421"
---
# <a name="icordebugprocess6processstatechanged-method"></a><span data-ttu-id="e5e60-102">ICorDebugProcess6::ProcessStateChanged 方法</span><span class="sxs-lookup"><span data-stu-id="e5e60-102">ICorDebugProcess6::ProcessStateChanged Method</span></span>
<span data-ttu-id="e5e60-103">通知[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)進程正在執行。</span><span class="sxs-lookup"><span data-stu-id="e5e60-103">Notifies [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5e60-104">語法</span><span class="sxs-lookup"><span data-stu-id="e5e60-104">Syntax</span></span>  
  
```cpp  
HRESULT ProcessStateChanged(   [in] CorDebugStateChange change);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5e60-105">參數</span><span class="sxs-lookup"><span data-stu-id="e5e60-105">Parameters</span></span>  
 `change`  
 <span data-ttu-id="e5e60-106">在[ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md)列舉的成員</span><span class="sxs-lookup"><span data-stu-id="e5e60-106">[in] A member of the [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) enumeration</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5e60-107">備註</span><span class="sxs-lookup"><span data-stu-id="e5e60-107">Remarks</span></span>  
 <span data-ttu-id="e5e60-108">偵錯工具會呼叫這個方法，以通知[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)進程正在執行。</span><span class="sxs-lookup"><span data-stu-id="e5e60-108">The debugger calls this method to notify [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e5e60-109">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="e5e60-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5e60-110">需求</span><span class="sxs-lookup"><span data-stu-id="e5e60-110">Requirements</span></span>  
 <span data-ttu-id="e5e60-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e5e60-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5e60-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e5e60-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e5e60-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e5e60-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5e60-114">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5e60-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5e60-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="e5e60-115">See also</span></span>

- [<span data-ttu-id="e5e60-116">ICorDebugProcess6 介面</span><span class="sxs-lookup"><span data-stu-id="e5e60-116">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="e5e60-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="e5e60-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

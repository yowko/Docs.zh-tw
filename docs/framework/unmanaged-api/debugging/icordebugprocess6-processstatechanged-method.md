---
title: ICorDebugProcess6::ProcessStateChanged 方法
ms.date: 03/30/2017
ms.assetid: fb6d30d9-54f3-462b-8ebf-ce0440791ad5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6f25e25f94dae1a959cbb813a44a7f4f09eaa69c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474588"
---
# <a name="icordebugprocess6processstatechanged-method"></a><span data-ttu-id="53655-102">ICorDebugProcess6::ProcessStateChanged 方法</span><span class="sxs-lookup"><span data-stu-id="53655-102">ICorDebugProcess6::ProcessStateChanged Method</span></span>
<span data-ttu-id="53655-103">會告知[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)處理序執行。</span><span class="sxs-lookup"><span data-stu-id="53655-103">Notifies [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53655-104">語法</span><span class="sxs-lookup"><span data-stu-id="53655-104">Syntax</span></span>  
  
```  
HRESULT ProcessStateChanged(   [in] CorDebugStateChange change);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53655-105">參數</span><span class="sxs-lookup"><span data-stu-id="53655-105">Parameters</span></span>  
 `change`  
 <span data-ttu-id="53655-106">[in]成員[ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md)列舉</span><span class="sxs-lookup"><span data-stu-id="53655-106">[in] A member of the [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) enumeration</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53655-107">備註</span><span class="sxs-lookup"><span data-stu-id="53655-107">Remarks</span></span>  
 <span data-ttu-id="53655-108">偵錯工具呼叫此方法來通知[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)處理序執行。</span><span class="sxs-lookup"><span data-stu-id="53655-108">The debugger calls this method to notify [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="53655-109">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="53655-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53655-110">需求</span><span class="sxs-lookup"><span data-stu-id="53655-110">Requirements</span></span>  
 <span data-ttu-id="53655-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="53655-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53655-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="53655-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="53655-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="53655-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53655-114">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53655-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53655-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53655-115">See also</span></span>
- [<span data-ttu-id="53655-116">ICorDebugProcess6 介面</span><span class="sxs-lookup"><span data-stu-id="53655-116">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="53655-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="53655-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

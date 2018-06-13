---
title: ICorDebugProcess6::ProcessStateChanged 方法
ms.date: 03/30/2017
ms.assetid: fb6d30d9-54f3-462b-8ebf-ce0440791ad5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc5861762242412d7ab6f0c02f2b8f5c149f9453
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420175"
---
# <a name="icordebugprocess6processstatechanged-method"></a><span data-ttu-id="51f8d-102">ICorDebugProcess6::ProcessStateChanged 方法</span><span class="sxs-lookup"><span data-stu-id="51f8d-102">ICorDebugProcess6::ProcessStateChanged Method</span></span>
<span data-ttu-id="51f8d-103">通知[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)處理序正在執行。</span><span class="sxs-lookup"><span data-stu-id="51f8d-103">Notifies [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51f8d-104">語法</span><span class="sxs-lookup"><span data-stu-id="51f8d-104">Syntax</span></span>  
  
```  
HRESULT ProcessStateChanged(   [in] CorDebugStateChange change);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="51f8d-105">參數</span><span class="sxs-lookup"><span data-stu-id="51f8d-105">Parameters</span></span>  
 `change`  
 <span data-ttu-id="51f8d-106">[in]成員[ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md)列舉</span><span class="sxs-lookup"><span data-stu-id="51f8d-106">[in] A member of the [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) enumeration</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="51f8d-107">備註</span><span class="sxs-lookup"><span data-stu-id="51f8d-107">Remarks</span></span>  
 <span data-ttu-id="51f8d-108">偵錯工具呼叫此方法來通知[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)處理序正在執行。</span><span class="sxs-lookup"><span data-stu-id="51f8d-108">The debugger calls this method to notify [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51f8d-109">本方法只適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="51f8d-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51f8d-110">需求</span><span class="sxs-lookup"><span data-stu-id="51f8d-110">Requirements</span></span>  
 <span data-ttu-id="51f8d-111">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="51f8d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51f8d-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="51f8d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="51f8d-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="51f8d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51f8d-114">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51f8d-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51f8d-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51f8d-115">See Also</span></span>  
 [<span data-ttu-id="51f8d-116">ICorDebugProcess6 介面</span><span class="sxs-lookup"><span data-stu-id="51f8d-116">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 [<span data-ttu-id="51f8d-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="51f8d-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

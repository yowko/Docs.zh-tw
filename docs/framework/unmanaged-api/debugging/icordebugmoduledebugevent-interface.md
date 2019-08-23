---
title: ICorDebugModuleDebugEvent 介面
ms.date: 03/30/2017
ms.assetid: 41950c52-1ac8-4212-b814-c77e20879f91
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 706f392652c5cb868e09d4ee9fcb69c6d3d92d2a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965090"
---
# <a name="icordebugmoduledebugevent-interface"></a><span data-ttu-id="007d6-102">ICorDebugModuleDebugEvent 介面</span><span class="sxs-lookup"><span data-stu-id="007d6-102">ICorDebugModuleDebugEvent Interface</span></span>
<span data-ttu-id="007d6-103">擴充[ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)介面, 以支援模組層級事件。</span><span class="sxs-lookup"><span data-stu-id="007d6-103">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support module-level events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="007d6-104">方法</span><span class="sxs-lookup"><span data-stu-id="007d6-104">Methods</span></span>  
  
|<span data-ttu-id="007d6-105">方法</span><span class="sxs-lookup"><span data-stu-id="007d6-105">Method</span></span>|<span data-ttu-id="007d6-106">說明</span><span class="sxs-lookup"><span data-stu-id="007d6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="007d6-107">GetModule 方法</span><span class="sxs-lookup"><span data-stu-id="007d6-107">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-getmodule-method.md)|<span data-ttu-id="007d6-108">取得剛載入或卸載的合併模組。</span><span class="sxs-lookup"><span data-stu-id="007d6-108">Gets the merged module that was just loaded or unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="007d6-109">備註</span><span class="sxs-lookup"><span data-stu-id="007d6-109">Remarks</span></span>  
 <span data-ttu-id="007d6-110">[MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md)和[MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md)事件種類會執行此介面。</span><span class="sxs-lookup"><span data-stu-id="007d6-110">The [MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) and [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) event types implement this interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="007d6-111">這個介面僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="007d6-111">The interface is available with .NET Native only.</span></span> <span data-ttu-id="007d6-112">嘗試在 .NET 原生之外的 ICorDebug 案例中呼叫 `QueryInterface` 以擷取介面指標，會傳回 `E_NOINTERFACE`。</span><span class="sxs-lookup"><span data-stu-id="007d6-112">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="007d6-113">需求</span><span class="sxs-lookup"><span data-stu-id="007d6-113">Requirements</span></span>  
 <span data-ttu-id="007d6-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="007d6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="007d6-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="007d6-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="007d6-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="007d6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="007d6-117">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="007d6-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="007d6-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="007d6-118">See also</span></span>

- [<span data-ttu-id="007d6-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="007d6-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="007d6-120">偵錯</span><span class="sxs-lookup"><span data-stu-id="007d6-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

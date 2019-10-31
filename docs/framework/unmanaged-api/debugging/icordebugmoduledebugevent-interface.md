---
title: ICorDebugModuleDebugEvent 介面
ms.date: 03/30/2017
ms.assetid: 41950c52-1ac8-4212-b814-c77e20879f91
ms.openlocfilehash: cca181c6af6db9f35ff7913e045a30e37e07a5e6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73110241"
---
# <a name="icordebugmoduledebugevent-interface"></a><span data-ttu-id="f0c32-102">ICorDebugModuleDebugEvent 介面</span><span class="sxs-lookup"><span data-stu-id="f0c32-102">ICorDebugModuleDebugEvent Interface</span></span>
<span data-ttu-id="f0c32-103">擴充[ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)介面，以支援模組層級事件。</span><span class="sxs-lookup"><span data-stu-id="f0c32-103">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support module-level events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f0c32-104">方法</span><span class="sxs-lookup"><span data-stu-id="f0c32-104">Methods</span></span>  
  
|<span data-ttu-id="f0c32-105">方法</span><span class="sxs-lookup"><span data-stu-id="f0c32-105">Method</span></span>|<span data-ttu-id="f0c32-106">描述</span><span class="sxs-lookup"><span data-stu-id="f0c32-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f0c32-107">GetModule 方法</span><span class="sxs-lookup"><span data-stu-id="f0c32-107">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-getmodule-method.md)|<span data-ttu-id="f0c32-108">取得剛載入或卸載的合併模組。</span><span class="sxs-lookup"><span data-stu-id="f0c32-108">Gets the merged module that was just loaded or unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0c32-109">備註</span><span class="sxs-lookup"><span data-stu-id="f0c32-109">Remarks</span></span>  
 <span data-ttu-id="f0c32-110">[MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md)和[MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md)事件種類會執行此介面。</span><span class="sxs-lookup"><span data-stu-id="f0c32-110">The [MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) and [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) event types implement this interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f0c32-111">這個介面僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="f0c32-111">The interface is available with .NET Native only.</span></span> <span data-ttu-id="f0c32-112">嘗試在 .NET 原生之外的 ICorDebug 案例中呼叫 `QueryInterface` 以擷取介面指標，會傳回 `E_NOINTERFACE`。</span><span class="sxs-lookup"><span data-stu-id="f0c32-112">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0c32-113">需求</span><span class="sxs-lookup"><span data-stu-id="f0c32-113">Requirements</span></span>  
 <span data-ttu-id="f0c32-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f0c32-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0c32-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f0c32-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f0c32-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f0c32-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0c32-117">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0c32-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0c32-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="f0c32-118">See also</span></span>

- [<span data-ttu-id="f0c32-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="f0c32-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="f0c32-120">偵錯</span><span class="sxs-lookup"><span data-stu-id="f0c32-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

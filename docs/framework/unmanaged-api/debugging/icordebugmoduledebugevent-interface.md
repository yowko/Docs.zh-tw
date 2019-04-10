---
title: ICorDebugModuleDebugEvent 介面
ms.date: 03/30/2017
ms.assetid: 41950c52-1ac8-4212-b814-c77e20879f91
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7bf1fa21872c710ebc69c45e9980aeaa577a45fc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59160910"
---
# <a name="icordebugmoduledebugevent-interface"></a><span data-ttu-id="cd67c-102">ICorDebugModuleDebugEvent 介面</span><span class="sxs-lookup"><span data-stu-id="cd67c-102">ICorDebugModuleDebugEvent Interface</span></span>
<span data-ttu-id="cd67c-103">擴充[ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)介面，以支援模組層級事件。</span><span class="sxs-lookup"><span data-stu-id="cd67c-103">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support module-level events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cd67c-104">方法</span><span class="sxs-lookup"><span data-stu-id="cd67c-104">Methods</span></span>  
  
|<span data-ttu-id="cd67c-105">方法</span><span class="sxs-lookup"><span data-stu-id="cd67c-105">Method</span></span>|<span data-ttu-id="cd67c-106">描述</span><span class="sxs-lookup"><span data-stu-id="cd67c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cd67c-107">GetModule 方法</span><span class="sxs-lookup"><span data-stu-id="cd67c-107">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-getmodule-method.md)|<span data-ttu-id="cd67c-108">取得剛載入或卸載的合併模組。</span><span class="sxs-lookup"><span data-stu-id="cd67c-108">Gets the merged module that was just loaded or unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd67c-109">備註</span><span class="sxs-lookup"><span data-stu-id="cd67c-109">Remarks</span></span>  
 <span data-ttu-id="cd67c-110">[MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md)並[MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md)事件類型會實作這個介面。</span><span class="sxs-lookup"><span data-stu-id="cd67c-110">The [MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) and [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) event types implement this interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cd67c-111">這個介面僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="cd67c-111">The interface is available with .NET Native only.</span></span> <span data-ttu-id="cd67c-112">嘗試在 .NET 原生之外的 ICorDebug 案例中呼叫 `QueryInterface` 以擷取介面指標，會傳回 `E_NOINTERFACE`。</span><span class="sxs-lookup"><span data-stu-id="cd67c-112">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd67c-113">需求</span><span class="sxs-lookup"><span data-stu-id="cd67c-113">Requirements</span></span>  
 <span data-ttu-id="cd67c-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cd67c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd67c-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cd67c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cd67c-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cd67c-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="cd67c-117">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="cd67c-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cd67c-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd67c-118">See also</span></span>

- [<span data-ttu-id="cd67c-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="cd67c-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="cd67c-120">偵錯</span><span class="sxs-lookup"><span data-stu-id="cd67c-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

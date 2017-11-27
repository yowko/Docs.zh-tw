---
title: "ICorDebugModuleDebugEvent 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 41950c52-1ac8-4212-b814-c77e20879f91
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dced93ab39529ec57fb6fb99603a197fb957be8d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmoduledebugevent-interface"></a><span data-ttu-id="6e200-102">ICorDebugModuleDebugEvent 介面</span><span class="sxs-lookup"><span data-stu-id="6e200-102">ICorDebugModuleDebugEvent Interface</span></span>
<span data-ttu-id="6e200-103">擴充[ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)介面，以支援模組層級事件。</span><span class="sxs-lookup"><span data-stu-id="6e200-103">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support module-level events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6e200-104">方法</span><span class="sxs-lookup"><span data-stu-id="6e200-104">Methods</span></span>  
  
|<span data-ttu-id="6e200-105">方法</span><span class="sxs-lookup"><span data-stu-id="6e200-105">Method</span></span>|<span data-ttu-id="6e200-106">說明</span><span class="sxs-lookup"><span data-stu-id="6e200-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6e200-107">GetModule 方法</span><span class="sxs-lookup"><span data-stu-id="6e200-107">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-getmodule-method.md)|<span data-ttu-id="6e200-108">取得剛載入或卸載的合併模組。</span><span class="sxs-lookup"><span data-stu-id="6e200-108">Gets the merged module that was just loaded or unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e200-109">備註</span><span class="sxs-lookup"><span data-stu-id="6e200-109">Remarks</span></span>  
 <span data-ttu-id="6e200-110">[MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md)和[MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md)事件類型會實作這個介面。</span><span class="sxs-lookup"><span data-stu-id="6e200-110">The [MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) and [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) event types implement this interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6e200-111">這個介面僅適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="6e200-111">The interface is available with .NET Native only.</span></span> <span data-ttu-id="6e200-112">嘗試在 .NET 原生之外的 ICorDebug 案例中呼叫 `QueryInterface` 以擷取介面指標，會傳回 `E_NOINTERFACE`。</span><span class="sxs-lookup"><span data-stu-id="6e200-112">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e200-113">需求</span><span class="sxs-lookup"><span data-stu-id="6e200-113">Requirements</span></span>  
 <span data-ttu-id="6e200-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6e200-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e200-115">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6e200-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6e200-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6e200-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e200-117">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e200-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e200-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e200-118">See Also</span></span>  
 [<span data-ttu-id="6e200-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="6e200-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="6e200-120">偵錯</span><span class="sxs-lookup"><span data-stu-id="6e200-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

---
title: ICorDebugModuleDebugEvent 介面
ms.date: 03/30/2017
ms.assetid: 41950c52-1ac8-4212-b814-c77e20879f91
ms.openlocfilehash: a2c7eaa8a2c811c1696024d9af4b715cc49e7caa
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792889"
---
# <a name="icordebugmoduledebugevent-interface"></a><span data-ttu-id="4d9eb-102">ICorDebugModuleDebugEvent 介面</span><span class="sxs-lookup"><span data-stu-id="4d9eb-102">ICorDebugModuleDebugEvent Interface</span></span>
<span data-ttu-id="4d9eb-103">擴充[ICorDebugDebugEvent](icordebugdebugevent-interface.md)介面，以支援模組層級事件。</span><span class="sxs-lookup"><span data-stu-id="4d9eb-103">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support module-level events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4d9eb-104">方法</span><span class="sxs-lookup"><span data-stu-id="4d9eb-104">Methods</span></span>  
  
|<span data-ttu-id="4d9eb-105">方法</span><span class="sxs-lookup"><span data-stu-id="4d9eb-105">Method</span></span>|<span data-ttu-id="4d9eb-106">描述</span><span class="sxs-lookup"><span data-stu-id="4d9eb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4d9eb-107">GetModule 方法</span><span class="sxs-lookup"><span data-stu-id="4d9eb-107">GetModule Method</span></span>](icordebugmoduledebugevent-getmodule-method.md)|<span data-ttu-id="4d9eb-108">取得剛載入或卸載的合併模組。</span><span class="sxs-lookup"><span data-stu-id="4d9eb-108">Gets the merged module that was just loaded or unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4d9eb-109">備註</span><span class="sxs-lookup"><span data-stu-id="4d9eb-109">Remarks</span></span>  
 <span data-ttu-id="4d9eb-110">[MODULE_LOADED](cordebugdebugeventkind-enumeration.md)和[MODULE_UNLOADED](cordebugdebugeventkind-enumeration.md)事件種類會執行此介面。</span><span class="sxs-lookup"><span data-stu-id="4d9eb-110">The [MODULE_LOADED](cordebugdebugeventkind-enumeration.md) and [MODULE_UNLOADED](cordebugdebugeventkind-enumeration.md) event types implement this interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4d9eb-111">這個介面僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="4d9eb-111">The interface is available with .NET Native only.</span></span> <span data-ttu-id="4d9eb-112">嘗試在 .NET 原生之外的 ICorDebug 案例中呼叫 `QueryInterface` 以擷取介面指標，會傳回 `E_NOINTERFACE`。</span><span class="sxs-lookup"><span data-stu-id="4d9eb-112">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d9eb-113">需求</span><span class="sxs-lookup"><span data-stu-id="4d9eb-113">Requirements</span></span>  
 <span data-ttu-id="4d9eb-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4d9eb-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d9eb-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4d9eb-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4d9eb-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4d9eb-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d9eb-117">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d9eb-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d9eb-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="4d9eb-118">See also</span></span>

- [<span data-ttu-id="4d9eb-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="4d9eb-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="4d9eb-120">偵錯</span><span class="sxs-lookup"><span data-stu-id="4d9eb-120">Debugging</span></span>](index.md)

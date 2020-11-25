---
title: ICorDebugModuleDebugEvent 介面
ms.date: 03/30/2017
ms.assetid: 41950c52-1ac8-4212-b814-c77e20879f91
ms.openlocfilehash: 62d419a193cff000e1dd748d0cbb6b61775a81aa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695812"
---
# <a name="icordebugmoduledebugevent-interface"></a><span data-ttu-id="47b92-102">ICorDebugModuleDebugEvent 介面</span><span class="sxs-lookup"><span data-stu-id="47b92-102">ICorDebugModuleDebugEvent Interface</span></span>

<span data-ttu-id="47b92-103">擴充 [ICorDebugDebugEvent](icordebugdebugevent-interface.md) 介面，以支援模組層級的事件。</span><span class="sxs-lookup"><span data-stu-id="47b92-103">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support module-level events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="47b92-104">方法</span><span class="sxs-lookup"><span data-stu-id="47b92-104">Methods</span></span>  
  
|<span data-ttu-id="47b92-105">方法</span><span class="sxs-lookup"><span data-stu-id="47b92-105">Method</span></span>|<span data-ttu-id="47b92-106">描述</span><span class="sxs-lookup"><span data-stu-id="47b92-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="47b92-107">GetModule 方法</span><span class="sxs-lookup"><span data-stu-id="47b92-107">GetModule Method</span></span>](icordebugmoduledebugevent-getmodule-method.md)|<span data-ttu-id="47b92-108">取得剛載入或卸載的合併模組。</span><span class="sxs-lookup"><span data-stu-id="47b92-108">Gets the merged module that was just loaded or unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47b92-109">備註</span><span class="sxs-lookup"><span data-stu-id="47b92-109">Remarks</span></span>  

 <span data-ttu-id="47b92-110">[MODULE_LOADED](cordebugdebugeventkind-enumeration.md)和[MODULE_UNLOADED](cordebugdebugeventkind-enumeration.md)事件種類會執行這個介面。</span><span class="sxs-lookup"><span data-stu-id="47b92-110">The [MODULE_LOADED](cordebugdebugeventkind-enumeration.md) and [MODULE_UNLOADED](cordebugdebugeventkind-enumeration.md) event types implement this interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="47b92-111">這個介面僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="47b92-111">The interface is available with .NET Native only.</span></span> <span data-ttu-id="47b92-112">嘗試在 .NET 原生之外的 ICorDebug 案例中呼叫 `QueryInterface` 以擷取介面指標，會傳回 `E_NOINTERFACE`。</span><span class="sxs-lookup"><span data-stu-id="47b92-112">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47b92-113">需求</span><span class="sxs-lookup"><span data-stu-id="47b92-113">Requirements</span></span>  

 <span data-ttu-id="47b92-114">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="47b92-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47b92-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="47b92-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="47b92-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="47b92-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="47b92-117">**.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47b92-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47b92-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47b92-118">See also</span></span>

- [<span data-ttu-id="47b92-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="47b92-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="47b92-120">偵錯</span><span class="sxs-lookup"><span data-stu-id="47b92-120">Debugging</span></span>](index.md)

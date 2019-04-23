---
title: ICorDebugDebugEvent 介面
ms.date: 03/30/2017
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 550cb6379ef0d5d17a3446b3f21120208b5a3dad
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59110184"
---
# <a name="icordebugdebugevent-interface"></a><span data-ttu-id="c74dc-102">ICorDebugDebugEvent 介面</span><span class="sxs-lookup"><span data-stu-id="c74dc-102">ICorDebugDebugEvent Interface</span></span>
<span data-ttu-id="c74dc-103">定義所有 `ICorDebug` 偵錯事件衍生的來源基底介面。</span><span class="sxs-lookup"><span data-stu-id="c74dc-103">Defines the base interface from which all `ICorDebug` debug events derive.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c74dc-104">方法</span><span class="sxs-lookup"><span data-stu-id="c74dc-104">Methods</span></span>  
  
|<span data-ttu-id="c74dc-105">方法</span><span class="sxs-lookup"><span data-stu-id="c74dc-105">Method</span></span>|<span data-ttu-id="c74dc-106">描述</span><span class="sxs-lookup"><span data-stu-id="c74dc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c74dc-107">GetEventKind 方法</span><span class="sxs-lookup"><span data-stu-id="c74dc-107">GetEventKind Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)|<span data-ttu-id="c74dc-108">指出這個 `ICorDebugDebugEvent` 物件所代表的事件類型。</span><span class="sxs-lookup"><span data-stu-id="c74dc-108">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>|  
|[<span data-ttu-id="c74dc-109">GetThread 方法</span><span class="sxs-lookup"><span data-stu-id="c74dc-109">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-getthread-method.md)|<span data-ttu-id="c74dc-110">取得發生事件的執行緒。</span><span class="sxs-lookup"><span data-stu-id="c74dc-110">Gets the thread on which the event occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c74dc-111">備註</span><span class="sxs-lookup"><span data-stu-id="c74dc-111">Remarks</span></span>  
 <span data-ttu-id="c74dc-112">下列介面衍生自 `ICorDebugDebugEvent` 介面：</span><span class="sxs-lookup"><span data-stu-id="c74dc-112">The following interfaces are derived from the `ICorDebugDebugEvent` interface:</span></span>  
  
-   [<span data-ttu-id="c74dc-113">ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="c74dc-113">ICorDebugExceptionDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
  
-   [<span data-ttu-id="c74dc-114">ICorDebugModuleDebugEvent</span><span class="sxs-lookup"><span data-stu-id="c74dc-114">ICorDebugModuleDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
>  <span data-ttu-id="c74dc-115">這個介面僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="c74dc-115">The interface is available with .NET Native only.</span></span> <span data-ttu-id="c74dc-116">嘗試在 .NET 原生之外的 ICorDebug 案例中呼叫 `QueryInterface` 以擷取介面指標，會傳回 `E_NOINTERFACE`。</span><span class="sxs-lookup"><span data-stu-id="c74dc-116">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c74dc-117">需求</span><span class="sxs-lookup"><span data-stu-id="c74dc-117">Requirements</span></span>  
 <span data-ttu-id="c74dc-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c74dc-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c74dc-119">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c74dc-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c74dc-120">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c74dc-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c74dc-121">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c74dc-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c74dc-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c74dc-122">See also</span></span>

- [<span data-ttu-id="c74dc-123">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="c74dc-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="c74dc-124">偵錯</span><span class="sxs-lookup"><span data-stu-id="c74dc-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

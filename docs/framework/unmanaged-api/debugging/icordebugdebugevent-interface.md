---
title: "ICorDebugDebugEvent 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b4422b165f06b60dedff95fc3de58e5627db7fac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdebugevent-interface"></a><span data-ttu-id="deb11-102">ICorDebugDebugEvent 介面</span><span class="sxs-lookup"><span data-stu-id="deb11-102">ICorDebugDebugEvent Interface</span></span>
<span data-ttu-id="deb11-103">定義所有 `ICorDebug` 偵錯事件衍生的來源基底介面。</span><span class="sxs-lookup"><span data-stu-id="deb11-103">Defines the base interface from which all `ICorDebug` debug events derive.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="deb11-104">方法</span><span class="sxs-lookup"><span data-stu-id="deb11-104">Methods</span></span>  
  
|<span data-ttu-id="deb11-105">方法</span><span class="sxs-lookup"><span data-stu-id="deb11-105">Method</span></span>|<span data-ttu-id="deb11-106">說明</span><span class="sxs-lookup"><span data-stu-id="deb11-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="deb11-107">GetEventKind 方法</span><span class="sxs-lookup"><span data-stu-id="deb11-107">GetEventKind Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)|<span data-ttu-id="deb11-108">指出這個 `ICorDebugDebugEvent` 物件所代表的事件類型。</span><span class="sxs-lookup"><span data-stu-id="deb11-108">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>|  
|[<span data-ttu-id="deb11-109">GetThread 方法</span><span class="sxs-lookup"><span data-stu-id="deb11-109">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-getthread-method.md)|<span data-ttu-id="deb11-110">取得發生事件的執行緒。</span><span class="sxs-lookup"><span data-stu-id="deb11-110">Gets the thread on which the event occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="deb11-111">備註</span><span class="sxs-lookup"><span data-stu-id="deb11-111">Remarks</span></span>  
 <span data-ttu-id="deb11-112">下列介面衍生自 `ICorDebugDebugEvent` 介面：</span><span class="sxs-lookup"><span data-stu-id="deb11-112">The following interfaces are derived from the `ICorDebugDebugEvent` interface:</span></span>  
  
-   [<span data-ttu-id="deb11-113">ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="deb11-113">ICorDebugExceptionDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
  
-   [<span data-ttu-id="deb11-114">ICorDebugModuleDebugEvent</span><span class="sxs-lookup"><span data-stu-id="deb11-114">ICorDebugModuleDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
>  <span data-ttu-id="deb11-115">這個介面僅適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="deb11-115">The interface is available with .NET Native only.</span></span> <span data-ttu-id="deb11-116">嘗試在 .NET 原生之外的 ICorDebug 案例中呼叫 `QueryInterface` 以擷取介面指標，會傳回 `E_NOINTERFACE`。</span><span class="sxs-lookup"><span data-stu-id="deb11-116">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="deb11-117">需求</span><span class="sxs-lookup"><span data-stu-id="deb11-117">Requirements</span></span>  
 <span data-ttu-id="deb11-118">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="deb11-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="deb11-119">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="deb11-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="deb11-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="deb11-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="deb11-121">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="deb11-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="deb11-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="deb11-122">See Also</span></span>  
 [<span data-ttu-id="deb11-123">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="deb11-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="deb11-124">偵錯</span><span class="sxs-lookup"><span data-stu-id="deb11-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

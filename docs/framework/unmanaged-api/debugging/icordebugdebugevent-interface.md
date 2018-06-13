---
title: ICorDebugDebugEvent 介面
ms.date: 03/30/2017
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a2543a9629c60fde2b2f14c11898ba3e9df3c82
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419308"
---
# <a name="icordebugdebugevent-interface"></a><span data-ttu-id="58d35-102">ICorDebugDebugEvent 介面</span><span class="sxs-lookup"><span data-stu-id="58d35-102">ICorDebugDebugEvent Interface</span></span>
<span data-ttu-id="58d35-103">定義所有 `ICorDebug` 偵錯事件衍生的來源基底介面。</span><span class="sxs-lookup"><span data-stu-id="58d35-103">Defines the base interface from which all `ICorDebug` debug events derive.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="58d35-104">方法</span><span class="sxs-lookup"><span data-stu-id="58d35-104">Methods</span></span>  
  
|<span data-ttu-id="58d35-105">方法</span><span class="sxs-lookup"><span data-stu-id="58d35-105">Method</span></span>|<span data-ttu-id="58d35-106">描述</span><span class="sxs-lookup"><span data-stu-id="58d35-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="58d35-107">GetEventKind 方法</span><span class="sxs-lookup"><span data-stu-id="58d35-107">GetEventKind Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)|<span data-ttu-id="58d35-108">指出這個 `ICorDebugDebugEvent` 物件所代表的事件類型。</span><span class="sxs-lookup"><span data-stu-id="58d35-108">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>|  
|[<span data-ttu-id="58d35-109">GetThread 方法</span><span class="sxs-lookup"><span data-stu-id="58d35-109">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-getthread-method.md)|<span data-ttu-id="58d35-110">取得發生事件的執行緒。</span><span class="sxs-lookup"><span data-stu-id="58d35-110">Gets the thread on which the event occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58d35-111">備註</span><span class="sxs-lookup"><span data-stu-id="58d35-111">Remarks</span></span>  
 <span data-ttu-id="58d35-112">下列介面衍生自 `ICorDebugDebugEvent` 介面：</span><span class="sxs-lookup"><span data-stu-id="58d35-112">The following interfaces are derived from the `ICorDebugDebugEvent` interface:</span></span>  
  
-   [<span data-ttu-id="58d35-113">ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="58d35-113">ICorDebugExceptionDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
  
-   [<span data-ttu-id="58d35-114">ICorDebugModuleDebugEvent</span><span class="sxs-lookup"><span data-stu-id="58d35-114">ICorDebugModuleDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
>  <span data-ttu-id="58d35-115">這個介面僅適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="58d35-115">The interface is available with .NET Native only.</span></span> <span data-ttu-id="58d35-116">嘗試在 .NET 原生之外的 ICorDebug 案例中呼叫 `QueryInterface` 以擷取介面指標，會傳回 `E_NOINTERFACE`。</span><span class="sxs-lookup"><span data-stu-id="58d35-116">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58d35-117">需求</span><span class="sxs-lookup"><span data-stu-id="58d35-117">Requirements</span></span>  
 <span data-ttu-id="58d35-118">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="58d35-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58d35-119">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="58d35-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="58d35-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58d35-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58d35-121">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58d35-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58d35-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58d35-122">See Also</span></span>  
 [<span data-ttu-id="58d35-123">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="58d35-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="58d35-124">偵錯</span><span class="sxs-lookup"><span data-stu-id="58d35-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

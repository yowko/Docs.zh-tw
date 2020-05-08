---
title: ICorDebugDebugEvent 介面
ms.date: 03/30/2017
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
ms.openlocfilehash: a66012651d4b307d06a5a3bff675a248cc0ee376
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976352"
---
# <a name="icordebugdebugevent-interface"></a><span data-ttu-id="e65e1-102">ICorDebugDebugEvent 介面</span><span class="sxs-lookup"><span data-stu-id="e65e1-102">ICorDebugDebugEvent Interface</span></span>
<span data-ttu-id="e65e1-103">定義所有 `ICorDebug` 偵錯事件衍生的來源基底介面。</span><span class="sxs-lookup"><span data-stu-id="e65e1-103">Defines the base interface from which all `ICorDebug` debug events derive.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e65e1-104">方法</span><span class="sxs-lookup"><span data-stu-id="e65e1-104">Methods</span></span>  
  
|<span data-ttu-id="e65e1-105">方法</span><span class="sxs-lookup"><span data-stu-id="e65e1-105">Method</span></span>|<span data-ttu-id="e65e1-106">描述</span><span class="sxs-lookup"><span data-stu-id="e65e1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e65e1-107">GetEventKind 方法</span><span class="sxs-lookup"><span data-stu-id="e65e1-107">GetEventKind Method</span></span>](icordebugdebugevent-geteventkind-method.md)|<span data-ttu-id="e65e1-108">指出這個 `ICorDebugDebugEvent` 物件所代表的事件類型。</span><span class="sxs-lookup"><span data-stu-id="e65e1-108">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>|  
|[<span data-ttu-id="e65e1-109">GetThread 方法</span><span class="sxs-lookup"><span data-stu-id="e65e1-109">GetThread Method</span></span>](icordebugdebugevent-getthread-method.md)|<span data-ttu-id="e65e1-110">取得發生事件的執行緒。</span><span class="sxs-lookup"><span data-stu-id="e65e1-110">Gets the thread on which the event occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e65e1-111">備註</span><span class="sxs-lookup"><span data-stu-id="e65e1-111">Remarks</span></span>  
 <span data-ttu-id="e65e1-112">下列介面衍生自 `ICorDebugDebugEvent` 介面：</span><span class="sxs-lookup"><span data-stu-id="e65e1-112">The following interfaces are derived from the `ICorDebugDebugEvent` interface:</span></span>  
  
- [<span data-ttu-id="e65e1-113">ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="e65e1-113">ICorDebugExceptionDebugEvent</span></span>](icordebugexceptiondebugevent-interface.md)  
  
- [<span data-ttu-id="e65e1-114">ICorDebugModuleDebugEvent</span><span class="sxs-lookup"><span data-stu-id="e65e1-114">ICorDebugModuleDebugEvent</span></span>](icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
> <span data-ttu-id="e65e1-115">這個介面僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="e65e1-115">The interface is available with .NET Native only.</span></span> <span data-ttu-id="e65e1-116">嘗試在 .NET 原生之外的 ICorDebug 案例中呼叫 `QueryInterface` 以擷取介面指標，會傳回 `E_NOINTERFACE`。</span><span class="sxs-lookup"><span data-stu-id="e65e1-116">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e65e1-117">需求</span><span class="sxs-lookup"><span data-stu-id="e65e1-117">Requirements</span></span>  
 <span data-ttu-id="e65e1-118">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e65e1-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e65e1-119">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e65e1-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e65e1-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e65e1-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e65e1-121">**.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e65e1-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e65e1-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e65e1-122">See also</span></span>

- [<span data-ttu-id="e65e1-123">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="e65e1-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="e65e1-124">偵錯</span><span class="sxs-lookup"><span data-stu-id="e65e1-124">Debugging</span></span>](index.md)

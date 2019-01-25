---
title: ICorDebugVirtualUnwinder 介面
ms.date: 03/30/2017
ms.assetid: a09e9ccc-0b37-43e3-95c1-bc5fa7ee5f42
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9db6b83e2feedd761b95dec455213051e37366e1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54684141"
---
# <a name="icordebugvirtualunwinder-interface"></a><span data-ttu-id="f5250-102">ICorDebugVirtualUnwinder 介面</span><span class="sxs-lookup"><span data-stu-id="f5250-102">ICorDebugVirtualUnwinder Interface</span></span>
<span data-ttu-id="f5250-103">提供可協助堆疊回溯的方法。</span><span class="sxs-lookup"><span data-stu-id="f5250-103">Provides methods to help in stack unwinding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f5250-104">方法</span><span class="sxs-lookup"><span data-stu-id="f5250-104">Methods</span></span>  
  
|<span data-ttu-id="f5250-105">方法</span><span class="sxs-lookup"><span data-stu-id="f5250-105">Method</span></span>|<span data-ttu-id="f5250-106">名稱</span><span class="sxs-lookup"><span data-stu-id="f5250-106">Name</span></span>|  
|------------|----------|  
|[<span data-ttu-id="f5250-107">GetContext 方法</span><span class="sxs-lookup"><span data-stu-id="f5250-107">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-getcontext-method.md)|<span data-ttu-id="f5250-108">取得此回溯器的目前內容。</span><span class="sxs-lookup"><span data-stu-id="f5250-108">Gets the current context of this unwinder.</span></span>|  
|[<span data-ttu-id="f5250-109">Next 方法</span><span class="sxs-lookup"><span data-stu-id="f5250-109">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-next-method.md)|<span data-ttu-id="f5250-110">進入呼叫端的內容。</span><span class="sxs-lookup"><span data-stu-id="f5250-110">Advances to the caller's context.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5250-111">備註</span><span class="sxs-lookup"><span data-stu-id="f5250-111">Remarks</span></span>  
 <span data-ttu-id="f5250-112">`ICorDebugVirtualUnwinder` 介面的成員由偵錯工具實作，協助堆疊回溯。</span><span class="sxs-lookup"><span data-stu-id="f5250-112">The members of the `ICorDebugVirtualUnwinder` interface are implemented by the debugger to help in stack unwinding.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f5250-113">這個介面僅適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="f5250-113">This interface is available with .NET Native only.</span></span> <span data-ttu-id="f5250-114">如果您在 .NET 原生之外針對 ICorDebug 案例實作這個介面，Common Language Runtime 會忽略這個介面。</span><span class="sxs-lookup"><span data-stu-id="f5250-114">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5250-115">需求</span><span class="sxs-lookup"><span data-stu-id="f5250-115">Requirements</span></span>  
 <span data-ttu-id="f5250-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f5250-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5250-117">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f5250-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f5250-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f5250-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5250-119">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5250-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5250-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5250-120">See also</span></span>
- [<span data-ttu-id="f5250-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="f5250-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="f5250-122">偵錯</span><span class="sxs-lookup"><span data-stu-id="f5250-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

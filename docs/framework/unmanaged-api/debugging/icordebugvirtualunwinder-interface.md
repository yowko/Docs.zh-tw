---
title: "ICorDebugVirtualUnwinder 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a09e9ccc-0b37-43e3-95c1-bc5fa7ee5f42
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 936df5c3d913a2ee5a1648906fb3ece2751d8ef5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvirtualunwinder-interface"></a><span data-ttu-id="6bb22-102">ICorDebugVirtualUnwinder 介面</span><span class="sxs-lookup"><span data-stu-id="6bb22-102">ICorDebugVirtualUnwinder Interface</span></span>
<span data-ttu-id="6bb22-103">提供可協助堆疊回溯的方法。</span><span class="sxs-lookup"><span data-stu-id="6bb22-103">Provides methods to help in stack unwinding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6bb22-104">方法</span><span class="sxs-lookup"><span data-stu-id="6bb22-104">Methods</span></span>  
  
|<span data-ttu-id="6bb22-105">方法</span><span class="sxs-lookup"><span data-stu-id="6bb22-105">Method</span></span>|<span data-ttu-id="6bb22-106">名稱</span><span class="sxs-lookup"><span data-stu-id="6bb22-106">Name</span></span>|  
|------------|----------|  
|[<span data-ttu-id="6bb22-107">GetContext 方法</span><span class="sxs-lookup"><span data-stu-id="6bb22-107">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-getcontext-method.md)|<span data-ttu-id="6bb22-108">取得此回溯器的目前內容。</span><span class="sxs-lookup"><span data-stu-id="6bb22-108">Gets the current context of this unwinder.</span></span>|  
|[<span data-ttu-id="6bb22-109">Next 方法</span><span class="sxs-lookup"><span data-stu-id="6bb22-109">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-next-method.md)|<span data-ttu-id="6bb22-110">進入呼叫端的內容。</span><span class="sxs-lookup"><span data-stu-id="6bb22-110">Advances to the caller's context.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6bb22-111">備註</span><span class="sxs-lookup"><span data-stu-id="6bb22-111">Remarks</span></span>  
 <span data-ttu-id="6bb22-112">`ICorDebugVirtualUnwinder` 介面的成員由偵錯工具實作，協助堆疊回溯。</span><span class="sxs-lookup"><span data-stu-id="6bb22-112">The members of the `ICorDebugVirtualUnwinder` interface are implemented by the debugger to help in stack unwinding.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6bb22-113">這個介面僅適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="6bb22-113">This interface is available with .NET Native only.</span></span> <span data-ttu-id="6bb22-114">如果您在 .NET 原生之外針對 ICorDebug 案例實作這個介面，Common Language Runtime 會忽略這個介面。</span><span class="sxs-lookup"><span data-stu-id="6bb22-114">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bb22-115">需求</span><span class="sxs-lookup"><span data-stu-id="6bb22-115">Requirements</span></span>  
 <span data-ttu-id="6bb22-116">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6bb22-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bb22-117">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6bb22-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6bb22-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6bb22-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6bb22-119">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bb22-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bb22-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="6bb22-120">See Also</span></span>  
 [<span data-ttu-id="6bb22-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="6bb22-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="6bb22-122">偵錯</span><span class="sxs-lookup"><span data-stu-id="6bb22-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

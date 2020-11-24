---
title: ICorDebugVirtualUnwinder 介面
ms.date: 03/30/2017
ms.assetid: a09e9ccc-0b37-43e3-95c1-bc5fa7ee5f42
ms.openlocfilehash: 67f2234d37165e421874815bdc2ef34f8f50749a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679373"
---
# <a name="icordebugvirtualunwinder-interface"></a><span data-ttu-id="745dd-102">ICorDebugVirtualUnwinder 介面</span><span class="sxs-lookup"><span data-stu-id="745dd-102">ICorDebugVirtualUnwinder Interface</span></span>

<span data-ttu-id="745dd-103">提供可協助堆疊回溯的方法。</span><span class="sxs-lookup"><span data-stu-id="745dd-103">Provides methods to help in stack unwinding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="745dd-104">方法</span><span class="sxs-lookup"><span data-stu-id="745dd-104">Methods</span></span>  
  
|<span data-ttu-id="745dd-105">方法</span><span class="sxs-lookup"><span data-stu-id="745dd-105">Method</span></span>|<span data-ttu-id="745dd-106">名稱</span><span class="sxs-lookup"><span data-stu-id="745dd-106">Name</span></span>|  
|------------|----------|  
|[<span data-ttu-id="745dd-107">GetContext 方法</span><span class="sxs-lookup"><span data-stu-id="745dd-107">GetContext Method</span></span>](icordebugvirtualunwinder-getcontext-method.md)|<span data-ttu-id="745dd-108">取得此回溯器的目前內容。</span><span class="sxs-lookup"><span data-stu-id="745dd-108">Gets the current context of this unwinder.</span></span>|  
|[<span data-ttu-id="745dd-109">下一個方法</span><span class="sxs-lookup"><span data-stu-id="745dd-109">Next Method</span></span>](icordebugvirtualunwinder-next-method.md)|<span data-ttu-id="745dd-110">進入呼叫端的內容。</span><span class="sxs-lookup"><span data-stu-id="745dd-110">Advances to the caller's context.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="745dd-111">備註</span><span class="sxs-lookup"><span data-stu-id="745dd-111">Remarks</span></span>  

 <span data-ttu-id="745dd-112">`ICorDebugVirtualUnwinder` 介面的成員由偵錯工具實作，協助堆疊回溯。</span><span class="sxs-lookup"><span data-stu-id="745dd-112">The members of the `ICorDebugVirtualUnwinder` interface are implemented by the debugger to help in stack unwinding.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="745dd-113">這個介面僅適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="745dd-113">This interface is available with .NET Native only.</span></span> <span data-ttu-id="745dd-114">如果您在 .NET 原生之外針對 ICorDebug 案例實作這個介面，Common Language Runtime 會忽略這個介面。</span><span class="sxs-lookup"><span data-stu-id="745dd-114">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="745dd-115">需求</span><span class="sxs-lookup"><span data-stu-id="745dd-115">Requirements</span></span>  

 <span data-ttu-id="745dd-116">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="745dd-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="745dd-117">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="745dd-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="745dd-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="745dd-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="745dd-119">**.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="745dd-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="745dd-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="745dd-120">See also</span></span>

- [<span data-ttu-id="745dd-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="745dd-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="745dd-122">偵錯</span><span class="sxs-lookup"><span data-stu-id="745dd-122">Debugging</span></span>](index.md)

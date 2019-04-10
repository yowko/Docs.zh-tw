---
title: ICorDebugVariableSymbol 介面
ms.date: 03/30/2017
ms.assetid: 0e58b85e-69bd-41ff-bedb-8cdc8be6a7a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4c7cdababd1e4b5fae4f5e48a654f861b708a6e3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59226556"
---
# <a name="icordebugvariablesymbol-interface"></a><span data-ttu-id="4bd34-102">ICorDebugVariableSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="4bd34-102">ICorDebugVariableSymbol Interface</span></span>
<span data-ttu-id="4bd34-103">擷取變數的偵錯符號資訊。</span><span class="sxs-lookup"><span data-stu-id="4bd34-103">Retrieves the debug symbol information for a variable.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4bd34-104">方法</span><span class="sxs-lookup"><span data-stu-id="4bd34-104">Methods</span></span>  
  
|<span data-ttu-id="4bd34-105">方法</span><span class="sxs-lookup"><span data-stu-id="4bd34-105">Method</span></span>|<span data-ttu-id="4bd34-106">描述</span><span class="sxs-lookup"><span data-stu-id="4bd34-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4bd34-107">GetName 方法</span><span class="sxs-lookup"><span data-stu-id="4bd34-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getname-method.md)|<span data-ttu-id="4bd34-108">取得變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="4bd34-108">Gets the name of a variable.</span></span>|  
|[<span data-ttu-id="4bd34-109">GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="4bd34-109">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getsize-method.md)|<span data-ttu-id="4bd34-110">取得變數的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="4bd34-110">Gets the size of a variable in bytes.</span></span>|  
|[<span data-ttu-id="4bd34-111">GetSlotIndex 方法</span><span class="sxs-lookup"><span data-stu-id="4bd34-111">GetSlotIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getslotindex-method.md)|<span data-ttu-id="4bd34-112">取得區域變數的 Managed 位置索引。</span><span class="sxs-lookup"><span data-stu-id="4bd34-112">Gets the managed slot index of a local variable.</span></span>|  
|[<span data-ttu-id="4bd34-113">GetValue 方法</span><span class="sxs-lookup"><span data-stu-id="4bd34-113">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getvalue-method.md)|<span data-ttu-id="4bd34-114">取得變數的值做為位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="4bd34-114">Gets the value of a variable as a byte array.</span></span>|  
|[<span data-ttu-id="4bd34-115">SetValue 方法</span><span class="sxs-lookup"><span data-stu-id="4bd34-115">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-setvalue-method.md)|<span data-ttu-id="4bd34-116">指派位元組陣列的值給變數。</span><span class="sxs-lookup"><span data-stu-id="4bd34-116">Assigns the value of a byte array to a variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4bd34-117">備註</span><span class="sxs-lookup"><span data-stu-id="4bd34-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4bd34-118">這個介面僅適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="4bd34-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="4bd34-119">如果您在 .NET 原生之外針對 ICorDebug 案例實作這個介面，Common Language Runtime 會忽略這個介面。</span><span class="sxs-lookup"><span data-stu-id="4bd34-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4bd34-120">需求</span><span class="sxs-lookup"><span data-stu-id="4bd34-120">Requirements</span></span>  
 <span data-ttu-id="4bd34-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4bd34-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bd34-122">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4bd34-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4bd34-123">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4bd34-123">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="4bd34-124">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="4bd34-124">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4bd34-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4bd34-125">See also</span></span>

- [<span data-ttu-id="4bd34-126">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="4bd34-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="4bd34-127">偵錯</span><span class="sxs-lookup"><span data-stu-id="4bd34-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

---
title: "ICorDebugVariableSymbol 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 0e58b85e-69bd-41ff-bedb-8cdc8be6a7a2
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3a09fab1468435212c4437c58c113691e049b1ac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvariablesymbol-interface"></a><span data-ttu-id="70654-102">ICorDebugVariableSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="70654-102">ICorDebugVariableSymbol Interface</span></span>
<span data-ttu-id="70654-103">擷取變數的偵錯符號資訊。</span><span class="sxs-lookup"><span data-stu-id="70654-103">Retrieves the debug symbol information for a variable.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="70654-104">方法</span><span class="sxs-lookup"><span data-stu-id="70654-104">Methods</span></span>  
  
|<span data-ttu-id="70654-105">方法</span><span class="sxs-lookup"><span data-stu-id="70654-105">Method</span></span>|<span data-ttu-id="70654-106">描述</span><span class="sxs-lookup"><span data-stu-id="70654-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="70654-107">GetName 方法</span><span class="sxs-lookup"><span data-stu-id="70654-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getname-method.md)|<span data-ttu-id="70654-108">取得變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="70654-108">Gets the name of a variable.</span></span>|  
|[<span data-ttu-id="70654-109">GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="70654-109">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getsize-method.md)|<span data-ttu-id="70654-110">取得變數的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="70654-110">Gets the size of a variable in bytes.</span></span>|  
|[<span data-ttu-id="70654-111">GetSlotIndex 方法</span><span class="sxs-lookup"><span data-stu-id="70654-111">GetSlotIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getslotindex-method.md)|<span data-ttu-id="70654-112">取得區域變數的 Managed 位置索引。</span><span class="sxs-lookup"><span data-stu-id="70654-112">Gets the managed slot index of a local variable.</span></span>|  
|[<span data-ttu-id="70654-113">GetValue 方法</span><span class="sxs-lookup"><span data-stu-id="70654-113">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getvalue-method.md)|<span data-ttu-id="70654-114">取得變數的值做為位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="70654-114">Gets the value of a variable as a byte array.</span></span>|  
|[<span data-ttu-id="70654-115">SetValue 方法</span><span class="sxs-lookup"><span data-stu-id="70654-115">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-setvalue-method.md)|<span data-ttu-id="70654-116">指派位元組陣列的值給變數。</span><span class="sxs-lookup"><span data-stu-id="70654-116">Assigns the value of a byte array to a variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70654-117">備註</span><span class="sxs-lookup"><span data-stu-id="70654-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="70654-118">這個介面僅適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="70654-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="70654-119">如果您在 .NET 原生之外針對 ICorDebug 案例實作這個介面，Common Language Runtime 會忽略這個介面。</span><span class="sxs-lookup"><span data-stu-id="70654-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70654-120">需求</span><span class="sxs-lookup"><span data-stu-id="70654-120">Requirements</span></span>  
 <span data-ttu-id="70654-121">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="70654-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70654-122">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="70654-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="70654-123">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="70654-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="70654-124">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70654-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70654-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="70654-125">See Also</span></span>  
 [<span data-ttu-id="70654-126">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="70654-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="70654-127">偵錯</span><span class="sxs-lookup"><span data-stu-id="70654-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

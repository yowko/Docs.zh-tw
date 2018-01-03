---
title: "ICorDebugMemoryBuffer 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 85dc2d65-3657-4b93-9f23-9feaa95d37ff
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 98703b07f6601307b5f26aa14b2faf67f8823be5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmemorybuffer-interface"></a><span data-ttu-id="e33d8-102">ICorDebugMemoryBuffer 介面</span><span class="sxs-lookup"><span data-stu-id="e33d8-102">ICorDebugMemoryBuffer Interface</span></span>
<span data-ttu-id="e33d8-103">代表記憶體內部緩衝區。</span><span class="sxs-lookup"><span data-stu-id="e33d8-103">Represents an in-memory buffer.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e33d8-104">方法</span><span class="sxs-lookup"><span data-stu-id="e33d8-104">Methods</span></span>  
  
|<span data-ttu-id="e33d8-105">方法</span><span class="sxs-lookup"><span data-stu-id="e33d8-105">Method</span></span>|<span data-ttu-id="e33d8-106">描述</span><span class="sxs-lookup"><span data-stu-id="e33d8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e33d8-107">GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="e33d8-107">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getsize-method.md)|<span data-ttu-id="e33d8-108">取得以位元組為單位的記憶體緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="e33d8-108">Gets the size of the memory buffer in bytes.</span></span>|  
|[<span data-ttu-id="e33d8-109">GetStartAddress 方法</span><span class="sxs-lookup"><span data-stu-id="e33d8-109">GetStartAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getstartaddress-method.md)|<span data-ttu-id="e33d8-110">取得記憶體緩衝區的起始位址。</span><span class="sxs-lookup"><span data-stu-id="e33d8-110">Gets the starting address of the memory buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e33d8-111">備註</span><span class="sxs-lookup"><span data-stu-id="e33d8-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e33d8-112">這個介面僅適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="e33d8-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="e33d8-113">如果您在 .NET 原生之外針對 ICorDebug 案例實作這個介面，Common Language Runtime 會忽略這個介面。</span><span class="sxs-lookup"><span data-stu-id="e33d8-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e33d8-114">需求</span><span class="sxs-lookup"><span data-stu-id="e33d8-114">Requirements</span></span>  
 <span data-ttu-id="e33d8-115">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e33d8-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e33d8-116">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e33d8-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e33d8-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e33d8-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e33d8-118">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e33d8-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e33d8-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="e33d8-119">See Also</span></span>  
 [<span data-ttu-id="e33d8-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="e33d8-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="e33d8-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="e33d8-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

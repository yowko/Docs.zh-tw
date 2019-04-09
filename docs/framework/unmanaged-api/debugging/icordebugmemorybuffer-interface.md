---
title: ICorDebugMemoryBuffer 介面
ms.date: 03/30/2017
ms.assetid: 85dc2d65-3657-4b93-9f23-9feaa95d37ff
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e12b50e964ec470b843ae35c960f20c5675fd572
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072905"
---
# <a name="icordebugmemorybuffer-interface"></a><span data-ttu-id="c5507-102">ICorDebugMemoryBuffer 介面</span><span class="sxs-lookup"><span data-stu-id="c5507-102">ICorDebugMemoryBuffer Interface</span></span>
<span data-ttu-id="c5507-103">代表記憶體內部緩衝區。</span><span class="sxs-lookup"><span data-stu-id="c5507-103">Represents an in-memory buffer.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c5507-104">方法</span><span class="sxs-lookup"><span data-stu-id="c5507-104">Methods</span></span>  
  
|<span data-ttu-id="c5507-105">方法</span><span class="sxs-lookup"><span data-stu-id="c5507-105">Method</span></span>|<span data-ttu-id="c5507-106">描述</span><span class="sxs-lookup"><span data-stu-id="c5507-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c5507-107">GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="c5507-107">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getsize-method.md)|<span data-ttu-id="c5507-108">取得以位元組為單位的記憶體緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="c5507-108">Gets the size of the memory buffer in bytes.</span></span>|  
|[<span data-ttu-id="c5507-109">GetStartAddress 方法</span><span class="sxs-lookup"><span data-stu-id="c5507-109">GetStartAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getstartaddress-method.md)|<span data-ttu-id="c5507-110">取得記憶體緩衝區的起始位址。</span><span class="sxs-lookup"><span data-stu-id="c5507-110">Gets the starting address of the memory buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5507-111">備註</span><span class="sxs-lookup"><span data-stu-id="c5507-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c5507-112">這個介面僅適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="c5507-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="c5507-113">如果您在 .NET 原生之外針對 ICorDebug 案例實作這個介面，Common Language Runtime 會忽略這個介面。</span><span class="sxs-lookup"><span data-stu-id="c5507-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5507-114">需求</span><span class="sxs-lookup"><span data-stu-id="c5507-114">Requirements</span></span>  
 <span data-ttu-id="c5507-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c5507-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5507-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c5507-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c5507-117">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c5507-117">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="c5507-118">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="c5507-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c5507-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5507-119">See also</span></span>

- [<span data-ttu-id="c5507-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="c5507-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="c5507-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="c5507-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

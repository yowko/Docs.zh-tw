---
title: ICorDebugMemoryBuffer 介面
ms.date: 03/30/2017
ms.assetid: 85dc2d65-3657-4b93-9f23-9feaa95d37ff
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a1bc8e1206b8a82127645362cfe0a124074271c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414399"
---
# <a name="icordebugmemorybuffer-interface"></a><span data-ttu-id="3ba0b-102">ICorDebugMemoryBuffer 介面</span><span class="sxs-lookup"><span data-stu-id="3ba0b-102">ICorDebugMemoryBuffer Interface</span></span>
<span data-ttu-id="3ba0b-103">代表記憶體內部緩衝區。</span><span class="sxs-lookup"><span data-stu-id="3ba0b-103">Represents an in-memory buffer.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3ba0b-104">方法</span><span class="sxs-lookup"><span data-stu-id="3ba0b-104">Methods</span></span>  
  
|<span data-ttu-id="3ba0b-105">方法</span><span class="sxs-lookup"><span data-stu-id="3ba0b-105">Method</span></span>|<span data-ttu-id="3ba0b-106">描述</span><span class="sxs-lookup"><span data-stu-id="3ba0b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3ba0b-107">GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="3ba0b-107">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getsize-method.md)|<span data-ttu-id="3ba0b-108">取得以位元組為單位的記憶體緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="3ba0b-108">Gets the size of the memory buffer in bytes.</span></span>|  
|[<span data-ttu-id="3ba0b-109">GetStartAddress 方法</span><span class="sxs-lookup"><span data-stu-id="3ba0b-109">GetStartAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getstartaddress-method.md)|<span data-ttu-id="3ba0b-110">取得記憶體緩衝區的起始位址。</span><span class="sxs-lookup"><span data-stu-id="3ba0b-110">Gets the starting address of the memory buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ba0b-111">備註</span><span class="sxs-lookup"><span data-stu-id="3ba0b-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3ba0b-112">這個介面僅適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="3ba0b-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="3ba0b-113">如果您在 .NET 原生之外針對 ICorDebug 案例實作這個介面，Common Language Runtime 會忽略這個介面。</span><span class="sxs-lookup"><span data-stu-id="3ba0b-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ba0b-114">需求</span><span class="sxs-lookup"><span data-stu-id="3ba0b-114">Requirements</span></span>  
 <span data-ttu-id="3ba0b-115">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3ba0b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ba0b-116">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3ba0b-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3ba0b-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3ba0b-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3ba0b-118">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ba0b-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ba0b-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ba0b-119">See Also</span></span>  
 [<span data-ttu-id="3ba0b-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="3ba0b-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="3ba0b-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="3ba0b-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

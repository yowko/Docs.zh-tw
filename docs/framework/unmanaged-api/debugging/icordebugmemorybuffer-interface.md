---
title: ICorDebugMemoryBuffer 介面
ms.date: 03/30/2017
ms.assetid: 85dc2d65-3657-4b93-9f23-9feaa95d37ff
ms.openlocfilehash: 60f3b0c3230c524ca7d308d3cb80e50b0693715d
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212330"
---
# <a name="icordebugmemorybuffer-interface"></a><span data-ttu-id="1cc7b-102">ICorDebugMemoryBuffer 介面</span><span class="sxs-lookup"><span data-stu-id="1cc7b-102">ICorDebugMemoryBuffer Interface</span></span>
<span data-ttu-id="1cc7b-103">代表記憶體內部緩衝區。</span><span class="sxs-lookup"><span data-stu-id="1cc7b-103">Represents an in-memory buffer.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1cc7b-104">方法</span><span class="sxs-lookup"><span data-stu-id="1cc7b-104">Methods</span></span>  
  
|<span data-ttu-id="1cc7b-105">方法</span><span class="sxs-lookup"><span data-stu-id="1cc7b-105">Method</span></span>|<span data-ttu-id="1cc7b-106">描述</span><span class="sxs-lookup"><span data-stu-id="1cc7b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1cc7b-107">GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="1cc7b-107">GetSize Method</span></span>](icordebugmemorybuffer-getsize-method.md)|<span data-ttu-id="1cc7b-108">取得以位元組為單位的記憶體緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="1cc7b-108">Gets the size of the memory buffer in bytes.</span></span>|  
|[<span data-ttu-id="1cc7b-109">GetStartAddress 方法</span><span class="sxs-lookup"><span data-stu-id="1cc7b-109">GetStartAddress Method</span></span>](icordebugmemorybuffer-getstartaddress-method.md)|<span data-ttu-id="1cc7b-110">取得記憶體緩衝區的起始位址。</span><span class="sxs-lookup"><span data-stu-id="1cc7b-110">Gets the starting address of the memory buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1cc7b-111">備註</span><span class="sxs-lookup"><span data-stu-id="1cc7b-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1cc7b-112">這個介面僅適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="1cc7b-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="1cc7b-113">如果您在 .NET 原生之外針對 ICorDebug 案例實作這個介面，Common Language Runtime 會忽略這個介面。</span><span class="sxs-lookup"><span data-stu-id="1cc7b-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1cc7b-114">需求</span><span class="sxs-lookup"><span data-stu-id="1cc7b-114">Requirements</span></span>  
 <span data-ttu-id="1cc7b-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1cc7b-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1cc7b-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1cc7b-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1cc7b-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1cc7b-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1cc7b-118">**.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1cc7b-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cc7b-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="1cc7b-119">See also</span></span>

- [<span data-ttu-id="1cc7b-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="1cc7b-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="1cc7b-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="1cc7b-121">Debugging</span></span>](index.md)

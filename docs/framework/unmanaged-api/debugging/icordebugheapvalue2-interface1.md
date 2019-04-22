---
title: ICorDebugHeapValue2 介面
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue2
helpviewer_keywords:
- ICorDebugHeapValue2 interface [.NET Framework debugging]
ms.assetid: 87360a52-90b1-4ada-80c0-589a556116d8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 870de1d3db1e415792437e9763dc13bf8066913f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59159636"
---
# <a name="icordebugheapvalue2-interface"></a><span data-ttu-id="68633-102">ICorDebugHeapValue2 介面</span><span class="sxs-lookup"><span data-stu-id="68633-102">ICorDebugHeapValue2 Interface</span></span>

<span data-ttu-id="68633-103">ICorDebugHeapValue，提供支援，以通用語言執行平台 (CLR) 所處理的延伸模組。</span><span class="sxs-lookup"><span data-stu-id="68633-103">An extension of ICorDebugHeapValue that provides support for common language runtime (CLR) handles.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="68633-104">方法</span><span class="sxs-lookup"><span data-stu-id="68633-104">Methods</span></span>  
  
|<span data-ttu-id="68633-105">方法</span><span class="sxs-lookup"><span data-stu-id="68633-105">Method</span></span>|<span data-ttu-id="68633-106">描述</span><span class="sxs-lookup"><span data-stu-id="68633-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="68633-107">CreateHandle 方法</span><span class="sxs-lookup"><span data-stu-id="68633-107">CreateHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue2-createhandle-method.md)|<span data-ttu-id="68633-108">建立指定型別的控制代碼，這個`ICorDebugHeapValue2`物件。</span><span class="sxs-lookup"><span data-stu-id="68633-108">Creates a handle of the specified type for this `ICorDebugHeapValue2` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68633-109">備註</span><span class="sxs-lookup"><span data-stu-id="68633-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="68633-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="68633-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68633-111">需求</span><span class="sxs-lookup"><span data-stu-id="68633-111">Requirements</span></span>  
 <span data-ttu-id="68633-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="68633-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68633-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="68633-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="68633-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68633-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68633-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68633-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68633-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68633-116">See also</span></span>

- [<span data-ttu-id="68633-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="68633-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

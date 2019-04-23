---
title: ICorDebugAssembly2 介面
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly2
helpviewer_keywords:
- ICorDebugAssembly2 interface [.NET Framework debugging]
ms.assetid: c0766e29-e573-4f9a-a928-167d1de5aa7e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 70eac63855f16205c3d5dbcb28305481b986484c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59201165"
---
# <a name="icordebugassembly2-interface"></a><span data-ttu-id="87914-102">ICorDebugAssembly2 介面</span><span class="sxs-lookup"><span data-stu-id="87914-102">ICorDebugAssembly2 Interface</span></span>

<span data-ttu-id="87914-103">表示組件。</span><span class="sxs-lookup"><span data-stu-id="87914-103">Represents an assembly.</span></span> <span data-ttu-id="87914-104">這個介面是 ICorDebugAssembly 介面的延伸模組。</span><span class="sxs-lookup"><span data-stu-id="87914-104">This interface is an extension of the ICorDebugAssembly interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="87914-105">方法</span><span class="sxs-lookup"><span data-stu-id="87914-105">Methods</span></span>  
  
|<span data-ttu-id="87914-106">方法</span><span class="sxs-lookup"><span data-stu-id="87914-106">Method</span></span>|<span data-ttu-id="87914-107">描述</span><span class="sxs-lookup"><span data-stu-id="87914-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="87914-108">IsFullyTrusted 方法</span><span class="sxs-lookup"><span data-stu-id="87914-108">IsFullyTrusted Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly2-isfullytrusted-method.md)|<span data-ttu-id="87914-109">取得值，指出是否將組件是否已授與完全信任執行階段安全性系統。</span><span class="sxs-lookup"><span data-stu-id="87914-109">Gets a value that indicates whether the assembly has been granted full trust by the runtime security system.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87914-110">備註</span><span class="sxs-lookup"><span data-stu-id="87914-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="87914-111">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="87914-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87914-112">需求</span><span class="sxs-lookup"><span data-stu-id="87914-112">Requirements</span></span>  
 <span data-ttu-id="87914-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="87914-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87914-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="87914-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="87914-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="87914-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87914-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87914-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87914-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87914-117">See also</span></span>

- [<span data-ttu-id="87914-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="87914-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

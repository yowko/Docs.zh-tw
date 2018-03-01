---
title: "ICorDebugMetaDataLocator 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugMetaDataLocator
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMetaDataLocator
helpviewer_keywords:
- ICorDebugMetaDataLocator interface [.NET Framework debugging]
ms.assetid: 287f5ecd-863f-4090-a615-077859f0257b
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: dead97961713f2d19147e242a6161aa9477905a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmetadatalocator-interface"></a><span data-ttu-id="03e5f-102">ICorDebugMetaDataLocator 介面</span><span class="sxs-lookup"><span data-stu-id="03e5f-102">ICorDebugMetaDataLocator Interface</span></span>
<span data-ttu-id="03e5f-103">提供中繼資料資訊給偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="03e5f-103">Provides metadata information to the debugger.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="03e5f-104">方法</span><span class="sxs-lookup"><span data-stu-id="03e5f-104">Methods</span></span>  
  
|<span data-ttu-id="03e5f-105">方法</span><span class="sxs-lookup"><span data-stu-id="03e5f-105">Method</span></span>|<span data-ttu-id="03e5f-106">描述</span><span class="sxs-lookup"><span data-stu-id="03e5f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="03e5f-107">GetMetaData 方法</span><span class="sxs-lookup"><span data-stu-id="03e5f-107">GetMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmetadatalocator-getmetadata-method.md)|<span data-ttu-id="03e5f-108">要求偵錯工具傳回完整路徑到模組，其需要中繼資料以完成偵錯工具的要求。</span><span class="sxs-lookup"><span data-stu-id="03e5f-108">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03e5f-109">備註</span><span class="sxs-lookup"><span data-stu-id="03e5f-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="03e5f-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="03e5f-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03e5f-111">需求</span><span class="sxs-lookup"><span data-stu-id="03e5f-111">Requirements</span></span>  
 <span data-ttu-id="03e5f-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="03e5f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03e5f-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="03e5f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="03e5f-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="03e5f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="03e5f-115">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03e5f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03e5f-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="03e5f-116">See Also</span></span>  
 [<span data-ttu-id="03e5f-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="03e5f-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="03e5f-118">偵錯</span><span class="sxs-lookup"><span data-stu-id="03e5f-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

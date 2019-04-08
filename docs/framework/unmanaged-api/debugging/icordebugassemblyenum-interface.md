---
title: ICorDebugAssemblyEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugAssemblyEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssemblyEnum
helpviewer_keywords:
- ICorDebugAssemblyEnum interface [.NET Framework debugging]
ms.assetid: 891ceb43-5161-421e-a0bf-299962fd7efd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7fef4d757cf528cd3dc7d79db04d33c2cad9bbf1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59189826"
---
# <a name="icordebugassemblyenum-interface"></a><span data-ttu-id="12a90-102">ICorDebugAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="12a90-102">ICorDebugAssemblyEnum Interface</span></span>

<span data-ttu-id="12a90-103">實作 ICorDebugEnum 方法，並列舉 ICorDebugAssembly 陣列。</span><span class="sxs-lookup"><span data-stu-id="12a90-103">Implements ICorDebugEnum methods and enumerates ICorDebugAssembly arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="12a90-104">方法</span><span class="sxs-lookup"><span data-stu-id="12a90-104">Methods</span></span>  
  
|<span data-ttu-id="12a90-105">方法</span><span class="sxs-lookup"><span data-stu-id="12a90-105">Method</span></span>|<span data-ttu-id="12a90-106">描述</span><span class="sxs-lookup"><span data-stu-id="12a90-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="12a90-107">下一個方法</span><span class="sxs-lookup"><span data-stu-id="12a90-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassemblyenum-next-method.md)|<span data-ttu-id="12a90-108">取得指定的數目`ICorDebugAssembly`在列舉中，從目前位置開始的執行個體。</span><span class="sxs-lookup"><span data-stu-id="12a90-108">Gets the specified number of `ICorDebugAssembly` instances in the enumeration, starting from the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12a90-109">備註</span><span class="sxs-lookup"><span data-stu-id="12a90-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="12a90-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="12a90-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12a90-111">需求</span><span class="sxs-lookup"><span data-stu-id="12a90-111">Requirements</span></span>  
 <span data-ttu-id="12a90-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="12a90-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12a90-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="12a90-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="12a90-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12a90-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="12a90-115">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="12a90-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="12a90-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12a90-116">See also</span></span>

- [<span data-ttu-id="12a90-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="12a90-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

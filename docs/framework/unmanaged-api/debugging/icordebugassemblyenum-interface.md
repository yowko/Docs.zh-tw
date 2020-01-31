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
ms.openlocfilehash: 1893f1f08d727606fecda7669719760179bb76f9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76778052"
---
# <a name="icordebugassemblyenum-interface"></a><span data-ttu-id="91c55-102">ICorDebugAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="91c55-102">ICorDebugAssemblyEnum Interface</span></span>

<span data-ttu-id="91c55-103">會執行 ICorDebugEnum 方法並列舉 ICorDebugAssembly 陣列。</span><span class="sxs-lookup"><span data-stu-id="91c55-103">Implements ICorDebugEnum methods and enumerates ICorDebugAssembly arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="91c55-104">方法</span><span class="sxs-lookup"><span data-stu-id="91c55-104">Methods</span></span>  
  
|<span data-ttu-id="91c55-105">方法</span><span class="sxs-lookup"><span data-stu-id="91c55-105">Method</span></span>|<span data-ttu-id="91c55-106">描述</span><span class="sxs-lookup"><span data-stu-id="91c55-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="91c55-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="91c55-107">Next Method</span></span>](icordebugassemblyenum-next-method.md)|<span data-ttu-id="91c55-108">從目前位置開始，取得列舉中指定數目的 `ICorDebugAssembly` 實例。</span><span class="sxs-lookup"><span data-stu-id="91c55-108">Gets the specified number of `ICorDebugAssembly` instances in the enumeration, starting from the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91c55-109">備註</span><span class="sxs-lookup"><span data-stu-id="91c55-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="91c55-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="91c55-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91c55-111">需求</span><span class="sxs-lookup"><span data-stu-id="91c55-111">Requirements</span></span>  
 <span data-ttu-id="91c55-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="91c55-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91c55-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="91c55-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="91c55-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91c55-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91c55-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91c55-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91c55-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="91c55-116">See also</span></span>

- [<span data-ttu-id="91c55-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="91c55-117">Debugging Interfaces</span></span>](debugging-interfaces.md)

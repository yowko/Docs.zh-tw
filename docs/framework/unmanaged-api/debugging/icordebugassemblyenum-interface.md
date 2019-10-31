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
ms.openlocfilehash: aa0bc34c3cb3ac330582cee0843022e913376fc2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192164"
---
# <a name="icordebugassemblyenum-interface"></a><span data-ttu-id="4c5ef-102">ICorDebugAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="4c5ef-102">ICorDebugAssemblyEnum Interface</span></span>

<span data-ttu-id="4c5ef-103">會執行 ICorDebugEnum 方法並列舉 ICorDebugAssembly 陣列。</span><span class="sxs-lookup"><span data-stu-id="4c5ef-103">Implements ICorDebugEnum methods and enumerates ICorDebugAssembly arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4c5ef-104">方法</span><span class="sxs-lookup"><span data-stu-id="4c5ef-104">Methods</span></span>  
  
|<span data-ttu-id="4c5ef-105">方法</span><span class="sxs-lookup"><span data-stu-id="4c5ef-105">Method</span></span>|<span data-ttu-id="4c5ef-106">描述</span><span class="sxs-lookup"><span data-stu-id="4c5ef-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4c5ef-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="4c5ef-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassemblyenum-next-method.md)|<span data-ttu-id="4c5ef-108">從目前位置開始，取得列舉中指定數目的 `ICorDebugAssembly` 實例。</span><span class="sxs-lookup"><span data-stu-id="4c5ef-108">Gets the specified number of `ICorDebugAssembly` instances in the enumeration, starting from the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c5ef-109">備註</span><span class="sxs-lookup"><span data-stu-id="4c5ef-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4c5ef-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="4c5ef-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c5ef-111">需求</span><span class="sxs-lookup"><span data-stu-id="4c5ef-111">Requirements</span></span>  
 <span data-ttu-id="4c5ef-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4c5ef-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c5ef-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4c5ef-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4c5ef-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4c5ef-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4c5ef-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c5ef-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c5ef-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="4c5ef-116">See also</span></span>

- [<span data-ttu-id="4c5ef-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="4c5ef-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

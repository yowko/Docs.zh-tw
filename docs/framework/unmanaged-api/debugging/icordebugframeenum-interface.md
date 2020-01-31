---
title: ICorDebugFrameEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugFrameEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrameEnum
helpviewer_keywords:
- ICorDebugFrameEnum interface [.NET Framework debugging]
ms.assetid: ee3f85d3-044e-46b8-945c-93ebfa5d9e91
topic_type:
- apiref
ms.openlocfilehash: 6cc1ef5f778902efaa53156fbefe334046c82114
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794529"
---
# <a name="icordebugframeenum-interface"></a><span data-ttu-id="cf16a-102">ICorDebugFrameEnum 介面</span><span class="sxs-lookup"><span data-stu-id="cf16a-102">ICorDebugFrameEnum Interface</span></span>

<span data-ttu-id="cf16a-103">會執行 ICorDebugEnum 方法，並列舉 ICorDebugFrame 陣列。</span><span class="sxs-lookup"><span data-stu-id="cf16a-103">Implements ICorDebugEnum methods, and enumerates ICorDebugFrame arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cf16a-104">方法</span><span class="sxs-lookup"><span data-stu-id="cf16a-104">Methods</span></span>  
  
|<span data-ttu-id="cf16a-105">方法</span><span class="sxs-lookup"><span data-stu-id="cf16a-105">Method</span></span>|<span data-ttu-id="cf16a-106">描述</span><span class="sxs-lookup"><span data-stu-id="cf16a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cf16a-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="cf16a-107">Next Method</span></span>](icordebugframeenum-next-method.md)|<span data-ttu-id="cf16a-108">從列舉中取得指定數目的 `ICorDebugFrame` 實例，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="cf16a-108">Gets the specified number of `ICorDebugFrame` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cf16a-109">備註</span><span class="sxs-lookup"><span data-stu-id="cf16a-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cf16a-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="cf16a-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf16a-111">需求</span><span class="sxs-lookup"><span data-stu-id="cf16a-111">Requirements</span></span>  
 <span data-ttu-id="cf16a-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cf16a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf16a-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cf16a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cf16a-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cf16a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cf16a-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf16a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf16a-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="cf16a-116">See also</span></span>

- [<span data-ttu-id="cf16a-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="cf16a-117">Debugging Interfaces</span></span>](debugging-interfaces.md)

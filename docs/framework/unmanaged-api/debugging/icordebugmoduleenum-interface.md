---
title: ICorDebugModuleEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugModuleEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleEnum
helpviewer_keywords:
- ICorDebugModuleEnum interface [.NET Framework debugging]
ms.assetid: 2fb93cd6-6d47-4fdc-a9a0-047726fd03a1
topic_type:
- apiref
ms.openlocfilehash: b019c198635373fa6aaea01914dc9747b7486ae0
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792885"
---
# <a name="icordebugmoduleenum-interface"></a><span data-ttu-id="11638-102">ICorDebugModuleEnum 介面</span><span class="sxs-lookup"><span data-stu-id="11638-102">ICorDebugModuleEnum Interface</span></span>

<span data-ttu-id="11638-103">會執行 ICorDebugEnum 方法，並列舉 ICorDebugModule 陣列。</span><span class="sxs-lookup"><span data-stu-id="11638-103">Implements ICorDebugEnum methods, and enumerates ICorDebugModule arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="11638-104">方法</span><span class="sxs-lookup"><span data-stu-id="11638-104">Methods</span></span>  
  
|<span data-ttu-id="11638-105">方法</span><span class="sxs-lookup"><span data-stu-id="11638-105">Method</span></span>|<span data-ttu-id="11638-106">描述</span><span class="sxs-lookup"><span data-stu-id="11638-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="11638-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="11638-107">Next Method</span></span>](icordebugmoduleenum-next-method.md)|<span data-ttu-id="11638-108">從列舉中取得指定數目的 `ICorDebugModule` 實例，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="11638-108">Gets the specified number of `ICorDebugModule` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11638-109">備註</span><span class="sxs-lookup"><span data-stu-id="11638-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="11638-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="11638-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11638-111">需求</span><span class="sxs-lookup"><span data-stu-id="11638-111">Requirements</span></span>  
 <span data-ttu-id="11638-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="11638-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11638-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="11638-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="11638-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11638-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11638-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11638-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11638-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="11638-116">See also</span></span>

- [<span data-ttu-id="11638-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="11638-117">Debugging Interfaces</span></span>](debugging-interfaces.md)

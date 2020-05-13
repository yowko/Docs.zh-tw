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
ms.openlocfilehash: 4bc8d56bf116cd64e3e1c5d2238e557784c56711
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209587"
---
# <a name="icordebugframeenum-interface"></a><span data-ttu-id="b5430-102">ICorDebugFrameEnum 介面</span><span class="sxs-lookup"><span data-stu-id="b5430-102">ICorDebugFrameEnum Interface</span></span>

<span data-ttu-id="b5430-103">會執行 ICorDebugEnum 方法，並列舉 ICorDebugFrame 陣列。</span><span class="sxs-lookup"><span data-stu-id="b5430-103">Implements ICorDebugEnum methods, and enumerates ICorDebugFrame arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b5430-104">方法</span><span class="sxs-lookup"><span data-stu-id="b5430-104">Methods</span></span>  
  
|<span data-ttu-id="b5430-105">方法</span><span class="sxs-lookup"><span data-stu-id="b5430-105">Method</span></span>|<span data-ttu-id="b5430-106">描述</span><span class="sxs-lookup"><span data-stu-id="b5430-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b5430-107">下一個方法</span><span class="sxs-lookup"><span data-stu-id="b5430-107">Next Method</span></span>](icordebugframeenum-next-method.md)|<span data-ttu-id="b5430-108">`ICorDebugFrame`從列舉中取得指定的實例數目，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="b5430-108">Gets the specified number of `ICorDebugFrame` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5430-109">備註</span><span class="sxs-lookup"><span data-stu-id="b5430-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b5430-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="b5430-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5430-111">需求</span><span class="sxs-lookup"><span data-stu-id="b5430-111">Requirements</span></span>  
 <span data-ttu-id="b5430-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b5430-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5430-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b5430-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b5430-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b5430-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b5430-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5430-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5430-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="b5430-116">See also</span></span>

- [<span data-ttu-id="b5430-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="b5430-117">Debugging Interfaces</span></span>](debugging-interfaces.md)

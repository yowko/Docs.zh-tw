---
title: ICorDebugThreadEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugThreadEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThreadEnum
helpviewer_keywords:
- ICorDebugThreadEnum interface [.NET Framework debugging]
ms.assetid: 796de687-7dd4-4b7b-a10b-8bf22dc7779f
topic_type:
- apiref
ms.openlocfilehash: 6de2cb7c1a1423c5bd38a6f2e5d01c39166ab119
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791324"
---
# <a name="icordebugthreadenum-interface"></a><span data-ttu-id="86702-102">ICorDebugThreadEnum 介面</span><span class="sxs-lookup"><span data-stu-id="86702-102">ICorDebugThreadEnum Interface</span></span>
<span data-ttu-id="86702-103">會執行 ICorDebugEnum 方法並列舉 ICorDebugThread 陣列。</span><span class="sxs-lookup"><span data-stu-id="86702-103">Implements ICorDebugEnum methods and enumerates ICorDebugThread arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="86702-104">方法</span><span class="sxs-lookup"><span data-stu-id="86702-104">Methods</span></span>  
  
|<span data-ttu-id="86702-105">方法</span><span class="sxs-lookup"><span data-stu-id="86702-105">Method</span></span>|<span data-ttu-id="86702-106">描述</span><span class="sxs-lookup"><span data-stu-id="86702-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="86702-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="86702-107">Next Method</span></span>](icordebugthreadenum-next-method.md)|<span data-ttu-id="86702-108">從列舉中取得指定數目的 `ICorDebugThread` 實例，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="86702-108">Gets the specified number of `ICorDebugThread` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86702-109">備註</span><span class="sxs-lookup"><span data-stu-id="86702-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="86702-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="86702-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86702-111">需求</span><span class="sxs-lookup"><span data-stu-id="86702-111">Requirements</span></span>  
 <span data-ttu-id="86702-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="86702-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86702-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="86702-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86702-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86702-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86702-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86702-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86702-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="86702-116">See also</span></span>

- [<span data-ttu-id="86702-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="86702-117">Debugging Interfaces</span></span>](debugging-interfaces.md)

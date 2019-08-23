---
title: ICorDebugChainEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugChainEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChainEnum
helpviewer_keywords:
- ICorDebugChainEnum interface [.NET Framework debugging]
ms.assetid: 6639335c-48e1-4e74-a4f3-70a6a0f54af1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e41cf2ebf0cc64ee7cf720643ae3229cdfbad1ad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969294"
---
# <a name="icordebugchainenum-interface"></a><span data-ttu-id="d0079-102">ICorDebugChainEnum 介面</span><span class="sxs-lookup"><span data-stu-id="d0079-102">ICorDebugChainEnum Interface</span></span>

<span data-ttu-id="d0079-103">會執行 ICorDebugEnum 方法, 並列舉 ICorDebugChain 陣列。</span><span class="sxs-lookup"><span data-stu-id="d0079-103">Implements ICorDebugEnum methods, and enumerates ICorDebugChain arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d0079-104">方法</span><span class="sxs-lookup"><span data-stu-id="d0079-104">Methods</span></span>  
  
|<span data-ttu-id="d0079-105">方法</span><span class="sxs-lookup"><span data-stu-id="d0079-105">Method</span></span>|<span data-ttu-id="d0079-106">說明</span><span class="sxs-lookup"><span data-stu-id="d0079-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d0079-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="d0079-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchainenum-next-method.md)|<span data-ttu-id="d0079-108">從列舉中取得指定`ICorDebugChain`的實例數目, 從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="d0079-108">Gets the specified number of `ICorDebugChain` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0079-109">備註</span><span class="sxs-lookup"><span data-stu-id="d0079-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d0079-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="d0079-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0079-111">需求</span><span class="sxs-lookup"><span data-stu-id="d0079-111">Requirements</span></span>  
 <span data-ttu-id="d0079-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d0079-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0079-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d0079-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d0079-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d0079-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0079-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0079-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0079-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0079-116">See also</span></span>

- [<span data-ttu-id="d0079-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="d0079-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

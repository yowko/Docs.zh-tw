---
title: ICorDebugBreakpointEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpointEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpointEnum
helpviewer_keywords:
- ICorDebugBreakpointEnum interface [.NET Framework debugging]
ms.assetid: 4c6f4f6e-52cc-402e-881b-7b8526544c90
topic_type:
- apiref
ms.openlocfilehash: 97e06a2f20dcc2bb3815b98ba29ff230e37ff29d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730158"
---
# <a name="icordebugbreakpointenum-interface"></a><span data-ttu-id="95a81-102">ICorDebugBreakpointEnum 介面</span><span class="sxs-lookup"><span data-stu-id="95a81-102">ICorDebugBreakpointEnum Interface</span></span>

<span data-ttu-id="95a81-103">會實 ICorDebugEnum 方法，並列舉 ICorDebugBreakpoint 陣列。</span><span class="sxs-lookup"><span data-stu-id="95a81-103">Implements ICorDebugEnum methods, and enumerates ICorDebugBreakpoint arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="95a81-104">方法</span><span class="sxs-lookup"><span data-stu-id="95a81-104">Methods</span></span>  
  
|<span data-ttu-id="95a81-105">方法</span><span class="sxs-lookup"><span data-stu-id="95a81-105">Method</span></span>|<span data-ttu-id="95a81-106">描述</span><span class="sxs-lookup"><span data-stu-id="95a81-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="95a81-107">下一個方法</span><span class="sxs-lookup"><span data-stu-id="95a81-107">Next Method</span></span>](icordebugbreakpointenum-next-method.md)|<span data-ttu-id="95a81-108">`ICorDebugBreakpoint`從目前位置開始，取得列舉的指定實例數目。</span><span class="sxs-lookup"><span data-stu-id="95a81-108">Gets the specified number of `ICorDebugBreakpoint` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95a81-109">備註</span><span class="sxs-lookup"><span data-stu-id="95a81-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="95a81-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="95a81-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95a81-111">需求</span><span class="sxs-lookup"><span data-stu-id="95a81-111">Requirements</span></span>  

 <span data-ttu-id="95a81-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="95a81-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95a81-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="95a81-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="95a81-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="95a81-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="95a81-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95a81-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95a81-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95a81-116">See also</span></span>

- [<span data-ttu-id="95a81-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="95a81-117">Debugging Interfaces</span></span>](debugging-interfaces.md)

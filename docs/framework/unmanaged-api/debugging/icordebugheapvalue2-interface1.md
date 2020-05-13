---
title: ICorDebugHeapValue2 介面
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue2
helpviewer_keywords:
- ICorDebugHeapValue2 interface [.NET Framework debugging]
ms.assetid: 87360a52-90b1-4ada-80c0-589a556116d8
topic_type:
- apiref
ms.openlocfilehash: bf9b0b7a9bcd09d6e4b3a2cecac1f1b1e711b6bb
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213773"
---
# <a name="icordebugheapvalue2-interface"></a><span data-ttu-id="be580-102">ICorDebugHeapValue2 介面</span><span class="sxs-lookup"><span data-stu-id="be580-102">ICorDebugHeapValue2 Interface</span></span>

<span data-ttu-id="be580-103">ICorDebugHeapValue 的延伸模組，可提供 common language runtime （CLR）控制碼的支援。</span><span class="sxs-lookup"><span data-stu-id="be580-103">An extension of ICorDebugHeapValue that provides support for common language runtime (CLR) handles.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="be580-104">方法</span><span class="sxs-lookup"><span data-stu-id="be580-104">Methods</span></span>  
  
|<span data-ttu-id="be580-105">方法</span><span class="sxs-lookup"><span data-stu-id="be580-105">Method</span></span>|<span data-ttu-id="be580-106">描述</span><span class="sxs-lookup"><span data-stu-id="be580-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="be580-107">CreateHandle 方法</span><span class="sxs-lookup"><span data-stu-id="be580-107">CreateHandle Method</span></span>](icordebugheapvalue2-createhandle-method.md)|<span data-ttu-id="be580-108">建立這個物件之指定類型的控制碼 `ICorDebugHeapValue2` 。</span><span class="sxs-lookup"><span data-stu-id="be580-108">Creates a handle of the specified type for this `ICorDebugHeapValue2` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="be580-109">備註</span><span class="sxs-lookup"><span data-stu-id="be580-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="be580-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="be580-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be580-111">需求</span><span class="sxs-lookup"><span data-stu-id="be580-111">Requirements</span></span>  
 <span data-ttu-id="be580-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="be580-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be580-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="be580-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="be580-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be580-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be580-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be580-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be580-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="be580-116">See also</span></span>

- [<span data-ttu-id="be580-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="be580-117">Debugging Interfaces</span></span>](debugging-interfaces.md)

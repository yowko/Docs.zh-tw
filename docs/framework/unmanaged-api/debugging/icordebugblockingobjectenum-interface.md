---
title: ICorDebugBlockingObjectEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugBlockingObjectEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBlockingObjectEnum
helpviewer_keywords:
- ICorDebugBlockingObjectEnum interface [.NET Framework debugging]
ms.assetid: 208e5c2d-3f3f-404e-8b3c-7cccc14ddb16
topic_type:
- apiref
ms.openlocfilehash: 8be4332da77c3fbf4229a3fbeb9ba835a7a13eee
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894798"
---
# <a name="icordebugblockingobjectenum-interface"></a><span data-ttu-id="8c0bd-102">ICorDebugBlockingObjectEnum 介面</span><span class="sxs-lookup"><span data-stu-id="8c0bd-102">ICorDebugBlockingObjectEnum Interface</span></span>
<span data-ttu-id="8c0bd-103">提供[CorDebugBlockingObject](cordebugblockingobject-structure.md)結構清單的列舉值。</span><span class="sxs-lookup"><span data-stu-id="8c0bd-103">Provides an enumerator for a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span> <span data-ttu-id="8c0bd-104">這個介面是 ICorDebugEnum 介面的子類別。</span><span class="sxs-lookup"><span data-stu-id="8c0bd-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8c0bd-105">方法</span><span class="sxs-lookup"><span data-stu-id="8c0bd-105">Methods</span></span>  
  
|<span data-ttu-id="8c0bd-106">方法</span><span class="sxs-lookup"><span data-stu-id="8c0bd-106">Method</span></span>|<span data-ttu-id="8c0bd-107">描述</span><span class="sxs-lookup"><span data-stu-id="8c0bd-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8c0bd-108">下一個方法</span><span class="sxs-lookup"><span data-stu-id="8c0bd-108">Next Method</span></span>](icordebugblockingobjectenum-next-method.md)|<span data-ttu-id="8c0bd-109">列舉[CorDebugBlockingObject](cordebugblockingobject-structure.md)結構的清單。</span><span class="sxs-lookup"><span data-stu-id="8c0bd-109">Enumerates through a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c0bd-110">備註</span><span class="sxs-lookup"><span data-stu-id="8c0bd-110">Remarks</span></span>  
 <span data-ttu-id="8c0bd-111">每個 `CorDebugBlockingObject` 結構各代表一個封鎖執行緒的物件。</span><span class="sxs-lookup"><span data-stu-id="8c0bd-111">Each `CorDebugBlockingObject` structure represents an object that is blocking a thread.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8c0bd-112">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="8c0bd-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c0bd-113">需求</span><span class="sxs-lookup"><span data-stu-id="8c0bd-113">Requirements</span></span>  
 <span data-ttu-id="8c0bd-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8c0bd-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c0bd-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8c0bd-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8c0bd-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8c0bd-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c0bd-117">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c0bd-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c0bd-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c0bd-118">See also</span></span>

- [<span data-ttu-id="8c0bd-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="8c0bd-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="8c0bd-120">偵錯</span><span class="sxs-lookup"><span data-stu-id="8c0bd-120">Debugging</span></span>](index.md)

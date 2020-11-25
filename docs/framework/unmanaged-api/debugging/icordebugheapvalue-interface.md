---
title: ICorDebugHeapValue 介面
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue
helpviewer_keywords:
- ICorDebugHeapValue interface [.NET Framework debugging]
ms.assetid: 1bca66db-0359-4ae8-846e-e35f7e547e8b
topic_type:
- apiref
ms.openlocfilehash: ee3ea319360bba1a113c15daf8cf143ea512e5cd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733317"
---
# <a name="icordebugheapvalue-interface"></a><span data-ttu-id="bbf6e-102">ICorDebugHeapValue 介面</span><span class="sxs-lookup"><span data-stu-id="bbf6e-102">ICorDebugHeapValue Interface</span></span>

<span data-ttu-id="bbf6e-103">"ICorDebugValue" 的子類別，代表 common language runtime (CLR) 垃圾收集行程所收集的物件。</span><span class="sxs-lookup"><span data-stu-id="bbf6e-103">A subclass of "ICorDebugValue" that represents an object that has been collected by the common language runtime (CLR) garbage collector.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bbf6e-104">方法</span><span class="sxs-lookup"><span data-stu-id="bbf6e-104">Methods</span></span>  
  
|<span data-ttu-id="bbf6e-105">方法</span><span class="sxs-lookup"><span data-stu-id="bbf6e-105">Method</span></span>|<span data-ttu-id="bbf6e-106">描述</span><span class="sxs-lookup"><span data-stu-id="bbf6e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bbf6e-107">CreateRelocBreakpoint 方法</span><span class="sxs-lookup"><span data-stu-id="bbf6e-107">CreateRelocBreakpoint Method</span></span>](icordebugheapvalue-createrelocbreakpoint-method.md)|<span data-ttu-id="bbf6e-108">未實作。</span><span class="sxs-lookup"><span data-stu-id="bbf6e-108">Not implemented.</span></span>|  
|[<span data-ttu-id="bbf6e-109">IsValid 方法</span><span class="sxs-lookup"><span data-stu-id="bbf6e-109">IsValid Method</span></span>](icordebugheapvalue-isvalid-method.md)|<span data-ttu-id="bbf6e-110">取得值，這個值表示這個所表示的物件是否 `ICorDebugHeapValue` 有效，或是否已由垃圾收集行程回收。</span><span class="sxs-lookup"><span data-stu-id="bbf6e-110">Gets a value that indicates whether the object represented by this `ICorDebugHeapValue` is valid, or has been reclaimed by the garbage collector.</span></span> <span data-ttu-id="bbf6e-111">在 .NET Framework 版本2.0 中，此方法已被取代。</span><span class="sxs-lookup"><span data-stu-id="bbf6e-111">This method has been deprecated in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bbf6e-112">備註</span><span class="sxs-lookup"><span data-stu-id="bbf6e-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bbf6e-113">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="bbf6e-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbf6e-114">需求</span><span class="sxs-lookup"><span data-stu-id="bbf6e-114">Requirements</span></span>  

 <span data-ttu-id="bbf6e-115">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bbf6e-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbf6e-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bbf6e-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bbf6e-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bbf6e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bbf6e-118">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbf6e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbf6e-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bbf6e-119">See also</span></span>

- [<span data-ttu-id="bbf6e-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="bbf6e-120">Debugging Interfaces</span></span>](debugging-interfaces.md)

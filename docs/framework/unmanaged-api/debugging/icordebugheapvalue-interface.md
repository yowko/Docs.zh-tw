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
ms.openlocfilehash: fa31b8a6cc96935319e9bef3e561790b65e33a87
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777582"
---
# <a name="icordebugheapvalue-interface"></a><span data-ttu-id="fffc6-102">ICorDebugHeapValue 介面</span><span class="sxs-lookup"><span data-stu-id="fffc6-102">ICorDebugHeapValue Interface</span></span>

<span data-ttu-id="fffc6-103">"ICorDebugValue" 的子類別，代表由 common language runtime （CLR）垃圾收集行程所收集的物件。</span><span class="sxs-lookup"><span data-stu-id="fffc6-103">A subclass of "ICorDebugValue" that represents an object that has been collected by the common language runtime (CLR) garbage collector.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fffc6-104">方法</span><span class="sxs-lookup"><span data-stu-id="fffc6-104">Methods</span></span>  
  
|<span data-ttu-id="fffc6-105">方法</span><span class="sxs-lookup"><span data-stu-id="fffc6-105">Method</span></span>|<span data-ttu-id="fffc6-106">描述</span><span class="sxs-lookup"><span data-stu-id="fffc6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fffc6-107">CreateRelocBreakpoint 方法</span><span class="sxs-lookup"><span data-stu-id="fffc6-107">CreateRelocBreakpoint Method</span></span>](icordebugheapvalue-createrelocbreakpoint-method.md)|<span data-ttu-id="fffc6-108">未實作。</span><span class="sxs-lookup"><span data-stu-id="fffc6-108">Not implemented.</span></span>|  
|[<span data-ttu-id="fffc6-109">IsValid 方法</span><span class="sxs-lookup"><span data-stu-id="fffc6-109">IsValid Method</span></span>](icordebugheapvalue-isvalid-method.md)|<span data-ttu-id="fffc6-110">取得值，指出此 `ICorDebugHeapValue` 所表示的物件是否有效，或是否已由垃圾收集行程回收。</span><span class="sxs-lookup"><span data-stu-id="fffc6-110">Gets a value that indicates whether the object represented by this `ICorDebugHeapValue` is valid, or has been reclaimed by the garbage collector.</span></span> <span data-ttu-id="fffc6-111">這個方法已在 .NET Framework 版本2.0 中被取代。</span><span class="sxs-lookup"><span data-stu-id="fffc6-111">This method has been deprecated in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fffc6-112">備註</span><span class="sxs-lookup"><span data-stu-id="fffc6-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fffc6-113">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="fffc6-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fffc6-114">需求</span><span class="sxs-lookup"><span data-stu-id="fffc6-114">Requirements</span></span>  
 <span data-ttu-id="fffc6-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fffc6-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fffc6-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fffc6-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fffc6-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fffc6-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fffc6-118">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fffc6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fffc6-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="fffc6-119">See also</span></span>

- [<span data-ttu-id="fffc6-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="fffc6-120">Debugging Interfaces</span></span>](debugging-interfaces.md)

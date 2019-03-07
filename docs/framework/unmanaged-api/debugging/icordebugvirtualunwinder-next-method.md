---
title: ICorDebugVirtualUnwinder::Next 方法
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c05fcc9a40c3d47949b547164dc56f6a2246838
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468906"
---
# <a name="icordebugvirtualunwindernext-method"></a><span data-ttu-id="c6133-102">ICorDebugVirtualUnwinder::Next 方法</span><span class="sxs-lookup"><span data-stu-id="c6133-102">ICorDebugVirtualUnwinder::Next Method</span></span>
<span data-ttu-id="c6133-103">進入呼叫端的內容。</span><span class="sxs-lookup"><span data-stu-id="c6133-103">Advances to the caller's context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6133-104">語法</span><span class="sxs-lookup"><span data-stu-id="c6133-104">Syntax</span></span>  
  
```  
HRESULT Next();  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6133-105">參數</span><span class="sxs-lookup"><span data-stu-id="c6133-105">Parameters</span></span>  
 <span data-ttu-id="c6133-106">無。</span><span class="sxs-lookup"><span data-stu-id="c6133-106">None.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c6133-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="c6133-107">Return Value</span></span>  
 <span data-ttu-id="c6133-108">如果成功發生回溯，會傳回 `S_OK`，如果因為沒有更多框架，而無法完成回溯，則傳回 `CORDBG_S_AT_END_OF_STACK`。</span><span class="sxs-lookup"><span data-stu-id="c6133-108">`S_OK` if the unwind occurred successfully, or `CORDBG_S_AT_END_OF_STACK` if the unwind cannot be completed because there are no more frames.</span></span>  
  
 <span data-ttu-id="c6133-109">如果傳回失敗的 HRESULT，ICorDebug 應用程式開發介面會傳回 `CORDBG_E_DATA_TARGET_ERROR`。</span><span class="sxs-lookup"><span data-stu-id="c6133-109">If a failing HRESULT is returned, ICorDebug APIs will return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6133-110">備註</span><span class="sxs-lookup"><span data-stu-id="c6133-110">Remarks</span></span>  
 <span data-ttu-id="c6133-111">堆疊查核器應該會確保其繼續進行，以致於最後呼叫 `Next` 時，會傳回失敗 HRESULT 或 `CORDBG_S_AT_END_OF_STACK`。</span><span class="sxs-lookup"><span data-stu-id="c6133-111">The stack walker should ensure that it makes forward progress, so that eventually a call to `Next` will return a failing HRESULT or `CORDBG_S_AT_END_OF_STACK`.</span></span> <span data-ttu-id="c6133-112">傳回`S_OK`無限期可能會造成無限迴圈。</span><span class="sxs-lookup"><span data-stu-id="c6133-112">Returning `S_OK` indefinitely may cause an infinite loop.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6133-113">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="c6133-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6133-114">需求</span><span class="sxs-lookup"><span data-stu-id="c6133-114">Requirements</span></span>  
 <span data-ttu-id="c6133-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c6133-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6133-116">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c6133-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c6133-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c6133-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6133-118">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6133-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6133-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6133-119">See also</span></span>
- [<span data-ttu-id="c6133-120">ICorDebugMemoryBuffer 介面</span><span class="sxs-lookup"><span data-stu-id="c6133-120">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="c6133-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="c6133-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

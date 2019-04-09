---
title: 'Icordebugvirtualunwinder:: Next 方法'
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 74be827dc97213507b96da9e025923f859011acd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076883"
---
# <a name="icordebugvirtualunwindernext-method"></a><span data-ttu-id="9f99e-102">Icordebugvirtualunwinder:: Next 方法</span><span class="sxs-lookup"><span data-stu-id="9f99e-102">ICorDebugVirtualUnwinder::Next Method</span></span>
<span data-ttu-id="9f99e-103">進入呼叫端的內容。</span><span class="sxs-lookup"><span data-stu-id="9f99e-103">Advances to the caller's context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f99e-104">語法</span><span class="sxs-lookup"><span data-stu-id="9f99e-104">Syntax</span></span>  
  
```  
HRESULT Next();  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f99e-105">參數</span><span class="sxs-lookup"><span data-stu-id="9f99e-105">Parameters</span></span>  
 <span data-ttu-id="9f99e-106">無。</span><span class="sxs-lookup"><span data-stu-id="9f99e-106">None.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9f99e-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="9f99e-107">Return Value</span></span>  
 `S_OK` <span data-ttu-id="9f99e-108">如果順利進行回溯或`CORDBG_S_AT_END_OF_STACK`如果無法完成回溯，因為有更多框架。</span><span class="sxs-lookup"><span data-stu-id="9f99e-108">if the unwind occurred successfully, or `CORDBG_S_AT_END_OF_STACK` if the unwind cannot be completed because there are no more frames.</span></span>  
  
 <span data-ttu-id="9f99e-109">如果傳回失敗的 HRESULT，ICorDebug 應用程式開發介面會傳回 `CORDBG_E_DATA_TARGET_ERROR`。</span><span class="sxs-lookup"><span data-stu-id="9f99e-109">If a failing HRESULT is returned, ICorDebug APIs will return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f99e-110">備註</span><span class="sxs-lookup"><span data-stu-id="9f99e-110">Remarks</span></span>  
 <span data-ttu-id="9f99e-111">堆疊查核器應該會確保其繼續進行，以致於最後呼叫 `Next` 時，會傳回失敗 HRESULT 或 `CORDBG_S_AT_END_OF_STACK`。</span><span class="sxs-lookup"><span data-stu-id="9f99e-111">The stack walker should ensure that it makes forward progress, so that eventually a call to `Next` will return a failing HRESULT or `CORDBG_S_AT_END_OF_STACK`.</span></span> <span data-ttu-id="9f99e-112">傳回`S_OK`無限期可能會造成無限迴圈。</span><span class="sxs-lookup"><span data-stu-id="9f99e-112">Returning `S_OK` indefinitely may cause an infinite loop.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9f99e-113">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="9f99e-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f99e-114">需求</span><span class="sxs-lookup"><span data-stu-id="9f99e-114">Requirements</span></span>  
 <span data-ttu-id="9f99e-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9f99e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f99e-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9f99e-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9f99e-117">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9f99e-117">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="9f99e-118">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="9f99e-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9f99e-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9f99e-119">See also</span></span>

- [<span data-ttu-id="9f99e-120">ICorDebugMemoryBuffer 介面</span><span class="sxs-lookup"><span data-stu-id="9f99e-120">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="9f99e-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="9f99e-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

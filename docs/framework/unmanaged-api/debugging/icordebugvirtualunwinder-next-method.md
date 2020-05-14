---
title: ICorDebugVirtualUnwinder::Next 方法
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
ms.openlocfilehash: 55f10a6148f0b11cf74492afe947d5921a1d1458
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396431"
---
# <a name="icordebugvirtualunwindernext-method"></a><span data-ttu-id="bf9b4-102">ICorDebugVirtualUnwinder::Next 方法</span><span class="sxs-lookup"><span data-stu-id="bf9b4-102">ICorDebugVirtualUnwinder::Next Method</span></span>
<span data-ttu-id="bf9b4-103">進入呼叫端的內容。</span><span class="sxs-lookup"><span data-stu-id="bf9b4-103">Advances to the caller's context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf9b4-104">語法</span><span class="sxs-lookup"><span data-stu-id="bf9b4-104">Syntax</span></span>  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf9b4-105">參數</span><span class="sxs-lookup"><span data-stu-id="bf9b4-105">Parameters</span></span>  
 <span data-ttu-id="bf9b4-106">無。</span><span class="sxs-lookup"><span data-stu-id="bf9b4-106">None.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bf9b4-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="bf9b4-107">Return Value</span></span>  
 <span data-ttu-id="bf9b4-108">如果成功發生回溯，會傳回 `S_OK`，如果因為沒有更多框架，而無法完成回溯，則傳回 `CORDBG_S_AT_END_OF_STACK`。</span><span class="sxs-lookup"><span data-stu-id="bf9b4-108">`S_OK` if the unwind occurred successfully, or `CORDBG_S_AT_END_OF_STACK` if the unwind cannot be completed because there are no more frames.</span></span>  
  
 <span data-ttu-id="bf9b4-109">如果傳回失敗的 HRESULT，ICorDebug 應用程式開發介面會傳回 `CORDBG_E_DATA_TARGET_ERROR`。</span><span class="sxs-lookup"><span data-stu-id="bf9b4-109">If a failing HRESULT is returned, ICorDebug APIs will return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf9b4-110">備註</span><span class="sxs-lookup"><span data-stu-id="bf9b4-110">Remarks</span></span>  
 <span data-ttu-id="bf9b4-111">堆疊查核器應該會確保其繼續進行，以致於最後呼叫 `Next` 時，會傳回失敗 HRESULT 或 `CORDBG_S_AT_END_OF_STACK`。</span><span class="sxs-lookup"><span data-stu-id="bf9b4-111">The stack walker should ensure that it makes forward progress, so that eventually a call to `Next` will return a failing HRESULT or `CORDBG_S_AT_END_OF_STACK`.</span></span> <span data-ttu-id="bf9b4-112">`S_OK`無限期地傳回可能會造成無限迴圈。</span><span class="sxs-lookup"><span data-stu-id="bf9b4-112">Returning `S_OK` indefinitely may cause an infinite loop.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bf9b4-113">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="bf9b4-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf9b4-114">需求</span><span class="sxs-lookup"><span data-stu-id="bf9b4-114">Requirements</span></span>  
 <span data-ttu-id="bf9b4-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bf9b4-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf9b4-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bf9b4-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bf9b4-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf9b4-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf9b4-118">**.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf9b4-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf9b4-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="bf9b4-119">See also</span></span>

- [<span data-ttu-id="bf9b4-120">ICorDebugMemoryBuffer 介面</span><span class="sxs-lookup"><span data-stu-id="bf9b4-120">ICorDebugMemoryBuffer Interface</span></span>](icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="bf9b4-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="bf9b4-121">Debugging Interfaces</span></span>](debugging-interfaces.md)

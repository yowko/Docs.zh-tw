---
title: ICorDebugNativeFrame::SetIP 方法
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.SetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::SetIP
helpviewer_keywords:
- ICorDebugNativeFrame::SetIP method [.NET Framework debugging]
- SetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 57784a51-c76d-48f8-9392-584d0e1946d9
topic_type:
- apiref
ms.openlocfilehash: 65de42a0b86e4b4593b7880e9dc290ce00007a40
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709254"
---
# <a name="icordebugnativeframesetip-method"></a><span data-ttu-id="b625c-102">ICorDebugNativeFrame::SetIP 方法</span><span class="sxs-lookup"><span data-stu-id="b625c-102">ICorDebugNativeFrame::SetIP Method</span></span>

<span data-ttu-id="b625c-103">將指令指標設定為原生程式碼中指定的位移位置。</span><span class="sxs-lookup"><span data-stu-id="b625c-103">Sets the instruction pointer to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b625c-104">語法</span><span class="sxs-lookup"><span data-stu-id="b625c-104">Syntax</span></span>  
  
```cpp  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b625c-105">參數</span><span class="sxs-lookup"><span data-stu-id="b625c-105">Parameters</span></span>  

 `nOffset`  
 <span data-ttu-id="b625c-106">在原生程式碼中的位移位置。</span><span class="sxs-lookup"><span data-stu-id="b625c-106">[in] The offset location in the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b625c-107">備註</span><span class="sxs-lookup"><span data-stu-id="b625c-107">Remarks</span></span>  

 <span data-ttu-id="b625c-108">呼叫以 `SetIP` 立即使目前線程的所有框架和鏈失效。</span><span class="sxs-lookup"><span data-stu-id="b625c-108">Calls to `SetIP` immediately invalidate all frames and chains for the current thread.</span></span> <span data-ttu-id="b625c-109">如果偵錯工具在呼叫之後需要框架資訊 `SetIP` ，則必須執行新的堆疊追蹤。</span><span class="sxs-lookup"><span data-stu-id="b625c-109">If the debugger needs frame information after a call to `SetIP`, it must perform a new stack trace.</span></span>  
  
 <span data-ttu-id="b625c-110">[ICorDebug](icordebug-interface.md) 會嘗試將堆疊框架保持在有效的狀態。</span><span class="sxs-lookup"><span data-stu-id="b625c-110">[ICorDebug](icordebug-interface.md) will attempt to keep the stack frame in a valid state.</span></span> <span data-ttu-id="b625c-111">但是，即使框架處於有效的狀態，但在執行時間中，還是可能發生問題，例如未初始化的區域變數等等。</span><span class="sxs-lookup"><span data-stu-id="b625c-111">However, even if the frame is in a valid state, as far as the runtime is concerned, there still may be problems, such as uninitialized local variables, and so on.</span></span> <span data-ttu-id="b625c-112">呼叫端負責確保執行中程式的一致性。</span><span class="sxs-lookup"><span data-stu-id="b625c-112">The caller is responsible for insuring coherency of the running program.</span></span>  
  
 <span data-ttu-id="b625c-113">在64位平臺上，指令指標無法移出 `catch` 或 `finally` 封鎖。</span><span class="sxs-lookup"><span data-stu-id="b625c-113">On 64-bit platforms, the instruction pointer cannot be moved out of a `catch` or `finally` block.</span></span> <span data-ttu-id="b625c-114">如果 `SetIP` 呼叫以在64位平臺上進行這類移動，它會傳回指出失敗的 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="b625c-114">If `SetIP` is called to make such a move on a 64-bit platform, it will return an HRESULT indicating failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b625c-115">需求</span><span class="sxs-lookup"><span data-stu-id="b625c-115">Requirements</span></span>  

 <span data-ttu-id="b625c-116">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b625c-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b625c-117">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b625c-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b625c-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b625c-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b625c-119">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b625c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b625c-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b625c-120">See also</span></span>

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
ms.openlocfilehash: 786c0e7b38c74fd02dd6f7536af1899f295b0305
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206448"
---
# <a name="icordebugnativeframesetip-method"></a><span data-ttu-id="ab219-102">ICorDebugNativeFrame::SetIP 方法</span><span class="sxs-lookup"><span data-stu-id="ab219-102">ICorDebugNativeFrame::SetIP Method</span></span>
<span data-ttu-id="ab219-103">將指令指標設定為原生程式碼中指定的位移位置。</span><span class="sxs-lookup"><span data-stu-id="ab219-103">Sets the instruction pointer to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab219-104">語法</span><span class="sxs-lookup"><span data-stu-id="ab219-104">Syntax</span></span>  
  
```cpp  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab219-105">參數</span><span class="sxs-lookup"><span data-stu-id="ab219-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="ab219-106">在機器碼中的位移位置。</span><span class="sxs-lookup"><span data-stu-id="ab219-106">[in] The offset location in the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab219-107">備註</span><span class="sxs-lookup"><span data-stu-id="ab219-107">Remarks</span></span>  
 <span data-ttu-id="ab219-108">呼叫會 `SetIP` 立即使目前線程的所有框架和鏈失效。</span><span class="sxs-lookup"><span data-stu-id="ab219-108">Calls to `SetIP` immediately invalidate all frames and chains for the current thread.</span></span> <span data-ttu-id="ab219-109">如果偵錯工具在呼叫之後需要框架資訊 `SetIP` ，則必須執行新的堆疊追蹤。</span><span class="sxs-lookup"><span data-stu-id="ab219-109">If the debugger needs frame information after a call to `SetIP`, it must perform a new stack trace.</span></span>  
  
 <span data-ttu-id="ab219-110">[ICorDebug](icordebug-interface.md)會嘗試將堆疊框架保持在有效的狀態。</span><span class="sxs-lookup"><span data-stu-id="ab219-110">[ICorDebug](icordebug-interface.md) will attempt to keep the stack frame in a valid state.</span></span> <span data-ttu-id="ab219-111">不過，即使畫面格處於有效的狀態，只要執行時間關心，仍然可能會有問題，例如未初始化的區域變數等等。</span><span class="sxs-lookup"><span data-stu-id="ab219-111">However, even if the frame is in a valid state, as far as the runtime is concerned, there still may be problems, such as uninitialized local variables, and so on.</span></span> <span data-ttu-id="ab219-112">呼叫端負責確保執行中程式的一致性。</span><span class="sxs-lookup"><span data-stu-id="ab219-112">The caller is responsible for insuring coherency of the running program.</span></span>  
  
 <span data-ttu-id="ab219-113">在64位平臺上，無法將指令指標移出 `catch` 或 `finally` 區塊。</span><span class="sxs-lookup"><span data-stu-id="ab219-113">On 64-bit platforms, the instruction pointer cannot be moved out of a `catch` or `finally` block.</span></span> <span data-ttu-id="ab219-114">如果 `SetIP` 呼叫以在64位平臺上進行這類移動，則會傳回表示失敗的 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="ab219-114">If `SetIP` is called to make such a move on a 64-bit platform, it will return an HRESULT indicating failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab219-115">需求</span><span class="sxs-lookup"><span data-stu-id="ab219-115">Requirements</span></span>  
 <span data-ttu-id="ab219-116">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ab219-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab219-117">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ab219-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ab219-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab219-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab219-119">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab219-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab219-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab219-120">See also</span></span>

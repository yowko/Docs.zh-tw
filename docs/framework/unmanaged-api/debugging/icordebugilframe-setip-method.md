---
title: ICorDebugILFrame::SetIP 方法
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.SetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::SetIP
helpviewer_keywords:
- SetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::SetIP method [.NET Framework debugging]
ms.assetid: 23f38dc1-85e4-4263-9235-2d05bbb6a833
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a25e52c6b858aaa602ffade0e407b1aaf6e5c67e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995580"
---
# <a name="icordebugilframesetip-method"></a><span data-ttu-id="74909-102">ICorDebugILFrame::SetIP 方法</span><span class="sxs-lookup"><span data-stu-id="74909-102">ICorDebugILFrame::SetIP Method</span></span>
<span data-ttu-id="74909-103">設定指令指標到 Microsoft intermediate language (MSIL) 程式碼中指定的位移位置。</span><span class="sxs-lookup"><span data-stu-id="74909-103">Sets the instruction pointer to the specified offset location in the Microsoft intermediate language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74909-104">語法</span><span class="sxs-lookup"><span data-stu-id="74909-104">Syntax</span></span>  
  
```  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74909-105">參數</span><span class="sxs-lookup"><span data-stu-id="74909-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="74909-106">MSIL 程式碼中的位移的位置。</span><span class="sxs-lookup"><span data-stu-id="74909-106">The offset location in the MSIL code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74909-107">備註</span><span class="sxs-lookup"><span data-stu-id="74909-107">Remarks</span></span>  
 <span data-ttu-id="74909-108">呼叫`SetIP`立即使其失效，所有的框架和目前執行緒的鏈結。</span><span class="sxs-lookup"><span data-stu-id="74909-108">Calls to `SetIP` immediately invalidate all frames and chains for the current thread.</span></span> <span data-ttu-id="74909-109">如果偵錯工具必須在呼叫之後的畫面格資訊`SetIP`，它必須執行新的堆疊追蹤。</span><span class="sxs-lookup"><span data-stu-id="74909-109">If the debugger needs frame information after a call to `SetIP`, it must perform a new stack trace.</span></span>  
  
 <span data-ttu-id="74909-110">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)會嘗試將保留的堆疊框架處於有效狀態。</span><span class="sxs-lookup"><span data-stu-id="74909-110">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) will attempt to keep the stack frame in a valid state.</span></span> <span data-ttu-id="74909-111">不過，即使框架是處於有效狀態，仍可能有問題，例如未初始化的本機變數。</span><span class="sxs-lookup"><span data-stu-id="74909-111">However, even if the frame is in a valid state, there still may be problems such as uninitialized local variables.</span></span> <span data-ttu-id="74909-112">呼叫端會負責確保執行程式的一致性。</span><span class="sxs-lookup"><span data-stu-id="74909-112">The caller is responsible for ensuring the coherency of the running program.</span></span>  
  
 <span data-ttu-id="74909-113">在 64 位元平台，指令指標無法移出`catch`或`finally`區塊。</span><span class="sxs-lookup"><span data-stu-id="74909-113">On 64-bit platforms, the instruction pointer cannot be moved out of a `catch` or `finally` block.</span></span> <span data-ttu-id="74909-114">如果`SetIP`呼叫進行的 64 位元平台上的這類移動，它會傳回 HRESULT，指出失敗。</span><span class="sxs-lookup"><span data-stu-id="74909-114">If `SetIP` is called to make such a move on a 64-bit platform, it will return an HRESULT indicating failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74909-115">需求</span><span class="sxs-lookup"><span data-stu-id="74909-115">Requirements</span></span>  
 <span data-ttu-id="74909-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="74909-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74909-117">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="74909-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="74909-118">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="74909-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74909-119">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74909-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

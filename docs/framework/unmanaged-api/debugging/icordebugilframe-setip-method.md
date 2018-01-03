---
title: "ICorDebugILFrame::SetIP 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame.SetIP
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame::SetIP
helpviewer_keywords:
- SetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::SetIP method [.NET Framework debugging]
ms.assetid: 23f38dc1-85e4-4263-9235-2d05bbb6a833
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: daffbbd9e961f4fdc7ff2e3c9be57e41e8fa3f78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframesetip-method"></a><span data-ttu-id="46aeb-102">ICorDebugILFrame::SetIP 方法</span><span class="sxs-lookup"><span data-stu-id="46aeb-102">ICorDebugILFrame::SetIP Method</span></span>
<span data-ttu-id="46aeb-103">將指令指標設定為 Microsoft intermediate language (MSIL) 程式碼中指定的位移位置。</span><span class="sxs-lookup"><span data-stu-id="46aeb-103">Sets the instruction pointer to the specified offset location in the Microsoft intermediate language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46aeb-104">語法</span><span class="sxs-lookup"><span data-stu-id="46aeb-104">Syntax</span></span>  
  
```  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="46aeb-105">參數</span><span class="sxs-lookup"><span data-stu-id="46aeb-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="46aeb-106">MSIL 程式碼中的位移的位置。</span><span class="sxs-lookup"><span data-stu-id="46aeb-106">The offset location in the MSIL code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46aeb-107">備註</span><span class="sxs-lookup"><span data-stu-id="46aeb-107">Remarks</span></span>  
 <span data-ttu-id="46aeb-108">呼叫`SetIP`立即使所有框架和目前執行緒的鏈結。</span><span class="sxs-lookup"><span data-stu-id="46aeb-108">Calls to `SetIP` immediately invalidate all frames and chains for the current thread.</span></span> <span data-ttu-id="46aeb-109">如果偵錯工具需要呼叫之後的畫面格資訊`SetIP`，它必須執行新的堆疊追蹤。</span><span class="sxs-lookup"><span data-stu-id="46aeb-109">If the debugger needs frame information after a call to `SetIP`, it must perform a new stack trace.</span></span>  
  
 <span data-ttu-id="46aeb-110">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)會嘗試保留的堆疊框架是處於有效狀態。</span><span class="sxs-lookup"><span data-stu-id="46aeb-110">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) will attempt to keep the stack frame in a valid state.</span></span> <span data-ttu-id="46aeb-111">不過，即使框架是處於有效狀態，仍可能有問題，例如未初始化的區域變數。</span><span class="sxs-lookup"><span data-stu-id="46aeb-111">However, even if the frame is in a valid state, there still may be problems such as uninitialized local variables.</span></span> <span data-ttu-id="46aeb-112">呼叫端會負責確保執行程式的一致性。</span><span class="sxs-lookup"><span data-stu-id="46aeb-112">The caller is responsible for ensuring the coherency of the running program.</span></span>  
  
 <span data-ttu-id="46aeb-113">64 位元平台上，指令指標無法移出`catch`或`finally`區塊。</span><span class="sxs-lookup"><span data-stu-id="46aeb-113">On 64-bit platforms, the instruction pointer cannot be moved out of a `catch` or `finally` block.</span></span> <span data-ttu-id="46aeb-114">如果`SetIP`稱為 「 若要讓這類的 64 位元平台上移動，它會傳回 HRESULT，指出失敗。</span><span class="sxs-lookup"><span data-stu-id="46aeb-114">If `SetIP` is called to make such a move on a 64-bit platform, it will return an HRESULT indicating failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46aeb-115">需求</span><span class="sxs-lookup"><span data-stu-id="46aeb-115">Requirements</span></span>  
 <span data-ttu-id="46aeb-116">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="46aeb-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46aeb-117">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="46aeb-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="46aeb-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="46aeb-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46aeb-119">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46aeb-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

---
title: ICorDebugILFrame::GetIP 方法
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::GetIP method [.NET Framework debugging]
ms.assetid: 18217ba1-1776-4297-a3b9-f77e64b0fead
topic_type:
- apiref
ms.openlocfilehash: f30516a8f59b90de9b4c052d92a8c88575ace3c4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178829"
---
# <a name="icordebugilframegetip-method"></a><span data-ttu-id="2bd3a-102">ICorDebugILFrame::GetIP 方法</span><span class="sxs-lookup"><span data-stu-id="2bd3a-102">ICorDebugILFrame::GetIP Method</span></span>
<span data-ttu-id="2bd3a-103">獲取指令指標的值和描述指令指標值的位組合值。</span><span class="sxs-lookup"><span data-stu-id="2bd3a-103">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bd3a-104">語法</span><span class="sxs-lookup"><span data-stu-id="2bd3a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2bd3a-105">參數</span><span class="sxs-lookup"><span data-stu-id="2bd3a-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="2bd3a-106">[出]指令指標的值。</span><span class="sxs-lookup"><span data-stu-id="2bd3a-106">[out] The value of the instruction pointer.</span></span>  
  
 `pMappingResult`  
 <span data-ttu-id="2bd3a-107">[出]指向 CorDebugMappingResult 枚舉值的位狀組合的指標，用於描述如何獲取指令指標的值。</span><span class="sxs-lookup"><span data-stu-id="2bd3a-107">[out] A pointer to a bitwise combination of the CorDebugMappingResult enumeration values that describe how the value of the instruction pointer was obtained.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2bd3a-108">備註</span><span class="sxs-lookup"><span data-stu-id="2bd3a-108">Remarks</span></span>  
 <span data-ttu-id="2bd3a-109">指令指標的值是堆疊幀的偏移量到函數的 Microsoft 中間語言 （MSIL） 代碼中。</span><span class="sxs-lookup"><span data-stu-id="2bd3a-109">The value of the instruction pointer is the stack frame's offset into the function's Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="2bd3a-110">如果堆疊幀處於活動狀態，則此位址是執行的下一個指令。</span><span class="sxs-lookup"><span data-stu-id="2bd3a-110">If the stack frame is active, this address is the next instruction to execute.</span></span> <span data-ttu-id="2bd3a-111">如果堆疊幀未處於活動狀態，則此位址是重新啟動堆疊幀時執行的下一個指令。</span><span class="sxs-lookup"><span data-stu-id="2bd3a-111">If the stack frame is not active, this address is the next instruction to execute when the stack frame is reactivated.</span></span>  
  
 <span data-ttu-id="2bd3a-112">如果此幀是即時 （JIT） 編譯幀，則指令指標的值將通過從實際本機指令指標向後映射來確定，因此該值可能僅是近似值。</span><span class="sxs-lookup"><span data-stu-id="2bd3a-112">If this frame is a just-in-time (JIT) compiled frame, the value of the instruction pointer will be determined by mapping backwards from the actual native instruction pointer, so the value may be only approximate.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bd3a-113">需求</span><span class="sxs-lookup"><span data-stu-id="2bd3a-113">Requirements</span></span>  
 <span data-ttu-id="2bd3a-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2bd3a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2bd3a-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2bd3a-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2bd3a-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2bd3a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2bd3a-117">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2bd3a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

---
title: ICorDebugNativeFrame::CanSetIP 方法
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.CanSetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::CanSetIP
helpviewer_keywords:
- ICorDebugNativeFrame::CanSetIP method [.NET Framework debugging]
- CanSetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 13258ac6-f4e4-4f66-8fc3-f1244417a3c3
topic_type:
- apiref
ms.openlocfilehash: b3758ac1a84092b8bf2678f9cc2c19c9d9961690
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137318"
---
# <a name="icordebugnativeframecansetip-method"></a><span data-ttu-id="6919b-102">ICorDebugNativeFrame::CanSetIP 方法</span><span class="sxs-lookup"><span data-stu-id="6919b-102">ICorDebugNativeFrame::CanSetIP Method</span></span>
<span data-ttu-id="6919b-103">取得 HRESULT，指出是否可以安全地將指令指標（IP）設定為機器碼中的指定位移位置。</span><span class="sxs-lookup"><span data-stu-id="6919b-103">Gets an HRESULT that indicates whether it is safe to set the instruction pointer (IP) to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6919b-104">語法</span><span class="sxs-lookup"><span data-stu-id="6919b-104">Syntax</span></span>  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32            nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6919b-105">參數</span><span class="sxs-lookup"><span data-stu-id="6919b-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="6919b-106">在指令指標所需的設定。</span><span class="sxs-lookup"><span data-stu-id="6919b-106">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6919b-107">備註</span><span class="sxs-lookup"><span data-stu-id="6919b-107">Remarks</span></span>  
 <span data-ttu-id="6919b-108">呼叫[ICorDebugNativeFrame：： SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)方法之前，請先使用 `CanSetIP` 方法。</span><span class="sxs-lookup"><span data-stu-id="6919b-108">Use the `CanSetIP` method prior to calling the [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) method.</span></span> <span data-ttu-id="6919b-109">如果 `CanSetIP` 傳回 S_OK 以外的任何 HRESULT，您仍然可以叫用 `ICorDebugNativeFrame::SetIP`，但不保證偵錯工具將會繼續執行所要調試之程式碼的安全和正確執行。</span><span class="sxs-lookup"><span data-stu-id="6919b-109">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugNativeFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6919b-110">需求</span><span class="sxs-lookup"><span data-stu-id="6919b-110">Requirements</span></span>  
 <span data-ttu-id="6919b-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6919b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6919b-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6919b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6919b-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6919b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6919b-114">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6919b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6919b-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="6919b-115">See also</span></span>

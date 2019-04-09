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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd16db8c009fe81f2674a8bf9c7ad3a2a4827777
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59092847"
---
# <a name="icordebugnativeframecansetip-method"></a><span data-ttu-id="b1f8b-102">ICorDebugNativeFrame::CanSetIP 方法</span><span class="sxs-lookup"><span data-stu-id="b1f8b-102">ICorDebugNativeFrame::CanSetIP Method</span></span>
<span data-ttu-id="b1f8b-103">取得 HRESULT，指出是否以原生程式碼中，設定為指定的位移位置的指令指標 (IP) 安全。</span><span class="sxs-lookup"><span data-stu-id="b1f8b-103">Gets an HRESULT that indicates whether it is safe to set the instruction pointer (IP) to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1f8b-104">語法</span><span class="sxs-lookup"><span data-stu-id="b1f8b-104">Syntax</span></span>  
  
```  
HRESULT CanSetIP (  
    [in] ULONG32            nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1f8b-105">參數</span><span class="sxs-lookup"><span data-stu-id="b1f8b-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="b1f8b-106">[in]指令指標所需的設定。</span><span class="sxs-lookup"><span data-stu-id="b1f8b-106">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1f8b-107">備註</span><span class="sxs-lookup"><span data-stu-id="b1f8b-107">Remarks</span></span>  
 <span data-ttu-id="b1f8b-108">使用`CanSetIP`方法之前呼叫[icordebugnativeframe:: Setip](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="b1f8b-108">Use the `CanSetIP` method prior to calling the [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) method.</span></span> <span data-ttu-id="b1f8b-109">如果`CanSetIP`會傳回任何 HRESULT 以外 s_ok 時，您可以仍然叫用`ICorDebugNativeFrame::SetIP`，但不偵錯工具，將會繼續進行偵錯程式碼的安全且正確執行的保證。</span><span class="sxs-lookup"><span data-stu-id="b1f8b-109">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugNativeFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1f8b-110">需求</span><span class="sxs-lookup"><span data-stu-id="b1f8b-110">Requirements</span></span>  
 <span data-ttu-id="b1f8b-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b1f8b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1f8b-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b1f8b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b1f8b-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b1f8b-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b1f8b-114">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="b1f8b-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b1f8b-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1f8b-115">See also</span></span>

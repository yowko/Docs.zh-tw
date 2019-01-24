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
ms.openlocfilehash: 204cfc110ec6c8a11ec37505f8cf0c70d619e4b2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660810"
---
# <a name="icordebugnativeframecansetip-method"></a><span data-ttu-id="d4f72-102">ICorDebugNativeFrame::CanSetIP 方法</span><span class="sxs-lookup"><span data-stu-id="d4f72-102">ICorDebugNativeFrame::CanSetIP Method</span></span>
<span data-ttu-id="d4f72-103">取得 HRESULT，指出是否以原生程式碼中，設定為指定的位移位置的指令指標 (IP) 安全。</span><span class="sxs-lookup"><span data-stu-id="d4f72-103">Gets an HRESULT that indicates whether it is safe to set the instruction pointer (IP) to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4f72-104">語法</span><span class="sxs-lookup"><span data-stu-id="d4f72-104">Syntax</span></span>  
  
```  
HRESULT CanSetIP (  
    [in] ULONG32            nOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d4f72-105">參數</span><span class="sxs-lookup"><span data-stu-id="d4f72-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="d4f72-106">[in]指令指標所需的設定。</span><span class="sxs-lookup"><span data-stu-id="d4f72-106">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4f72-107">備註</span><span class="sxs-lookup"><span data-stu-id="d4f72-107">Remarks</span></span>  
 <span data-ttu-id="d4f72-108">使用`CanSetIP`方法之前呼叫[icordebugnativeframe:: Setip](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="d4f72-108">Use the `CanSetIP` method prior to calling the [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) method.</span></span> <span data-ttu-id="d4f72-109">如果`CanSetIP`會傳回任何 HRESULT 以外 s_ok 時，您可以仍然叫用`ICorDebugNativeFrame::SetIP`，但不偵錯工具，將會繼續進行偵錯程式碼的安全且正確執行的保證。</span><span class="sxs-lookup"><span data-stu-id="d4f72-109">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugNativeFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4f72-110">需求</span><span class="sxs-lookup"><span data-stu-id="d4f72-110">Requirements</span></span>  
 <span data-ttu-id="d4f72-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d4f72-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4f72-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d4f72-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d4f72-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d4f72-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4f72-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4f72-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4f72-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4f72-115">See also</span></span>


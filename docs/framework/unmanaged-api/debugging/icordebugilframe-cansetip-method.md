---
title: ICorDebugILFrame::CanSetIP 方法
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.CanSetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::CanSetIP
helpviewer_keywords:
- CanSetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::CanSetIP method [.NET Framework debugging]
ms.assetid: 16caf02f-c71e-486c-90b0-f0e54357d8f0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 75b28dafae2861a2d33363f95a46bf1abf4cda35
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756585"
---
# <a name="icordebugilframecansetip-method"></a><span data-ttu-id="2e6a3-102">ICorDebugILFrame::CanSetIP 方法</span><span class="sxs-lookup"><span data-stu-id="2e6a3-102">ICorDebugILFrame::CanSetIP Method</span></span>
<span data-ttu-id="2e6a3-103">取得 HRESULT，指出是否將指令指標設定為在 Microsoft Intermediate Language (MSIL) 程式碼中指定的位移位置的安全。</span><span class="sxs-lookup"><span data-stu-id="2e6a3-103">Gets an HRESULT that indicates whether it is safe to set the instruction pointer to the specified offset location in Microsoft Intermediate Language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e6a3-104">語法</span><span class="sxs-lookup"><span data-stu-id="2e6a3-104">Syntax</span></span>  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32   nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e6a3-105">參數</span><span class="sxs-lookup"><span data-stu-id="2e6a3-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="2e6a3-106">[in]指令指標所需的設定。</span><span class="sxs-lookup"><span data-stu-id="2e6a3-106">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e6a3-107">備註</span><span class="sxs-lookup"><span data-stu-id="2e6a3-107">Remarks</span></span>  
 <span data-ttu-id="2e6a3-108">使用`CanSetIP`方法之前呼叫[icordebugilframe:: Setip](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="2e6a3-108">Use the `CanSetIP` method before calling the [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) method.</span></span> <span data-ttu-id="2e6a3-109">如果`CanSetIP`會傳回任何 HRESULT 以外 s_ok 時，您可以仍然叫用`ICorDebugILFrame::SetIP`，但不偵錯工具，將會繼續進行偵錯程式碼的安全且正確執行的保證。</span><span class="sxs-lookup"><span data-stu-id="2e6a3-109">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugILFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e6a3-110">需求</span><span class="sxs-lookup"><span data-stu-id="2e6a3-110">Requirements</span></span>  
 <span data-ttu-id="2e6a3-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2e6a3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e6a3-112">**標頭：** CorDebug.idl、 CorDebug，h</span><span class="sxs-lookup"><span data-stu-id="2e6a3-112">**Header:** CorDebug.idl, CorDebug,h</span></span>  
  
 <span data-ttu-id="2e6a3-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2e6a3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e6a3-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e6a3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

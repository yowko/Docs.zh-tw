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
ms.openlocfilehash: 2bd4ab4a080461c56b0287d24aa288847445d803
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210315"
---
# <a name="icordebugilframecansetip-method"></a><span data-ttu-id="ec4da-102">ICorDebugILFrame::CanSetIP 方法</span><span class="sxs-lookup"><span data-stu-id="ec4da-102">ICorDebugILFrame::CanSetIP Method</span></span>
<span data-ttu-id="ec4da-103">取得 HRESULT，指出是否可以安全地在 Microsoft 中繼語言（MSIL）程式碼中，將指令指標設定為指定的位移位置。</span><span class="sxs-lookup"><span data-stu-id="ec4da-103">Gets an HRESULT that indicates whether it is safe to set the instruction pointer to the specified offset location in Microsoft Intermediate Language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec4da-104">語法</span><span class="sxs-lookup"><span data-stu-id="ec4da-104">Syntax</span></span>  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32   nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec4da-105">參數</span><span class="sxs-lookup"><span data-stu-id="ec4da-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="ec4da-106">在指令指標所需的設定。</span><span class="sxs-lookup"><span data-stu-id="ec4da-106">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec4da-107">備註</span><span class="sxs-lookup"><span data-stu-id="ec4da-107">Remarks</span></span>  
 <span data-ttu-id="ec4da-108">`CanSetIP`呼叫[ICorDebugILFrame：： SetIP](icordebugilframe-setip-method.md)方法之前，請先使用方法。</span><span class="sxs-lookup"><span data-stu-id="ec4da-108">Use the `CanSetIP` method before calling the [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md) method.</span></span> <span data-ttu-id="ec4da-109">如果傳回 `CanSetIP` 除了 S_OK 以外的任何 HRESULT，您仍然可以叫用 `ICorDebugILFrame::SetIP` ，但不保證偵錯工具會繼續執行所要調試之程式碼的安全和正確執行。</span><span class="sxs-lookup"><span data-stu-id="ec4da-109">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugILFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec4da-110">需求</span><span class="sxs-lookup"><span data-stu-id="ec4da-110">Requirements</span></span>  
 <span data-ttu-id="ec4da-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ec4da-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec4da-112">**標頭：** Cordebug.h .idl、Cordebug.h、h</span><span class="sxs-lookup"><span data-stu-id="ec4da-112">**Header:** CorDebug.idl, CorDebug,h</span></span>  
  
 <span data-ttu-id="ec4da-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ec4da-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec4da-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec4da-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

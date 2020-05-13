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
ms.openlocfilehash: 21890f8130ec677cb88f2f5d7ef648aa19e67e71
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213058"
---
# <a name="icordebugnativeframecansetip-method"></a><span data-ttu-id="f99a7-102">ICorDebugNativeFrame::CanSetIP 方法</span><span class="sxs-lookup"><span data-stu-id="f99a7-102">ICorDebugNativeFrame::CanSetIP Method</span></span>
<span data-ttu-id="f99a7-103">取得 HRESULT，指出是否可以安全地將指令指標（IP）設定為機器碼中的指定位移位置。</span><span class="sxs-lookup"><span data-stu-id="f99a7-103">Gets an HRESULT that indicates whether it is safe to set the instruction pointer (IP) to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f99a7-104">語法</span><span class="sxs-lookup"><span data-stu-id="f99a7-104">Syntax</span></span>  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32            nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f99a7-105">參數</span><span class="sxs-lookup"><span data-stu-id="f99a7-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="f99a7-106">在指令指標所需的設定。</span><span class="sxs-lookup"><span data-stu-id="f99a7-106">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f99a7-107">備註</span><span class="sxs-lookup"><span data-stu-id="f99a7-107">Remarks</span></span>  
 <span data-ttu-id="f99a7-108">`CanSetIP`呼叫[ICorDebugNativeFrame：： SetIP](icordebugnativeframe-setip-method.md)方法之前，請先使用方法。</span><span class="sxs-lookup"><span data-stu-id="f99a7-108">Use the `CanSetIP` method prior to calling the [ICorDebugNativeFrame::SetIP](icordebugnativeframe-setip-method.md) method.</span></span> <span data-ttu-id="f99a7-109">如果傳回 `CanSetIP` 除了 S_OK 以外的任何 HRESULT，您仍然可以叫用 `ICorDebugNativeFrame::SetIP` ，但不保證偵錯工具會繼續執行所要調試之程式碼的安全和正確執行。</span><span class="sxs-lookup"><span data-stu-id="f99a7-109">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugNativeFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f99a7-110">需求</span><span class="sxs-lookup"><span data-stu-id="f99a7-110">Requirements</span></span>  
 <span data-ttu-id="f99a7-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f99a7-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f99a7-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f99a7-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f99a7-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f99a7-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f99a7-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f99a7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f99a7-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f99a7-115">See also</span></span>

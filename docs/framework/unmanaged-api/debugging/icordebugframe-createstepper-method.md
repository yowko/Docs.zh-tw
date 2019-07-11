---
title: ICorDebugFrame::CreateStepper 方法
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.CreateStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::CreateStepper
helpviewer_keywords:
- ICorDebugFrame::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 689e7f28-20c1-4d5c-9baa-17441cd63a88
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fd105a5cbdb857aaa902e60968ff1d94473259b6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754235"
---
# <a name="icordebugframecreatestepper-method"></a><span data-ttu-id="97d40-102">ICorDebugFrame::CreateStepper 方法</span><span class="sxs-lookup"><span data-stu-id="97d40-102">ICorDebugFrame::CreateStepper Method</span></span>
<span data-ttu-id="97d40-103">取得可讓偵錯工具執行逐步執行的作業，相對於這個 ICorDebugFrame 步進。</span><span class="sxs-lookup"><span data-stu-id="97d40-103">Gets a stepper that allows the debugger to perform stepping operations relative to this ICorDebugFrame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97d40-104">語法</span><span class="sxs-lookup"><span data-stu-id="97d40-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateStepper (  
    [out] ICorDebugStepper   **ppStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97d40-105">參數</span><span class="sxs-lookup"><span data-stu-id="97d40-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="97d40-106">[out]ICorDebugStepper 物件，可讓偵錯工具執行逐步執行的作業，相對於目前的框架的位址指標。</span><span class="sxs-lookup"><span data-stu-id="97d40-106">[out] A pointer to the address of an ICorDebugStepper object that allows the debugger to perform stepping operations relative to the current frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="97d40-107">備註</span><span class="sxs-lookup"><span data-stu-id="97d40-107">Remarks</span></span>  
 <span data-ttu-id="97d40-108">如果框架不在使用中，步進物件通常需要返回框架前完成的步驟。</span><span class="sxs-lookup"><span data-stu-id="97d40-108">If the frame is not active, the stepper object will typically have to return to the frame before the step is completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97d40-109">需求</span><span class="sxs-lookup"><span data-stu-id="97d40-109">Requirements</span></span>  
 <span data-ttu-id="97d40-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="97d40-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97d40-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="97d40-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="97d40-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="97d40-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97d40-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97d40-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

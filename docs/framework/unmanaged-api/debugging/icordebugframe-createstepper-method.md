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
ms.openlocfilehash: 6ea2b24d37f56a5cb9e6b3dea0d666c8acc719dc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091037"
---
# <a name="icordebugframecreatestepper-method"></a><span data-ttu-id="8be1b-102">ICorDebugFrame::CreateStepper 方法</span><span class="sxs-lookup"><span data-stu-id="8be1b-102">ICorDebugFrame::CreateStepper Method</span></span>
<span data-ttu-id="8be1b-103">取得分檔器，讓偵錯工具能夠執行相對於此 ICorDebugFrame 的逐步操作。</span><span class="sxs-lookup"><span data-stu-id="8be1b-103">Gets a stepper that allows the debugger to perform stepping operations relative to this ICorDebugFrame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8be1b-104">語法</span><span class="sxs-lookup"><span data-stu-id="8be1b-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateStepper (  
    [out] ICorDebugStepper   **ppStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8be1b-105">參數</span><span class="sxs-lookup"><span data-stu-id="8be1b-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="8be1b-106">脫銷ICorDebugStepper 物件位址的指標，可讓偵錯工具執行相對於目前框架的逐步操作。</span><span class="sxs-lookup"><span data-stu-id="8be1b-106">[out] A pointer to the address of an ICorDebugStepper object that allows the debugger to perform stepping operations relative to the current frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8be1b-107">備註</span><span class="sxs-lookup"><span data-stu-id="8be1b-107">Remarks</span></span>  
 <span data-ttu-id="8be1b-108">如果框架不在使用中，則在步驟完成之前，分檔器物件通常必須回到框架。</span><span class="sxs-lookup"><span data-stu-id="8be1b-108">If the frame is not active, the stepper object will typically have to return to the frame before the step is completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8be1b-109">需求</span><span class="sxs-lookup"><span data-stu-id="8be1b-109">Requirements</span></span>  
 <span data-ttu-id="8be1b-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8be1b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8be1b-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8be1b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8be1b-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8be1b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8be1b-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8be1b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

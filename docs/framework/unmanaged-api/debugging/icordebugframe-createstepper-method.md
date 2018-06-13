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
ms.openlocfilehash: 3662ed8a3fda5881b0e0929a830d19b0d805299f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411027"
---
# <a name="icordebugframecreatestepper-method"></a><span data-ttu-id="9bd85-102">ICorDebugFrame::CreateStepper 方法</span><span class="sxs-lookup"><span data-stu-id="9bd85-102">ICorDebugFrame::CreateStepper Method</span></span>
<span data-ttu-id="9bd85-103">取得 stepper，可讓偵錯工具執行相對於這個 ICorDebugFrame 逐步執行的作業。</span><span class="sxs-lookup"><span data-stu-id="9bd85-103">Gets a stepper that allows the debugger to perform stepping operations relative to this ICorDebugFrame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bd85-104">語法</span><span class="sxs-lookup"><span data-stu-id="9bd85-104">Syntax</span></span>  
  
```  
HRESULT CreateStepper (  
    [out] ICorDebugStepper   **ppStepper  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9bd85-105">參數</span><span class="sxs-lookup"><span data-stu-id="9bd85-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="9bd85-106">[out]ICorDebugStepper 物件，可讓偵錯工具執行相對於目前的框架逐步執行作業的位址指標。</span><span class="sxs-lookup"><span data-stu-id="9bd85-106">[out] A pointer to the address of an ICorDebugStepper object that allows the debugger to perform stepping operations relative to the current frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9bd85-107">備註</span><span class="sxs-lookup"><span data-stu-id="9bd85-107">Remarks</span></span>  
 <span data-ttu-id="9bd85-108">如果框架不在使用中，stepper 物件通常必須回到框架之前會完成此步驟。</span><span class="sxs-lookup"><span data-stu-id="9bd85-108">If the frame is not active, the stepper object will typically have to return to the frame before the step is completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9bd85-109">需求</span><span class="sxs-lookup"><span data-stu-id="9bd85-109">Requirements</span></span>  
 <span data-ttu-id="9bd85-110">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9bd85-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bd85-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9bd85-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9bd85-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9bd85-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9bd85-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9bd85-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

---
title: ICorDebugStepper::Deactivate 方法
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.Deactivate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::Deactivate
helpviewer_keywords:
- Deactivate method [.NET Framework debugging]
- ICorDebugStepper::Deactivate method [.NET Framework debugging]
ms.assetid: 855f4199-b62d-40ce-998e-1eb4a1772142
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bcd7bfb52cadf740d8fe3cb92a09b071f530b7ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417397"
---
# <a name="icordebugstepperdeactivate-method"></a><span data-ttu-id="8c3e5-102">ICorDebugStepper::Deactivate 方法</span><span class="sxs-lookup"><span data-stu-id="8c3e5-102">ICorDebugStepper::Deactivate Method</span></span>
<span data-ttu-id="8c3e5-103">會導致此 ICorDebugStepper 取消它所收到的最後一個步驟命令。</span><span class="sxs-lookup"><span data-stu-id="8c3e5-103">Causes this ICorDebugStepper to cancel the last step command that it received.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c3e5-104">語法</span><span class="sxs-lookup"><span data-stu-id="8c3e5-104">Syntax</span></span>  
  
```  
HRESULT Deactivate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="8c3e5-105">備註</span><span class="sxs-lookup"><span data-stu-id="8c3e5-105">Remarks</span></span>  
 <span data-ttu-id="8c3e5-106">已取消最近收到的步驟命令之後發出新的逐步執行指令。</span><span class="sxs-lookup"><span data-stu-id="8c3e5-106">A new stepping command may be issued after the most recently received step command has been canceled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c3e5-107">需求</span><span class="sxs-lookup"><span data-stu-id="8c3e5-107">Requirements</span></span>  
 <span data-ttu-id="8c3e5-108">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8c3e5-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c3e5-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8c3e5-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8c3e5-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8c3e5-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c3e5-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c3e5-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

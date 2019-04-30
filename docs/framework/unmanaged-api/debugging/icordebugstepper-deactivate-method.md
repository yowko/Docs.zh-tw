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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994327"
---
# <a name="icordebugstepperdeactivate-method"></a><span data-ttu-id="1dd04-102">ICorDebugStepper::Deactivate 方法</span><span class="sxs-lookup"><span data-stu-id="1dd04-102">ICorDebugStepper::Deactivate Method</span></span>
<span data-ttu-id="1dd04-103">會導致此 ICorDebugStepper 取消它收到的最後一個步驟命令。</span><span class="sxs-lookup"><span data-stu-id="1dd04-103">Causes this ICorDebugStepper to cancel the last step command that it received.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dd04-104">語法</span><span class="sxs-lookup"><span data-stu-id="1dd04-104">Syntax</span></span>  
  
```  
HRESULT Deactivate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="1dd04-105">備註</span><span class="sxs-lookup"><span data-stu-id="1dd04-105">Remarks</span></span>  
 <span data-ttu-id="1dd04-106">最近收到的步驟命令已被取消之後，可能會發出新的逐步執行命令。</span><span class="sxs-lookup"><span data-stu-id="1dd04-106">A new stepping command may be issued after the most recently received step command has been canceled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1dd04-107">需求</span><span class="sxs-lookup"><span data-stu-id="1dd04-107">Requirements</span></span>  
 <span data-ttu-id="1dd04-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1dd04-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1dd04-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1dd04-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1dd04-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1dd04-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1dd04-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1dd04-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

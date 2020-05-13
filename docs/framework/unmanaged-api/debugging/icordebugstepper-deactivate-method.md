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
ms.openlocfilehash: 760f69baf311cf320e9c358ba1c45c942934f1a5
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379401"
---
# <a name="icordebugstepperdeactivate-method"></a><span data-ttu-id="55bd8-102">ICorDebugStepper::Deactivate 方法</span><span class="sxs-lookup"><span data-stu-id="55bd8-102">ICorDebugStepper::Deactivate Method</span></span>
<span data-ttu-id="55bd8-103">導致此 ICorDebugStepper 取消它所收到的最後一個步驟命令。</span><span class="sxs-lookup"><span data-stu-id="55bd8-103">Causes this ICorDebugStepper to cancel the last step command that it received.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55bd8-104">語法</span><span class="sxs-lookup"><span data-stu-id="55bd8-104">Syntax</span></span>  
  
```cpp  
HRESULT Deactivate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="55bd8-105">備註</span><span class="sxs-lookup"><span data-stu-id="55bd8-105">Remarks</span></span>  
 <span data-ttu-id="55bd8-106">在最近收到的步驟命令取消之後，可能會發出新的逐步執行命令。</span><span class="sxs-lookup"><span data-stu-id="55bd8-106">A new stepping command may be issued after the most recently received step command has been canceled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55bd8-107">需求</span><span class="sxs-lookup"><span data-stu-id="55bd8-107">Requirements</span></span>  
 <span data-ttu-id="55bd8-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="55bd8-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55bd8-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="55bd8-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="55bd8-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="55bd8-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55bd8-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55bd8-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

---
title: ICorDebugController::IsRunning 方法
ms.date: 03/30/2017
api_name:
- ICorDebugController.IsRunning
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::IsRunning
helpviewer_keywords:
- IsRunning method [.NET Framework debugging]
- ICorDebugController::IsRunning method [.NET Framework debugging]
ms.assetid: b33ff059-40c4-4dfe-9cb2-21bfed2de0b0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 99dbe5c5da5b8c169e34aa29afca507cc6624f0f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748800"
---
# <a name="icordebugcontrollerisrunning-method"></a><span data-ttu-id="476bf-102">ICorDebugController::IsRunning 方法</span><span class="sxs-lookup"><span data-stu-id="476bf-102">ICorDebugController::IsRunning Method</span></span>
<span data-ttu-id="476bf-103">取得值，指出是否在程序中的執行緒目前正在自由。</span><span class="sxs-lookup"><span data-stu-id="476bf-103">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="476bf-104">語法</span><span class="sxs-lookup"><span data-stu-id="476bf-104">Syntax</span></span>  
  
```cpp  
HRESULT IsRunning (  
    [out] BOOL *pbRunning  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="476bf-105">參數</span><span class="sxs-lookup"><span data-stu-id="476bf-105">Parameters</span></span>  
 `pbRunning`  
 <span data-ttu-id="476bf-106">[out]為值的指標`true`自由; 否則執行程序中的執行緒如果`false`。</span><span class="sxs-lookup"><span data-stu-id="476bf-106">[out] A pointer to a value that is `true` if the threads in the process are running freely; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="476bf-107">需求</span><span class="sxs-lookup"><span data-stu-id="476bf-107">Requirements</span></span>  
 <span data-ttu-id="476bf-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="476bf-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="476bf-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="476bf-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="476bf-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="476bf-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="476bf-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="476bf-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="476bf-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="476bf-112">See also</span></span>

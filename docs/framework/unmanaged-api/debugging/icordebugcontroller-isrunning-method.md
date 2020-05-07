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
ms.openlocfilehash: 89ea9f221ad55063e4186cc27cc8038334d800d4
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82892870"
---
# <a name="icordebugcontrollerisrunning-method"></a><span data-ttu-id="8dce4-102">ICorDebugController::IsRunning 方法</span><span class="sxs-lookup"><span data-stu-id="8dce4-102">ICorDebugController::IsRunning Method</span></span>
<span data-ttu-id="8dce4-103">取得值，指出進程中的執行緒目前是否可自由執行。</span><span class="sxs-lookup"><span data-stu-id="8dce4-103">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8dce4-104">語法</span><span class="sxs-lookup"><span data-stu-id="8dce4-104">Syntax</span></span>  
  
```cpp  
HRESULT IsRunning (  
    [out] BOOL *pbRunning  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8dce4-105">參數</span><span class="sxs-lookup"><span data-stu-id="8dce4-105">Parameters</span></span>  
 `pbRunning`  
 <span data-ttu-id="8dce4-106">脫銷值的指標，如果進程中`true`的執行緒是自由執行，則為，否則為`false`。</span><span class="sxs-lookup"><span data-stu-id="8dce4-106">[out] A pointer to a value that is `true` if the threads in the process are running freely; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8dce4-107">需求</span><span class="sxs-lookup"><span data-stu-id="8dce4-107">Requirements</span></span>  
 <span data-ttu-id="8dce4-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8dce4-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8dce4-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8dce4-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8dce4-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8dce4-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8dce4-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8dce4-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dce4-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8dce4-112">See also</span></span>

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
ms.openlocfilehash: a5eae9e14bcd0ca430f03a873818246896438463
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59227089"
---
# <a name="icordebugcontrollerisrunning-method"></a><span data-ttu-id="d02a1-102">ICorDebugController::IsRunning 方法</span><span class="sxs-lookup"><span data-stu-id="d02a1-102">ICorDebugController::IsRunning Method</span></span>
<span data-ttu-id="d02a1-103">取得值，指出是否在程序中的執行緒目前正在自由。</span><span class="sxs-lookup"><span data-stu-id="d02a1-103">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d02a1-104">語法</span><span class="sxs-lookup"><span data-stu-id="d02a1-104">Syntax</span></span>  
  
```  
HRESULT IsRunning (  
    [out] BOOL *pbRunning  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d02a1-105">參數</span><span class="sxs-lookup"><span data-stu-id="d02a1-105">Parameters</span></span>  
 `pbRunning`  
 <span data-ttu-id="d02a1-106">[out]為值的指標`true`自由; 否則執行程序中的執行緒如果`false`。</span><span class="sxs-lookup"><span data-stu-id="d02a1-106">[out] A pointer to a value that is `true` if the threads in the process are running freely; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d02a1-107">需求</span><span class="sxs-lookup"><span data-stu-id="d02a1-107">Requirements</span></span>  
 <span data-ttu-id="d02a1-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d02a1-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d02a1-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d02a1-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d02a1-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d02a1-110">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="d02a1-111">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="d02a1-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d02a1-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d02a1-112">See also</span></span>

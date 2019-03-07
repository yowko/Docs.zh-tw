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
ms.openlocfilehash: 7eef04dfb305978c81f465ecb37eda75a52f25e4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57502944"
---
# <a name="icordebugcontrollerisrunning-method"></a><span data-ttu-id="9781f-102">ICorDebugController::IsRunning 方法</span><span class="sxs-lookup"><span data-stu-id="9781f-102">ICorDebugController::IsRunning Method</span></span>
<span data-ttu-id="9781f-103">取得值，指出是否在程序中的執行緒目前正在自由。</span><span class="sxs-lookup"><span data-stu-id="9781f-103">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9781f-104">語法</span><span class="sxs-lookup"><span data-stu-id="9781f-104">Syntax</span></span>  
  
```  
HRESULT IsRunning (  
    [out] BOOL *pbRunning  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9781f-105">參數</span><span class="sxs-lookup"><span data-stu-id="9781f-105">Parameters</span></span>  
 `pbRunning`  
 <span data-ttu-id="9781f-106">[out]為值的指標`true`自由; 否則執行程序中的執行緒如果`false`。</span><span class="sxs-lookup"><span data-stu-id="9781f-106">[out] A pointer to a value that is `true` if the threads in the process are running freely; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9781f-107">需求</span><span class="sxs-lookup"><span data-stu-id="9781f-107">Requirements</span></span>  
 <span data-ttu-id="9781f-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9781f-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9781f-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9781f-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9781f-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9781f-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9781f-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9781f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9781f-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9781f-112">See also</span></span>


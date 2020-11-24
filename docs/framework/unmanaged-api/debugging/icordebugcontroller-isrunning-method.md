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
ms.openlocfilehash: 73ed86ee12b02d292dc6dfc1d652459a679f81ca
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679932"
---
# <a name="icordebugcontrollerisrunning-method"></a><span data-ttu-id="c2c48-102">ICorDebugController::IsRunning 方法</span><span class="sxs-lookup"><span data-stu-id="c2c48-102">ICorDebugController::IsRunning Method</span></span>

<span data-ttu-id="c2c48-103">取得值，這個值表示進程中的執行緒目前是否可自由執行。</span><span class="sxs-lookup"><span data-stu-id="c2c48-103">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2c48-104">語法</span><span class="sxs-lookup"><span data-stu-id="c2c48-104">Syntax</span></span>  
  
```cpp  
HRESULT IsRunning (  
    [out] BOOL *pbRunning  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2c48-105">參數</span><span class="sxs-lookup"><span data-stu-id="c2c48-105">Parameters</span></span>  

 `pbRunning`  
 <span data-ttu-id="c2c48-106">擴展值的指標， `true` 如果進程中的執行緒可自由執行，則為，否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="c2c48-106">[out] A pointer to a value that is `true` if the threads in the process are running freely; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2c48-107">需求</span><span class="sxs-lookup"><span data-stu-id="c2c48-107">Requirements</span></span>  

 <span data-ttu-id="c2c48-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c2c48-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2c48-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c2c48-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c2c48-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2c48-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2c48-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2c48-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2c48-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2c48-112">See also</span></span>

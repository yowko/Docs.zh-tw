---
title: ICorDebugEval::IsActive 方法
ms.date: 03/30/2017
api_name:
- ICorDebugEval.IsActive
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::IsActive
helpviewer_keywords:
- IsActive method, ICorDebugEval interface [.NET Framework debugging]
- ICorDebugEval::IsActive method [.NET Framework debugging]
ms.assetid: bf2bba24-d278-43bd-b1c5-35680e748d3e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: be7dde136c5bc26148468d3d8031426b17f44292
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753126"
---
# <a name="icordebugevalisactive-method"></a><span data-ttu-id="0e770-102">ICorDebugEval::IsActive 方法</span><span class="sxs-lookup"><span data-stu-id="0e770-102">ICorDebugEval::IsActive Method</span></span>
<span data-ttu-id="0e770-103">取得值，指出這個 ICorDebugEval 物件目前是否正在執行。</span><span class="sxs-lookup"><span data-stu-id="0e770-103">Gets a value that indicates whether this ICorDebugEval object is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e770-104">語法</span><span class="sxs-lookup"><span data-stu-id="0e770-104">Syntax</span></span>  
  
```cpp  
HRESULT IsActive (  
    [out] BOOL              *pbActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e770-105">參數</span><span class="sxs-lookup"><span data-stu-id="0e770-105">Parameters</span></span>  
 `pbActive`  
 <span data-ttu-id="0e770-106">[out]值，指出這項評估是否在作用中的指標。</span><span class="sxs-lookup"><span data-stu-id="0e770-106">[out] Pointer to a value that indicates whether this evaluation is active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e770-107">需求</span><span class="sxs-lookup"><span data-stu-id="0e770-107">Requirements</span></span>  
 <span data-ttu-id="0e770-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0e770-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e770-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0e770-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0e770-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0e770-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0e770-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e770-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

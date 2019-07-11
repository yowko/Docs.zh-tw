---
title: ICorDebugCode::GetFunction 方法
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetFunction
helpviewer_keywords:
- GetFunction method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetFunction method [.NET Framework debugging]
ms.assetid: c568b737-fdb2-4816-accd-051f5ab760f1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 10ab92c660353bea85bbd0918a25f716898ef837
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747531"
---
# <a name="icordebugcodegetfunction-method"></a><span data-ttu-id="dbea6-102">ICorDebugCode::GetFunction 方法</span><span class="sxs-lookup"><span data-stu-id="dbea6-102">ICorDebugCode::GetFunction Method</span></span>
<span data-ttu-id="dbea6-103">取得與此 「 ICorDebugCode"相關聯 「 ICorDebugFunction"。</span><span class="sxs-lookup"><span data-stu-id="dbea6-103">Gets the "ICorDebugFunction" associated with this "ICorDebugCode".</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbea6-104">語法</span><span class="sxs-lookup"><span data-stu-id="dbea6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunction (  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dbea6-105">參數</span><span class="sxs-lookup"><span data-stu-id="dbea6-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="dbea6-106">[out]函式的位址指標。</span><span class="sxs-lookup"><span data-stu-id="dbea6-106">[out] A pointer to the address of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dbea6-107">備註</span><span class="sxs-lookup"><span data-stu-id="dbea6-107">Remarks</span></span>  
 <span data-ttu-id="dbea6-108">`ICorDebugCode` 和`ICorDebugFunction`維護一對一的關聯性。</span><span class="sxs-lookup"><span data-stu-id="dbea6-108">`ICorDebugCode` and `ICorDebugFunction` maintain a one-to-one relationship.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbea6-109">需求</span><span class="sxs-lookup"><span data-stu-id="dbea6-109">Requirements</span></span>  
 <span data-ttu-id="dbea6-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dbea6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbea6-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dbea6-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dbea6-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dbea6-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dbea6-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbea6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbea6-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dbea6-114">See also</span></span>

---
title: ICorDebugCode::GetVersionNumber 方法
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetVersionNumber
helpviewer_keywords:
- GetVersionNumber method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetVersionNumber method [.NET Framework debugging]
ms.assetid: c8e02518-679f-4e9f-8a28-ba4a89a3876f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 155a8d5465e0fb19c55c9d11b67c6031c2b2c4a3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747515"
---
# <a name="icordebugcodegetversionnumber-method"></a><span data-ttu-id="705f8-102">ICorDebugCode::GetVersionNumber 方法</span><span class="sxs-lookup"><span data-stu-id="705f8-102">ICorDebugCode::GetVersionNumber Method</span></span>
<span data-ttu-id="705f8-103">取得識別此 「 ICorDebugCode"表示的程式碼的版本以一為基的號碼。</span><span class="sxs-lookup"><span data-stu-id="705f8-103">Gets the one-based number that identifies the version of the code that this "ICorDebugCode" represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="705f8-104">語法</span><span class="sxs-lookup"><span data-stu-id="705f8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionNumber (  
    [out] ULONG32    *nVersion  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="705f8-105">參數</span><span class="sxs-lookup"><span data-stu-id="705f8-105">Parameters</span></span>  
 `nVersion`  
 <span data-ttu-id="705f8-106">[out]版本號碼，程式碼的指標。</span><span class="sxs-lookup"><span data-stu-id="705f8-106">[out] A pointer to the version number of the code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="705f8-107">備註</span><span class="sxs-lookup"><span data-stu-id="705f8-107">Remarks</span></span>  
 <span data-ttu-id="705f8-108">版本號碼會遞增每個執行程式碼編輯後繼續 (EnC) 作業的時間。</span><span class="sxs-lookup"><span data-stu-id="705f8-108">The version number is incremented each time an edit-and-continue (EnC) operation is performed on the code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="705f8-109">需求</span><span class="sxs-lookup"><span data-stu-id="705f8-109">Requirements</span></span>  
 <span data-ttu-id="705f8-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="705f8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="705f8-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="705f8-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="705f8-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="705f8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="705f8-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="705f8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="705f8-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="705f8-114">See also</span></span>

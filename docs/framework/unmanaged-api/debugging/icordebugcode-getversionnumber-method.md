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
ms.openlocfilehash: 003b29501e8f22ed9010a9f16a4f7ee67bce03a8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61750133"
---
# <a name="icordebugcodegetversionnumber-method"></a><span data-ttu-id="01924-102">ICorDebugCode::GetVersionNumber 方法</span><span class="sxs-lookup"><span data-stu-id="01924-102">ICorDebugCode::GetVersionNumber Method</span></span>
<span data-ttu-id="01924-103">取得識別此 「 ICorDebugCode"表示的程式碼的版本以一為基的號碼。</span><span class="sxs-lookup"><span data-stu-id="01924-103">Gets the one-based number that identifies the version of the code that this "ICorDebugCode" represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01924-104">語法</span><span class="sxs-lookup"><span data-stu-id="01924-104">Syntax</span></span>  
  
```  
HRESULT GetVersionNumber (  
    [out] ULONG32    *nVersion  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01924-105">參數</span><span class="sxs-lookup"><span data-stu-id="01924-105">Parameters</span></span>  
 `nVersion`  
 <span data-ttu-id="01924-106">[out]版本號碼，程式碼的指標。</span><span class="sxs-lookup"><span data-stu-id="01924-106">[out] A pointer to the version number of the code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01924-107">備註</span><span class="sxs-lookup"><span data-stu-id="01924-107">Remarks</span></span>  
 <span data-ttu-id="01924-108">版本號碼會遞增每個執行程式碼編輯後繼續 (EnC) 作業的時間。</span><span class="sxs-lookup"><span data-stu-id="01924-108">The version number is incremented each time an edit-and-continue (EnC) operation is performed on the code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01924-109">需求</span><span class="sxs-lookup"><span data-stu-id="01924-109">Requirements</span></span>  
 <span data-ttu-id="01924-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="01924-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01924-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="01924-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="01924-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01924-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01924-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01924-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01924-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01924-114">See also</span></span>

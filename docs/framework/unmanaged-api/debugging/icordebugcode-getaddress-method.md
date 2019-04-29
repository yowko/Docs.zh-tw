---
title: ICorDebugCode::GetAddress 方法
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetAddress
helpviewer_keywords:
- GetAddress method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetAddress method [.NET Framework debugging]
ms.assetid: cc507cb0-df2e-49c2-b32e-0c3271a8df9a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 11ced90b88f083eb69b06d197d64a8ef4252f9d5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61750419"
---
# <a name="icordebugcodegetaddress-method"></a><span data-ttu-id="d913c-102">ICorDebugCode::GetAddress 方法</span><span class="sxs-lookup"><span data-stu-id="d913c-102">ICorDebugCode::GetAddress Method</span></span>
<span data-ttu-id="d913c-103">取得這個 「 ICorDebugCode 」 介面表示的程式碼片段的相對虛擬位址 (RVA)。</span><span class="sxs-lookup"><span data-stu-id="d913c-103">Gets the relative virtual address (RVA) of the code segment that this "ICorDebugCode" interface represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d913c-104">語法</span><span class="sxs-lookup"><span data-stu-id="d913c-104">Syntax</span></span>  
  
```  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS *pStart  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d913c-105">參數</span><span class="sxs-lookup"><span data-stu-id="d913c-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="d913c-106">[out]程式碼區段的 RVA 指標。</span><span class="sxs-lookup"><span data-stu-id="d913c-106">[out] A pointer to the RVA of the code segment.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d913c-107">需求</span><span class="sxs-lookup"><span data-stu-id="d913c-107">Requirements</span></span>  
 <span data-ttu-id="d913c-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d913c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d913c-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d913c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d913c-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d913c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d913c-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d913c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d913c-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d913c-112">See also</span></span>

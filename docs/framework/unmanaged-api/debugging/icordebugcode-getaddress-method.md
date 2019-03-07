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
ms.openlocfilehash: dda5883d8a1de11fa282e8b8e0fafe924f2d8b7a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494502"
---
# <a name="icordebugcodegetaddress-method"></a><span data-ttu-id="eaaa7-102">ICorDebugCode::GetAddress 方法</span><span class="sxs-lookup"><span data-stu-id="eaaa7-102">ICorDebugCode::GetAddress Method</span></span>
<span data-ttu-id="eaaa7-103">取得這個 「 ICorDebugCode 」 介面表示的程式碼片段的相對虛擬位址 (RVA)。</span><span class="sxs-lookup"><span data-stu-id="eaaa7-103">Gets the relative virtual address (RVA) of the code segment that this "ICorDebugCode" interface represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eaaa7-104">語法</span><span class="sxs-lookup"><span data-stu-id="eaaa7-104">Syntax</span></span>  
  
```  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS *pStart  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eaaa7-105">參數</span><span class="sxs-lookup"><span data-stu-id="eaaa7-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="eaaa7-106">[out]程式碼區段的 RVA 指標。</span><span class="sxs-lookup"><span data-stu-id="eaaa7-106">[out] A pointer to the RVA of the code segment.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eaaa7-107">需求</span><span class="sxs-lookup"><span data-stu-id="eaaa7-107">Requirements</span></span>  
 <span data-ttu-id="eaaa7-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="eaaa7-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eaaa7-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eaaa7-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eaaa7-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eaaa7-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eaaa7-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eaaa7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaaa7-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eaaa7-112">See also</span></span>


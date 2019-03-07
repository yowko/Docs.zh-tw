---
title: ICorDebugCode::GetSize 方法
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetSize method [.NET Framework debugging]
ms.assetid: 115bc6de-f5e2-4e8e-bb38-c7cf54045434
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3bd21e43973d116e4383d88bd5ce90f0fbfeb1a6
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471471"
---
# <a name="icordebugcodegetsize-method"></a><span data-ttu-id="f4e8e-102">ICorDebugCode::GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="f4e8e-102">ICorDebugCode::GetSize Method</span></span>
<span data-ttu-id="f4e8e-103">取得大小，以位元組為單位，此 「 ICorDebugCode"所表示的二進位程式碼。</span><span class="sxs-lookup"><span data-stu-id="f4e8e-103">Gets the size, in bytes, of the binary code represented by this "ICorDebugCode".</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4e8e-104">語法</span><span class="sxs-lookup"><span data-stu-id="f4e8e-104">Syntax</span></span>  
  
```  
HRESULT GetSize (  
    [out] ULONG32    *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4e8e-105">參數</span><span class="sxs-lookup"><span data-stu-id="f4e8e-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="f4e8e-106">[out]指標大小 （位元組），二進位檔的程式碼這個`ICorDebugCode`物件表示。</span><span class="sxs-lookup"><span data-stu-id="f4e8e-106">[out] A pointer to the size, in bytes, of the binary code that this `ICorDebugCode` object represents.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4e8e-107">需求</span><span class="sxs-lookup"><span data-stu-id="f4e8e-107">Requirements</span></span>  
 <span data-ttu-id="f4e8e-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f4e8e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4e8e-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f4e8e-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f4e8e-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f4e8e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f4e8e-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4e8e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4e8e-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4e8e-112">See also</span></span>


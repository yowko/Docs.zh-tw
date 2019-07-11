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
ms.openlocfilehash: 52ba9d5bac5e772d721d38e4e8a7ba6757d0ae2e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747497"
---
# <a name="icordebugcodegetsize-method"></a><span data-ttu-id="ad096-102">ICorDebugCode::GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="ad096-102">ICorDebugCode::GetSize Method</span></span>
<span data-ttu-id="ad096-103">取得大小，以位元組為單位，此 「 ICorDebugCode"所表示的二進位程式碼。</span><span class="sxs-lookup"><span data-stu-id="ad096-103">Gets the size, in bytes, of the binary code represented by this "ICorDebugCode".</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad096-104">語法</span><span class="sxs-lookup"><span data-stu-id="ad096-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize (  
    [out] ULONG32    *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad096-105">參數</span><span class="sxs-lookup"><span data-stu-id="ad096-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="ad096-106">[out]指標大小 （位元組），二進位檔的程式碼這個`ICorDebugCode`物件表示。</span><span class="sxs-lookup"><span data-stu-id="ad096-106">[out] A pointer to the size, in bytes, of the binary code that this `ICorDebugCode` object represents.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad096-107">需求</span><span class="sxs-lookup"><span data-stu-id="ad096-107">Requirements</span></span>  
 <span data-ttu-id="ad096-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ad096-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad096-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ad096-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ad096-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad096-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad096-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad096-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad096-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad096-112">See also</span></span>

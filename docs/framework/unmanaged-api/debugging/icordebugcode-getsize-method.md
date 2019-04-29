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
ms.openlocfilehash: 678b7fbd595b1238b7025c22b0ed80b02ed4becd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61750198"
---
# <a name="icordebugcodegetsize-method"></a><span data-ttu-id="f7f4b-102">ICorDebugCode::GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="f7f4b-102">ICorDebugCode::GetSize Method</span></span>
<span data-ttu-id="f7f4b-103">取得大小，以位元組為單位，此 「 ICorDebugCode"所表示的二進位程式碼。</span><span class="sxs-lookup"><span data-stu-id="f7f4b-103">Gets the size, in bytes, of the binary code represented by this "ICorDebugCode".</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7f4b-104">語法</span><span class="sxs-lookup"><span data-stu-id="f7f4b-104">Syntax</span></span>  
  
```  
HRESULT GetSize (  
    [out] ULONG32    *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7f4b-105">參數</span><span class="sxs-lookup"><span data-stu-id="f7f4b-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="f7f4b-106">[out]指標大小 （位元組），二進位檔的程式碼這個`ICorDebugCode`物件表示。</span><span class="sxs-lookup"><span data-stu-id="f7f4b-106">[out] A pointer to the size, in bytes, of the binary code that this `ICorDebugCode` object represents.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7f4b-107">需求</span><span class="sxs-lookup"><span data-stu-id="f7f4b-107">Requirements</span></span>  
 <span data-ttu-id="f7f4b-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f7f4b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7f4b-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f7f4b-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f7f4b-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7f4b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7f4b-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7f4b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7f4b-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7f4b-112">See also</span></span>

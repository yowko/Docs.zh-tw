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
ms.openlocfilehash: a3d4609d79bb424cabc011122480f952f0f877f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411230"
---
# <a name="icordebugcodegetversionnumber-method"></a><span data-ttu-id="b8e54-102">ICorDebugCode::GetVersionNumber 方法</span><span class="sxs-lookup"><span data-stu-id="b8e54-102">ICorDebugCode::GetVersionNumber Method</span></span>
<span data-ttu-id="b8e54-103">取得識別此 「 ICorDebugCode"表示的程式碼的版本 1 為基底的數目。</span><span class="sxs-lookup"><span data-stu-id="b8e54-103">Gets the one-based number that identifies the version of the code that this "ICorDebugCode" represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8e54-104">語法</span><span class="sxs-lookup"><span data-stu-id="b8e54-104">Syntax</span></span>  
  
```  
HRESULT GetVersionNumber (  
    [out] ULONG32    *nVersion  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b8e54-105">參數</span><span class="sxs-lookup"><span data-stu-id="b8e54-105">Parameters</span></span>  
 `nVersion`  
 <span data-ttu-id="b8e54-106">[out]程式碼的版本號碼的指標。</span><span class="sxs-lookup"><span data-stu-id="b8e54-106">[out] A pointer to the version number of the code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8e54-107">備註</span><span class="sxs-lookup"><span data-stu-id="b8e54-107">Remarks</span></span>  
 <span data-ttu-id="b8e54-108">版本號碼會遞增每個程式碼執行編輯後繼續 (EnC) 作業的時間。</span><span class="sxs-lookup"><span data-stu-id="b8e54-108">The version number is incremented each time an edit-and-continue (EnC) operation is performed on the code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8e54-109">需求</span><span class="sxs-lookup"><span data-stu-id="b8e54-109">Requirements</span></span>  
 <span data-ttu-id="b8e54-110">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b8e54-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8e54-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b8e54-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b8e54-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b8e54-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8e54-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8e54-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8e54-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8e54-114">See Also</span></span>  
 

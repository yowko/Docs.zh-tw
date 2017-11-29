---
title: "ICorDebugCode::GetVersionNumber 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCode.GetVersionNumber
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode::GetVersionNumber
helpviewer_keywords:
- GetVersionNumber method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetVersionNumber method [.NET Framework debugging]
ms.assetid: c8e02518-679f-4e9f-8a28-ba4a89a3876f
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cd467f047131bbb078c72db9daca2cbc5a87a7be
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcodegetversionnumber-method"></a><span data-ttu-id="4074e-102">ICorDebugCode::GetVersionNumber 方法</span><span class="sxs-lookup"><span data-stu-id="4074e-102">ICorDebugCode::GetVersionNumber Method</span></span>
<span data-ttu-id="4074e-103">取得識別此 「 ICorDebugCode"表示的程式碼的版本 1 為基底的數目。</span><span class="sxs-lookup"><span data-stu-id="4074e-103">Gets the one-based number that identifies the version of the code that this "ICorDebugCode" represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4074e-104">語法</span><span class="sxs-lookup"><span data-stu-id="4074e-104">Syntax</span></span>  
  
```  
HRESULT GetVersionNumber (  
    [out] ULONG32    *nVersion  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4074e-105">參數</span><span class="sxs-lookup"><span data-stu-id="4074e-105">Parameters</span></span>  
 `nVersion`  
 <span data-ttu-id="4074e-106">[out]程式碼的版本號碼的指標。</span><span class="sxs-lookup"><span data-stu-id="4074e-106">[out] A pointer to the version number of the code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4074e-107">備註</span><span class="sxs-lookup"><span data-stu-id="4074e-107">Remarks</span></span>  
 <span data-ttu-id="4074e-108">版本號碼會遞增每個程式碼執行編輯後繼續 (EnC) 作業的時間。</span><span class="sxs-lookup"><span data-stu-id="4074e-108">The version number is incremented each time an edit-and-continue (EnC) operation is performed on the code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4074e-109">需求</span><span class="sxs-lookup"><span data-stu-id="4074e-109">Requirements</span></span>  
 <span data-ttu-id="4074e-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4074e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4074e-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4074e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4074e-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4074e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4074e-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4074e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4074e-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4074e-114">See Also</span></span>  
 

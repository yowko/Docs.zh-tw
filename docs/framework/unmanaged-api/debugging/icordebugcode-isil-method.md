---
title: ICorDebugCode::IsIL 方法
ms.date: 03/30/2017
api_name:
- ICorDebugCode.IsIL
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::IsIL
helpviewer_keywords:
- ICorDebugCode::IsIL method [.NET Framework debugging]
- IsIL method [.NET Framework debugging]
ms.assetid: 132ef8cc-d938-43f3-b8f2-e3b97c0ceb33
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ccebe01c853677f7c78731e757ef7a5f090d6919
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415187"
---
# <a name="icordebugcodeisil-method"></a><span data-ttu-id="29e5e-102">ICorDebugCode::IsIL 方法</span><span class="sxs-lookup"><span data-stu-id="29e5e-102">ICorDebugCode::IsIL Method</span></span>
<span data-ttu-id="29e5e-103">取得值，指出是否此"ICorDebugCode 」 表示已編譯的 Microsoft 中繼語言 (MSIL) 中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="29e5e-103">Gets a value that indicates whether this "ICorDebugCode" represents code that was compiled in Microsoft intermediate language (MSIL).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29e5e-104">語法</span><span class="sxs-lookup"><span data-stu-id="29e5e-104">Syntax</span></span>  
  
```  
HRESULT IsIL (  
    [out] BOOL       *pbIL  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="29e5e-105">參數</span><span class="sxs-lookup"><span data-stu-id="29e5e-105">Parameters</span></span>  
 `pbIL`  
 <span data-ttu-id="29e5e-106">[out]`true`如果這個`ICorDebugCode`代表已編譯的 MSIL 中; 否則程式碼`false`。</span><span class="sxs-lookup"><span data-stu-id="29e5e-106">[out] `true` if this `ICorDebugCode` represents code that was compiled in MSIL; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29e5e-107">需求</span><span class="sxs-lookup"><span data-stu-id="29e5e-107">Requirements</span></span>  
 <span data-ttu-id="29e5e-108">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="29e5e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29e5e-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="29e5e-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="29e5e-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29e5e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29e5e-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29e5e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29e5e-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29e5e-112">See Also</span></span>  
 

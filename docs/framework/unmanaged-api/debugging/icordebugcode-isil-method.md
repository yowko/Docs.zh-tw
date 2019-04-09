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
ms.openlocfilehash: a82606d90444c2d543065287780e42da4f8b4943
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59180683"
---
# <a name="icordebugcodeisil-method"></a><span data-ttu-id="d8882-102">ICorDebugCode::IsIL 方法</span><span class="sxs-lookup"><span data-stu-id="d8882-102">ICorDebugCode::IsIL Method</span></span>
<span data-ttu-id="d8882-103">取得值，指出是否此 「 ICorDebugCode"代表已編譯的 Microsoft intermediate language (MSIL) 程式碼。</span><span class="sxs-lookup"><span data-stu-id="d8882-103">Gets a value that indicates whether this "ICorDebugCode" represents code that was compiled in Microsoft intermediate language (MSIL).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8882-104">語法</span><span class="sxs-lookup"><span data-stu-id="d8882-104">Syntax</span></span>  
  
```  
HRESULT IsIL (  
    [out] BOOL       *pbIL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8882-105">參數</span><span class="sxs-lookup"><span data-stu-id="d8882-105">Parameters</span></span>  
 `pbIL`  
 <span data-ttu-id="d8882-106">[out]`true`如果這個`ICorDebugCode`表示 MSIL 中編譯; 否則程式碼`false`。</span><span class="sxs-lookup"><span data-stu-id="d8882-106">[out] `true` if this `ICorDebugCode` represents code that was compiled in MSIL; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8882-107">需求</span><span class="sxs-lookup"><span data-stu-id="d8882-107">Requirements</span></span>  
 <span data-ttu-id="d8882-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d8882-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8882-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d8882-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8882-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8882-110">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="d8882-111">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="d8882-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d8882-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8882-112">See also</span></span>

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
ms.openlocfilehash: 0a81f4a53954c559ab12e27bcf039b7b1a1804cc
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700787"
---
# <a name="icordebugcodeisil-method"></a><span data-ttu-id="6f373-102">ICorDebugCode::IsIL 方法</span><span class="sxs-lookup"><span data-stu-id="6f373-102">ICorDebugCode::IsIL Method</span></span>

<span data-ttu-id="6f373-103">取得值，指出這個 "ICorDebugCode" 是否代表以 Microsoft 中繼語言（MSIL）編譯的程式碼。</span><span class="sxs-lookup"><span data-stu-id="6f373-103">Gets a value that indicates whether this "ICorDebugCode" represents code that was compiled in Microsoft intermediate language (MSIL).</span></span>

## <a name="syntax"></a><span data-ttu-id="6f373-104">語法</span><span class="sxs-lookup"><span data-stu-id="6f373-104">Syntax</span></span>

```cpp
HRESULT IsIL (
    [out] BOOL       *pbIL
);
```

## <a name="parameters"></a><span data-ttu-id="6f373-105">參數</span><span class="sxs-lookup"><span data-stu-id="6f373-105">Parameters</span></span>
 `pbIL`  
 <span data-ttu-id="6f373-106">[out] `true`，如果這個 `ICorDebugCode` 代表以 MSIL 編譯的程式碼，則為，否則，`false`。</span><span class="sxs-lookup"><span data-stu-id="6f373-106">[out] `true` if this `ICorDebugCode` represents code that was compiled in MSIL; otherwise, `false`.</span></span>

## <a name="requirements"></a><span data-ttu-id="6f373-107">需求</span><span class="sxs-lookup"><span data-stu-id="6f373-107">Requirements</span></span>

 <span data-ttu-id="6f373-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6f373-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  

 <span data-ttu-id="6f373-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6f373-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  

 <span data-ttu-id="6f373-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6f373-110">**Library:** CorGuids.lib</span></span>  

 <span data-ttu-id="6f373-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f373-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
 

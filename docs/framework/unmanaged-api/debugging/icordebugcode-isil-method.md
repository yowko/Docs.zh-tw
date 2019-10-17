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
ms.openlocfilehash: 1b7cbadbd1494d5e4d1488dd12296f4f90890127
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395489"
---
# <a name="icordebugcodeisil-method"></a><span data-ttu-id="2d44e-102">ICorDebugCode::IsIL 方法</span><span class="sxs-lookup"><span data-stu-id="2d44e-102">ICorDebugCode::IsIL Method</span></span>

<span data-ttu-id="2d44e-103">取得值，指出這個 "ICorDebugCode" 是否代表以 Microsoft 中繼語言（MSIL）編譯的程式碼。</span><span class="sxs-lookup"><span data-stu-id="2d44e-103">Gets a value that indicates whether this "ICorDebugCode" represents code that was compiled in Microsoft intermediate language (MSIL).</span></span>

## <a name="syntax"></a><span data-ttu-id="2d44e-104">語法</span><span class="sxs-lookup"><span data-stu-id="2d44e-104">Syntax</span></span>

```cpp
HRESULT IsIL (
    [out] BOOL       *pbIL
);
```

## <a name="parameters"></a><span data-ttu-id="2d44e-105">參數</span><span class="sxs-lookup"><span data-stu-id="2d44e-105">Parameters</span></span>

`pbIL`  
<span data-ttu-id="2d44e-106">[out] `true`，如果這個 `ICorDebugCode` 代表以 MSIL 編譯的程式碼，則為，否則，`false`。</span><span class="sxs-lookup"><span data-stu-id="2d44e-106">[out] `true` if this `ICorDebugCode` represents code that was compiled in MSIL; otherwise, `false`.</span></span>

## <a name="requirements"></a><span data-ttu-id="2d44e-107">需求</span><span class="sxs-lookup"><span data-stu-id="2d44e-107">Requirements</span></span>

<span data-ttu-id="2d44e-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2d44e-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="2d44e-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2d44e-109">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="2d44e-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2d44e-110">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="2d44e-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d44e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

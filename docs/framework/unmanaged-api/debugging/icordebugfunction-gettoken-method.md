---
title: ICorDebugFunction::GetToken 方法
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetToken
helpviewer_keywords:
- ICorDebugFunction::GetToken method [.NET Framework debugging]
- GetToken method, ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: c6bbf479-062e-48e9-9c70-0f92e293e36a
topic_type:
- apiref
ms.openlocfilehash: 4229d567fc4ced5e3b78b390ced29fb9ea60f93b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137836"
---
# <a name="icordebugfunctiongettoken-method"></a><span data-ttu-id="c4361-102">ICorDebugFunction::GetToken 方法</span><span class="sxs-lookup"><span data-stu-id="c4361-102">ICorDebugFunction::GetToken Method</span></span>
<span data-ttu-id="c4361-103">取得此函式的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="c4361-103">Gets the metadata token for this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4361-104">語法</span><span class="sxs-lookup"><span data-stu-id="c4361-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken (  
    [out] mdMethodDef *pMethodDef  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4361-105">參數</span><span class="sxs-lookup"><span data-stu-id="c4361-105">Parameters</span></span>  
 `pMethodDef`  
 <span data-ttu-id="c4361-106">脫銷參考此函式中繼資料之 `mdMethodDef` token 的指標。</span><span class="sxs-lookup"><span data-stu-id="c4361-106">[out] A pointer to an `mdMethodDef` token that references the metadata for this function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4361-107">需求</span><span class="sxs-lookup"><span data-stu-id="c4361-107">Requirements</span></span>  
 <span data-ttu-id="c4361-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c4361-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4361-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c4361-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4361-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4361-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4361-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4361-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

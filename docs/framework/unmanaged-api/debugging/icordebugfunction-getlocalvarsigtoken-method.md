---
title: ICorDebugFunction::GetLocalVarSigToken 方法
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetLocalVarSigToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetLocalVarSigToken
helpviewer_keywords:
- ICorDebugFunction::GetLocalVarSigToken method [.NET Framework debugging]
- GetLocalVarSigToken method [.NET Framework debugging]
ms.assetid: 31e53494-bcc9-4981-91a4-f7e0f02cad48
topic_type:
- apiref
ms.openlocfilehash: c159a175ddd380015cc2dc21637c8b63fd3caea6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137887"
---
# <a name="icordebugfunctiongetlocalvarsigtoken-method"></a><span data-ttu-id="5cb6e-102">ICorDebugFunction::GetLocalVarSigToken 方法</span><span class="sxs-lookup"><span data-stu-id="5cb6e-102">ICorDebugFunction::GetLocalVarSigToken Method</span></span>
<span data-ttu-id="5cb6e-103">取得此 ICorDebugFunction 實例所表示之函式的區域變數簽章的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="5cb6e-103">Gets the metadata token for the local variable signature of the function that is represented by this ICorDebugFunction instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cb6e-104">語法</span><span class="sxs-lookup"><span data-stu-id="5cb6e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalVarSigToken (  
    [out] mdSignature *pmdSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5cb6e-105">參數</span><span class="sxs-lookup"><span data-stu-id="5cb6e-105">Parameters</span></span>  
 `pmdSig`  
 <span data-ttu-id="5cb6e-106">脫銷此函式的區域變數簽章之 `mdSignature` token 的指標，如果此函式沒有任何區域變數，則為 `mdSignatureNil`。</span><span class="sxs-lookup"><span data-stu-id="5cb6e-106">[out] A pointer to the `mdSignature` token for the local variable signature of this function, or `mdSignatureNil`, if this function has no local variables.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5cb6e-107">需求</span><span class="sxs-lookup"><span data-stu-id="5cb6e-107">Requirements</span></span>  
 <span data-ttu-id="5cb6e-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5cb6e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cb6e-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5cb6e-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5cb6e-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5cb6e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5cb6e-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5cb6e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

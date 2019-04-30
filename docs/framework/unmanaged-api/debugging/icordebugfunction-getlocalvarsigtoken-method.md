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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a682999c888a93cef94162a8179673c862dc43ce
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988711"
---
# <a name="icordebugfunctiongetlocalvarsigtoken-method"></a><span data-ttu-id="1b86e-102">ICorDebugFunction::GetLocalVarSigToken 方法</span><span class="sxs-lookup"><span data-stu-id="1b86e-102">ICorDebugFunction::GetLocalVarSigToken Method</span></span>
<span data-ttu-id="1b86e-103">取得區域變數簽章這個 ICorDebugFunction 執行個體所表示的函式的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="1b86e-103">Gets the metadata token for the local variable signature of the function that is represented by this ICorDebugFunction instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b86e-104">語法</span><span class="sxs-lookup"><span data-stu-id="1b86e-104">Syntax</span></span>  
  
```  
HRESULT GetLocalVarSigToken (  
    [out] mdSignature *pmdSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b86e-105">參數</span><span class="sxs-lookup"><span data-stu-id="1b86e-105">Parameters</span></span>  
 `pmdSig`  
 <span data-ttu-id="1b86e-106">[out]指標`mdSignature`本機變數的簽章，此函式的語彙基元或`mdSignatureNil`，如果此函式沒有任何區域變數。</span><span class="sxs-lookup"><span data-stu-id="1b86e-106">[out] A pointer to the `mdSignature` token for the local variable signature of this function, or `mdSignatureNil`, if this function has no local variables.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b86e-107">需求</span><span class="sxs-lookup"><span data-stu-id="1b86e-107">Requirements</span></span>  
 <span data-ttu-id="1b86e-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1b86e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b86e-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1b86e-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1b86e-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b86e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b86e-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b86e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

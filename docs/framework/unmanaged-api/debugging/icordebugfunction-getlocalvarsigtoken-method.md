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
ms.openlocfilehash: a923701b05f7d283c4fd464d470fb0c9243c1bd5
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213604"
---
# <a name="icordebugfunctiongetlocalvarsigtoken-method"></a><span data-ttu-id="4e86b-102">ICorDebugFunction::GetLocalVarSigToken 方法</span><span class="sxs-lookup"><span data-stu-id="4e86b-102">ICorDebugFunction::GetLocalVarSigToken Method</span></span>
<span data-ttu-id="4e86b-103">取得此 ICorDebugFunction 實例所表示之函式的區域變數簽章的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="4e86b-103">Gets the metadata token for the local variable signature of the function that is represented by this ICorDebugFunction instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e86b-104">語法</span><span class="sxs-lookup"><span data-stu-id="4e86b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalVarSigToken (  
    [out] mdSignature *pmdSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e86b-105">參數</span><span class="sxs-lookup"><span data-stu-id="4e86b-105">Parameters</span></span>  
 `pmdSig`  
 <span data-ttu-id="4e86b-106">脫銷此函式之區域變數簽章的 `mdSignature` token 指標，如果此函式 `mdSignatureNil` 沒有任何區域變數，則為。</span><span class="sxs-lookup"><span data-stu-id="4e86b-106">[out] A pointer to the `mdSignature` token for the local variable signature of this function, or `mdSignatureNil`, if this function has no local variables.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e86b-107">需求</span><span class="sxs-lookup"><span data-stu-id="4e86b-107">Requirements</span></span>  
 <span data-ttu-id="4e86b-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4e86b-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e86b-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4e86b-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4e86b-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4e86b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e86b-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e86b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

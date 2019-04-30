---
title: ICorDebugFrame::GetFunctionToken 方法
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetFunctionToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetFunctionToken
helpviewer_keywords:
- ICorDebugFrame::GetFunctionToken method [.NET Framework debugging]
- GetFunctionToken method [.NET Framework debugging]
ms.assetid: a46925b3-3bf8-404f-9f30-a86ae41032c1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 156c16f73916d2b4efa1c1b3541a772fb43dd470
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988763"
---
# <a name="icordebugframegetfunctiontoken-method"></a><span data-ttu-id="fb19a-102">ICorDebugFrame::GetFunctionToken 方法</span><span class="sxs-lookup"><span data-stu-id="fb19a-102">ICorDebugFrame::GetFunctionToken Method</span></span>
<span data-ttu-id="fb19a-103">取得包含此堆疊框架相關聯的程式碼的函式的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="fb19a-103">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb19a-104">語法</span><span class="sxs-lookup"><span data-stu-id="fb19a-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionToken (  
    [out] mdMethodDef        *pToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb19a-105">參數</span><span class="sxs-lookup"><span data-stu-id="fb19a-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="fb19a-106">[out]指標`mdMethodDef`語彙基元所參考的函式的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="fb19a-106">[out] A pointer to an `mdMethodDef` token that references the metadata for the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb19a-107">需求</span><span class="sxs-lookup"><span data-stu-id="fb19a-107">Requirements</span></span>  
 <span data-ttu-id="fb19a-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fb19a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb19a-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fb19a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fb19a-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb19a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb19a-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb19a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

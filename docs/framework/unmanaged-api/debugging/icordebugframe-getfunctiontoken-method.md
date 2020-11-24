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
ms.openlocfilehash: 3430c5062bd5633e1178226974b7358783192e51
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675980"
---
# <a name="icordebugframegetfunctiontoken-method"></a><span data-ttu-id="8b904-102">ICorDebugFrame::GetFunctionToken 方法</span><span class="sxs-lookup"><span data-stu-id="8b904-102">ICorDebugFrame::GetFunctionToken Method</span></span>

<span data-ttu-id="8b904-103">取得函式的元資料標記，該函式包含與這個堆疊框架相關聯的程式碼。</span><span class="sxs-lookup"><span data-stu-id="8b904-103">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b904-104">語法</span><span class="sxs-lookup"><span data-stu-id="8b904-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionToken (  
    [out] mdMethodDef        *pToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b904-105">參數</span><span class="sxs-lookup"><span data-stu-id="8b904-105">Parameters</span></span>  

 `pToken`  
 <span data-ttu-id="8b904-106">擴展參考函式 `mdMethodDef` 中繼資料的權杖指標。</span><span class="sxs-lookup"><span data-stu-id="8b904-106">[out] A pointer to an `mdMethodDef` token that references the metadata for the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b904-107">需求</span><span class="sxs-lookup"><span data-stu-id="8b904-107">Requirements</span></span>  

 <span data-ttu-id="8b904-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8b904-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b904-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8b904-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8b904-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b904-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b904-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b904-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

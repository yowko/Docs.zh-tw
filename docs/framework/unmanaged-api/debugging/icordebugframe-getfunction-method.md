---
title: ICorDebugFrame::GetFunction 方法
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetFunction
helpviewer_keywords:
- GetFunction method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetFunction method [.NET Framework debugging]
ms.assetid: 879d2311-0ff1-4616-a8b3-959ea5868b2e
topic_type:
- apiref
ms.openlocfilehash: 39175e338e4fd98dd4af1325138da732ed81c764
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137913"
---
# <a name="icordebugframegetfunction-method"></a><span data-ttu-id="40763-102">ICorDebugFrame::GetFunction 方法</span><span class="sxs-lookup"><span data-stu-id="40763-102">ICorDebugFrame::GetFunction Method</span></span>
<span data-ttu-id="40763-103">取得包含與此堆疊框架相關聯之程式碼的函式。</span><span class="sxs-lookup"><span data-stu-id="40763-103">Gets the function that contains the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40763-104">語法</span><span class="sxs-lookup"><span data-stu-id="40763-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunction (  
    [out] ICorDebugFunction  **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40763-105">參數</span><span class="sxs-lookup"><span data-stu-id="40763-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="40763-106">脫銷ICorDebugFunction 物件位址的指標，代表包含與此堆疊框架相關聯之程式碼的函式。</span><span class="sxs-lookup"><span data-stu-id="40763-106">[out] A pointer to the address of an ICorDebugFunction object that represents the function containing the code associated with this stack frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40763-107">備註</span><span class="sxs-lookup"><span data-stu-id="40763-107">Remarks</span></span>  
 <span data-ttu-id="40763-108">如果框架未與任何特定的函式相關聯，`GetFunction` 方法可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="40763-108">The `GetFunction` method may fail if the frame is not associated with any particular function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40763-109">需求</span><span class="sxs-lookup"><span data-stu-id="40763-109">Requirements</span></span>  
 <span data-ttu-id="40763-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="40763-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40763-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="40763-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="40763-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="40763-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40763-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40763-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

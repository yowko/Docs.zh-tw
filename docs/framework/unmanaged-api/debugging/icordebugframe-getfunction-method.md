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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a48396f8ef668cfe7755b2718180317b465793b6
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57475277"
---
# <a name="icordebugframegetfunction-method"></a><span data-ttu-id="de40d-102">ICorDebugFrame::GetFunction 方法</span><span class="sxs-lookup"><span data-stu-id="de40d-102">ICorDebugFrame::GetFunction Method</span></span>
<span data-ttu-id="de40d-103">取得包含此堆疊框架相關聯的程式碼的函式。</span><span class="sxs-lookup"><span data-stu-id="de40d-103">Gets the function that contains the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de40d-104">語法</span><span class="sxs-lookup"><span data-stu-id="de40d-104">Syntax</span></span>  
  
```  
HRESULT GetFunction (  
    [out] ICorDebugFunction  **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="de40d-105">參數</span><span class="sxs-lookup"><span data-stu-id="de40d-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="de40d-106">[out]ICorDebugFunction 物件，表示包含此堆疊框架相關聯的程式碼的函式的位址指標。</span><span class="sxs-lookup"><span data-stu-id="de40d-106">[out] A pointer to the address of an ICorDebugFunction object that represents the function containing the code associated with this stack frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de40d-107">備註</span><span class="sxs-lookup"><span data-stu-id="de40d-107">Remarks</span></span>  
 <span data-ttu-id="de40d-108">`GetFunction`如果框架不是任何特定的函式相關聯，方法可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="de40d-108">The `GetFunction` method may fail if the frame is not associated with any particular function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de40d-109">需求</span><span class="sxs-lookup"><span data-stu-id="de40d-109">Requirements</span></span>  
 <span data-ttu-id="de40d-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="de40d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de40d-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="de40d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="de40d-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="de40d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="de40d-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de40d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

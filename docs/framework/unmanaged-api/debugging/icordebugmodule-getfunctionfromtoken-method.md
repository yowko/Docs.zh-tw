---
title: ICorDebugModule::GetFunctionFromToken 方法
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetFunctionFromToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetFunctionFromToken
helpviewer_keywords:
- GetFunctionFromToken method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetFunctionFromToken method [.NET Framework debugging]
ms.assetid: 6fe12194-4ef7-43c1-9570-ade35ccf127a
topic_type:
- apiref
ms.openlocfilehash: a33b6ff308f3444496e5a1cb2e04f28e80305db5
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212575"
---
# <a name="icordebugmodulegetfunctionfromtoken-method"></a><span data-ttu-id="0ba92-102">ICorDebugModule::GetFunctionFromToken 方法</span><span class="sxs-lookup"><span data-stu-id="0ba92-102">ICorDebugModule::GetFunctionFromToken Method</span></span>
<span data-ttu-id="0ba92-103">取得元資料標記所指定的函式。</span><span class="sxs-lookup"><span data-stu-id="0ba92-103">Gets the function that is specified by the metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ba92-104">語法</span><span class="sxs-lookup"><span data-stu-id="0ba92-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromToken(  
    [in] mdMethodDef methodDef,  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ba92-105">參數</span><span class="sxs-lookup"><span data-stu-id="0ba92-105">Parameters</span></span>  
 `methodDef`  
 <span data-ttu-id="0ba92-106">在`mdMethodDef`參考函數中繼資料的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="0ba92-106">[in] A `mdMethodDef` metadata token that references the function's metadata.</span></span>  
  
 `ppFunction`  
 <span data-ttu-id="0ba92-107">脫銷代表函式之 ICorDebugFunction 介面物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="0ba92-107">[out] A pointer to the address of a ICorDebugFunction interface object that represents the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ba92-108">備註</span><span class="sxs-lookup"><span data-stu-id="0ba92-108">Remarks</span></span>  
 <span data-ttu-id="0ba92-109">`GetFunctionFromToken`如果傳入的值 `methodDef` 未參考 Microsoft 中繼語言（MSIL）方法，此方法會傳回 CORDBG_E_FUNCTION_NOT_IL HRESULT。</span><span class="sxs-lookup"><span data-stu-id="0ba92-109">The `GetFunctionFromToken` method returns a CORDBG_E_FUNCTION_NOT_IL HRESULT if the value passed in `methodDef` does not refer to a Microsoft intermediate language (MSIL) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ba92-110">需求</span><span class="sxs-lookup"><span data-stu-id="0ba92-110">Requirements</span></span>  
 <span data-ttu-id="0ba92-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0ba92-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ba92-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0ba92-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0ba92-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0ba92-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0ba92-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ba92-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

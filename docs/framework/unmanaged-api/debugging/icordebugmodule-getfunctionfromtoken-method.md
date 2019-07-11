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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 547986633172d6f5e6549ad2048833dc9fb0cef3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763476"
---
# <a name="icordebugmodulegetfunctionfromtoken-method"></a><span data-ttu-id="a6499-102">ICorDebugModule::GetFunctionFromToken 方法</span><span class="sxs-lookup"><span data-stu-id="a6499-102">ICorDebugModule::GetFunctionFromToken Method</span></span>
<span data-ttu-id="a6499-103">取得指定中繼資料語彙基元的函式。</span><span class="sxs-lookup"><span data-stu-id="a6499-103">Gets the function that is specified by the metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6499-104">語法</span><span class="sxs-lookup"><span data-stu-id="a6499-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromToken(  
    [in] mdMethodDef methodDef,  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6499-105">參數</span><span class="sxs-lookup"><span data-stu-id="a6499-105">Parameters</span></span>  
 `methodDef`  
 <span data-ttu-id="a6499-106">[in]A`mdMethodDef`參考函式的中繼資料的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="a6499-106">[in] A `mdMethodDef` metadata token that references the function's metadata.</span></span>  
  
 `ppFunction`  
 <span data-ttu-id="a6499-107">[out]ICorDebugFunction 介面物件，表示函式的位址指標。</span><span class="sxs-lookup"><span data-stu-id="a6499-107">[out] A pointer to the address of a ICorDebugFunction interface object that represents the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6499-108">備註</span><span class="sxs-lookup"><span data-stu-id="a6499-108">Remarks</span></span>  
 <span data-ttu-id="a6499-109">`GetFunctionFromToken`如果傳入的值，方法會傳回 CORDBG_E_FUNCTION_NOT_IL HRESULT`methodDef`不是指 Microsoft intermediate language (MSIL) 方法。</span><span class="sxs-lookup"><span data-stu-id="a6499-109">The `GetFunctionFromToken` method returns a CORDBG_E_FUNCTION_NOT_IL HRESULT if the value passed in `methodDef` does not refer to a Microsoft intermediate language (MSIL) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6499-110">需求</span><span class="sxs-lookup"><span data-stu-id="a6499-110">Requirements</span></span>  
 <span data-ttu-id="a6499-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a6499-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6499-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a6499-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a6499-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a6499-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6499-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6499-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
